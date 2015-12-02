Title: Review: Python for Data Analysis, by Wes McKinney
Date: 2013-12-18
Category: Book Reviews
Tags: reviews, pandas
Slug: python_data_analysis
Author: Cavendish McKay
Summary: Data wrangling with pandas

I’ve finished my first pass through Wes McKinney’s excellent book Python for Data Analysis, and have a few comments about it. I say it’s my first pass, because I’ll definitely be revisiting this text. It’s written in a way that it would be impossible (or at least very difficult) for one to extract all there is to learn from it in one reading, and it’s organized such that it will serve as a worthwhile reference.

I had the good fortune to participate in a tutorial session on pandas that Wes McKinney ran at the 2012 SciPy conference, and I was completely blown away by the capabilities he demonstrated. That was my first exposure to pandas (and in fact, that conference was my first really immersive exposure to the whole scientific python stack). The conference was in July, and this book came out in October, so there was a certain amount of foreshadowing of the book’s contents in the tutorial session. I regret that it has taken me this long to get around to reading it.

It’s important to note that while the title of the book is “Python for Data Analysis,” it’s really a book about pandas. That isn’t a criticism, by any means. pandas is a rich enough tool to merit a book (or more) written about it, and there isn’t anyone more qualified than Mr. McKinney to write such a book. There is, however, a danger in writing a book about a specific tool (and especially one that is under active development), and that is that the subject is something of a moving target. McKinney does a good job of pointing out a few specific parts that were likely to change rapidly after the book was published, so the attentive reader can refer to the current pandas documentation instead, but that’s a little bit of a hassle. Unavoidable, I think, but a little bit of a hassle all the same.

I loved the fact that the author introduced some real data sets and showed how one might perform some specific operations on them. Some of the topics covered are abstract enough that they would be very difficult to follow without having a concrete and relevant example. Having said that, there were a number of cases in which the data was generated randomly, with nonsensical column names, and it wasn’t always easy to track what was going on.

The book’s formatting also got in the way at times. I read the book both on my mac and on my iPad, in both the pdf and epub formats. The pdf files looked great, but the column width for the epub formats was occasionally narrow enough that the tables of data wrapped onto the next line and were very hard to read. This was especially problematic when reading in iBooks on my mac, or in landscape mode on my iPad. Making the font smaller helped.

In general, I thought the level of the text was pitched pretty well. If you’re an absolute novice, this is probably not the book for you; the learning curve will probably be steep enough to be frustrating. Otherwise, it’s likely there’s something in here that you can learn and apply.

And that’s the real catch. Mastering this kind of material requires some time and practice. Or, more realistically, some time and lots of practice. You won’t get much out of this book just by reading it. You’ll need to sit down and work through some data analysis projects, using the book as a reference for the various tasks you have to undertake to turn your data into a meaningful story. Since every data set is different, the exact features of pandas you need to extract meaning from your data will vary. And, since every project has its own set of questions, the amount and kind of processing and analysis required will vary greatly.

It’s clear from reading this book that pandas handles the data munging aspects of data science very well, and makes calculations on data pretty easy. McKinney does not touch at all on machine learning or natural language processing in this book, but wrangling your data into a dataframe before applying your clustering algorithm or sentiment analysis to it can’t hurt.

Would I recommend this book? Yes, without reservations. I think it belongs on the shelf (virtual or otherwise) of anyone who is serious about using python to store, process, or visualize data.
