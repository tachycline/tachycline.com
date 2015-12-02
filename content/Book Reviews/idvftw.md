Title: Review: Interactive Data Visualization for the Web, by Scott Murray
Date: 2013-12-11
Category: Book Reviews
Tags: reviews
Slug: interactive_data_viz
Author: Cavendish McKay
Summary: A reasonable introduction to D3, targeted at the non-programmer


My work tends to be quantitative, and in python, and so up to this point visualization for me has meant matplotlib.  On the other hand, I’m always blown away by the beautiful and interactive plots people are able to put together with D3. So, when I signed up for O’Reilly’s reviewer program, and saw that there was a D3 book among the available books, I put it on my list.  After reading it, I’m glad I did.

The book was a quick and easy read. Murray’s style is informal and a little breezy in places, but doesn’t get in the way of communicating the content. I got through it in two sittings, which seems like way too little time for a technical book, but in this case, the book is neither too technical, nor particularly dense.  That’s by design. Murray chose to pitch the book to people with no prior web or programming experience, and that heavily influenced what he was able to cover.

I have to acknowledge at this point that I’m not really the target audience for the book.  It’s true that I don’t consider myself a strong front-end person, but I’ve fiddled with websites since I was first introduced to the web in about 1995.  On top of that, I think like a programmer.  As a result, the first third to half of the book was full of stuff that I either knew already, or could have found trivially with google. But, for people who don’t have any background, the chapter that covers how html and css go together to make a web page (for example) could be useful.

I feel like Murray was able to accomplish his stated goal: cover the core of D3.js, without getting too bogged down with details or advanced features. I did feel by the end that I could sit down and at least rough out a visualization in D3, and that I’ll be able to extract the necessary information from the API docs and other online resources to make it look and behave how I want.  I recognize, though, that any nontrivial visualization I want to make is still going to take a significant amount of learning.  The core concepts are there, and I’ve been exposed to some of the available tools, but I’m not an expert.  And that’s okay.

There are a few choices the author made that I would have made differently. One in particular is related to group elements in his svg examples.  Nearly all of his examples involve manipulating a simple bar chart.  Over the course of a couple of chapters, Murray teaches the reader how to add and remove data elements, and how to add some activity with mouseovers and clicks.  The bars have text labels attached to them, In nearly every case, when he adds some functionality to the bars in the bar chart, the labels end up doing something different (and undesirable).  He then leaves “fixing the labels” as an exercise for the reader.

I’m all in favor of giving specific exercises. In fact, I think the book would benefit from more of them. This particular set of activities, though, are kind of useless, since they wouldn’t be necessary if the bars and labels were grouped together in a sane way from the beginning.  Murray mentions the g element and indicates that one of its main advantages is that you can transform a whole set of elements at once. Coincidentally, that would make all of the problems with the labels in the examples go away *for free*.  Additionally, doing so would set a good example in terms of writing code that’s easier to understand and maintain.

Since this book is pitched at beginners, I can imagine (though I don’t know for sure) that Murray avoided this approach because he thought it might be too abstract. He does make use of svg group elements in putting axes on his scatter plot (the other plot type that gets significant coverage in the book) but he doesn’t include an example in which he groups display elements that are communicate the data (as opposed to annotations).

This all leads to the big question: would I recommend this book?  For me, only a subset of the content in the book was useful, and my guess is that will be true of just about anyone who is interesting in learning how to use D3.  I mean, how many people in that category don’t know the basic structure of a web page, or the difference between CSS and JavaScript? And to be brutally honest, the absolute web novice who picks up this book hoping to come out the other end able to produce visualizations worthy of the New York Times is fooling him or herself.

On the other hand, if you’re willing to ignore or skim the fluff at the beginning, and you’re looking for a gentle introduction to D3 that still has enough meat to it to take you from completely uninitiated to functionally literate, this could be the book for you.

