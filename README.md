![screenshot-2017-10-16 top 100 baby names 2017](https://user-images.githubusercontent.com/2945099/31634699-4cc78946-b2bc-11e7-93db-bd83b95f64d7.png)

## Data
This template is good for data that has

- Change over time
- Deviation

It's good at seeing outliners and picking out individual series that can be compared against each other. 

## Usage
This template is used in [baby names](https://www.ons.gov.uk/peoplepopulationandcommunity/birthsdeathsandmarriages/livebirths/bulletins/babynamesenglandandwales/2016#the-number-of-different-baby-names-in-2016) and [infant mortality](http://visual.ons.gov.uk/uk-drops-in-european-child-mortality-rankings/). 

## Features
This templates has 
- parameterisable URLs
- Autocomplete dropdown

## File Structure

The files for each chart should be of the following format:

![image1](https://user-images.githubusercontent.com/2945099/30038486-1e58ac22-91bd-11e7-8356-96fd6a65c33d.png)

The config file contains all the variables which you can adjust. Inside the folder for your multiline chart there are .csv files which contain the data for your graph. The lib folder contains javascript libraries used. You'll also need the images folder.

If you’re making several charts they can share the same “lib” file as follows

![image2](https://user-images.githubusercontent.com/2945099/30038487-1e5cae94-91bd-11e7-9081-0ddaada98876.png)
![image3](https://user-images.githubusercontent.com/2945099/30038489-1e5d9f70-91bd-11e7-8ca6-8456a303b9da.png)
![image4](https://user-images.githubusercontent.com/2945099/30038488-1e5d650a-91bd-11e7-9746-3b1acf695c96.png)

## Data file(s)
To make a responsive multiline chart save your data in csv form of the following format: 

| date | var1 | var 2 | var 3| ...|
| ------------- | ------------- | ------------- | ------------- |-------|
| 2000 |  null | 15  | 19  | 23  |
| 2001 |  12   | 16  | 20  | 24  |
| 2002 |  13   | 17  | 21  | 25  |
| 2003 |  14   | 18  | 22  | 26  |

It’s important to insure the date column is named exactly “date”, with a lower case d. The first variable is plotted as time on the x axis. For each var, a line is drawn and it's plotted over time. For no data use `null`.

## config.json

Open the “config.json” file.  You can open this in a text editor such as Notepad++ or TextEdit or download a code editor such as Atom, Dreamweaver, Brackets or Sublime Text 2.

### essentials
These contain the main variables which the chart will need and will possibly need changing for each new chart.
```
"graphic_data_array": ["under5.csv","neonatal.csv"],
```
contain the names of csv files of the data to plot. The data must be in csv form as outlined above. If you put more data files in, you can switch between the data using tab buttons at the top. 
```
"tab_names":["Under 5 mortality","Neonatal mortality"],
```
specifies the text to be used in the tab buttons at the top.


Specify the date format the data uses – see the [D3 wiki about time formatting](https://github.com/mbostock/d3/wiki/Time-Formatting). 
```"dateFormat":"%Y",```

```"lineColours":["#66c2a5","#fc8d62","#8da0cb","#e78ac3","#a6d854","#666"],``` specifies the colours for each of the lines. Values can be rgb(0,0,0), Hex values or colour names. 
```
"legendLabels" : [],
```
The legend can be set which draws little lines above the line chart, although this isn't necessary because choices appear in the dropdown box. 

```
"sourceText":["Source information"],
"sourceURL":["http://www.ons.gov.uk/ons"],
```
set the text and link for the source.

`"keepurl":false,` specifies whether to keep the same lines between top tabs. Set to `true` if you want this option. Otherwise it will get rid of your choices when you click on the top tabs. 

  
`"yAxisLabel":"per 1000 live births",` sets the y axis label at the top

`"yAxisLabel2":"",` sets the y axis at the bottom. 

`"yAxisScale":` set the scale for the y axis. Option include `auto_min_max`, `auto_zero_max` or can be specified with an array e.g. `[0,140]`

`"yAxisBreak":` if set to true creates an icon to symbolise break in y axis.

`"yAxisBreak_sm_md_lg": [52, 52, 52]` sets the y axis position of the break icon in small, medium and large views. 

### optional 
```
"margin_sm": [10, 15, 28, 30],
"margin_md": [10, 15, 28, 30],
"margin_lg": [10, 15, 28, 30],
```
Sets the margin for the three different view sizes

```
"aspectRatio_sm" : [16,13],
"aspectRatio_md" : [16,12],
"aspectRatio_lg" : [16,10],
```
Set the aspect ratio for the three different view sizes

`"mobileBreakpoint" : 610,` set the width where the chart switches to the smallest view

`"xAxisTextFormat_sm_md_lg" : ["%y", "%Y", "%b %y"],` specifies the number format for the x-axis for the three chart sizes
                
```
"x_num_ticks_sm_md_lg" : [7,17,17],    
"y_num_ticks_sm_md_lg" : [6,8,10],
```
Set the preference for number of ticks on x and y-axis. This can be overwritten by D3.

```
"centre_line" : false,
"centre_line_value" : 0
```
Adds a horizontal line at y value `centre_line_value`
