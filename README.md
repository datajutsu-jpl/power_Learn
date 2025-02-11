# Healthcare - Dashboard

###Questions(KPIs)

	- What is the total count of patients since 2019?
	- What is the average stay?
	- What is the total revenue generated?
	- How many patients fall under  18-35 age buckets and other buckets?
	- Note down what medication was given to treat the patient [most and least prescribed]
 	- what are the medicine was effective in normal patients?
 	- Find out how may patients have taken cigna insurance?
  	- what is the count of the patient from California, Alabama, Alaska combined, and how many have cancer?
  	- which blood type patients are under diabetes?
	- Summarize how many patients have been admitted under various admission types and result type for the same?
	- Analyse the number of counts are normal ,admission type,gender percentage, state, blood type and insurance wise.


## Problem Statement

	This dashboard helps in understanding the patients medical record. It Also comes in handy in terms of . It also comes in handy in knowing the medical status, improvements and progress by some particular sates.
	Through the therapy given through different medications we can get to know their improvement areas and effectiveness of the same, thus the treatment cane be improved.
	It also lets us know the average stay,total patient, revenu generaed and many more.

### Steps followed 

 - Step 1 : Loaded data into Power BI Desktop, dataset as a exce file.
 - Step 2 : Open power query editor & in view tab under Data preview section, check "column distribution", "column quality" & "column profile" options.
 - Step 3 : Also since by default, profile will be opened only for 1000 rows so you need to select "column profiling based on entire dataset".
 - Step 4 : It was observed that couple columns which appeared irrelevant and added no values to the data set were removed.
 - Step 5 : Columns like name, medical condition, insurance provider had improper case, Hence formatted to properly.
 - Step 6 : Created a calculated column and named years inorder to exract only the years from the date column.
 - Step 7 : Created the a custom column for age buckets , wrote dax to achieve this.
 - Step 8 : Created a seerated measures table to roganize the data effeciently neatly.
 - Step 10 : Renamed columns accordingly and changed the data type.
 - Step11 : Sorted the data set based on name column alphabetically.
 - Step 12 : From the visualization pane, visuals were added to derive the insights.
 - Step 13 : Since the data contains various aspects displaying the history of meical, thus in order to represent the data different visual were added using the three ellipses in the visualizations pane in report view. 
 - Step 14 : Visual filters (Slicers) were added for four fields named "Medical Codition", "State", "Gender & "Insurace Provider".

 - Step 15 : Three card visuals were added to the canvas, one representing total patients along with average stay & other representing revenue generated.
         	  Using visual level filter from the filters pane, basic filtering is being used.
            
 	 In the above  report view, under the insert tab, a text box was added to the canvas, wherein the title was mentioned.


 - Step 16 : With reference of the date column extracted the year , for a better visual represntation.

Snap of the column 




 -Step 17: Created new column and following DAX expression written:
       
      Age Category = SWITCH(
    TRUE(),
        Healthcare[Age]<= 18, "Below 18", 
        Healthcare[Age]> 18 && Healthcare[Age] <= 35, "18-35",
        Healthcare[Age]> 35 && Healthcare[Age] <=50, "35-50",
        Healthcare[Age]> 50 && Healthcare[Age] <=65, "50-65",
        Healthcare[Age]> 65, "above 65"
        )
Snap of new calculated column ,

