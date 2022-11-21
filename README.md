# PROJECT-VISUALIZATION


<< banner >>


The goal of this project is to work a database and to extract some information using a visualization tool (Power BI or Tableau).


## ETL


I choose some databases from Kaggle and The World Bank to get the **extraction**:

- Cause of deaths around the World (Historical Data) / (main)

- Cancer death rates in the world (add)

- Total population by Year (1990-2019) and Countries (add)


I decided to include cancer cases in the final database to keep it in mind and the total population to check the impact about all registered deaths as part of total population.

During the **transformation** of the main table :

- I navigated to the dataframe to check countries (204), years (30, from 1990 to 2019)

- I checked nulls, duplicates and data type.

During the **transformation** of the cancer table :

- I navigated to the dataframe to check years (30, from 1990 to 2019) and countries (267). Using a loop, I checked the common countries between cancer and main table and I got 203 countries in common and 64 countries that were not in the main table. The missing country was 'Micronesia' so I added to the cancer table with its code (FSM) and empty values (0). This way, I got the table with the countries I wanted with 29 more diseases (different types of cancer).

- Column names was changed for convenience.

- At this point, I merged main and cancer table, I created a new column as 'Total' with the sum of all diseases on table by year and country. Shape of both tables were the same. Data type was reviewed.

During the **transformation** of the population table :

- I navigated to the dataframe to check years (30, from 1990 to 2019) and countries (204). Checking countries, 175 were in the main table and 29 of them not but reviewing the population table I figured out typo errors, so I decided to take countries by Code and not by name. This way, only 189 countries were in common between both tables so the missing values were filled by zero.

- Column names was changed for convenience with RegEx.

- My main problem was about some missing values that were not nulls, were '..' and I tried RegEx, iloc, loc, loop.. and I did not obtain what I wanted to, so my solution was export the table as xlsx to modify the values by hand.

- Data type was corrected to int from object.

- The final population table had to be similar has the main where the columns were country, code, year and diseases, but it was not. Population table columns were country, code, years and population. So I created a new dataframe looping the columns I wanted to get the final table.

- Finally I merged main table (with cancer values) and population table to get my final database.

For my **loading** process, I uploaded the final table in Power BI to start with the visualization.


## Visualization

My objective with this database is to get the relevant information about most frequent diseases around the world and to know why they are as a Health professional. From now to the end of the visualization, you can call me Dr. Quintana. 

The top global causes of death, according the WHO (World Health Organization), in order of total number of lives lost, are associated with three broad topics: **cardiovascular** (ischaemic heart disease, stroke), **respiratory** (chronic obstructive pulmonary disease, lower respiratory infections) and **neonatal conditions** – which include birth asphyxia and birth trauma, neonatal sepsis and infections, and preterm birth complications<sup>**1**</sup>.

*China* has the highest value about **cardiovascular diseases** through the years (100 million of cases since 1990 to 2019), followed by India and Russia. Rapid socioeconomic progress has greatly affected the lifestyle in China. Consequently, owing to lifestyle changes, urbanization, and accelerated population aging, the risk of cardiovascular diseases (CVD) has increased<sup>**2**</sup>.

*India and China* are involved in several cases of **respiratory diseases** (lower respiratory infections and chronic respiratory diseases) with more than 40 million of cases since 1990 to 2019. One of the major sources of air pollution in China and India is from sulfur-dioxide emissions. The major contributor to the sulfur- dioxide emissions is due to increased coal consumption in the industrial sectors in both countries along the last decades<sup>**3**</sup>.

About **neonatal and maternal disorders**, *India* has reached more than 20 millions of cases since 1990 to 2019, far away from the second country (Pakistan) with near 8 millions of cases. There are three causes of all neonatal deaths in India: prematurity & low birthweight; neonatal infections, comprising pneumonia, neonatal sepsis and infections of the central nervous system; and birth asphyxia & birth trauma. Each of the major causes of neonatal deaths could be prevented or treated with known, highly effective and widely practicable interventions such as improvements in prenatal care, intrapartum care, postnatal family-community care and tetanus toxoid immunization. This has been possible among the years with better health conditions and hospitalary resources<sup>**4**</sup>.

**Cancer** has become a huge topic in nowdays diseases due to the constant growing of types and different cases, being responsible of a several amount of deaths by year: near a 60 million of deaths in 30 years in China, followed by near 20 millions of deaths in USA and India. While incidence and mortality rates for most cancers (including lung, colorectum, female breast, and prostate) are decreasing in the United States and many other western countries, they are increasing in several less developed and economically transitioning countries because of adoption of unhealthy western lifestyles such as smoking and physical inactivity and consumption of calorie-dense food. Indeed, the rates for lung and colon cancers in a few of these countries have already surpassed those in the United States and other western countries. Most developing countries also continue to be disproportionately affected by cancers related to infectious agents, such as cervix, liver, and stomach cancers<sup>**5**</sup>.

