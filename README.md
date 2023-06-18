**Project Write-Up: Census Data Analysis of Town B**

**Introduction**
Town B is a moderate sized town in-between two cities connected by motorways. The town does not 
have a university, but some students live in the town and go to the cities where the schools are. As a 
member of the local government team saddled with the responsibility of making decisions on the 
social amenity to be built on the unoccupied piece of land in the town and what sort of investment 
would fit the needs of the community, I have taken up the task to clean the data, analyse it and 
based on the analysis make recommendations to the team.

**Data Cleaning**
The first step I took was to use various exploratory data analysis methods to understand the data.
From the data exploration, I was able to note that some columns need to be cleaned before I start 
the analysis. Details of the cleaning step are highlighted below:

Age Column: The age column is in the float type. Age should be a whole number ideally. So, I 
converted the age column to integer. I also created another column to put the ages into groups for 
further analysis (Age Pyramid, etc)

Religion Column: I noticed 2,489 blank entries. When I dug further, I discovered that all in the 
population with age below 18 (2,431) have blank entries. These were left as they were, but the 
remaining 58 entries were changed to the unknown.
Someone’s religion was entered as empty string. I checked the other members of his household just to see what I can infer from them but only 
his wife is a Christian his children are still minors, so it is difficult to use that in generalizing for the family, so I change the empty string to unknown also.
Another person entered her religion as ‘Sith’. I initially thought this was misspelt but upon checking I noticed it’s a form of Jediism, which was not 
considered a religion in the UK(Diaz, 2017). I changed this to None.

Another entry in the religion column is ‘nope’ which I also changed to None as nope is an informal way of saying No (Cambridge Dictionary, 2023)
Marital Status Column: As with the religion column, all minors have their entries as blank, so I 
changed it to Single (Minor) to differentiate it from the single adults. 

There was an empty string entry, for this I checked the other members of his household then 
discovered that he is married to the head of the house and has 2 children, so I changed the entry to 
married.
Some entries who just turned 18 and are university students are married or divorced. It is 
very uncommon to be divorced or even married at that age especially when you are a university 
student. I changed these entries to ‘Single’.

I noticed some outliers
but I decided to keep 
them. For example, 
there are some old 
people (Age above 80)
who are single, I checked 
to ensure its not a mix 
up and discovered most 
of them are the only 
ones living in their 
household except a 
woman who has two 
sons living in her 
household. I decided to 
leave it as it were as it is 
not uncommon to have 
children as a single.

Occupation Column: The occupation column came to me as being tricky as there are 1,080 entries. It 
was difficult to work with it. I noticed an empty string, the person is a 9 year old and it is fitting to 
change the entry to ‘Student’ which is the entry for 5 to 9 years. I changed all students below 18 
years to ‘Student(Minor)’ to differentiate them from the other students (university students and PhD 
students).

I then created another column to categorize the occupation column so it will be easy to carry out 
further analysis. The categories created are:
• Student (Minor): All entries that contain the word ‘student’ and are below 18 years
• Child: Those entered as child from the onset
• Student: All students above 18 years including university and PhD students
• Retired: Any entry that contains the word ‘Retired’
• Unemployed: Those entered as unemployed from the onset
• Employed: Every other entry

Infirmity Column
The infirmity column contains some empty strings which I changed to “unknown” as there was no 
information to guide me in replacing them.


**Analysis**

Population Pyramid
The plot of population pyramid reveals that there is a concentration of the population in the school 
age bands and the middle age bands. This suggests that the birth rate is lower than it is in previous 
periods and that there may be migration of people into the town especially between 35 - 39 years


Birth Rate and Death Rate
The birth rate was computed by using the methodology in ONS (2023).The current crude birth rate is 11 births per thousand. I also calculated for the last 5 and 10 years 
using the estimated population and it was 15 and 17 respectively corroborating the evidence from 
the age pyramid that the birth rate for the town is declining.
The death rate was tricky to calculate since the data does not contain record of deaths. I will infer 
this by summing up the difference between the population in the different age band (the older ones, 
above 65 years as this difference is most likely as a result of death than migration). The death rate is 
estimated at 9 deaths per 1,000. This is lower than the birth rate, suggesting that there is a natural 
increase in population. However, we need to also consider other factors such as migration in 
population increase.

