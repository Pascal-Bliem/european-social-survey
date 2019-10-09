# Insights from the 8th European Social Survey

In this **full-stack data science project**, I will analyze the 8th European Social Survey. 

> *How do the citizens of European countries think about certain social issues? What about climate change, politics, immigration, individual well-being? How do people's opinions and beliefs differ within a country or among the countries?*

I attempt to answer these question here. After a contextual introduction, we will start with **data selection and cleaning**, followed by interactive **visualization and exploration**. In the second half of the project, we will gain deeper insights by employing **statistical inference** and **machine learning** methods and discuss their validity and interpretability.

If you come from a non-technical background, you may want to jump to the next section in which I provide a [non-technical short summary](#sum). If you are comfortable with reading Python code and have some basic knowledge of statistics and machine learning, better have a look at the whole project, which is contained in this [Jupyter notebook](./insights-from-the-european-social-survey-8.ipynb). The interactive visualization uses Java Script which cannot be rendered here on GitHub - please view the notebook [here on Jupyter's nbviewer](https://nbviewer.jupyter.org/github/Pascal-Bliem/european-social-survey/blob/master/insights-from-the-european-social-survey-8.ipynb). 

In case this link does not work, please go on [nbviewer.jupyter.org](https://nbviewer.jupyter.org/) and paste the URL  
https://github.com/Pascal-Bliem/european-social-survey/blob/master/insights-from-the-european-social-survey-8.ipynb  
into the search bar.

Thanks for your interest in the project, I hope you will find it interesting. If you have any questions, please feel free to message me.

## Non-technical short summary <a id="sum" ><a/>

This short summary is aimed at people who are interested in this cool project but are not so comfortable with reading code or discussing math details. I'll try to focus more on the interesting results, less on the technical details, and hopefully inspire you to look for what interests you in this survey. 

We'll cover the following parts here:
1. [Introduction](#introduction) - what is this project all about?
2. [Data selection and cleaning](#data) - bringing the data in a useful shape
3. [Exploration and visualization](#viz) - taking a look a the data's story
4. [Statistical tests](#stats) - how significant are the effects we observe?
5. [Predicting survey answers](#ml) - using algorithms to understand people
6. [Conclusion](#conclusion)

<p align="center">
<img src="./figures/europe.png" alt="europe" height="150"/>
</p>

### Introduction <a id="introduction"></a>
Europe is a vast and diverse continent and its population is a fascinating subject for sociological studies. The [European Social Survey](https://www.europeansocialsurvey.org/) provides great data sets for exactly that purpose. According to their own description, *"The European Social Survey (ESS) is an academically driven cross-national survey that has been conducted across Europe since its establishment in 2001. Every two years, face-to-face interviews are conducted with newly selected, cross-sectional samples. The survey measures the attitudes, beliefs and behaviour patterns of diverse populations in more than thirty nations."*. This data set contains the results of the 8th round of the ESS surveyed in 2016/17.

We may wonder, how do the citizens of European countries think about certain social issues?  What about climate change, politics, immigration, individual well-being? How do people's opinions and beliefs differ within a country or among the countries? I'm personally interested in these questions because I have been roaming around Asia for a long time but soon I may return to Europe. I've been quite disconnected from my home country but I heard the horror stories about anti-democratic political parties on the rise, anti-immigration tendencies, people denying climate change, and so on. One can easily get the impression from the media that many people are unhappy or dissatisfied about a lot of things. That's scary enough to make me want to check some actual numbers instead of listening to all the flashy headlines. Follow along while I dig into this data set to see what I should expect when I get back home to Europe soon. Oh, one more thing before we start: for whatever reason Israel took part in this survey; last time I checked Israel was not in Europe, but hey, welcome on board friends.

### Data selection and cleaning <a id="data"></a>
Before we can do any meaningful analysis, the data has to be in a tidy and organized shape. With such a big survey, however, it unfortunately does not come like this naturally. 44387 people took part in this survey. When dealing with a lot of numbers, it can be too easy to forget what is actually behind them - so at this point we should remind ourselves that each of these rows corresponds to a real human being who took the time for this survey. We should be grateful towards these people and appreciate their contribution to our scientific understanding. But now back to the data: Real data can be dirty! What does that mean in this example? 
 
<p align="center">
<img src="./figures/datacleaning.png" alt="datacleaning" height="150"/>  
</p>
<p align="center">
<em>Data cleaning</em> 
</p>

The answers to the survey questions are called **variables** or **features** in this context. These 534 variables per person are grouped in topics such as media and social trust, politics, subjective well-being, social issues, climate change etc. which contain important information for us, but also administrative variables (such as interview dates) and interview code variables, and country specific variables which do not contribute the information we are looking for, so we have to get rid of them first. We'll only keep the ones that answer questions like *"On a scale of 0 to 10, how much do you agree with..."* and a few others like, country, gender, and age.

Another point to consider is that the ordinal answers to questions are not all on the same scale (e.g. 1 to 5 vs. 0 to 10) and some of the scales seem to be in reverse order with respect to how the corresponding question was phrased. Sometimes it makes sense to vary scales in surveys if the social scientists from up to 30 different countries are interested in a specific degree of detail and maybe scales are reversed to avoid [leading questions](https://en.wikipedia.org/wiki/Leading_question) in the survey (questions which suggest a certain answer). Whatever the reason may be, it does not help our understanding; therefore, I re-reversed the respective scales. Please refer to the [survey documentation](./ESS8e02.1.pdf) for more details.

Of course, there are also invalid answers, e.g. when people refused to answer, they don't know, or the answer is missing for an unspecified reason. These invalid responses are encoded with a lot of different numbers and it is crucial to make sure they are identified correctly and do not accidentally end up in the analysis. Generally, there are a lot of different ways of how the question encoding was designed. This  may be the result of many different groups of people from different institutions and countries working on this survey. I'll spare you from the rest of the details here, but I hope I made clear that already a lot of time and effort has to go into data preparation before we can even start the analysis.

### Exploration and visualization <a id="viz"></a>
Now that we got the data cleaned, we want to find out what story it tells. We want to see what people answered to all these questions, how these answers differ by country or gender, and how the answers to some questions correlate with the answers to other questions. Which country is the happiest? Who feels the most trust in politics, feels most responsible for climate change, and do  women and men have different opinions on it? The best way to explore such questions is to visualize them in an interactive way so that we can click around, select different variables, and graphically see how the responses differ between the countries. Unfortunately, GitHub can not render the figures in an interctive way so you'll either have to see them in the project notebook, or I'll just show you the static version here.



