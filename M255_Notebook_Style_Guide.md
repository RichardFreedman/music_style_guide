# Encoding Music Notebook Model Homework Report
Richard Freedman
2024-06-25

# About The Style Guide

This Style Guide is for **Music 255: Encoding Music**. In it we detail
some guidelines that will help you to create Jupyter notebooks that are
both functional (containing functional code and useful outputs) and
clear (framing code and output with narrative content where you will
explain the *motivation* for your work, how you *implemented* your plan,
and how you *explain or interpret* the results in light of what you have
learned and heard.

Below you will learn:

-   How to set up your notebook with Python libraries and add the
    special Quarto markdown cell at the start
-   The basics of markdown, and how to use it
-   How to use headers and sections to guide your reader through your
    work
-   How to format text (bold, italics, and verbatim code)
-   How to make sure you code is explained clearly with comments
-   How to make lists (numbered and unumbered or bullet points)
-   How to cite books, articles, and digital resources (URLs)
-   How to make sure your figures and other outputs have captions

# Quarto and Python

The [Quarto publishing system](https://quarto.org/) is a key part of the
process of creating clear narrative reports from your work. To prepare
your notebook to work with Quarto, you will need to include a special
`raw` YAML cell at the start of your notebook. It should look like this.
Yes, you need to include the `---` as the first and last line of this
special cell.

    ---
    title: "Your Project Name"
    author: 'Your Name'
    date: 'Today's Date'

    format:
      html:
        code-fold: true
        embed-resources: true
    plotly-connected: true
    jupyter: python3

    ---

You will need to import Python libraries needed for your work. But to
make charts and graphs appear as they should in Quarto, you will also
need to include some special code indicated after the imports:

    # import libraries
    from community import community_louvain
    from copy import deepcopy
    from IPython.display import SVG
    import altair as alt
    import glob as glob
    import numpy as np
    import os
    import pandas as pd
    import re
    import networkx as nx
    import plotly.express as px
    import requests

    # setup plotting for quarto
    alt.renderers.enable('default')
    import plotly.io as pio
    pio.renderers.default = "plotly_mimetype+notebook_connected"

    # supress warnings
    import warnings
    warnings.filterwarnings('ignore')

``` python
# import libraries
from community import community_louvain
from copy import deepcopy
from IPython.display import SVG
import altair as alt
import glob as glob
import numpy as np
import os
import pandas as pd
import re
import networkx as nx
import plotly.express as px
import requests

# setup plotting for quarto
alt.renderers.enable('default')
import plotly.io as pio
pio.renderers.default = "plotly_mimetype+notebook_connected"

# supress warnings
import warnings
warnings.filterwarnings('ignore')
```

# Markdown

Markdown is fairly easy to learn. It provides a simple way to format
text and code in ways that will follow consistent design, in the
notebook output and in the Quarto publication, too.

There are many guides to markdown: such as [this
cheatsheet](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet),
or a guide from
[Quarto](https://quarto.org/docs/authoring/markdown-basics.html).

# Section Headings

Headings are indicated with some number of `#` (then a space) before
your text. Add more `#` for subheadings. See [Quarto MD
Guide](https://quarto.org/docs/authoring/markdown-basics.html#headings)

Use H1 styles for your **Motivation**, **Implementation** and
**Explanation** sections of your work. For example:

``` python
# Motivation
```

Within these you can break your prose into subsections with lower level
headings to guide your reader through various sub themes or important
ideas:

``` python
### Header Level 3
#### Header Level 4
##### Header Level 5
```

These would appear as:

### Header Level 3

#### Header Level 4

##### Header Level 5

# Text Formatting (Bold, Italic, and Code)

### Bold and Italic

Use **bold** (`**your bold text**`) for emphasis of key words or
phrases.

*Italics* (`*your italic text*`) are used for the titles of publications
or musical works.

Be sure to follow the [Music Style Guide
conventions](https://github.com/RichardFreedman/music_style_guide/blob/main/sections/4_citing_sources.md)
for titles of musical works, or essays and books you cite.

### Verbatim Code

It is often useful to show some short portion of your code as you
explain a key method, problem, or solution. Of course you will need to
be selective with this, but including non-functional **verbatim code**
in the narrative portions of your notebook will help others understand
how you translate qualitative questions or logical steps into
algorithmic form.

Such passages of **verbatim code** can be done in either of two ways.
For a one-line snippet wrap your code in backtick marks like
<span style="background-color: #D3D3D3;">\`your code here\`</span>.

For any code longer than just a single line, follow this convention:

    ```python
    a = 1
    b = 2
    c = a + b
    print(c)
    ```

See the [Quarto MD
Guide](https://quarto.org/docs/authoring/markdown-basics.html#text-formatting).

### Code with Comments

In addition to such verbatim quotations of code, you will also want to
include **comments** in the working code itself. There is no need to
explain every step in a process. But comments to identify key functions
or sections of your work are a key part of documentation, so you can
understand what you are doing and others can learn from or adapt your
work.

In Python, line that start with `#` are understood as comments, and are
not part of the functional code itself. Here is an example in which each
and every step has an explanatory comment (you don’t need to be this
detailed, but it will give you an idea of what you can do):

``` python
# Step 1: Initialize the list
numbers = [4, 5, 6, 3, 9]

# Step 2: Choose the constant
constant = 4

# Step 3: Use list comprehension to multiply each element by the constant. This solution uses list comprehension; the statement within `[ ]` is in effect a `for` loop
multiplied_numbers = [number * constant for number in numbers]

# Step 4: Print the result
print("The list after constant multiplication:", multiplied_numbers)
```

### Folded Code in Quarto

In your notebook, the actual code shown above will of course be in a
code cell. When run in JupyterLab it will appear as such, followed by
the output cell. But when you render your notebook as interactive HTML
in Quarto, the code cells will be temporarily hidden (“folded” in the
language of Quarto). Users can click the `Code` the contents of the code
cell (complete with your comments). Otherwise they will only see the
output. This is why including print statements and other explanatory
commentary in the markdown cells is crucial!

``` python
# Step 1: Initialize the list
numbers = [4, 5, 6, 3, 9]

# Step 2: Choose the constant
constant = 4

# Step 3: Use list comprehension to multiply each element by the constant. This solution uses list comprehension; the statement within `[ ]` is in effect a `for` loop
multiplied_numbers = [number * constant for number in numbers]

# Step 4: Print the result
print("The list after constant multiplication:", multiplied_numbers)
```

    The list after constant multiplication: [16, 20, 24, 12, 36]

# Citations and Linked URLS

### Citing Books and Articles

References to scholarly writings should follow the [Haverford College
Music Style
Guide](https://github.com/RichardFreedman/music_style_guide/blob/main/sections/4_citing_sources.md)
system. Here we rely on the [Chicago Manual of Style
Author-Date](https://www.chicagomanualofstyle.org/tools_citationguide/citation-guide-2.html)
system.

For example, in the body of your argument you might write (the **BOLD**
reference is just for emphasis):

> Carolyn Abbate has urged musicologists to consider the practical and
> corporeal dimensions of music (**Abbate 2004: 508**).

Notice that the author-date reference contains the *exact location of
the material you are quoting* or referring to. The bibliography is the
place for the *full details about where to find this particular
publication*. In the author-date system:

> Abbate, Carolyn. 2004. “Music—Drastic or Gnostic?” *Critical Inquiry*
> 30, no. 3: 505-36.

The *bibliography* goes at the *end* of your notebook (see below).

### Citing a Web Resource

If you are **citing a web resource** (a database, digital project, a
streaming service like Spotify or Naxos, or some other ‘born digital’
content), then see the [Chicago Manual of
Style](https://www.chicagomanualofstyle.org/tools_citationguide/citation-guide-2.html#cg-website)
solutions for these cases.

Note that in markdown, you can easily like the full URL of the resource
behind some display text. put the **display name** you want in square
brackets, followed immediately by the **complete url** in parentheses.
For example:

`[Quarto Guide](https://quarto.org/docs/authoring/markdown-basics.html#lists)`

# Lists, Bullets, Numbers

Lists are helpful for steps or key points. See [Quarto
Guide](https://quarto.org/docs/authoring/markdown-basics.html#lists):

### Bulleted Lists (Unordered)

    * unordered list item
    * another item
        + sub-item 1
        + sub-item 2
            - sub-sub-item 1

### Numbered Lists (Ordered)

    1. first itme
    2. second item
        i) sub-item 1
             A.  sub-sub-item 1

# Tables, Figures and Captions

When you display charts or data in your notebook you will want to label
them with a caption and label:

`Figure 1:  Bubble Chart of GDP and Life Expectancy`

`Table 1: GDP and Life Expectancy Data (Sample)`

See the [Music Style
Guide](https://github.com/RichardFreedman/music_style_guide/blob/main/sections/9_transcriptions_figures.md#figures)
for more information.

#### Adding A Caption to a Dataframe Table

Here we consider a sample dataset from the Plotly Express library that
relates to GDP and Life Expectancy around the world. Import the data and
filter for the year=2007. Since it’s a large dataset, we will show just
the first 20 rows `head(10)`:

``` python
gapminder = px.data.gapminder()=
gapminder2007 = gapminder.query("year == 2007").head(10)
gapminder2007
```

The code will certainly show the data. But we also need a caption and
label. Do it this way:

``` python
gapminder2007.head(20).style.set_caption("Table 1: Life Expectancy Data").set_table_styles([{
    'selector': 'caption',
    'props': [
        ('color', 'black'),
        ('font-size', '24px')
    ]
}])
```

Notice that you can set the color and side of the caption, no less than
the text of the caption itself.

#### Caption for a Plotly Express Chart

Plotly Express is our standard library for barchart, scatterplots and
other visualizations. In the following scatterplot, we use the `title`
attribute to specify a label and title:

``` python
gapminder = px.data.gapminder()

gapminder2007 = gapminder.query("year == 2007")
fig = px.scatter(gapminder2007, 
                 x="gdpPercap", y="lifeExp", color="continent", 
                 size="pop", size_max=60,
                 hover_name="country",
                 title="Figure 1:  Bubble Chart of GDP and Life Expectancy")
fig.show()
```

``` python
# gapminder data with title
gapminder = px.data.gapminder()
gapminder2007 = gapminder.query("year == 2007")
gapminder2007.head(10).style.set_caption("Table 1: Life Expectancy and GDP").set_table_styles([{
    'selector': 'caption',
    'props': [
        ('color', 'black'),
        ('font-size', '24px')
    ]
}])
```

<style type="text/css">
#T_6b3eb caption {
  color: black;
  font-size: 24px;
}
</style>

<table id="T_6b3eb" data-quarto-postprocess="true">
<thead>
<tr class="header">
<th class="blank level0" data-quarto-table-cell-role="th"> </th>
<th id="T_6b3eb_level0_col0" class="col_heading level0 col0"
data-quarto-table-cell-role="th">country</th>
<th id="T_6b3eb_level0_col1" class="col_heading level0 col1"
data-quarto-table-cell-role="th">continent</th>
<th id="T_6b3eb_level0_col2" class="col_heading level0 col2"
data-quarto-table-cell-role="th">year</th>
<th id="T_6b3eb_level0_col3" class="col_heading level0 col3"
data-quarto-table-cell-role="th">lifeExp</th>
<th id="T_6b3eb_level0_col4" class="col_heading level0 col4"
data-quarto-table-cell-role="th">pop</th>
<th id="T_6b3eb_level0_col5" class="col_heading level0 col5"
data-quarto-table-cell-role="th">gdpPercap</th>
<th id="T_6b3eb_level0_col6" class="col_heading level0 col6"
data-quarto-table-cell-role="th">iso_alpha</th>
<th id="T_6b3eb_level0_col7" class="col_heading level0 col7"
data-quarto-table-cell-role="th">iso_num</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td id="T_6b3eb_level0_row0" class="row_heading level0 row0"
data-quarto-table-cell-role="th">11</td>
<td id="T_6b3eb_row0_col0" class="data row0 col0">Afghanistan</td>
<td id="T_6b3eb_row0_col1" class="data row0 col1">Asia</td>
<td id="T_6b3eb_row0_col2" class="data row0 col2">2007</td>
<td id="T_6b3eb_row0_col3" class="data row0 col3">43.828000</td>
<td id="T_6b3eb_row0_col4" class="data row0 col4">31889923</td>
<td id="T_6b3eb_row0_col5" class="data row0 col5">974.580338</td>
<td id="T_6b3eb_row0_col6" class="data row0 col6">AFG</td>
<td id="T_6b3eb_row0_col7" class="data row0 col7">4</td>
</tr>
<tr class="even">
<td id="T_6b3eb_level0_row1" class="row_heading level0 row1"
data-quarto-table-cell-role="th">23</td>
<td id="T_6b3eb_row1_col0" class="data row1 col0">Albania</td>
<td id="T_6b3eb_row1_col1" class="data row1 col1">Europe</td>
<td id="T_6b3eb_row1_col2" class="data row1 col2">2007</td>
<td id="T_6b3eb_row1_col3" class="data row1 col3">76.423000</td>
<td id="T_6b3eb_row1_col4" class="data row1 col4">3600523</td>
<td id="T_6b3eb_row1_col5" class="data row1 col5">5937.029526</td>
<td id="T_6b3eb_row1_col6" class="data row1 col6">ALB</td>
<td id="T_6b3eb_row1_col7" class="data row1 col7">8</td>
</tr>
<tr class="odd">
<td id="T_6b3eb_level0_row2" class="row_heading level0 row2"
data-quarto-table-cell-role="th">35</td>
<td id="T_6b3eb_row2_col0" class="data row2 col0">Algeria</td>
<td id="T_6b3eb_row2_col1" class="data row2 col1">Africa</td>
<td id="T_6b3eb_row2_col2" class="data row2 col2">2007</td>
<td id="T_6b3eb_row2_col3" class="data row2 col3">72.301000</td>
<td id="T_6b3eb_row2_col4" class="data row2 col4">33333216</td>
<td id="T_6b3eb_row2_col5" class="data row2 col5">6223.367465</td>
<td id="T_6b3eb_row2_col6" class="data row2 col6">DZA</td>
<td id="T_6b3eb_row2_col7" class="data row2 col7">12</td>
</tr>
<tr class="even">
<td id="T_6b3eb_level0_row3" class="row_heading level0 row3"
data-quarto-table-cell-role="th">47</td>
<td id="T_6b3eb_row3_col0" class="data row3 col0">Angola</td>
<td id="T_6b3eb_row3_col1" class="data row3 col1">Africa</td>
<td id="T_6b3eb_row3_col2" class="data row3 col2">2007</td>
<td id="T_6b3eb_row3_col3" class="data row3 col3">42.731000</td>
<td id="T_6b3eb_row3_col4" class="data row3 col4">12420476</td>
<td id="T_6b3eb_row3_col5" class="data row3 col5">4797.231267</td>
<td id="T_6b3eb_row3_col6" class="data row3 col6">AGO</td>
<td id="T_6b3eb_row3_col7" class="data row3 col7">24</td>
</tr>
<tr class="odd">
<td id="T_6b3eb_level0_row4" class="row_heading level0 row4"
data-quarto-table-cell-role="th">59</td>
<td id="T_6b3eb_row4_col0" class="data row4 col0">Argentina</td>
<td id="T_6b3eb_row4_col1" class="data row4 col1">Americas</td>
<td id="T_6b3eb_row4_col2" class="data row4 col2">2007</td>
<td id="T_6b3eb_row4_col3" class="data row4 col3">75.320000</td>
<td id="T_6b3eb_row4_col4" class="data row4 col4">40301927</td>
<td id="T_6b3eb_row4_col5" class="data row4 col5">12779.379640</td>
<td id="T_6b3eb_row4_col6" class="data row4 col6">ARG</td>
<td id="T_6b3eb_row4_col7" class="data row4 col7">32</td>
</tr>
<tr class="even">
<td id="T_6b3eb_level0_row5" class="row_heading level0 row5"
data-quarto-table-cell-role="th">71</td>
<td id="T_6b3eb_row5_col0" class="data row5 col0">Australia</td>
<td id="T_6b3eb_row5_col1" class="data row5 col1">Oceania</td>
<td id="T_6b3eb_row5_col2" class="data row5 col2">2007</td>
<td id="T_6b3eb_row5_col3" class="data row5 col3">81.235000</td>
<td id="T_6b3eb_row5_col4" class="data row5 col4">20434176</td>
<td id="T_6b3eb_row5_col5" class="data row5 col5">34435.367440</td>
<td id="T_6b3eb_row5_col6" class="data row5 col6">AUS</td>
<td id="T_6b3eb_row5_col7" class="data row5 col7">36</td>
</tr>
<tr class="odd">
<td id="T_6b3eb_level0_row6" class="row_heading level0 row6"
data-quarto-table-cell-role="th">83</td>
<td id="T_6b3eb_row6_col0" class="data row6 col0">Austria</td>
<td id="T_6b3eb_row6_col1" class="data row6 col1">Europe</td>
<td id="T_6b3eb_row6_col2" class="data row6 col2">2007</td>
<td id="T_6b3eb_row6_col3" class="data row6 col3">79.829000</td>
<td id="T_6b3eb_row6_col4" class="data row6 col4">8199783</td>
<td id="T_6b3eb_row6_col5" class="data row6 col5">36126.492700</td>
<td id="T_6b3eb_row6_col6" class="data row6 col6">AUT</td>
<td id="T_6b3eb_row6_col7" class="data row6 col7">40</td>
</tr>
<tr class="even">
<td id="T_6b3eb_level0_row7" class="row_heading level0 row7"
data-quarto-table-cell-role="th">95</td>
<td id="T_6b3eb_row7_col0" class="data row7 col0">Bahrain</td>
<td id="T_6b3eb_row7_col1" class="data row7 col1">Asia</td>
<td id="T_6b3eb_row7_col2" class="data row7 col2">2007</td>
<td id="T_6b3eb_row7_col3" class="data row7 col3">75.635000</td>
<td id="T_6b3eb_row7_col4" class="data row7 col4">708573</td>
<td id="T_6b3eb_row7_col5" class="data row7 col5">29796.048340</td>
<td id="T_6b3eb_row7_col6" class="data row7 col6">BHR</td>
<td id="T_6b3eb_row7_col7" class="data row7 col7">48</td>
</tr>
<tr class="odd">
<td id="T_6b3eb_level0_row8" class="row_heading level0 row8"
data-quarto-table-cell-role="th">107</td>
<td id="T_6b3eb_row8_col0" class="data row8 col0">Bangladesh</td>
<td id="T_6b3eb_row8_col1" class="data row8 col1">Asia</td>
<td id="T_6b3eb_row8_col2" class="data row8 col2">2007</td>
<td id="T_6b3eb_row8_col3" class="data row8 col3">64.062000</td>
<td id="T_6b3eb_row8_col4" class="data row8 col4">150448339</td>
<td id="T_6b3eb_row8_col5" class="data row8 col5">1391.253792</td>
<td id="T_6b3eb_row8_col6" class="data row8 col6">BGD</td>
<td id="T_6b3eb_row8_col7" class="data row8 col7">50</td>
</tr>
<tr class="even">
<td id="T_6b3eb_level0_row9" class="row_heading level0 row9"
data-quarto-table-cell-role="th">119</td>
<td id="T_6b3eb_row9_col0" class="data row9 col0">Belgium</td>
<td id="T_6b3eb_row9_col1" class="data row9 col1">Europe</td>
<td id="T_6b3eb_row9_col2" class="data row9 col2">2007</td>
<td id="T_6b3eb_row9_col3" class="data row9 col3">79.441000</td>
<td id="T_6b3eb_row9_col4" class="data row9 col4">10392226</td>
<td id="T_6b3eb_row9_col5" class="data row9 col5">33692.605080</td>
<td id="T_6b3eb_row9_col6" class="data row9 col6">BEL</td>
<td id="T_6b3eb_row9_col7" class="data row9 col7">56</td>
</tr>
</tbody>
</table>

``` python
a = 1
```

``` python
# Plotly Express scatterplot with title and label

fig = px.scatter(gapminder2007, 
                 x="gdpPercap", y="lifeExp", color="continent", 
                 size="pop", size_max=60,
                 hover_name="country",
                 title="Figure 1:  Bubble Chart of GDP and Life Expectancy")
fig.show()
```

        <script type="text/javascript">
        window.PlotlyConfig = {MathJaxConfig: 'local'};
        if (window.MathJax && window.MathJax.Hub && window.MathJax.Hub.Config) {window.MathJax.Hub.Config({SVG: {font: "STIX-Web"}});}
        if (typeof require !== 'undefined') {
        require.undef("plotly");
        requirejs.config({
            paths: {
                'plotly': ['https://cdn.plot.ly/plotly-2.27.0.min']
            }
        });
        require(['plotly'], function(Plotly) {
            window._Plotly = Plotly;
        });
        }
        </script>
        

![](M255_Notebook_Style_Guide_files/images/cell-6-output-2.png)

# Bibliography

Abbate, Carolyn. 2004. “Music—Drastic or Gnostic?” *Critical Inquiry*
30: 505-36.
