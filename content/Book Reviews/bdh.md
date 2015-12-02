Title: Review: The Bad Data Handbook, by Q. Ethan McCallum
Date: 2014-1-29
Category: Book Reviews
Tags: reviews, data
Slug: bad_data_handbook
Author: Cavendish McKay
Summary: (Some) good approaches to bad data

Tolstoy wrote: “Happy families are all alike; every unhappy family is unhappy in its own way.” That’s kind of the case with data, as well. Clean, well-behaved data is all alike, but each piece of bad data is bad in its own way. That’s the situation that the Bad Data Handbook, by Q. Ethan McCallum (published by O’Reilly) tries to address.

Partly because bad data can be bad in so many different ways, the book is kind of a mixed bag. Each chapter is written by a different data professional, with a different set of experiences and perspective. The result is a very broad look at how one’s assumptions about data can break down, and how one might go about recovering from those broken assumptions. On the other hand, each chapter reads more like an individual essay than like a part of a larger whole. Such is the difficulty with books that have more than one author.

There are some excellent nuggets of wisdom in this book, but you have to dig for them. Chapter 5, (Re)Organizing the Web’s Data, for example, suggests that you always cache a local copy of websites you’re scraping, for two reasons: first, it reduces load, and second, it allows you to keep track of changes to the source material. I’ve done a bit of web scraping, and it’s very true that when you’re debugging the data extraction part of a scraper, you end up hitting the site repeatedly (especially if there are unexpected edge cases you need to work out). Storing a local copy of each page makes a lot of sense, but it didn’t occur to me. One potential downside is that if the pages are generated from a database, and include a lot of boilerplate, the size of the data you’re storing can get large.

Chapter 7, Will the Bad Data Please Stand Up? presents three anecdotes to communicate the fact that often when we think our data is bad, it’s actually our thinking, and not the data, that has the problem. The underlying theme is that trying to understand the data (especially when it is unexpected, or “bad”) can lead to questions that are interesting and useful, but not answerable from the data itself.

Chapter 12, “When Databases Attack: A Guide for When to Stick to Files” points to (and tries to address) a weakness that many of us have for whatever the new hotness is, tool wise. Knowing enough about a particular tool to get a project running does not mean that you know enough about it to decide if that tool is really the appropriate one of the job. Of course, the ability to make those kinds of decisions comes from experience, and experience often comes from making the wrong decisions, so this pitfall is unavoidable, to some degree. But, it’s worth putting the question out there: is this the right tool for this job? Was the tool designed for a use case that’s similar enough to what I’m doing that I can make it work well without too much hassle? And, do the performance tradeoffs required by this tool help me, or hurt me in this analysis?

There are, of course, others bits of wisdom in this book; I just picked three representative slices. Each reader will have a different background and different needs, and will therefore find different parts of the book useful. And, I suppose that’s the appeal of something so broadly written. There’s a hope that there’s at least a part of it that could be useful to any reader.

I think the book is worth having on the shelf, but I also think it needs to be read intelligently: study the parts that are useful to you, and skim or skip the parts that aren’t.