*China* has made considerable efforts to prevent and control cancer, but cancer is still a major national health problem. Besides the vast number of cancer cases, the different cancer profiles between China’s rural and urban areas, as well as by its east, middle, and west regions, reflect not only the uneven economic development, but also possibly dietary (low fruit and vegetable intake) and lifestyle (alcohol drinking and smoking) differences in the development of cancer. Developed countries have made strides in prevention of some cancers, such as tumors caused by smoking and chronic infections, the incidence of these cancers are on the rise in developing countries. For lung and liver cancers, mortality has increased rapidly mainly due to the increasing exposure of smoking and hepatitis B virus (HBV)/hepatitis C virus (HCV) infection. Other factors could be environmental factors, overweight and obesity, physical inactivity and reproductive factors<sup>**6**</sup>.

Instead of this situation in China, breast cancer is common in the *United States* and other developed countries, with one in eight women being diagnosed during their lifetime. The most common breast cancer risk factors are related to estrogen exposure over the course of our lifetime. A Western lifestyle increases these risk factors. In colon and rectum cancers in USA, researchers have found some evidence to suggest that obesity, sedentary behavior, poor diet and other environmental factors may play a role in increased rates of early onset colorectal cancer. Smoking is still the main cause of lung cancers in USA. Cigarette smoking is the number one risk factor for lung cancer. In the United States, cigarette smoking is linked to about 80% to 90% of lung cancer deaths. Using other tobacco products such as cigars or pipes also increases the risk for lung cancer<sup>**7**</sup>.
    
Looking back over the past years, not all of diseases show an important growing year by year. We can observe how some diseases have different trend for history circumstances, such as HIV/AIDS, Tuberculosis or Dementia.
    
    - **Tuberculosis** had a peak around 1990-1992 with near 1.8 million of cases that was decreasing throught the years until reaching almost a 40% less of affected people. Although tuberculosis can be completely cured with the proper treatment regimen, it remains one of the top 10 causes and the leading cause of death from a single infectious agent in 2019. A reduction was observed in the absolute number of deaths in 2000 where the number of cases declined slowly since a high growing up in 90s due to HIV epidemic, infected inmigrants and congregations<sup>**8**</sup>.
    
    - **HIV/AIDS**. The number of AIDS-related deaths increased throughout the 1990s and reached a peak in 2004-2005 when in both years close to 2 million people died. Since then the annual number of deaths from AIDS declined as well and was since halved. 2016 was the first year since the peak in which fewer than 1 million people died from AIDS. Keeping in mind pharmaceuticals allow infected people to live with HIV, AIDS-related deaths will decrease<sup>**8**</sup>. Graphic shows a close normal distribution when cases are low at the begining and end of the graphic with a peak in the middle.
    
    - **Dementia**. As the populations of the U.S. and Europe age and life expectancy increases, the prevalence of dementia and Alzheimer’s disease has dramatically increased, due to the larger pool of people in the ages of highest risk. Currently, 47 million people worldwide live with dementia. Due to the rapidly aging population, the number of people living with the disease is expected to triple over the next 30 years, as is the expected socioeconomic burden associated with dementia. We can appreciate this increase through the years, triplicating the dementia cases between 1990 and 2019<sup>**8**</sup>.
    
