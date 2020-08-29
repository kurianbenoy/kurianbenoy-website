---
title: Making Cartoonizer web-app
type: post
author: kurianbenoy
---

// how toonit was created, why it's being created, talk about our team


// flask end point exposal
// share snippets of code

About 1 month back, Bhavesh Bhatt created [a youtube video showing how to cartoonize
images](https://www.youtube.com/watch?v=eTMGoXgq6uM) which was based on Tensorflow implementation of CVPR 2020 paper:
"Learning to Cartoonize using white-box Cartoon Representations. I went ahead and tried the code snippet immediately 
and it did give amazing results. I discussed about the idea of making a App which renders on top of it with my friend
Jimmy as a side project , and he was  hooked on it. During this time, my friend Francis used to called me occasionally
to help him with his placement preparation. The thing about Francis is if you have a interview tommorrow which requires
you to learn some software like Adobe XD immediately, he could do it within a day. I reached out to him whether he was
interested, and he was relecuant not to join the team first, because he felt his skills were not that great. If you are
a beginner this is something so commonly seen. Please don't miss out your opportunities like this.

If you are checking out Bhavesh video, you will realise to do inference. You just need to run just 1 file in test_code
called `cartoonize.py`, for running inference of your code. And if you are adding a new image, you need to add your
images in the folder `test_images`. Run the command:

```
python3 cartoonize.py
```

Cartoonized images could be found on the adjacent folder called `cartoonized_images`.

Let's call the boiler code which is the cartoonize.py:

```
import os
import cv2
import numpy as np
import tensorflow as tf
import network
import guided_filter

def resize_crop(image):
    h, w, c = np.shape(image)
    if min(h, w) > 720:
        if h > w:
            h, w = int(720 * h / w), 720
        else:
            h, w = 720, int(720 * w / h)
    image = cv2.resize(image, (w, h), interpolation=cv2.INTER_AREA)
    h, w = (h // 8) * 8, (w // 8) * 8
    image = image[:h, :w, :]
    return image


def cartoonize(img_name, load_folder, save_folder, model_path):
    input_photo = tf.placeholder(tf.float32, [1, None, None, 3])
    network_out = network.unet_generator(input_photo)
    final_out = guided_filter.guided_filter(input_photo, network_out, r=1, eps=5e-3)

    all_vars = tf.trainable_variables()
    gene_vars = [var for var in all_vars if "generator" in var.name]
    saver = tf.train.Saver(var_list=gene_vars)

    config = tf.ConfigProto()
    config.gpu_options.allow_growth = True
    sess = tf.Session(config=config)

    sess.run(tf.global_variables_initializer())
    saver.restore(sess, tf.train.latest_checkpoint(model_path))
    name_list = os.listdir(load_folder)
    load_path = os.path.join(load_folder, img_name)
    print(load_path)
    save_path = os.path.join(save_folder, img_name)
    image = cv2.imread(load_path)
    image = resize_crop(image)
    batch_image = image.astype(np.float32) / 127.5 - 1
    batch_image = np.expand_dims(batch_image, axis=0)
    output = sess.run(final_out, feed_dict={input_photo: batch_image})
    output = (np.squeeze(output) + 1) * 127.5
    output = np.clip(output, 0, 255).astype(np.uint8)
    cv2.imwrite(save_path, output)
```

## Building Flask(app)

One way is to build a simple Flask app. Flask makes it easy to quickly create web applications. I won’t go into the details of Flask in this post—you can find out more here.

Writing routes(ie URLS)

```
@app.route("/", methods=["GET", "POST"])
def home():
    return render_template("index_toonit.html")


@app.route("/upload", methods=["POST"])
def upload():
    if request.method == "POST":
        # read the POST request input
        image_file = request.files["image"]
        if image_file:
            print(image_file)
            image_location = os.path.join(UPLOAD_FOLDER, image_file.filename)
            color_location = os.path.join(save_folder, image_file.filename)
            image_file.save(image_location)
            img_name = image_file.filename
            cartoonize(img_name, UPLOAD_FOLDER, save_folder, model_path)
            return render_template("result.html", color_loc=img_name)

```

## Frontend

You can check the code in github it's too difficult to paste everything as a code snippet


Next up, I will talk one under mentioned aspect of using Open source projects. You always need to mention the exact
license you will be using, and be sure to comply on what they are using. 

If you are using a project with MIT License, there is not to worry further about it.

Yet the project, was being licensed under [CC BY-NC-SA
4.0](https://creativecommons.org/licenses/by-nc-sa/4.0/legalcode), a very tricky license in my opinion. Bascially
licenses like Creative commons are used for art works, which is a original piece of work. It's not a software license
such and such. If you look at the terms, if you are following this license some of the salient features are:

- be non-commercial
- share-alike everything. (Not sure, whether it's meaning you can't modify the code
- Even further work on top of this, should use the same software license
