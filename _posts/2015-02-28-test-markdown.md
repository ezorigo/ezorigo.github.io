---
layout: post
title: Data Storytelling
subtitle: International football results from 1872 to 2019
gh-repo: ezorigo/Data-Storytelling
gh-badge: [star, fork, follow]
tags: 
comments: true
---

# **Work in progress**

#### Dataset by [Mart Jürisoo](https://www.kaggle.com/martj42/international-football-results-from-1872-to-2017)

Mart Jürisoo's data description:

>This dataset includes 40,838 results of international football matches starting from the very first official match in 1972 up to 2019. The matches range from FIFA World Cup to FIFI Wild Cup to regular friendly matches. The matches are strictly men's full internationals and the data does not include Olympic Games or matches where at least one of the teams was the nation's B-team, U-23 or a league select team.

>results.csv includes the following columns:

> * date - date of the match
> * home_team - the name of the home team
> * away_team - the name of the away team
> * home_score - full-time home team score including extra time, not including penalty-shootouts
> * away_score - full-time away team score including extra time, not including penalty-shootouts
> * tournament - the name of the tournament
> * city - the name of the city/town/administrative unit where the match was played
> * country - the name of the country where the match was played
> * neutral - TRUE/FALSE column indicating whether the match was played at a neutral venue

#### Let's read the csv into Pandas dataframe

```python
# read the csv into a pandas dataframe
import pandas as pd

df = pd.read_csv('results.csv')

print(df.shape)
df.head()
```
       | date	| home_team	| away_team	| home_score	| away_score	| tournament	| city	| country	| neutral|
|------|------|-----------|-----------|------------|------------|------------|------|---------|--------|
 **1** |  1872-11-30	| Scotland	| England	|0	|0	|Friendly	|Glasgow	|Scotland	|False    
 **2** |1873-03-08	|England	|Scotland	|4	|2	|Friendly	|London|	England	|False
 **3** |1874-03-07	|Scotland	|England	|2	|1	|Friendly|	Glasgow	|Scotland	False
 **4** |1875-03-06	|England	Scotland|	2|	2	|Friendly	|London	|England|False
 **5** |1876-03-04	|Scotland	|England	|3	|0	|Friendly|	Glasgow	|Scotland|	False
```python
# check for NaN values

df.isna().sum()
```

```python
date          0
home_team     0
away_team     0
home_score    0
away_score    0
tournament    0
city          0
country       0
neutral       0
dtype: int64
```

![pic1][barplot]

![pic2][barplot1]

 <head> 
 <!-- Plotly.js -->
 <script src="https://cdn.plot.ly/plotly-latest.min.js"></script> 
 </head> 
 <body> 
 <!-- Plotly chart will be drawn inside this DIV --> 
 <div id="myDiv"></div> 
 <script> 
Plotly.d3.csv('https://raw.githubusercontent.com/ezorigo/Data-Storytelling/master/usasoccer.csv', function(err, rows){

    function unpack(rows, key) {
        return rows.map(function(row) { return row[key]; });
    }

    var scl = [[0.000000,'rgb(166,206,227)'],[0.090909,'rgb(31,120,180)'],[0.181818,'rgb(178,223,138)'],[0.272727,'rgb(51,160,44)'],[0.363636,'rgb(251,154,153)'],[0.454545,'rgb(227,26,28)'],[0.545455,'rgb(253,191,111)'],[0.636364,'rgb(255,127,0)'],[0.727273,'rgb(202,178,214)'],[0.818182,'rgb(106,61,154)'],[0.909091,'rgb(255,255,153)']];

    var data = [{
        type:'scattergeo',
        locationmode: 'country names',
        lon: unpack(rows, 'long'),
        lat: unpack(rows, 'lat'),
        hoverinfo: unpack(rows, 'text'),
        text: unpack(rows, 'text'),
        mode: 'markers',
        marker: {
            colorscale: scl,
            color: unpack(rows, 'tournament_id')
        }
    }];


    var layout = {
        title: 'US International Soccer Matches Since 1885',
        geo: {
            scope: 'world',
            projection: {
                type: 'natural earth'
            }
        }
    };

    Plotly.plot(myDiv, data, layout, {showLink: false});

});
 </script> 
 </body> 



Here's a code chunk:

~~~
var foo = function(x) {
  return(x + 5);
}
foo(3)
~~~

And here is the same code with syntax highlighting:

```javascript
var foo = function(x) {
  return(x + 5);
}
foo(3)
```

And here is the same code yet again but with line numbers:

{% highlight javascript linenos %}
var foo = function(x) {
  return(x + 5);
}
foo(3)
{% endhighlight %}

[barplot]: (https://github.com/ezorigo/ezorigo.github.io/blob/master/img/barplot1.png)
[barplot1]: (https://github.com/ezorigo/ezorigo.github.io/blob/master/img/barplot2%20normalized.png)
