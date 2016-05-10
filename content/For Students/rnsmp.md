Title: REPL, Notebook, Script, Module, Package
Date: 2016-04-27
Category: For Students
Tags: 
Slug: REPL_etc
Author: Cavendish McKay
Summary: Levels of python orgainization and when to use them.

# REPL, Notebook, Script, Module, Package
## Levels of python orgainization and when to use them

One of the challenges for people who are new to programming is understanding
how to collect and organize their code. This difficulty is especially true in interpreted languages
like python, because there are a number of different ways to write and execute code.
In this essay, I'll discuss five:

* the REPL (read eval print loop)
* the Jupyter (formerly IPython) notebook
* scripts
* modules
* packages

I've ordered these loosely according to their potential for code reuse, though as
we'll see, there are a few other considerations that come into play.

## REPL
Most people are first exposed to python via the REPL (read eval print loop). This is an interactive session with the python interpreter; it Reads your input, Evaluates it, and Prints the output. It does
this over and over again until you tell it to quit (the Loop). If you type `python` at a command prompt with no arguments, the python interpreter starts up and presents you with a REPL.

    Python 3.5.1 |Continuum Analytics, Inc.| (default, Dec  7 2015, 11:24:55) 
    [GCC 4.2.1 (Apple Inc. build 5577)] on darwin
    Type "help", "copyright", "credits" or "license" for more information.
    >>> 5+3
    8
    >>> 

The REPL is a standard interaction pattern for interpreted languages, and is a great way to explore and learn. You get immediate feedback, so if you're not quite sure how to do something, you can tweak
it until you get exactly what you want. Python has a lot of features for introspection, too, so you can
look at the effects of your statements even if they don't print anything themselves.

There are two major disadvantages of the REPL, though. First, it's totally ephemeral. This is fine if you have some task you only want to do once, but if your goal is to do something over and over again (as is often the case when you're programming), the REPL probably isn't your best choice: once you quit, both your input and output are gone.

The second disadvantage of the REPL is related to the way in which you enter your input. Since you enter code one line at a time, writing complex branches or loops (not to mention function or class definitions) can be difficult. Since most interesting code requires ideas that are hard to express in a single line, this can make using the REPL for doing real work awkward (though not impossible).

I've moved to the Notebook (which we will meet next) for nearly all of my interactvie python needs, with only one real exception. If I'm using python as a calculator and don't need to save the calculation for any reason, I'll sometimes use the REPL rather than a notebook.

## Notebook
The Jupyter (formerly IPython) Notebook is an interactive environment that addresses the two shortcomings of the REPL I've listed above. Additionally, it lets you include plots, animations, external media, mathematical notation, markdown, and HTML alongside your code. Though the project started as a python-only environment, there are now backend kernels for a wide variety of languages (which was the primary driver behind spinning the notebook out of the IPython project and adopting the name Jupyter).

The notebook consists of a list of *cells*, which can either contain code or markdown. Code cells can be edited after execution, and can be executed in arbitrary order, which can lead to some confusion at times. In particular, it's possible for function or variable definitions in the kernel's namespace to be different from what it looks like they ought to be just from reading the cells in order. When in doubt, it can be useful to restart the kernel and re-execute all of the cells. Of course, if there are pieces of code that take a long time to execute, rerunning the whole notebook may not be an attractive option.

I use notebooks for exploratory work, but I think an even stronger use case is for communication. The ability to include LaTeX, markdown, and graphics with the code makes this format ideal for teaching, either about code or about whatever problem domain you're working in (typically physics and math, in my case). In addition to the extra explanatory power one gets from a richer writing environment, it's relatively easy to structure notebooks in such a way that the reader can experiment and explore on their own.

