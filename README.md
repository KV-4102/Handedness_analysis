# Handedness_analysis
In this project, we will explore this phenomenon using age distribution data to see if we can reproduce a difference in average age at death purely from the changing rates of left-handedness over time, refuting the claim of early death for left-handers. This notebook uses pandas and Bayesian statistics to analyze the probability of being a certain age at death given that you are reported as left-handed or right-handed.

**1)Locating the oldLeft-Handed Demographic**

A survey conducted by National Geographic in 1986 garnered an extensive dataset comprising over a million responses. This dataset encompassed information regarding respondents' age, gender, as well as their hand preferences for tasks such as throwing and writing. Upon thorough examination of this dataset, researchers Avery Gilbert and Charles Wysocki observed a noteworthy pattern: the prevalence of left-handedness was approximately 13% among individuals below the age of 40, but gradually declined with increasing age to approximately 5% among those aged 80 and above. Their analysis further revealed that this age-dependent trend was predominantly influenced by the evolving social acceptance of left-handedness.

This intriguing discovery implies that the rates of left-handedness are not solely a product of one's chronological age but are intrinsically linked to the era in which one was born. Consequently, if the same survey were conducted today, we could anticipate a modified manifestation of the same distribution, contingent upon the prevailing attitudes towards left-handedness. This raises a fascinating question concerning the potential impact of this shifting rate on the apparent average lifespan of left-handed individuals. However, before delving into the implications for life expectancy, it is prudent to commence our exploration by graphically depicting the variations in left-handedness rates across different age groups.


![image](https://github.com/KV-4102/Handedness_analysis/assets/128924918/23ada2a8-48cd-4c89-bb47-a47a73219b5f)

**Trends in Left-Handedness Rates Across Eras**

Our next step involves the transformation of this dataset into a comprehensive plot illustrating the prevalence of left-handedness in relation to the birth year. To ensure a unified representation, we will compute an average rate by amalgamating data from both male and female participants.

Given that the original study was conducted in 1986, the resulting data from this transformation will provide us with a crucial insight – specifically, it will depict the proportion of individuals alive in 1986 who exhibit left-handedness tendencies, contingent upon their birth year.

![image](https://github.com/KV-4102/Handedness_analysis/assets/128924918/d5925390-83f5-4168-b7c8-97b90b7e1c7b)
