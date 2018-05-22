# Wbgt
This project is a small part of my master thesis in KEIO university. The objective of this script is to collect weather forecast from a website. The target is the WBGT (Wet Buld Globe Temperature), this index is used to characterize heatwave. I used these data for my heatstroke prevention system. I hope this script can be useful to see how to do "web scraping", so I will explain all steps.

#The target
We are going to use the environment ministry website, and especially for Tokyo area ([HERE](http://www.wbgt.env.go.jp/graph_ref_td.php?region=03&prefecture=44&point=44132)) The website give us a nice forecast table for the next 3days. 3 days can be short but enough for the prove of concept of our system.

<img src="/images/ministry.JPG" width="400">

We are targeting the 3 days forecast table:

<img src="/images/table.JPG" width="450">

#Developer mode
Now in order to extract specific data, it's important to see how the webpage is structured and where are the data encoded. To do so, I recommend to explore the page on developer mode/inspector (Ctrl+Alt+C). Now we can see the matching between the target and the displayed web page code. (htlm help [HERE](http://www.simplehtmlguide.com/cheatsheet.php)

<img src="/images/inspect.JPG" width="300">

#Extracting the data
To get the webpage content, we used the library [requests](http://docs.python-requests.org/en/master/user/install/). We simply do a request to the url target and use Beautiful Soup in order to do all the preprocessing :)

<img src="/images/get.JPG" width="450">

Then we extract the wanted table's data with the function find_all and the htlm tag "tr" and the class used to display the data:
We extract the data in 3 strings for each forecasted day. (I really think this can be in a more smartly way but I am not good enough on the scrapping topics to find a solution quickly :D) I find it easier to work with string parameter.
D0 for today / D1 for tomorrow / D2 for the day after tomorrow

<img src="/images/extract.JPG" width="450">

#Getting the average on each day
The following code do the average on each day. I used the fact the date and each wbgt are separated by "\n", and use a double boucle structure to make the average.

<img src="/images/ave.JPG" width="450">

#Data file creation/update
Finally, we update the data file with the today's data (or create a new one if there is no file)

<img src="/images/update.JPG" width="450">

In this repository, you can find the python script. 
Do not hesitate in you have any question or advice :)
