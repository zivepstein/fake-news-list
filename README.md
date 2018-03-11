# fake news list

Here we outline the methodology we used to create our list of hyper-partisan, satire and fake news domains. Specifically, we describe each of the lists we aggregated, and we scored the domains in each of those lists.

1. David Lazer and colleagues looked at domains that snopes.com articles link to. In the repo, this file is called `ASnopes domains annotated with urls.csv` They manually classify 171 of these domains into categories of green (reasonable and accountable journalism, 18), yellow (low quality journalism, 24), orange (negligent or deceptive, 47), red (little regard for the truth, 61), or satire (self-described satirical, 5). We consider a domain from this list SATIRE if it is Satire, HYPERPARTISAN if it is orange, and FAKE if it is red. We do not include green or yellow domains in our list.

2. [Buzzfeed created a list](https://www.buzzfeed.com/craigsilverman/top-fake-news-of-2016?utm_term=.kpl9an9AL#.aj4qmkqjo) of 215 fake news sites. This analysis focused exclusively on stories that were 100% false and that originated on fake news websites — it did not include misreported news or partisan misrepresentations of real events. We merge `sites_2016.csv` and `sites_2017.csv` into one large list, and mark each of the domains in that list as FAKE.

3. Buzzfeed also created a [list of 667 hyper-partisan sites](https://github.com/BuzzFeedNews/2017-08-partisan-sites-and-facebook-pages/tree/master/data)related to the US election, and coded them as “left” or “right” leaning. This file is called `C3all_partisan_sites.csv`

4. [Melissa Zimdar's list of 1001 domains](https://docs.google.com/document/d/10eA5-mCZLSS4MQY5QGb5ewC3VAL6pLkT53V_81ZyitM/preview) tags domains as being of various types include unreliable, bias (used for Breitbart), fake (bostonleader.com) and satirical (bostontribune.com). Each domain could be receive up to three different type tags. She wrote an article describing here methodology [here](https://www.washingtonpost.com/posteverything/wp/2016/11/18/my-fake-news-list-went-viral-but-made-up-stories-are-only-part-of-the-problem/?utm_term=.856e9fe7bef4). The data is contained in a file called DSearachable Spreadsheet Database - Sheet1.csv. We counter a domain as FAKE if its first, second, or third type was fake. We counted  a domain as SATIRE if its first second or third type was satire. We counted a domain as HYPERPARTISAN if its first second or third type was bias, conspiracy, unreliable, clickbait, junksci, hate or rumor. The data contained in a file called `DSearachable Spreadsheet Database - Sheet1.csv`. We do not score the types unknown, political, reliable or state.

5. Politifact produced [a list of 330 fake news sites](http://www.politifact.com/punditfact/article/2017/apr/20/politifacts-guide-fake-news-websites-and-what-they/). It is contained in a file called `Fpolifact.csv`. We counted a domain as SATIRE if it marked as parody, and as FAKE if it was marked as fake news or imposter sites. 

Next, we take these 5 lists and perform an outer join on url. We then compute a sum of FAKE, SATIRE, and HYPERPARTISAN that is a total score of each across the 5 lists (so the maximum score is 5). We also compute a general COUNT, which is the number of times a given domain occurs across the all lists. After the join, our final list contains 1790 sites.