An interesting view of data places us in isolated cases where a disease, injury or accident has had a huge impact in death rates in a particular moment in history. I talk about deaths by malaria in Nigeria and Congo Republic, by poisonings in China, by heat/cold exposures, by forces of nature or terrorism and conflicts.

    - **Malaria**. Malaria remains a major cause of morbidity and mortality in Africa. Annually, *Plasmodium falciparum* infection causes more than 200 million clinical cases and over 400 000 attributable deaths on the continent, which accounts for 92% of the global malaria burden. In the period from 2000 to 2015, malaria burden reduced substantially in part due to a reinvigorated multilateral commitment to, and a 20-fold increase in international investment in, malaria control. Despite the declining trends through 2015, more recent estimates show that if the current increases in malaria cases and deaths continue, then the epidemic of malaria in 2030 might not be achieved<sup>**9**</sup>.
    
    - **Poisonings by CO in China**. Carbon monoxide (CO) poisoning is one of the most common causes of fatal poisoning worldwide. CO is produced by internal combustion engines, fossil fuel furnaces and fire and is toxic. Although the CO emissions of modern cars are controlled by regulatory standards, they remain highly toxic in poorly ventilated environments. CO poisoning is the most common type of accidental poisoning. The burden of CO poisoning in China is higher than that in middle sociodemographic index regions and that worldwide. This difference can be partly explained by differences in economic structures and sociohistorical factors in China. In underdeveloped areas, especially remote rural areas in northern China, local residents prefer to use honeycomb briquettes for household heating. Therefore, accidents related to events such as chimney blockages or poor ventilation occur frequently, resulting in high rates of CO poisoning<sup>**9**</sup>. 

    - **Environmental heat and cold exposure**. In Russia, you can get as cold as -60°C at night in eastern Siberia, but the steppe regions of the central country often have temperatures of 35 degrees and more. In India, exposure to extreme heat affects health directly, exacerbating underlying conditions such as cardiovascular and respiratory disease, and causing heat stroke, adverse pregnancy outcomes, worsened sleep patterns, poor mental health, and increased injury-related death<sup>**10**</sup>.
    
    - **Exposure to forces of nature**. In Indonesia, the Sumatra-Andamán earthquake (Indian ocean earthquake and tsunami) ocurred in 2004, affecting to more than 200.000 people. In Haiti, the 2010 earthquake struck the zone taking 250.000 lives. A cyclone hit Bangladesh in 1991 and the Cyclone Nargis hit Myanmar in 2008, taking more than 100.000 lives each<sup>**10**</sup>.

    - **Terrorism and conflicts**. Iraq war, placed between 2003 and 2011, took more than 100.00 lifes by terrorism and conflicts. Same for Afghanistan war (2001 - 2021) and Syria war (2011). Ethiopia was affected by the Ethiopian Civil War (1974-1991) and the Eritrean-Ethiopian war (1998-2000). The Rwandan genocide affected more than 500.000 people in 1994. Burundian civil war, 1993-2005, took more than 150.000 lives<sup>**10**</sup>.

Finally, a simple overview about total of deaths / total population show us that 1-2% of the country population had died by some of the registered diseases, assuming a huge value of deaths in whole termins. 


***So please, take care of yourself and of your closest people for making the world a healthier world ♥***



## Resources

https://www.kaggle.com/datasets/iamsouravbanerjee/cause-of-deaths-around-the-world

https://www.kaggle.com/datasets/bahadirumutiscimen/cancer-death-rates-in-the-world-19902019

https://data.worldbank.org/
 
1. https://www.who.int/news-room/fact-sheets/detail/the-top-10-causes-of-death
    
2. https://www.ncbi.nlm.nih.gov/pmc/articles/PMC7008101/
    
3. https://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=&cad=rja&uact=8&ved=2ahUKEwj4pLrai737AhUbY6QEHX2WBckQFnoECBgQAw&url=https%3A%2F%2Fdialnet.unirioja.es%2Fdescarga%2Farticulo%2F1993815.pdf&usg=AOvVaw1e-MYfEQJ16Minc9LIdDNl
    
4. https://www.ncbi.nlm.nih.gov/pmc/articles/PMC3042727/  
    
5. https://aacrjournals.org/cebp/article/19/8/1893/68607/Global-Patterns-of-Cancer-Incidence-and-Mortality   
    
6. https://www.annalsofoncology.org/article/S0923-7534(19)37527-1/fulltext
   https://weekly.chinacdc.cn/en/article/doi/10.46234/ccdcw2022.036
    
7. https://www.sbi-online.org/endtheconfusion/Blog/TabId/546/ArtMID/1586/ArticleID/467/What-Can-I-Do-to-Reduce-My-Odds-of-Being-Diagnosed-with-Breast-Cancer.aspx
   https://www.keckmedicine.org/blog/why-is-colorectal-cancer-on-the-rise-for-younger-people/   
    
8. https://ourworldindata.org/hiv-aids
   https://www.cdc.gov/tb/education/corecurr/pdf/chapter1.pdf
   https://www.hsph.harvard.edu/news/press-releases/dementia-incidence-declined-every-decade-for-past-thirty-years/
   
9. https://www.ncbi.nlm.nih.gov/pmc/articles/PMC9371476/
   https://gh.bmj.com/content/bmjgh/5/11/e003217.full.pdf
    
10.https://www.worlddata.info/europe/russia/climate.php
   https://www.wikipedia.com
   
    
    
    
    
    
    
    
    
    
    
    
