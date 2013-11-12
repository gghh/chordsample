chordsample
===========

demostrative usage of a new API for the d3 chord diagram.

You have three lists of people:

```
nice_people := [charline, martin, benedikt, camilla]
rich_people := [sebastian, camilla]
smart_people := [larry, camilla, charline, gustavo, audrey]
```

and want to display visually the intersection between them.

You could use a Venn diagram[1], but that doesn't scale beyond three or four lists.
1. http://en.wikipedia.org/wiki/Venn_diagram

You could instead use a kind of circular representation, the one
invented by Martin Krzywinski[2][3] and ported into d3.js[4]

2. http://twitter.com/mkrzywinski
3. http://circos.ca/
4. http://bl.ocks.org/mbostock/4062006

How so? Each arc corresponds to a list, and a ribbon between two
lists accounts for common elements.

But still the current d3.js API for that is not as flexible as it should be[5]

5. http://www.gghh.name/dibtp/?p=234

I propose a different API[6][7] where the above illustration can be
described as follow: how many people are at the same time nice (group 0),
rich (group 1) and smart (group 2)? Not many, only Camilla actually.
It's the last block in the representation below: groups 0, 1 and 2
are "linked" by a ribbon of "width" 1.

Charline is smart and nice, but doesn't have much money: it's the
second-last block below, group 0 and 2 have a link of width 1.

Larry, Gustavo and Audrey are smart, but not rich nor nice:
group 2 has a "self link" of width 3 (three people).
Martin and Benedikt are very nice, and Sebastian is only rich.

```
[[{group: 1, value: 1}],

 [{group: 0, value: 2}],

 [{group: 2, value: 3}],

 [{group: 0, value: 1},
  {group: 2, value: 1}],

 [{group: 0, value: 1},
  {group: 1, value: 1},
  {group: 2, value: 1}]]
```

6. http://www.gghh.name/dibtp/?p=277
7. https://github.com/gghh/d3/commit/abf61037e6a58afa52f2c5099a507115bf3d66ce

The people_chord.html file in this repository shows the details of the API on this example.
To make it work, please download the d3.js file from my d3 fork:

https://github.com/gghh/d3/blob/master/d3.js

in the same folder where you have people_chord.html
