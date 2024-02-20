# Predictive-Analysis-of-Financial-Well-being-and-Health-with-PySpark-
Conducted detailed analysis correlating financial, situational, and demographic factors with individual health. 

Approach:
We had the following objectives when starting this project:

Identifying a business problem that adds value in a real-time setting.
Achieving efficiency in distributed (big data) processing during the whole project.

We initially discussed collecting live data, but owing to time and availability constraints, we restricted ourselves to data already available. We allocated a reasonable amount of time to identify a potential business problem and to collect its associated data - During this time we explored open data repositories such as data.gov, data.worldbank.org, dataverse.harvard.edu and also explored possibilities of scraping web data if we found a suitable problem for analysis.

In this process, we came across this gem of a dataset (consumerfinance.gov/data-research/financial-well-being-survey-data): A public use file containing information on a survey conducted by the Consumer Financial Protection Bureau(CFPB) in 2016 to assess the financial well-being of people living in the United States. The survey is well conducted with a comprehensive coverage of audiences from different backgrounds and demographics. The survey questionnaire is also very well-designed to ensure that an individual's exact financial state is captured along with relevant circumstances based on studies. This data seems to have been used in several studies and experiments, but with a wealth of information in it, there is so much more to extract from this data.

We took time to study each variable represented in this survey and CFPB's intent in capturing them. We also studied the response labels for each variable and designed our data pre-processing accordingly. The dataset(217 columns) can be categorized into the following sections for easier understanding:

individual and household characteristics
income, employment, and saving characteristics
financial experiences and behaviors
As a group, we looked into existing materials available on this dataset (as time allowed) and proposed several statistical and predictive analytics to be done on this data. We picked one that is most relevant and continued our analysis based on that proposal, which will be explained in the coming sections.

Objective:
The survey had some very interesting features - the individual's financial knowledge, their family situation, and their financial preferences to name a few. One that caught our attention is the feature 'health'. This is the individual's general take on their health and they were allowed to pick one among 5 options (ranging from 1-Poor to 5-Excellent). The intent of CFPB behind capturing this field is to see if and how an individual's health affects their financial well-being and the extent of it. While this is a good assumption, there is also the possibility that a person's health can be affected by their current financial status and by some other factors that have been captured in this dataset. Some interesting ones that stood out to us are -

'MATERIALISM': How much a person values material things such as cars and social status
'CONNECT': Psychological connectedness of a person to their environment
'MORTGAGE' and 'SAVINGS'
'FWB': The person is ahead or behind with their finances
While these fields may show interesting patterns, there could be so many other financial factors in the 217 columns that contribute to the overall health of an individual. To get a better correlation and to make the distinction lines a bit more clear, we club the existing categories to form 2 final categories.

1(Poor) and 2(Fair) will be clubbed into (0-Poor health)
3(Good), 4(Very Good), 5(Excellent) will be clubbed into (1-Good health)
Use of Technology:
The primary focus in our analysis was on achieving efficiency and scalability with processing - as is the intent of the ISM6562 course. While this data is not necessarily considered as 'big' in comparison to today's computing and storage systems' abilities, we ensured that this approach would work even if the data is scaled up. To achieve this we used specific technologies and made some assumptions which will be explained further.

We picked RDD-based Apache Spark over Apache Hadoop MapReduce for parallel computation owing to its better performance in iterative jobs which we would need for our project.
We will be working with a single-node cluster, but our analysis will assume operating on a multi-node cluster in all stages - the technicalities hidden by Spark's interface (We assume our program runs in the master node, and that the data is present in the data node)
