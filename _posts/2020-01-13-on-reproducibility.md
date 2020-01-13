---
layout: post
title: On Reproducibility
---
```
import reproducible_science
```

Reproducibility is important to science. A scientific result isn't considered confirmed until multiple studies have reached the same conclusion. Also, new work is more efficient if it can build on the foundations of past work.

I have opinions about science because I was trained as a physical chemist. And now that I'm entering the field of data science, I'm bringing those opinions with me. That's why I'm determined to make my work reproducible.

I realized this in my at the Metis Data Science Bootcamp when my group and I used code developed by four different people to run the same analysis on the same data and get the exact same results on four machines, one a Mac and three running some flavor of Linux.

Briefly, the project involved making recommendations to a hypothetical client about when and where do deploy street teams near subway stations to get pamphlets about the organization's upcoming gala in as many hands as possible. I worked on it with Eric Bassett, Eli T. Drumm, and Joanna Nachman. Details of the project, including a README, are [here](https://github.com/ekand/mtacular).

To organize the project, I took inspiration from the [cookie cutter data science tempate](https://drivendata.github.io/cookiecutter-data-science/), somewhat simplified to match our needs. Here's a brief summary of the directory structure:

```
.
├── data
│   ├── interim
│   └── raw
├── notebooks
│   └── code
│      
├── references
└── reports
    └── figures
```
There are a few key features here. First, data is separated from jupyter notebooks and python code. This separation helps to keep things organized.

Second, data is separated into raw data and interim data. The folder `data/raw` is, as the name suggests, for data in the original form as downloaded from the New York City Metropolitan Transportation Authority (MTA). This ensures that the analysis can always be run from the same starting point, even if the MTA website goes down. `data/interim`, again as the name suggests, is a folder for data that has been partially processed. Saving this data part way through the analysis can save time when developing and re-running the later steps of the data manipulation process.

A technical note: We needed to take an additional step to allow the python scripts in the `code` folder to "see" the data in the `data` folders. Here's an excerpt of the code that allows this:

```
from pathlib import Path
PROJECT_DIR = str(Path(__file__).resolve().parents[2])
```
Now, when loading the data, simply append `/data/raw/filename.csv` to the `PROJECT_DIR` string. This will work regardless of the placement of the project directory and works the same with on both Mac and Linux machines. (And presumably also on Windows, although we haven't tested that).

Coming from the world of physical chemistry, I'm used to measuring weak, noisy signals where the data will be slightly different on every run, although the patterns underlying the data should be consistent. In contrast, for this project, we had one data set which produced identical outcomes each time we rand the "experiment" of running the analysis. Granted, If we had, for example, separately analyzed data from different consecutive years, we would expect different but probably similar results. In any case, this kind of exact reproducibility was new to me and felt rather surprising.

Related to that, I was surprised when I learned that computers' random number generators are deterministic and "pseudo-random". But that's another blog post.

Getting back to the point, there was a major benefit to this organizational scheme. At one point a group member and I wound up with different results from what we thought was an equivalent process. Luckily, we knew where to look for the code that generated these results, and soon found the issue. (I had made a faulty assumption about an alternate method of calculation on one key step). After this, the calculation led to the same result.

I hope someone will pick up this process and try to run the analysis that we did if only to show that they can. It's one thing for four people working in the same building to run an identical analysis. It would be something more if a stranger I've never talked to managed to do the same. If you'd like to try, I encourage you to fork and clone the project's repo [here](https://github.com/ekand/mtacular) and tell me how it goes.

Thanks for reading and please let me know if you have questions or opinions about this!


-----