![Image](https://github.com/user-attachments/assets/fb5f717d-8973-4d46-8881-c8be824e8028)

        
 - Step 18 : New measure was created to find total count of patients

Following DAX expression was written for the same,
        
	Total Patients = DISTINCTCOUNT(Healthcare[Name])
        
A card visual was used to represent count of customers.

![Image](https://github.com/user-attachments/assets/3ae3e270-676c-4449-8e05-9bb6b1c4877d)

        
 - Step 19 : New measure was created to find  the average stay  
 
 Following DAX expression was written to find the average stay  
 
      	Average Stay = AVERAGEX(Healthcare,DATEDIFF(Healthcare[Date of Admission],Healthcare[Discharge Date],Day)) 
 
 A card visual was used to represent this perecntage.
 
 sanp of the average stay  
 
![Image](https://github.com/user-attachments/assets/788bc500-6afe-4936-94ec-951c80f7ce35)

 - Step 20 : Created a measures for calculating the revenue generated

	Revenue = SUM(Healthcare[Billing Amount])

A card visual was used to display the revenu genarated
 
![Image](https://github.com/user-attachments/assets/016b291d-f9cb-45ee-8a8e-9d34db6d2f1a)
 
above cards are intereactive with thfilters created

Line Chart

 - Step 21 : Decomposition tree was added to the report design to describe the levels as heirarchy 
	.
	(a) Total patients

  	(b) years
  
  	(c) medical condition
  
  	(d) Result type 
  
  	(e) result type 

Snap of the visual

![Image](https://github.com/user-attachments/assets/31d6c391-f318-458e-9fac-2925890b6f09)
  
Bar Chart

 - Step 22 : created bar chart for showcasing the count of patients with the admission type and test result. 
create seperately for admission type and reult and created bookmarks using the added an chart functionality  switching between the visuals.

 - Step 23 : created bar chart for viualizin count of patients by age group 
	added text box for name of the visuals 

	count of patient under below 18 = 0.6k
	count of patient under 18-35 = 9.8k
	count of patient under 35-50 = 8.9k
	count of patient under 50-65 = 9k
	count of patient under above 65 = 11.9kk
	etc.. 
snap of the bar chart

![Image](https://github.com/user-attachments/assets/a42437ee-6125-4a1e-91e7-35f952a1e3b7)

The count gives the appropriate count when filter comes into the action.

 -Step 24 : Created bar chart for cisualizing the count of patients admitted with type, this is helpful in showing the patients incomming and outgoing with result types

	The total admission including all the types
	2019 - 5.34k
	2020 - 8.16k
	2021 - 8k
	2022 - 8.01k
	2023 - 7.94k
	2024 - 2.79k
	
snap of the bar chart for admission type

![Image](https://github.com/user-attachments/assets/0e9ce541-4c04-4485-9e58-b2f835004855)

 - Step 25 : Added a bar chart for result type with bookmarks to switch between the visuals
	
	The total patients including all the result types
	2019 - 5k
	2020 - 8k
	2021 - 8k
	2022 - 8k
	2023 - 8k
	2024 - 3k

snap of the bar chart for result type

![Image](https://github.com/user-attachments/assets/f431bf05-39b2-4dad-a603-cfaef15afe69)

The count gives the appropriate count when filter comes into the action.

Pie  chart

 - Step 26 : Created a pie chart for visualize the percentage of medications given to the patient in order treat the patient.
	added text box for name of the visuals 
	
	most prescribed medicine is Lipitor
	least prescribed medicine is paracetamol

snap of the pie chart

![Image](https://github.com/user-attachments/assets/9f97ce2a-5ecd-4d4c-b9a7-7a0cce46fbb3)

 - Step 27 :  Created three bookmarks namely for opeining the slicer, closing the slicer ,clearing all the applied filters and bar chart switching,
	 alongside Used selection pane to group the visuals accordinlgy to manage the dashboard effieciently.

snap of the bookmarks and selection pane

![Image](https://github.com/user-attachments/assets/160bbc30-ad85-4d6d-9e94-c10d9f16d6e3)
 - Step 28:  Edited the tool tip by giving the similar colors accross the dashboard and font.

 - Step 29 : Created filters and added fields like insurance provider, gender, state, result type, medical condtion and blood type.

snap of the filters

![Image](https://github.com/user-attachments/assets/a437aece-ee4a-4cea-bf12-8791f07e0550)

# Snapshot of Dashboard 

![Image](https://github.com/user-attachments/assets/4407abc2-c11c-485b-958b-974597275322)

# Insights

	A single page report was created on Power BI Desktop & published to Power BI Service.

	###Following inferences can be drawn from the dashboard.

### [1] Total Number of Patients = 40000

   Number of patients fall under normal type(Male) 
	normal		
	2019 = 859 	
	2020 = 1372
	2021 = 1314
	2022 = 1397

      Number of patients fall under abnormal type(Female) = 6767
	abnormal		
	2019 = 824	
	2020 = 1345
	2021 = 1371
	2022 = 1354

	Average stay per patients is 16 and 15 through out.

### [2] patients by age catedgory

    a) Below 18 = 6.8k
    b) 18-35 = 9.8k
    c) 35-50 = 8.9k
    d) 50-65 = 9k
    e) above 65 = 11.9k
    
  
  	These count  will change if different visual filters will be applied.  
  
  ### [3] Most Prescribed medicine 
  
      a) Asthma - Paracetamol(20.48%)
      b) hypertension - aspirin(20.53%)
Will change according to the visual filters applied.

 ### Other insights
 
	Over the years it is noted that for diabetes the most effect category are above 65 at the same time 18-35 age category pateints have also been a victim of diabetes.
	Coming to the medication part for diatbetes ibuprofen, lipitor and pencillin are majorly prescribed. 
	The normal count of the patient over the years it is noted that only 2019 and 2024 has recorded the least at the same time can't deny the fact that the admissions in those two years were comparatively lower.

### Conclusion

	There are no big differences among the test result despite of the admission type, hence need to work improving the medical standards from better to best.Hereby the medical associations, 
	hospitals and doctors must come up with different medcaitions and treatment methods.If done we can expect a good rise in the result in coming years.
