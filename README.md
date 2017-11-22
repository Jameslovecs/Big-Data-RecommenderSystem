# Big-Data-RecommenderSystem

## Overview

In this project, I built a movie recommender system based on Item Collaborative Filtering using Hadoop MapReduce in Java (Docker).

## Project Data
Data comes from the training dataset of Netflix Prize Challenge. The following is the information from its README.

#### Training dataset file description

The file "training_set.tar" is a tar of a directory containing 17770 files, one
per movie.  The first line of each file contains the movie id followed by a
colon.  Each subsequent line in the file corresponds to a rating from a customer
and its date in the following format:

CustomerID,Rating,Date

- MovieIDs range from 1 to 17770 sequentially.
- CustomerIDs range from 1 to 2649429, with gaps. There are 480189 users.
- Ratings are on a five star (integral) scale from 1 to 5.
- Dates have the format YYYY-MM-DD.

#### Data preprocessing

I preprocessed the original dataset in two steps:

1. Change the data in each movie file into the following format: UserID, MovieID, Rating.
2. Merge 17770 movie files into one big input file since Hadoop is not good for dealing with lots of small files. And the big input file is the input of our recommender system.


## Building Steps

* Divide data by user id
* Build co-occurrence matrix
* Normalize the co-occurrence matrix
* Build rating matrix
* Multiply co-occurrence matrix and rating matrix
* Generate recommendation list


# Screenshot
<img src="https://github.com/Jameslovecs/Big-Data-RecommenderSystem/blob/master/Movie%20Recommender%20System.jpg"/>


## Deploy
we deploy a hadoop cluster on Docker, this cluster has one Masternode and two slavenodes. The whole project is based on the docker.


```
hadoop com.sun.tools.javac.Main *.java

jar cf recommender.jar *.class

hadoop jar recommender.jar Driver /input /dataDividedByUser /coOccurrenceMatrix /Normalize /Multiplication /Sum
```

* args0: original dataset

* args1: output directory for DividerByUser job

* args2: output directory for coOccurrenceMatrixBuilder job

* args3: output directory for Normalize job

* args4: output directory for Multiplication job

* args5: output directory for Sum job




