# Handedness_analysis
In this project, we will explore this phenomenon using age distribution data to see if we can reproduce a difference in average age at death purely from the changing rates of left-handedness over time, refuting the claim of early death for left-handers. This notebook uses pandas and Bayesian statistics to analyze the probability of being a certain age at death given that you are reported as left-handed or right-handed.


**Locating the old Left-Handed Demographic**

A survey conducted by National Geographic in 1986 garnered an extensive dataset comprising over a million responses. This dataset encompassed information regarding respondents' age, gender, as well as their hand preferences for tasks such as throwing and writing. Upon thorough examination of this dataset, researchers Avery Gilbert and Charles Wysocki observed a noteworthy pattern: the prevalence of left-handedness was approximately 13% among individuals below the age of 40, but gradually declined with increasing age to approximately 5% among those aged 80 and above. Their analysis further revealed that this age-dependent trend was predominantly influenced by the evolving social acceptance of left-handedness.

This intriguing discovery implies that the rates of left-handedness are not solely a product of one's chronological age but are intrinsically linked to the era in which one was born. Consequently, if the same survey were conducted today, we could anticipate a modified manifestation of the same distribution, contingent upon the prevailing attitudes towards left-handedness. This raises a fascinating question concerning the potential impact of this shifting rate on the apparent average lifespan of left-handed individuals. However, before delving into the implications for life expectancy, it is prudent to commence our exploration by graphically depicting the variations in left-handedness rates across different age groups.


