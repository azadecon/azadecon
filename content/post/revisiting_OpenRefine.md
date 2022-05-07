---
title: "Revisiting OpenRefine"
date: 2022-05-07T05:49:16+05:30
draft: false
author: Arshad
---



## What is OpenRefine and why use it:

(A detailed multi-part post series is to follow this summary post.)


When it comes to data, they come in various shapes and sizes. One special case is of cleaning textual data. Though it does not have to be qualitative in the likes of interviews which are detailed and is not within the scope of the tool used here. OpenRefine could be useful to clean data that has some structure, as in they are columnar. But within this restriction, they are somewhat messy. 

The survey data had responses which were not systematic and required interpretation. It contained spelling mistakes, had non-meaningful characters and data was not tidy. I have used OpenRefine to clean the data, at least for the primary steps. Thereafter I have imported the (somewhat) cleaned data in R for further cleaning and analysis.

**[Library carpentry](https://librarycarpentry.org/lc-open-refine/)** provides an excellent guide to install and to get a basic training on OpenRefine. 


## Additional comments to install OpenRefine (on Linux)
1. Downalod tar.giz from the **[OpenRefine website](https://openrefine.org/download.html)**
2. Install JAVA by `sudo apt install default-jre`
3. Extract OpenRefine.xxx.tar.giz into a folder and run `./refine` from the OpenRefine folder.


**[OpenRefine use manual](https://docs.openrefine.org/)** could be helpful when one delves deeper into the use.


Cleaning textual data might seem daunting and you would not know from where to begin. This is further complicated by the presence of full sentences, even more with half sentences and contextual, conversational responses. It is advisable to see the data (in most cases, a particular column) as a whole. What worked for me was to imagine myself interviewing the farmers. This is done by looking at only the unique values present in the column and not the every entry. Now that you have an idea about what kind of responses are there, this knowledge helps interpret the individual responses. This as a whole knowledge helps contextualise the incomplete and at times weird responses. 

Example: `Aapke paas kya bank khata hai?` ==> `Haan`; `ModiWala`; `Free wala`; `Bank mitra banwa diya tha, lekin Istemal nahi karte`. All these responses are affirmative but they are different in their information content. Which brings us to the next part of cleaning. The cleaning.

1. Try to extract maximum information possible while translating. Do not assume anything, do not infer more than what is provided. Do not take decisions at the stage of translation. At times it is tempting to infer a particular meaning of the responses but this should be avoided. Let such decision be left for the stage of analysis. For now only only a minimal change in the meaning should be employed.


1. Most common and useful features are going to be "text-facet", "text-filter", "cluster", "merge", "edit cells", "transform". Sometimes in that particular order.

1. The most used snippet of code used is `value.replace("old_value", "new_value")`. For example, if you have values `school` among others and you want to replace them with `india`. You can do so by using value.replace("school", "india"). Now if you have values `schooling` and `school` among others and you want to replace both of them with `india` and if you replace `school` first then you are going to be left with `india` and `indiaing`. Why? Order matters here. To execute a sensible replacement, it is better to follow a non-conflicting order. You should replace `schooling` first, followed by `school`. This principle makes sense with R as well. `Value replacemt` also works subsequently. The above replacement can be carried out as follows: `value.replace("schooling", "india").replace("school", "india")`












## Some additional tips on using OpenRefine.

1. Since OpenRefine uses (default) browser interface, it is advisable to use a separate one so that you do not clutter your workspace. 

2. Also, do not kill the background OpenRefine process (the terminal window). It might lead to data loss.

3. Additionally, it helps to increase the maximum heap size from the default one. On an 8 GB machine, 3-4 GB is ideal. 

4. Big raw datafiles would take a lot time to process each modifications. Which leads to slow data cleaning. It is advisable to load only a small portion of raw data.




























