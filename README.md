# Bridge Material and Design Analysis in Virginia, Washington, Texas and District of Columbia

## Introduction
Before bridges existed, people had to swim or travel by boat or ferry to move from one place to another, which could expose them to accidents in the water. The appearance of bridges provided a more convenient and safer way for people to travel for work, school, and daily activities. Thus, bridge engineering is vital in society, where every part of constructing a bridge needs careful consideration.

Material and design selection are especially important because they impact the safety, longevity, and functionality of bridges. For instance, choosing materials and designs that can withstand environmental and weather conditions in specific locations and support a certain number of users and average daily traffic is essential.

Therefore, this project focuses on material and design analysis for bridges in Virginia, Washington, Texas, and the District of Columbia. The goal is to explore which materials and designs are most popular in these states, identify the most common material and design combinations, and examine the association rules between material and design, both overall and for each state.

## Research Questions
1. Which materials are most popular across all states, and how does material popularity vary within each state?
   
2. Which designs are most popular across all states, and how does design popularity vary within each state?
 
3. Which material–design combinations are most frequently used across all states?
   
4. For each material, what percentage of bridges use each design across all states?
   
5. Which main span materials are most strongly associated with specific bridge designs across all states and within each state, and what factors contribute to these associations (support, confidence, lift)?

## Dataset Overview
The dataset was obtained from [InfoBridge](https://infobridge.fhwa.dot.gov/Data) on December 27, 2025, and filtered to include bridges located in Virginia, Washington, Texas, and the District of Columbia. It contains information such as state name, place name, county name, city name, structure number, structure length, average daily traffic, year built, main span material, main span design, bridge condition, bridge age, and other related attributes.

The dataset was loaded into Databricks as a Spark DataFrame. Selected columns — including state code, state name, structure number, owner agency, main span material, and main span design — were retained for analysis.

## Libraries Used
* **pandas** - data manipulation and analysis 
* **seaborn** - statistical data visualization 
* **matplotlib** - plotting and charting
* **pyspark.sql.functions** - Spark SQL functions and column operations   
* **pyspark.sql.window** - window functions in Spark 

## Project Files
* **README.md**  - project description and report
* **Bridge Analysis - Material and Design.ipynb** - Python Notebook
* **Bridge Analysis - Material and Design. html** - exported report for GitHub viewing

## Methods For Data Analysis
* The dataset was processed in Databricks using Spark, where selected columns were prepared, and text was standardized before further cleaning in a Pandas DataFrame.
  
* Data cleaning and preprocessing were then performed using Pandas in Python, including checking for duplicates, handling missing values, and preparing the data for exploratory analysis.
  
* Univariate analysis — such as identifying the top six materials or designs — was conducted across all states and within each state using Pandas, Seaborn, and Matplotlib in Python.
  
* Bivariate analysis — such as identifying the top 15 material–design combinations and examining the relationship between material and design — was performed using Pandas, Seaborn, and Matplotlib in Python.
  
* The dataset was then transferred back to Spark to implement association rule mining from scratch. Support, confidence, and lift were used to select the most meaningful rules across all states and within each state.

## Results
## Univariate Analysis
### Number Of Bridges By State
<img width="1630" height="1100" alt="image" src="https://github.com/user-attachments/assets/a1ccf569-69b7-4dcc-8767-0b3785f25b17" />

The first bar plot shows the number of bridges per state, with 56,949 bridges in Texas, 14,143 in Virginia, 8,519 in Washington, and 261 in the District of Columbia. 

Texas has the largest number of bridges among these states, while the District of Columbia has the smallest.
#
### Top 6 Material Counts Accoss These States
<img width="1802" height="1198" alt="image" src="https://github.com/user-attachments/assets/ce3bfb27-ca8f-4123-b75a-74dae3e1622c" />

The second bar plot shows the top six materials across these states, with 35,177 Concrete, 23,591 Prestressed Concrete, 9,936 Steel, 4,793 Steel Continuous, 3,693 Concrete Continuous, and 1,543 Prestressed Concrete Continuous bridges. 

Concrete is the leading material in this chart, indicating its widespread use across the selected states. It exceeds Prestressed Concrete by 11,586 bridges and is more than three times higher than Steel among the top six materials.

The dominance of concrete and prestressed concrete suggests a preference for materials that provide durability, cost efficiency, and flexibility across different bridge designs and traffic conditions.
#
### Top 6 Material Counts in Virginia
<img width="1804" height="1210" alt="image" src="https://github.com/user-attachments/assets/af30fab7-9ae3-4f97-8288-bb954a9ace62" />

The third bar plot shows the top six materials in Virginia, with 5,239 Concrete, 5,024 Steel, 1,641 Prestressed Concrete, 1,542 Steel Continuous, 323 Concrete Continuous, and 223 Prestressed Concrete Continuous bridges. 

Concrete remains the leading material for bridges in Virginia, with 215 more bridges than Steel, the second-highest material on the list.

Steel usage in Virginia is notably close to Concrete, suggesting a stronger presence of steel bridge construction compared to the overall trend.
#
### Top 6 Material Counts in Texas
<img width="1792" height="1216" alt="image" src="https://github.com/user-attachments/assets/11d5fe84-2c8d-419b-9545-a58f5bd78b88" />

The fourth bar plot shows the top six materials in Texas, with 28,444 Concrete, 19,207 Prestressed Concrete, 3,830 Steel, 2,982 Steel Continuous, 1,700 Concrete Continuous, and 287 Wood or Timber bridges. 

Concrete remains the leading material for bridges in Texas, with 9,237 more bridges than Prestressed Concrete. Texas closely resembles the overall trend in material popularity across states. 

This also indicates that the overall material trends across the selected states are largely influenced by Texas. Because Texas has the largest number of bridges among the selected states, its material distribution strongly shapes the overall material trends.
#
### Top 6 Material Counts in Washington
<img width="1808" height="1200" alt="image" src="https://github.com/user-attachments/assets/f1dd17f5-1e66-417c-9c1d-2a5169788f8a" />

The fifth bar plot shows the top six materials in Washington, with 2,715 Prestressed Concrete, 1,645 Concrete Continuous, 1,454 Concrete, 1,035 Prestressed Concrete Continuous, 962 Steel, and 452 Wood or Timber bridges. 

Prestressed Concrete is the leading material for bridges in Washington, with 1,070 more bridges than Concrete Continuous.

Washington differs from the overall trend in material popularity across these states. This variation in material choice may be influenced by factors such as weather conditions, geography, population, or traffic patterns in Washington state.
#
### Top 6 Material Counts in District of Columbia
<img width="2198" height="1202" alt="image" src="https://github.com/user-attachments/assets/c86f28c5-7147-4780-8de7-5f96d84ee0f6" />

The sixth bar plot shows the top six materials in the District of Columbia, with 120 Steel, 45 Steel Continuous, 40 Concrete, 28 Prestressed Concrete, 25 Concrete Continuous, and 1 Other Material Span, which nearly represents the overall material distribution of bridges in the District of Columbia. 

Since the District of Columbia only has 261 bridges compared to other states, nearly all bridges have been included on this list, except for two bridges.

“Other Material Span” is coded as 0 in [*Recording and Coding Guide for the Structure Inventory and Appraisal of the Nation’s Bridges* (FHWA)](https://www.fhwa.dot.gov/bridge/mtguide.pdf) and refers to materials are not classified as Concrete (1), Concrete Continuous (2), Steel (3), Steel Continuous (4), Prestressed Concrete (5), Prestressed Concrete Continuous (6), Wood or Timber (7), Masonry (8), Aluminum, Wrought Iron, or Cast Iron (9).
#
### Top 6 Design Counts Across These States
<img width="2396" height="1192" alt="image" src="https://github.com/user-attachments/assets/6386b9d4-0c2b-4f9b-894d-50e4a4966b87" />

The seventh bar plot shows the top six designs across these states, with 35,554 Stringer/Multi-beam or Girder, 25,274 Culvert, 7,776 Slab, 4,108 Box Beam or Girders – Multiple, 3,036 Tee Beam, and 1,588 Other Main Design/Construction bridges. 

Stringer/Multi-beam or Girder is the leading design across these states, with 10,280 more bridges than Culvert, the second-highest design on the list.

“Other Main Design/Construction” is coded as 00 in the *Recording and Coding Guide for the Structure Inventory and Appraisal of the Nation’s Bridges* (FHWA) and represents bridge designs that do not fall within the defined primary design categories in the coding guide.
#
### Top 6 Design Counts in Virginia
<img width="1974" height="1200" alt="image" src="https://github.com/user-attachments/assets/237ec2c7-3d3b-4dee-b7c0-a866c2a1e974" />

The eighth bar plot shows the top six designs in Virginia, with 6,699 Stringer/Multi-beam or Girder, 3,255 Culvert, 2,115 Slab, 833 Tee Beam, 497 Box Beam or Girders – Multiple, and 276 Arch – Deck bridges. 

Stringer/Multi-beam or Girder is the leading design in Virginia, with roughly twice as many bridges as Culvert and about three times as many as Slab. Virginia is similar to the overall trend in its top three most used designs.
#
### Top 6 Design Counts in Washington
<img width="1996" height="1200" alt="image" src="https://github.com/user-attachments/assets/acaaf55a-ece2-4eb7-a97e-6fc39618bf6e" />

The ninth bar plot shows the top six designs in Washington, with 3,534 Stringer/Multi-beam or Girder, 1,500 Slab, 1,065 Tee Beam, 617 Culvert, 616 Box Beam or Girders – Multiple, and 327 Channel Beam bridges. 

Stringer/Multi-beam or Girder remains the leading design in Washington, with more than twice as many bridges as Slab. While the leading design is consistent with the overall trend, the remaining design distribution differs from the overall pattern across states.
#
### Top 6 Design Counts in Texas
<img width="2382" height="1198" alt="image" src="https://github.com/user-attachments/assets/71562392-97ca-4540-ab1d-ae31d4b97950" />

The tenth bar plot shows the top six designs in Texas, with 25,157 Stringer/Multi-beam or Girder, 21,395 Culvert, 4,159 Slab, 2,985 Box Beam or Girders – Multiple, 1,534 Other Main Design/Construction, and 1,131 Tee Beam bridges.

Stringer/Multi-beam or Girder remains the leading design in Texas, with 3,762 more bridges than Culvert, the second-highest design on the list. 

Compared to other states in the analysis, Texas most closely resembles the overall trend in design popularity, as its top four most used designs match the overall pattern.
#
### Top 6 Design Counts in District of Columbia
<img width="1780" height="1198" alt="image" src="https://github.com/user-attachments/assets/50982181-1d0b-4799-9c1b-1723b050ea7e" />

The eleventh bar plot shows the top six designs in the District of Columbia, with 164 Stringer/Multi-beam or Girder, 23 Girder and Floorbeam System, 21 Frame, 18 Arch – Deck, 10 Box Beam or Girders – Multiple, and 7 Culvert bridges.

Stringer/Multi-beam or Girder remains the leading design in the District of Columbia, with 141 more bridges than Girder and Floorbeam System, the second-highest design on the list. While the leading design is consistent with the overall trend, the remaining design distribution differs from the overall pattern across states.

Overall, Texas is the most similar to the overall trend across states, sharing the same top four most used designs, followed by Virginia, which shares the top three most used designs. Washington and the District of Columbia do not follow the same pattern as the overall trend in their top six designs. Despite variations in design selection, Stringer/Multi-beam or Girder remains the leading design across these states.
#
## Bivariate Analysis
### Top 15 Material and Design Combinations Across States
<img width="500" height="500" alt="image" src="https://github.com/user-attachments/assets/546b2793-d811-4d38-971d-a3d98d42503f" />
<img width="2456" height="1200" alt="image" src="https://github.com/user-attachments/assets/fae1473c-bc55-44fe-9ec7-eec6df2710c4" />

The twelfth bar plot shows the top 15 combinations of material and design across states. The Concrete–Culvert combination leads the chart with 23,536 bridges, followed by Prestressed Concrete–Stringer/Multi-beam or Girder as the second-highest combination with 16,708 bridges, and Steel–Stringer/Multi-beam or Girder as the third-highest combination with 7,640 bridges. The leading combination has 6,828 more bridges than the second combination and more than triple the number of bridges compared to the third combination.
#
### The Relationship between Material and Design 
<img width="500" height="500" alt="image" src="https://github.com/user-attachments/assets/b846cb06-07ff-4280-aebc-d483fceee58c" />

<img width="991" height="936" alt="image" src="https://github.com/user-attachments/assets/fe2d88a9-a257-46fb-b616-722bd321fe96" />

The heatmap shows the relationship between material and design in percentage terms. In other words, it presents the percentage of bridges using each design within each material category.

Steel Continuous has 93.07% of bridges using Stringer/Multi-beam or Girder, which is the highest percentage in the results. This is followed by Wood or Timber with 92.55% using Stringer/Multi-beam or Girder, and Aluminum, Wrought Iron, or Cast Iron with 85.12% using Culvert.

Overall, Stringer/Multi-beam or Girder and Culvert appear as the dominant designs for several materials.
#
## Association Rules in Material and Design

Association rules in data mining are used to explore interesting relationships, correlations, or connections between variables in a dataset. The goal is to use rules to predict the occurrence of one item based on the presence of other items. For example, people who purchase milk may also buy bread and butter, or people who purchase bread may also buy butter and milk.

Association rules are measured using three key metrics: support, confidence, and lift.

### Formula

support = pair_count / total_bridges

confidence = pair_count / mat_count

lift = confidence / (des_count / total_bridges)

* Lift > 1: The pair occurs more often than expected by chance (strong association).
* Lift ≈ 1: The pair occurs as often as expected by chance (no association).
* Lift < 1: The pair occurs less often than expected (negative association).

Support is defined as the proportion of bridges that have a specific material–design pair out of all bridges, which is used to evaluate how common that pair is in the dataset.

Confidence represents the probability that a bridge uses a specific design given that it has a specific material, measuring how likely the pair is within that material category.

Lift indicates the strength of the association between material and design compared to what would be expected if they were independent.

### Best Rules

The best rules were filtered using support ≥ 0.01, confidence ≥ 0.30, and lift ≥ 1.10. The filtering criteria are explained below:

* Only material–design pairs that occur in at least 1% of all bridges (support ≥ 0.01) are considered.
* The design must appear in at least 30% of bridges with that material (confidence ≥ 0.30).
* The pair must occur at least 10% more often than expected by chance (lift ≥ 1.10).

These thresholds were selected to focus on meaningful and interpretable rules while reducing noise from rare combinations. 

The association rule metrics were computed manually in Spark to provide a transparent understanding of the relationship between material and design.
#
### Material and Design Best Rules Across States

The table of best rules is sorted first by lift from largest to smallest, followed by confidence and support in descending order.

<img width="2198" height="380" alt="image" src="https://github.com/user-attachments/assets/3bce225e-f9c3-4086-a26a-65fe9600fa95" />

The strongest rule is **Concrete Continuous → Slab**, which has the highest lift, indicating a strong association between this material and design.

The next strongest rule is **Concrete → Culvert**, showing that culvert design is highly common when concrete is used.

Another strong rule is **Steel Continuous → Stringer/Multi-beam or Girder**, suggesting this design is strongly associated with steel continuous bridges.
#
### Dominant Design for Each Material

The table below shows the top design rule with the highest lift (strongest association) for each material category.

<img width="2568" height="576" alt="image" src="https://github.com/user-attachments/assets/369cee2e-be24-49d2-83ab-ae6812fbbf39" />

The goal is to identify which design is most strongly associated with each material, providing insight into design preference by material type.

Because the overall best-rules table mainly highlights the most common material–design pairs, some materials may be underrepresented.

Therefore, selecting the top rule per material ensures that every material appears with its strongest design association, enabling more balanced insights across material categories and supporting material-specific planning considerations.
#
### Material and Design Best Rules in District of Columbia

The table of best rules is sorted first by lift from largest to smallest, followed by confidence and support in descending order.

<img width="2192" height="278" alt="image" src="https://github.com/user-attachments/assets/3bb571d5-e1ca-4aa7-93f0-0ecb3e2482a8" />

The strongest association is **Prestressed Concrete → Box Beam or Girders – Multiple**, followed by **Concrete Continuous → Frame**, while **Steel → Stringer/Multi-beam or Girder** represents the most common pairing rather than the strongest association.
#
### Material and Design Best Rules in Texas

The table of best rules is sorted first by lift from largest to smallest, followed by confidence and support in descending order.

<img width="2166" height="334" alt="image" src="https://github.com/user-attachments/assets/4a914078-a797-46e4-a9cd-6a6d03adf6cc" />

The strongest association is **Concrete Continuous → Slab**, followed by **Steel Continuous → Stringer/Multi-beam or Girder**. 

Although **Concrete → Culvert** ranks third by lift, it represents the most common material–design combination in Texas.
#
### Material and Design Best Rules in Virginia

The table of best rules is sorted first by lift from largest to smallest, followed by confidence and support in descending order.

<img width="2188" height="384" alt="image" src="https://github.com/user-attachments/assets/ae5f7eb1-699c-4e09-ba7b-b92b8b4e484b" />

The strongest association is **Concrete Continuous → Slab**, followed by **Prestressed Concrete -> Slab**. 

Although **Steel → Stringer/Multi-beam or Girder** has a lower lift, it represents the most common material–design combination in Virginia.
# 
### Material and Design Best Rules in Washington

The table of best rules is sorted first by lift from largest to smallest, followed by confidence and support in descending order.

<img width="2162" height="320" alt="image" src="https://github.com/user-attachments/assets/8fdf04e0-a571-48fb-a8e1-7ff520918159" />

The strongest association is **Wood or Timber -> Stringer/Multi-beam or Girder**, followed by **Concrete Continuous → Slab**.

Although **Prestressed Concrete → Stringer/Multi-beam or Girder** has a lower lift, it represents the most common material–design combination in Washington.
#
## Key Insights
* Concrete-based materials dominate bridge construction across states.
* Stringer/Multi-beam or Girder is the leading design in every state.
* Texas most closely matches the overall design trend; Washington and D.C. show greater variation.
* The most common material–design pair is Concrete → Culvert.
* Strong associations highlight typical design preference by material (e.g., Concrete Continuous → Slab, Steel Continuous → Stringer/Girder).
  
## Limitations
* This analysis only includes bridges from Texas, Virginia, Washington, and the District of Columbia, not all U.S. states.
* The study focuses on material and design selection and does not consider factors such as traffic volume, bridge condition, or structural dimensions.
* Results may not fully represent national patterns due to the limited geographic scope.

**Future work**: Expand the analysis to additional states and incorporate more variables to provide a more comprehensive view of bridge characteristics.

## References:
* [Choosing color palettes](https://seaborn.pydata.org/tutorial/color_palettes.html)
* [seaborn.heatmap](https://seaborn.pydata.org/generated/seaborn.heatmap.html)
* [Recording and Coding Guide for the Structure Inventory and Appraisal of the Nation’s Bridges* (FHWA)](https://www.fhwa.dot.gov/bridge/mtguide.pdf)
* [InfoBridge](https://infobridge.fhwa.dot.gov/Data)
* [Fundamental of Association Rule Mining](https://medium.com/image-processing-with-python/fundaments-of-associate-rule-mining-468801ec0a29)
* [Bridge design: process & considerations](https://fiveable.me/bridge-engineering/unit-2)
* [What Is the Most Effective Bridge Design? Key Factors for Structural Integrity and Longevity](https://morson-praxis.com/news/most-effective-bridge-designs/)
* [Why is concrete a popular commercial construction material?](https://www.evensonconcrete.com/news/why-is-concrete-a-popular-commercial-construction-material)
* [Steel Stringer/Multi Beam Bridges](https://www.ncdot.gov/initiatives-policies/Transportation/bridges/historic-bridges/bridge-types/Pages/steel-stringer.aspx#:~:text=Davidson%20County%20Bridge%2089%20on,later%20relocated%2C%20widened%20or%20strengthened.)
* [Spark SQL Guide](https://spark.apache.org/docs/latest/sql-ref-functions.html)


 


