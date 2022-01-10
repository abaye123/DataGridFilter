<!--
Edited
https://dillinger.io/
https://kramdown.gettalong.org/quickref.html
-->
![GitHub release (latest by date)](https://img.shields.io/github/v/release/macgile/DataGridFilter)

<!-- [![Github All Releases](https://img.shields.io/github/downloads/<-- User Name-->/<-- Your Repo Name-->/total.svg)]() -->

[![Github All Releases](https://img.shields.io/github/downloads/macgile/DataGridFilter/total.svg)]()


# WPF Filterable DataGrid, multi language
![datagrid image demo](FilterDataGrid.png)  

A DataGrid control that inherits from the base DataGrid control class and override some methods to implement filters  
for each column like Excel, in automatic or custom generation.  

Translation of labels and formatting of dates in the following languages: English, French, Russian, German, Italian, Chinese, Dutch.

 > *The translations are from google translate, if you find any errors or want to add other languages, please let me know.*

The **Nuget package** is available [here](https://www.nuget.org/packages/FilterDataGrid/).

To understand how the filter works, you can consult the article posted on [CodeProject](https://www.codeproject.com/Articles/5292782/WPF-DataGrid-Filterable-multi-language).


## How to use
 - There are two ways to install :
   + NuGet command : **Install-Package FilterDataGrid**
   + Or manually add **FilterDataGrid.dll** as reference in your project
   
 - Add **FilterDatagrid** into your xaml :   
 
      - **Namespace**  
		```xml 
		<Window xmlns:control="http://filterdatagrid.control.com/2021" ...
		```
	  - **Control**   
		```xml 
		<control:FilterDataGrid 
		 FilterLanguage="English" DateFormatString="d" ShowStatusBar="True" ShowElapsedTime="False" ...
		```   
		- Properties
		  - **ShowStatusBar** : *displays the status bar*, default : false  
		  - **ShowElapsedTime** : *displays the elapsed time of filtering in status bar*, default : false  
		  - **ShowRowsCount** : *display the number of rows*, default : false  
		  - **DateFormatString** : *date display format*, default : "d" 
		  > You must delete the time or set it to zero in the DateTime field, otherwise the filter does not work.    
[see the documentation "Standard date and time format strings"](https://docs.microsoft.com/en-us/dotnet/standard/base-types/standard-date-and-time-format-strings)
		  - **FilterLanguage** : *translation into available language*, default : English   

		>  

 	> *If you add custom columns, you must set **AutoGenerateColumns="False"*** 
		
	  - **Custom TextColumn**   
		```xml
		<control:FilterDataGrid.Columns>   
		    <control:DataGridTextColumn IsColumnFiltered="True" ...
		```
	  - **Custom TemplateColumn**  
	    > ***FieldName** property of **DataGridTemplateColumn** is required*   
	    
		```xml
		<control:FilterDataGrid.Columns>   
		    <control:DataGridTemplateColumn IsColumnFiltered="True"
			                            FieldName="LastName" ...
		```

## Global Style ##

>You can define a global style which overrides the default style of "FilterDataGrid"  

```xml
<Style
            x:Key="FilterDatagridStyle"
            BasedOn="{StaticResource {ComponentResourceKey TypeInTargetAssembly=control:FilterDataGrid,
                                                           ResourceId=FilterDataGridStyle}}"
            TargetType="{x:Type control:FilterDataGrid}">
            <Setter Property="Margin" Value="10" />
            <Setter Property="RowHeaderWidth" Value="40" />
	    ...
</Style>
```

## Benchmark ##

> Intel Core i7, 2.93 GHz, 16 GB, Windows 10, 64 bits.  
> Tested on the "Last name" column of the demo application using a random distinct name generator, between 5 and 8 letters in length.  
> *The elapsed time decreases based on the number of columns and filtered items.*


Number of rows | Opening of the PopUp | Applying the filter | Total (PopUp + Filter)
 --- | --- | --- | ---
10 000 | < 1 second | < 1 second | < 1 second 
100 000 | < 1 second | < 1 second | < 1 second 
500 000 | ± 1.5 second | ± 1 second	| ± 2.5 seconds 
1 000 000 | ± 3 seconds	| ± 1.5 seconds	| ± 4.5 seconds 

## Demonstration ##
![datagrid image demo](capture.gif)  

## Contributors
<a href="https://github.com/macgile/DataGridFilter/graphs/contributors">
  <img src="https://contrib.rocks/image?repo=macgile/DataGridFilter" />
</a>

<!-- Made with [contributors-img](https://contrib.rocks). -->
