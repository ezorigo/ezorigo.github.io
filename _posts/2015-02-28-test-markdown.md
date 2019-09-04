---
layout: post
title: Data Storytelling
subtitle: International football results from 1872 to 2019
gh-repo: ezorigo/Data-Storytelling
gh-badge: [star, fork, follow]
tags: 
comments: true
---

**Work in progress**

###Content

This dataset includes 40,838 results of international football matches starting from the very first official match in 1972 up to 2019. The matches range from FIFA World Cup to FIFI Wild Cup to regular friendly matches. The matches are strictly men's full internationals and the data does not include Olympic Games or matches where at least one of the teams was the nation's B-team, U-23 or a league select team.

results.csv includes the following columns:

 * date - date of the match
 * home_team - the name of the home team
 * away_team - the name of the away team
 * home_score - full-time home team score including extra time, not including penalty-shootouts
 * away_score - full-time away team score including extra time, not including penalty-shootouts
 * tournament - the name of the tournament
 * city - the name of the city/town/administrative unit where the match was played
 * country - the name of the country where the match was played
 * neutral - TRUE/FALSE column indicating whether the match was played at a neutral venue
 
Note on team and country names: For home and away teams the current name of the team has been used. For example, when in 1882 a team who called themselves Ireland played against England, in this dataset, it is called Northern Ireland because the current team of Northern Ireland is the successor of the 1882 Ireland team. This is done so it is easier to track the history and statistics of teams.

For country names, the name of the country at the time of the match is used. So when Ghana played in Accra, Gold Coast in the 1950s, even though the names of the home team and the country don't match, it was a home match for Ghana. This is indicated by the neutral column, which says FALSE for those matches, meaning it was not at a neutral venue.

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

    var scl = [[0.000000,	'rgb(166,206,227)'],[0.090909,	'rgb(31,120,180)'],[0.181818,	'rgb(178,223,138)'],[0.272727,	'rgb(51,160,44)'],[0.363636,	'rgb(251,154,153)'],[0.454545,	'rgb(227,26,28)'],[0.545455,	'rgb(253,191,111)'],[0.636364,	'rgb(255,127,0)'],[0.727273,	'rgb(202,178,214)'],[0.818182,	'rgb(106,61,154)'],[0.909091,	'rgb(255,255,153)']];

    var data = [{
        type:'scattergeo',
        lon: unpack(rows, 'long'),
        lat: unpack(rows, 'lat'),
        text:  unpack(rows, 'text'),
        mode: 'markers',
        marker: {
            colorscale: scl,
            color: unpack(rows, 'tournament_id')
        }
    }];


    var layout = {
        title: 'US International Soccer Matches Since 1885'
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


## Here is a secondary heading

Here's a useless table:

| Number | Next number | Previous number |
| :------ |:--- | :--- |
| Five | Six | Four |
| Ten | Eleven | Nine |
| Seven | Eight | Six |
| Two | Three | One |


How about a yummy crepe?

![Crepe](https://s3-media3.fl.yelpcdn.com/bphoto/cQ1Yoa75m2yUFFbY2xwuqw/348s.jpg)

It can also be centered!

![Crepe](https://s3-media3.fl.yelpcdn.com/bphoto/cQ1Yoa75m2yUFFbY2xwuqw/348s.jpg){: .center-block :}

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

## Boxes
You can add notification, warning and error boxes like this:

### Notification

{: .box-note}
**Note:** This is a notification box.

### Warning

{: .box-warning}
**Warning:** This is a warning box.

### Error

{: .box-error}
**Error:** This is an error box.