Household Occupancy
There are a total of 3,048 households in the town and the average household occupancy is 3. The 
average household size in the UK is currently at 2.4 while the areas with the highest rate have 3 as 
their size (ONS, 2022).
587 houses are over occupied in the town with 5 or more people living in each household accounting 
for 3,863 people accounting for 41% of the total population. If we are to ensure that no house is 
over-occupied, (except for large families who still have minors living them) there is need for 
additional 255 houses. This was derived by dividing the number of people in over-occupied houses 
by the average occupancy rate of the town, then subtracting the answer from the number of houses 
already over occupied

Street Housing
There are 105 streets in the town. The average number of households per street is 29 and there are 
34 streets with more than 29 households each. Meaning that only 32% of the streets are relatively 
densely populated. The plot below shows that the very densely populated streets in terms of 
households also have the highest occupancy rates, especially Love Avenue, Virgofix Crescent and 
Corporation Road. However, the city is generally sparsely populated, hence any need for housing 
should align with this notion.

Marriage and Divorce Rate

From the plot above, I can see that there is almost equality in the number of married male and 
female suggesting that the married couples stay together and a decline in the number of male 
divorcees compared to females, which suggests that some male partners move out of the town after 
getting divorced. I will use this in calculating my emigration rate later in the analysis.
The crude rates are calculated as seen in the table below:

Migration Rate 
I had to make a lot of assumptions here, as the data does not contain explicit information on 
migration. I will consider potential marital migration, student migration and temporary (lodgers and 
visitors).

Marital Migration: As seen earlier in figure 6, there is a difference in the number of female and male 
divorcees in the town, which suggests that male divorcees tend to move out of the town. I computed 
this difference as the potential marital emigration. From the population pyramid in figure 3, it is 
noteworthy that there is a sharp increase as we move from age band 30 – 34 to 35 – 39. I checked 
this difference (+133) and compared it with the relationship with head of house column. I noticed 
the sum of those who are husbands and wives to the head of house is 132. It might suggest that 
these 133 people moved in to the town when they got married. So, I took it as potential marital 
immigration.

Student Migration: Also from the population pyramid, it is obvious that there is a sharp decrease as 
we move from age band 20– 24 to 25 to 29 (being the age range for student graduation). I computed 
this as the student emigration rate.

Lodgers and Visitors Migration: 10% of the lodgers are students, so I assume they will move in and 
stay at least till they graduate. I also assumed that 10% more of the lodgers will move in more 
permanently to the town, making 20%. I then used this to compute the migration rate.
The total potential migration rate is computed as follows:

Potential Emigration = Potential Marital Emigration Rate + Potential Student Emigration Rate
Potential Immigration = Potential Marital Immigration Rate + Lodgers and Visitors Migration Rate
Potential Migration Rate = Potential Immigration – Potential Emigration
The potential migration rate is -13, which suggests that more people are leaving the town than 
moving in to the town.

To calculate total population change in the town, I used the method below:
Potential Population Change = Birth Rate – (Death Rate + Potential Migration Rate)
The potential population change is -11 per 1000 suggesting that the population is a slightly shrinking
population.

Employment Rate
There are 579 unemployed population in the town which is 6% of the total population and 8% of the 
employable population (Above 18 years). The unemployment rate is very high compared to UK’s 
current unemployment rate of 3.7% (ONS, 2023).
I reviewed the age groups of unemployed people and I saw that its more concentrated in the middle 
aged band. Which means these people can still work if we provide appropriate training for them. I 
used the minimum age of the retired people in the town as a benchmark to determine those who are 
still able to work. Any one who has not gotten to the retirement age should be able to work if trained
There are 545 people in this category 
which makes up 94% of the unemployed 
population. 

Let’s see how this can impact the 
unemployment rate. Assuming 100%
(although this is almost impossible) of 
the trainable people become employed 
afterwards, it will reduce the 
unemployment rate to 0.5%. Worst case 
scenario, if 60% of the trainable people 
become employed, it reduces 
unemployment rate to 3.6% which is just 
below the current UK rate.

Commuters
The data does not provide direct information about who might be a commuter. The only clear 
information we have about this is that there are university students living in the town but there is no 
university in the town. This means that these students commute to their school. I also considered 
the staff of the university, though it was not stated explicitly in the data. I searched for some 
keywords such as ‘Professor’, ‘Lecturer’, ‘Higher Education’ and ‘Research’. These are words common 
to a university. Using this method only, there are 622 people who regularly commute, and they make 
up 9% of the population.

