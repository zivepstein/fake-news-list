# fake news list

Here we outline the general methodology used to create our list of fake news domains. 

The first comes from David Lazer, who looks at sites that snopes.com articles link to. In the repo, this file is called `ASnopes domains annotated with urls.csv` They manually classify into categories of green (18), yellow (24), orange (47), red (61), or satire (5). We consider a domain from this list SATIRE if it is Satire, SKETCHY if it is orange, and FAKE if it is red. 

The second comes from [Buzzfeed] (https://www.buzzfeed.com/craigsilverman/top-fake-news-of-2016?utm_term=.kpl9an9AL#.aj4qmkqjo). This analysis focused exclusively on stories that were 100% false and that originated on fake news websites — it did not include misreported news or partisan misrepresentations of real events. We merge `sites_2016.csv` and `sites_2017.csv` into one super list, and mark each of those items as FAKE but not as SKETCHY or SATIRE.

Also from Buzzfeed, we use [Craig Silverman and colleagues list](https://github.com/BuzzFeedNews/2017-08-partisan-sites-and-facebook-pages/tree/master/data). They have curated 667 “hyperpartisan” sites related to the US election, and coded them as “left” and “right” leaning. This file is called `C3all_partisan_sites.csv` and we marked each of those domains as SKETCHY but not FAKE or SATIRE

We also took [Melissa Zimdar's list](https://docs.google.com/document/d/10eA5-mCZLSS4MQY5QGb5ewC3VAL6pLkT53V_81ZyitM/preview) who uses labels like unreliable, bias (used for Breitbart) and fake (bostonleader.com) and satirical etc (bostontribune.com). She wrote an article describing here methodology [here](https://www.washingtonpost.com/posteverything/wp/2016/11/18/my-fake-news-list-went-viral-but-made-up-stories-are-only-part-of-the-problem/?utm_term=.856e9fe7bef4). The data contained in a file called `DSearachable Spreadsheet Database - Sheet1.csv`. We marked a domain as FAKE if its first second or third type was fake. We marked it as SATIRE if its first second or third type was satire. We marked it SKETCHY if its first second or third type was bias, conspiracy, unreliable, clickbait, junksci, hate or rumor. 

We use [the list Politifact produced](http://www.politifact.com/punditfact/article/2017/apr/20/politifacts-guide-fake-news-websites-and-what-they/), which was last updated in November. It is marked as `Fpolifact.csv`. We marked a domain as SATIRE if it marked as parody, as FAKE if it was marked as fake news or imposter sites, and did not mark any of these sites as SKETCHY. 

We also use a list from Hoaxy, which can be found [here](https://docs.google.com/spreadsheets/d/1S5eDzOUEByRcHSwSNmSqjQMpaKcKXmUzYT6YlRy3UOg/edit#gid=1882442466) This is what we use for Hoaxy. It's not terribly up to date though. It is called `GClaim Sources - Public List.csv` in the repo. And we mark all of these as FAKE but not SATIRE or SKETCHY.  

Next, we take these 6 lists and perform an outer join on url. We then compute a sum of FAKE, SATIRE, and SKETCHY that is a total score of each across the 6 lists (so the maximum score is 6). We also compute a COUNT, which is the number of times a given domain occurs across the lists, by which we sort the data. 
