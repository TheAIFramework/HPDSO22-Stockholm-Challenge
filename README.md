# Welcome to the HP Data Science Open - Stockholm 22 Challenge !

This is it! This is where data scientists can flex :)

The short challenge should require less than ~100 lines of code in total. Let's goooo!

Your submission should be hosted on an internet accessible git-repo so it can be cloned. Include a README.md with *extremely* clear instructions on how to set up your code and run it. Email the link to your submission to robert@taif.co no later than 23:00 October 26th. Any commits after the deadline will not be used.

## Instructions

1. All sumbissions need to be able to take an argument input specifying folders with data. For example:

`user@HPZ:~/mysubmission$ julia mycode.jl /mnt/optane1/data /mnt/optane2/data`

Although this repo only includes one example file, expect us to test the code on around ~500GB of files.

2. Process Challenge STEP 1 and STEP 2 as quickly as possible. 

Time your code from the moment it reads data, until it has completed STEP 2 and prints the result.

**The winner will be selected according to 3 criteria: correctness, speed, and elegance.**

Looking forward to your awesome and creative submissions!!

Kind regards,
~ Robert

## STEP 1 - Loading Data

The challenge is centered on international airline flights.
Data is based on 2018 arline connectivity, not passenger volume.
It was generated using a 5-step self-avoiding diffusion simulation.

There are two sources of data.

1. A CSV file `airports.csv` describing airports and their location in latitude and longitude.

2. A `dat.bin` file with 100k samples of binary data serialized using ASN1 BER encoding.
Read more here: https://en.wikipedia.org/wiki/X.690#BER_encoding

Note that this is just a small subset with 10 million samples.
Your code should be instrumented to take folders as an argument and read all the *.bin files in them.

If you're having trouble reading the binary file, you may use the CSV file, though it may be counted against your final result. 

Each sample (binary frame or CSV row) has four Float32 values.
They are the source and the destination coordinates of flights.
In other words, two pairs of latitude and longitude.

Your first task is to figure out how many flights go to and from each airport.
You will find that some airports are busier than others.

## STEP 2: Analyzing data

Your task is to model the data in the following way
1. create an undirected graph with edge-weights set to the number of trips.
2. Perform hierarchical clustering on the graph distance matrix using mean distance similarity linkage.

Read more here: https://en.wikipedia.org/wiki/Hierarchical_clustering

3. Print a sorted list of the highest 5 airports in the resulting dendrogram.
4. (Bonus) Calculate the first 3 graph laplacian eigenvectors with the calculated edge-weights.
Treating them like spatial coordinates, print a sorted list of which airpoirts deviate most from the centroid.

Read more here: https://citeseerx.ist.psu.edu/viewdoc/summary?doi=10.1.1.183.1250

## Step 3: visualize

1. Render the data on a map displaying the various clusters

Read more about spectral layouts here:
https://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.3.2055&rep=rep1&type=pdf

![What a visualization of the data can look like.](https://github.com/TheAIFramework/HPDSO22-Stockholm-Challenge/raw/master/viz.png)