Infirmity
Infirmity makes up only 0.7% of the population. The average disability rate in UK is 22% (House of 
Commons, 2022). This is too minute to impact any decision.

Religion
45% of the population are not religiously inclined. Christians are the next largest religion. However, 
building a church is not ideal as they have many different branches within it (BBC, n.d.). The 
Catholics are next in number, and they already have a church. I considered the methodists who have 
the next highest members. Their average age is 45 years and median age is 43. Which shows that it 
has a possibility of growing in future. Also, there are quite a number of family-oriented people either 
married or divorced who are also still in the child bearing / rearing age, it is possible as their children
mature, they take on their religion. However, it is difficult to ascertain this as there are no religion 
entries for minors.

**Summary**
Based on the data provided and the analysis carried out:
• The population is a slightly shrinking one at -11 persons per 1,000 annual population change 
when I compared the death and birth rate to the migration rate.
• There is housing deficit in the town as 41% of the population live in over occupied houses.
• Only 32% of the streets are densely populated with number of houses higher than the town’s 
street average.
• The unemployment rate is currently at 8% but can be reduced to 3.6% by providing adequate 
training to those unemployed who are still below the minimum retirement age.
• 9% of the population regularly commute. There might be others but its difficult to identify 
them.
• 45% of the population are not religiously inclined. It is difficult to identify growing religion or 
infer transferability since all minors do not have entries for religion.

**Recommendation**
The following recommendations are made:
• It is important to invest in housing as deficit is an obvious problem of the town. The structure 
of the town shows that low density housing is more common since most of the streets are 
within the average number of houses per street. Hence it is advisable to invest in low density 
housing to provide houses for the 255 households. 
• The unemployment rate in the town is high compared to the UK average and 94% of these
are still under the retirement age. Hence it is important to invest in training to enable them 
take up employment, reduce the unemployment rate and increase the economic growth of 
the town (Pettinger, 2018). It will also attract new immigrants and commuters to the town, 
thereby increasing the need for housing in future and possibly a train station.

**Bibliography**
BBC (no date) Branches of christianity - god and authority in Christianity - GCSE Religious Studies 
Revision - Edexcel - BBC Bitesize (no date) BBC News. BBC. Available online: 
https://www.bbc.co.uk/bitesize/guides/zbj48mn/revision/8 [Accessed on 27/04/2023].
Cambridge Dictionary (no date). Available online:
https://dictionary.cambridge.org/dictionary/english/nope [Accessed on 30/03/2023].
Diaz, A (2017) IN A PRISON FAR, FAR AWAY ‘Sith Lord’ lag whinges he cannot practice Star Wars 
religion inside as he is banned from wearing a hoodie. Available online: 
https://www.thesun.co.uk/news/2511556/ [Accessed on 30/03/2023].
House of Commons (2022) UK disability statistics: Prevalence and life experiences. Available online: 
https://commonslibrary.parliament.uk/research-briefings/cbp-9602/ [Accessed on 27/04/2023].
Office for National Statistics (ONS) (2023) Employment in the UK: February 2023. Available online:
https://www.ons.gov.uk/employmentandlabourmarket/peopleinwork/employmentandemployeetyp
es/bulletins/employmentintheuk/february2023 [Accessed on 26/04/2023].
Office for National Statistics (ONS) (2022) Household and resident characteristics, England and Wales: 
Census 2021. Available online:
https://www.ons.gov.uk/peoplepopulationandcommunity/householdcharacteristics/homeinternetan
dsocialmediausage/bulletins/householdandresidentcharacteristicsenglandandwales/census2021
[Accessed on 12/04/2023].
Office for National Statistics (ONS) (2023) User guide to birth statistic. Available Online: 
https://www.ons.gov.uk/peoplepopulationandcommunity/birthsdeathsandmarriages/livebirths/met
hodologies/userguidetobirthstatistics [Accessed on 12/04/2023].
Pettinger, T. (2018) Should full employment be the primary macroeconomic objective?, Economics 
Help. Available online: https://www.economicshelp.org/macroeconomics/macroessays/should-aimgovtbe-full-employment/ (Accessed on 27/04/2023).