Notebooks render well to HTML (you interact with them in a browser, after all) and so publishing a notebook online, either as a blog post or as a standalone document, is pretty easy. In fact, there is a [gallery](http://nbviewer.jupyter.org) of notebooks that links up with github; you can keep your notebook in version control (you *are* using version control, right?) and make it available to others with no additional effort on your part. Of course, if you want people to be able to execute and interact with your notebook, you may have to share additional data or run a notebook server (which is beyond the scope of this document).

One last point about communicating with notebooks: it's actually possible to use the notebook as a presentation tool like powerpoint or keynote. You don't have the same degree of control over screen real estate that you would with a purpose-built presentation tool, but it's very easy to include code and results, and has plusses from the standpoint of openness and reproduceability.

So, what's the downside? It's relatively common for people to react to their first exposure to the notebook with a great deal of enthusiasm: "Let's notebook all the things!" Notebooks are *not* particularly convenient, however, for code reuse, and for similar reasons, they're not very effective for software development (where the software itself, and not the result, is the desired product).

So, let's talk about code reuse. That leads us into the next organizational category:

## Script
A *script* is just a collection of python statements in a file. Here's an example (a solution to a [hackerrank](www.hackerrank.com) challenge, stored in a file called `maplambda.py`):

    N = int(input())
    nums = [None]*N

    for i in range(N):
        if i == 0:
            nums[i] = 0
        elif i == 1:
            nums[i] = 1
        else:
            nums[i] = nums[i-1] + nums[i-2]

    cubes = map(lambda x: x**3, nums)
    print(cubes)

Unpacking this just a little bit, when you type `python maplambda.py` at the command prompt, it will wait for you to input an integer N, compute the first N Fibonacci numbers, and cube them. When it's done, it prints the list of cubes.  There is nothing here that couldn't be accomplished in a notebook (or in a REPL, for that matter), but having it in a script allows us to do the same task multiple times with slight variations (in this case, the number of cubes to calculate and print).

This is a really trivial example of code reuse, but the general principle applies all over the place. We often want to repeat a task with small variations. A slightly less trivial and more useful example is the case of producing a particular plot from different sets of data. Which data set you're using could be determined by requesting user input (as the script above), by command line options, by environment variables, by working directory, or by nearly anything else, really. Generally speaking, when you think of a python program (*i.e.*, a set of instructions intended to perform a particular task), you're thinking of a script.

## Module
The more complicated a programming task (and, by extension, the program written to accomplish that task) becomes, the less convenient it is to store the whole thing in a single script. Furthermore, there are almost always little pieces of functionality that are independent of each other and constitute natural chunks of program behavior. We store collections of related chunks in *modules* and *packages*. You can think of a module as a script that only contains definitions. That is, it doesn't do anything by itself, but instead provides you with some tools you can use to do whatever you want.

You access the contents of a module via the `import` statement. There are two main variations here: you can either import a specific item (*e.g.*, `from collections import defaultdict`) or an entire module (`import collections`). Both of these statements would allow you to use the `defaultdict` class in the `collections` module, though in the second case you would refer to it as `collections.defaultdict` instead of just `defaultdict`. You can additionally import either entire modules or pieces thereof using aliases: `from collections import defaultdict as dd`, for example. Then, if you wanted to use `defaultdict`, you would refer to it as `dd`.

Writing modules is simple. In fact, any script you write can be imported as a module (assuming, of course, that it has class, function, or variable definitions in it). For this reason, it's generally good practice to write all of your scripts as if they were going to be used as modules, and include whatever the desired functionality of the script is in a clause at the end. For example, here's a script-written-as-a-module from the 2015 SciPy tutorial on Scikit Learn (`plot_kneighbors_regularization.py`):

    import numpy as np
    import matplotlib.pyplot as plt

    from sklearn.neighbors import KNeighborsRegressor


    def make_dataset(n_samples=100):
        rnd = np.random.RandomState(42)
        x = np.linspace(-3, 3, n_samples)
        y_no_noise = np.sin(4 * x) + x
        y = y_no_noise + rnd.normal(size=len(x))
        return x, y


    def plot_regression_datasets():
        fig, axes = plt.subplots(1, 3, figsize=(15, 5))
        for n_samples, ax in zip([10, 100, 1000], axes):
            x, y = make_dataset(n_samples)
            ax.plot(x, y, 'o', alpha=.6)


    def plot_kneighbors_regularization():
        rnd = np.random.RandomState(42)
        x = np.linspace(-3, 3, 100)
        y_no_noise = np.sin(4 * x) + x
        y = y_no_noise + rnd.normal(size=len(x))
        X = x[:, np.newaxis]
        fig, axes = plt.subplots(1, 3, figsize=(15, 5))

        x_test = np.linspace(-3, 3, 1000)

        for n_neighbors, ax in zip([2, 5, 20], axes.ravel()):
            kneighbor_regression = KNeighborsRegressor(n_neighbors=n_neighbors)
            kneighbor_regression.fit(X, y)
            ax.plot(x, y_no_noise, label="true function")
            ax.plot(x, y, "o", label="data")
            ax.plot(x_test, kneighbor_regression.predict(x_test[:, np.newaxis]),
                    label="prediction")
            ax.legend()
            ax.set_title("n_neighbors = %d" % n_neighbors)

    if __name__ == "__main__":
        plot_kneighbors_regularization()
        plt.show()

This module defines three functions, any of which could by used by a script (or notebook, or other module) which `import`s it. If, on the other hand, it is run as a script, then the special variable `__name__` will be set to `"__main__"`, and the last if statement will cause the script to generate and show a plot.


## Package
A *package* is really just a collection of *module*s. In the above script, `numpy`, `matplotlib`, and `sklearn` are all packages which consist of multiple modules; `pyplot` is a module in the `matplotlib` package, and `neighbors` is a module in the `sklearn` package, for example.

To make a package, put the desired modules into a directory (or folder, if you're more comfortable with that term) and then create a (possibly empty) module called `__init__.py` in the same directory. You can then access the individual modules as `<packagename>.<modulename>`.

Let's suppose I have a package called `pystarlab`, which contains a module called `diagnostics`, which contains a function called `massradius`. If I have `import`ed the package, I could call that function via `pystarlab.diagnostics.massradius()`. While this approach makes it absolutely clear which function I'm calling, and where it resides in the package, I have to go through a lot of keystrokes to get there. I might not care that the `massradius` function is in the `diagnostics` module. This is where the `__init__.py` file comes in. Within that file, I can import the contents of the modules, and they will then be available within the main namespace. So, if `__init__.py` contains the line

    from .diagnostics import *

I can then access the `massradius` function as `pystarlab.massradius` instead of `pystarlab.diagnostics.massradius`. This is, incidentally, just about the only place that `from <module> import *` is remotely good practice.

## Summing up

* Organizing your code into modules and packages adds a significant amount of structure and reusability, and should be the way you approach coding projects.
* When you write scripts, it's typically a good idea to think of them as modules with a "script clause" at the end; if you later want to reuse pieces of them, it's much easier if you start with the module paradigm in mind.
* Notebooks are good for exploration and communication, but are not ideal for development work.