![image](https://github.com/KV-4102/Handedness_analysis/assets/128924918/23ada2a8-48cd-4c89-bb47-a47a73219b5f)


**Trends in Left-Handedness Rates Across Eras**

Our next step involves the transformation of this dataset into a comprehensive plot illustrating the prevalence of left-handedness in relation to the birth year. To ensure a unified representation, we will compute an average rate by amalgamating data from both male and female participants.

Given that the original study was conducted in 1986, the resulting data from this transformation will provide us with a crucial insight – specifically, it will depict the proportion of individuals alive in 1986 who exhibit left-handedness tendencies, contingent upon their birth year.

![image](https://github.com/KV-4102/Handedness_analysis/assets/128924918/d5925390-83f5-4168-b7c8-97b90b7e1c7b)


**The Application of Bayes' Theorem**

It's crucial to recognize that the likelihood of passing away at a specific age, given that you are left-handed, is not equivalent to the probability of being left-handed given that you've reached a certain age. This disparity underscores the significance of Bayes' theorem, a fundamental concept in conditional probability, enabling us to revise our beliefs based on observed evidence.

Our objective is to compute the probability of one's demise at age A, denoted as P(A | LH), for left-handed individuals. Similarly, we seek the same probability for right-handers, denoted as P(A | RH).

Bayes' theorem can be applied to the two events we are concerned with: left-handedness (LH) and the occurrence of death at age A.

![image](https://github.com/KV-4102/Handedness_analysis/assets/128924918/838939bf-f82e-4e1a-a5ce-8ea86916d15c)


P(LH | A) represents the probability that an individual is left-handed, given that they passed away at age A. P(A) stands for the overall probability of death occurring at age A, and P(LH) is the overall likelihood of being left-handed. We will now proceed to calculate each of these three values, commencing with P(LH | A).

To determine P(LH | A) for ages falling beyond the original dataset, we must extrapolate the data to encompass earlier and later years. Given that the rates exhibit a plateau in the early 1900s and late 1900s, we will employ several data points at each extremity and calculate the average to estimate the rates for those time frames. While the choice of the number of points used for this estimation may be somewhat arbitrary, we will opt for 10 data points, considering that the data appears relatively stable until approximately 1910.


**Estimating Typical Lifespan**

To gauge the probability of reaching a specific age, A, we can leverage data that provides insights into the number of individuals who passed away in a given year and their respective ages at the time of death. By normalizing these figures in relation to the total number of individuals who passed away, we can view this dataset as a probability distribution, offering the likelihood of passing away at age A. The dataset we will utilize for this purpose is derived from the entire United States for the year 1999, representing the closest available data within the relevant time frame.

In the following section, we will import the dataset containing information about the distribution of ages at the time of death and generate a corresponding plot. The first column within the dataset pertains to the age, while the subsequent columns denote the number of individuals who passed away at each respective age.

![image](https://github.com/KV-4102/Handedness_analysis/assets/128924918/d0203f0e-6f84-433f-b947-f710d1da5d3d)


**Determining the Overall Probability of Left-Handedness**


In the preceding code section, we imported data that provides us with the foundation for calculating P(A). Now, our focus shifts to P(LH), representing the likelihood that an individual who passed away in our specified study year is left-handed, with no additional information available about them. This essentially characterizes the average prevalence of left-handedness within the deceased population. To ascertain this probability, we perform a calculation that involves summing the individual probabilities of left-handedness for each age group, weighted by the number of deceased individuals within each age category. Subsequently, we normalize this calculated value by dividing it by the total number of deceased individuals, yielding a probability.



In mathematical terms, the computation is represented as follows, where N(A) signifies the count of individuals who passed away at age A (as provided by the 'death_distribution_data' dataframe):


![image](https://github.com/KV-4102/Handedness_analysis/assets/128924918/d4f0ba43-f8b4-40a7-99a0-107a04ecda50)

**Dying while Left-Handed and Right-Handed**

Now that we have the means to calculate the three essential quantities - P(A), P(LH), and P(LH | A) - we can integrate them using Bayes' rule to determine P(A | LH). This represents the probability of attaining a particular age, A, at the time of death within the study year, provided that an individual is left-handed. To provide a meaningful context, it is crucial to compare this probability with P(A | RH), which signifies the likelihood of reaching age A at death for right-handed individuals.

![image](https://github.com/KV-4102/Handedness_analysis/assets/128924918/ed6248d5-df2d-4c16-8188-1c1872a7e618)


We will perform this calculation twice: once for left-handers and once for right-handers.


**Visualizing Conditional Probability Distributions**

Now that we have established functions for computing the probability of being a certain age, A, at the time of death for left-handed and right-handed individuals, let's proceed to create graphical representations of these probabilities across a spectrum of ages, spanning from 6 to 120 years.

It is worth observing that the distribution for left-handed individuals exhibits a distinctive peak below the age of 70. This intriguing phenomenon indicates that, among the deceased population, left-handed individuals are more likely to be of a younger age at the time of their demise.


![image](https://github.com/KV-4102/Handedness_analysis/assets/128924918/129e6d3c-278f-465b-aa4f-f287589c9fcf)

**The Decisive Assessment: Age at Death for Left and Right-Handers**

At last, the moment of truth has arrived, where we shall compare our findings with those of the initial study that indicated a nine-year disparity in the average age at death for left-handed individuals. We can accomplish this by computing the mean of these probability distributions, akin to how we calculated P(LH) earlier, by weighting the probability distribution with respect to age and subsequently summing the outcome

![image](https://github.com/KV-4102/Handedness_analysis/assets/128924918/ebe54637-727c-4931-863c-4d461c42f647)

Output:

![image](https://github.com/KV-4102/Handedness_analysis/assets/128924918/48283471-c367-469c-b9fd-99e65c3b1e77)

**Concluding Remarks**

Our investigation has unveiled a significant age difference between left-handed and right-handed individuals, primarily driven by the shifting prevalence of left-handedness within the population. This presents encouraging news for left-handers, dispelling the notion of a shorter lifespan due to sinistrality. The reported rates of left-handedness have surged from a mere 3% in the early 1900s to approximately 11% in the present day. As a consequence, older generations are more inclined to be categorized as right-handed rather than left-handed, leading to a larger proportion of elderly right-handers in a sample of recently deceased individuals.

It's important to note that our observed age gap is somewhat less than the 9-year differential reported in the original study. Several factors may have contributed to this variation:

1. We employed death distribution data from a time frame almost a decade later than the study (1999 instead of 1991), and we utilized data from the entire United States rather than California alone, as in the original study.
2. Our extrapolation of left-handedness survey results to encompass older and younger age groups may not precisely align with the actual rates for those age categories.
One potential avenue for future investigation is to determine the expected variability in the age difference arising purely from random sampling. By taking smaller samples of recently deceased individuals and assigning handedness based on survey probabilities, we can explore the distribution of age differences. How frequently would we encounter a nine-year age gap using the same data and assumptions? While we won't delve into this here, it remains a feasible endeavor with the available data and the tools of random sampling.

To conclude, let's calculate the anticipated age gap if we were to conduct the study in 2018 instead of 1990. The resulting gap is notably smaller, as the rates of left-handedness have remained relatively stable for individuals born after approximately 1960. Both the National Geographic study and the 1990 study transpired during a unique era when handedness rates were undergoing substantial change across the lifespans of most individuals, accentuating the contrast in handedness between older and younger generations.

![image](https://github.com/KV-4102/Handedness_analysis/assets/128924918/b5bcac11-4391-4bc6-a98d-886ffaafd9c7)




