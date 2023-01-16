---
aliases:
- /2021/06/05/DoNotHarm
date: '2021-06-05'
layout: post
readtime: true
title: Do no harm - COC for programmers

---

[![Doctor Attacked](https://user-images.githubusercontent.com/24592806/120882009-a53e1980-c5f2-11eb-8b61-24ff9cd4bd48.png)](https://youtu.be/K6yrsdGP0bA)

The above video shows how a Junior Doctor has been attacked in Assam, India. It's very unfortunate to see doctors,
attacked like this and we have seen even things worse than this happen to doctors. Generally most of doctors in
the critical care units who work are usually Junior Doctors, who have to work long hours to get the initial experience. 
Yet these Junior doctors are usually at the receiving ends of the blows from relatives of deceased people in most of the cases.

When I watched this video, I was remembered about the oath doctors take and *Uncle Bob's Clean Coder book*. The oath is simple:

**DO NO HARM**

The human body is too complex to understand in it’s entirety and take years of expertise to specialize in something, but doctors
still take an oath to do no harm. New viruses can comes with lot of new novelty like Nipah, Covid-19, yet doctors still adhere to there oath of doing no harm.

I am sharing why Uncle Bobs suggest coders like you and me to take this oath of `DO NO HARM`. Uncle Bob is
sharing the story of one of his software failures:


>On one occasion I shipped a new release to several dozen customers. “Ship” is exactly the right word. I wrote the software onto tapes and shipped those tapes to the customers. The customers loaded the tapes and then rebooted the systems. 

>The new release fixed some minor defects and added a new feature that our customers had been demanding. We had told them we would provide that new feature by a certain date. I barely managed to overnight the tapes so that they’d arrive on the promised date. Two days later I got a call from our field service manager, Tom. He told me that several customers had complained that the “nightly routine” had not completed, and that they had gotten no reports. My heart sank because in order to ship the software on time, I had neglected to test the routine. I had tested much of the other functionality of the system, but testing the routine took hours, and I needed to ship the software. None of the bug fixes were in the routine code, so I felt safe.

>Losing a nightly report was a big deal. It meant that the repairmen had less to do and would be overbooked later. It meant that some customers might notice a fault and complain. Losing a night’s worth of data is enough to get a service area manager to call Tom and lambaste him. I fired up our lab system, loaded the new software, and then started a routine. It took several hours but then it aborted. The routine failed. Had I run this test before I shipped, the service areas wouldn’t have lost data, and the service area managers wouldn’t be roasting Tom right now. I phoned Tom to tell him that I could duplicate the problem. He told me that most of the other customers had called him with the same complaint. Then he asked me when I could fix it. I told him I didn’t know, but that I was working on it.

>In the meantime I told him that the customers should go back to the old software. He was angry at me saying that this was a double blow to the customers since they’d lost a whole night’s worth of data and couldn’t use the new feature they were promised. The bug was hard to find, and testing took several hours. The first fix didn’t work. Nor did the second. It took me several tries, and therefore several days, to figure out what had gone wrong. The whole time, Tom was calling me every few hours asking me when I’d have this fixed. He also made sure I knew about the earfuls he was getting from the service area managers, and just how embarrassing it was for him to tell them to put the old tapes back in.

>In the end, I found the defect, shipped the new tapes, and everything went back to normal. Tom, who was not my boss, cooled down and we put the whole episode behind us. My boss came to me when it was over and said, “I bet you aren’t going to do that again.” I agreed.

>Upon reflection I realized that shipping without testing the routine had been irresponsible. The reason I neglected the test was so I could say I had shipped on time. It was about me saving face. I had not been concerned about the customer, nor about my employer. I had only been concerned about my own reputation. I should have taken responsibility early and told Tom that the tests weren’t complete and that I was not prepared to ship the software on time. That would have been hard, and Tom would have been upset. But no customers would have lost data, and no service managers would have called.


**Now Uncle Bob says why we should take this simple oath as coders:**

![image](https://user-images.githubusercontent.com/24592806/120883409-99565580-c5fa-11eb-91e2-d185d5b4535b.png)


## Do No Harm

>So how do we take responsibility? There are some principles. Drawing from the Hippocratic oath may seem arrogant, but what better source is there? And, indeed, doesn’t it make sense that the first responsibility, and first goal, of an aspiring professional is to use his or her powers for good? What harm can a software developer do? From a purely software point of view, he or she can do harm to both the function and structure of the software. We’ll explore how to avoid doing just that.

### Do No Harm to Function
>Clearly, we want our software to work. Indeed, most of us are programmers today because we got something to work once and we want that feeling again. But we aren’t the only ones who want the software to work. Our customers and employers want it to work too. Indeed, they are paying us to create software that works just the way they want it to. We harm the function of our software when we create bugs. Therefore, in order to be professional, we must not create bugs. “But wait!” I hear you say. “That’s not reasonable. Software is too complex to create without bugs.

>Of course you are right. Software is too complex to create without bugs. Unfortunately that doesn’t let you off the hook. The human body is too complex to understand in it’s entirety, but doctors still take an oath to do no harm. If they don’t take themselves off a hook like that, how can we? “Are you telling us we must be perfect?” Do I hear you object? No, I’m telling you that you must be responsible for your imperfections. The fact that bugs will certainly occur in your code does not mean you aren’t responsible for them. The fact that the task to write perfect software is virtually impossible does not mean you aren’t responsible for the imperfection. It is the lot of a professional to be accountable for errors even though errors are virtually certain. So, my aspiring professional, the first thing you must practice is apologizing. Apologies are necessary, but insufficient. You cannot simply keep making the same errors over and over. As you mature in your profession, your error rate should rapidly decrease towards the asymptote of zero. It won’t ever get to zero, but it is your responsibility to get as close as possible to it.


`:wq`
