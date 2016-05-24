Title: How much data is enough?
Date: 2016-05-23
Category: Business
Tags: Predictive Analytics, Data
Slug: enough
Author: Cavendish McKay
Summary: How much data do you really need for predictive analytics?

I was having a conversation with a potential client the other day, and he commented, "I'm not sure we have enough data, or the right kind of data, to do good predictive analytics." For companies just beginning the journey into using their data effectively, this is a common concern, but in most cases it doesn't need to be.

For the past few years, **Big Data** has been increasing in hype and buzzword power. And, while it's true that more data is generally better, it's emphatically *not* true that your data needs to be "Big" to be useful. In fact, if your data really is "Big", it leads to a number of scaling-related headaches most people would prefer not to have to deal with.<sup id="a1">[1](#f1)</sup> So, let's accept for the moment that your data isn't (and needn't be) "Big". This still doesn't really answer the question, but it is at least a step in the right direction.

## Samples vs. Features
Before digging in to the meat of the question, we have to get a little bit of terminology straight. Most business data is multi-dimensional, but can generally be thought of in terms of two dimensions: the number of features and the number of samples. Thinking in this way, the *samples* are the individual measurements (customers, quotes, reviews, etc.) and the *features* are the quantities measured in each measurement (the collection of options, price, and relevant customer information in a particular quote, for example). If your data is collected in a spreadsheet or database, the samples generally correspond to rows, and the features generally correspond to columns.

Thought of in this way, the question of *how much* data is more or less a question about the number of *samples*, and the question of *what kind* of data is more or less a question about *features*. There is, of course, some overlap; a nonrepresentative collection of samples will lead to incorrect conclusions, and it's possible to have too few features to get the insight you're seeking. In most cases, though, we can treat the two questions separately.

## How much data is enough (or, how many samples)? 
Perhaps a better way to phrase this question is, "What's the smallest amount of data I can get away with using?" The only sensible answer to the question phrased in that way is another question: "How much uncertainty can you tolerate?" Since all methods used for predictive analytics are fundamentally statistical in nature, adding more data simply reduces the uncertainty in your model. Of course, it's possible to have so little data that the model you're using is meaningless--you can't build a classifier that sorts things into 10 categories if you only have 3 measurements, for example. At some point, though, the reduction in uncertainty you get from adding more data isn't worth the effort; it isn't going to change your decision making process.

The more practical answer is: start small, and increase until you're satisfied. At some point, increasing the number of samples won't change the results enough to matter. For this to work for you, you need to have dependable measures of how your model is performing (or, in other words, your degree of uncertainty), but that's the topic of another essay.

## What kind of data do we need (or, how many/which features)?
This question is, in many ways, more interesting than the last one. It's also harder to answer. It's where the "Domain expertise" section of the [Data Science Venn Diagram](http://www.anlytcs.com/2014/01/data-science-venn-diagram-v20.html) <sup id="a2">[2](#f2)</sup> comes into play. An ideal collection of features would consist of features that are:
* strongly correlated with whatever it is you're trying to predict,
* more or less equal in magnitude, and
* relatively independent of each other.

If you're especially lucky, they'll also be complete, in that they explain all of the variations in whatever you're trying to predict.  We don't live in an ideal world, so getting an ideal set of features is relatively rare.

As is true with the number of samples, there's some room for trial and error here, but unlike the number of samples, it is very possible to have too many features. For example, imagine that you're trying to model life insurance risk. Age is certainly going to play a role in your calculation. If you include both age and date of birth as features, however, you have some redundancy in your feature set. This may not be a problem in terms of making your risk prediction (though that depends on the algorithm you use), but if you want to answer the question "Out of this list of features, how imporant is age?" you'll probably be misled; some of the importance that should have been assigned to age gets assigned to date of birth, instead. Now, in this example, the redundancy is easy to spot, and to fix, but that isn't always the case.

The good news is that you can begin doing predictive modeling with very few features. Even a single feature can give you some insight. In the life insurance risk example above, it's possible to construct a model that only depends on age. Obviously, it isn't going to be as good as one that also considers other risk factors (medical history, lifestyle, genetics, etc.), but it's enough to get you started.

## Conclusion
The key takeaway here is this: start with the data you have, and test the quality of the output of the system you build with it. Once you've started, you can grow your system organically by tracking more features you think might be useful, and increasing the number of samples just by doing business.



## Notes
<b id="f1">1</b> As is the case with most buzzwords, there isn't a universally accepted definition for "Big Data", but it's generally regarded as a large enough data set to require more than one machine for processing (*i.e.*, it's either too big to fit in main memory, or too big to fit on a single disk, or something similar.) In that case, your analytics algorithms have to be able to work on smaller batches of data, and/or work in parallel. Additionally, if your data is really large, it makes sense to carry the computation to the data (using a paradigm like map-reduce, on top of technology like Hadoop) instead of the other way around. While it's certainly possible to do this, it adds a layer of complexity that you're better off avoiding if you can. [↩](#a1)

<b id="f2">2</b> There are many, many versions of this diagram. Most of them seem to be derived from [this version](http://drewconway.com/zia/2013/3/26/the-data-science-venn-diagram), but I like the one I linked to above a little better.  [↩](#a2)
