# Education-For-All-analysis
I was given a hypothetical problem to solve as a data analyst working for the charity, Education for All. I have been asked by the Head of fundraising to present the data on donor insights and donation rates. 

## Project Overview
-	Increase the number of donors in our database.
-	Increase the donation frequency of our donors.
-	Increase the value of donations in our database.

### Data sources
The primary data source for this analysis is the file link from the entrylevel platform.

### Tools
- Sqlite - analysis
- Tableau - visualization

### Exploratory Data Analysis
To understand the dataset, I asked questions as follows;

1.	What is the donation frequency rate?
2.	What is the donation frequency of the males’ and the females’?
3.	What is the sum of donations given once, weekly, monthly, and yearly?
4.	Who are the top 20 donors?
5.	Who are the least 15 donors?
6.	How many donors have a car?
7.	What is the average donation of donors from each job field?
8.	Which State gave the most donations? 

To get the business problem, I also used the root cause analysis to ask the questions below:

1.	Why is there no increase in the number of donors?
2.	Why is there a limited reach of donors in different States?
3.	Why do donors not have a clear view of what we have achieved so far?
4.	Why is there no age profiling of our donors in the data collected to give us a clear view of our target reach so far?

### Analysis
I was given two datasets to work with, EFO_Donation_Data containing data on;
-	Id
-	First_name
-	Last_name
-	Email
-	Gender
-	Job_field
-	Donation
-	State
-	Shirt_size

and EFO_Donor_Data containing data on;	
-	Donation_frequency
-	University
-	Car
-	Second_language
-	Favourite_colour
-	Movie_genre

Using SQLite, I imported both datasets to easily access them;

![image](https://github.com/VictoryOfejiro-O/education-for-all-analysis/assets/152421383/c4dde030-37c6-4079-9415-57b884fb0141)
I then joined both documents together using the JOIN command;
```sql
SELECT * FROM Donation_Data JOIN Donor_Data2 on Donation_Data.id = Donor_Data2.id;
```
```sql
 SELECT SUM(donation) FROM Donation_Data JOIN Donor_Data2 ON Donation_Data.ID = Donor_Data2.id;
```
```sql
SELECT SUM(donation) FROM Donation_Data JOIN Donor_Data2 ON Donation_Data.ID = Donor_Data2.id WHERE gender = 'Male';
SELECT SUM(donation) FROM Donation_Data JOIN Donor_Data2 ON Donation_Data.ID = Donor_Data2.id WHERE gender = 'Female';
```
```sql
SELECT * FROM Donation_Data JOIN Donor_Data2 ON Donation_Data.ID = Donor_Data2.id
ORDER by donation DESC
LIMIT 20;
```
```sql
SELECT * FROM Donation_Data JOIN Donor_Data2 ON Donation_Data.ID = Donor_Data2.id
WHERE donation <= 15
ORDER by donation DESC;
```
```sql
SELECT * FROM Donation_Data JOIN Donor_Data2 ON Donation_Data.ID = Donor_Data2.id
WHERE donation_frequency = 'Weekly';
SELECT * FROM Donation_Data JOIN Donor_Data2 ON Donation_Data.ID = Donor_Data2.id
WHERE donation_frequency = ‘Monthly’;
SELECT * FROM Donation_Data JOIN Donor_Data2 ON Donation_Data.ID = Donor_Data2.id
WHERE donation_frequency = ‘Yearly’;
SELECT * FROM Donation_Data JOIN Donor_Data2 ON Donation_Data.ID = Donor_Data2.id
WHERE donation_frequency = ‘Once’;
```
```sql
SELECT SUM(donation) FROM Donation_Data JOIN Donor_Data2 ON Donation_Data.ID = Donor_Data2.id
WHERE donation_frequency = 'Weekly'; 

SELECT SUM(donation) FROM Donation_Data JOIN Donor_Data2 ON Donation_Data.ID = Donor_Data2.id
WHERE donation_frequency = ‘Monthly’; 

SELECT SUM(donation) FROM Donation_Data JOIN Donor_Data2 ON Donation_Data.ID = Donor_Data2.id
WHERE donation_frequency = ‘Yearly’; 

SELECT SUM(donation) FROM Donation_Data JOIN Donor_Data2 ON Donation_Data.ID = Donor_Data2.id
WHERE donation_frequency = ‘Once’; 
```
```sql
SELECT count (donation) FROM Donation_Data JOIN Donor_Data2
on Donation_Data.id = Donor_Data2.id
where donation_frequency = 'Weekly';

SELECT count (donation) FROM Donation_Data JOIN Donor_Data2
on Donation_Data.id = Donor_Data2.id
where donation_frequency = ‘Monthly’;

SELECT count (donation) FROM Donation_Data JOIN Donor_Data2
on Donation_Data.id = Donor_Data2.id
where donation_frequency = ‘Yearly’;

SELECT count (donation) FROM Donation_Data JOIN Donor_Data2
on Donation_Data.id = Donor_Data2.id
where donation_frequency = ‘Once’;
```

### Tableau Visualizations
Figure 1: shows sum of donations given per gender and the frequency at which they were given.
![image](https://github.com/VictoryOfejiro-O/education-for-all-analysis/assets/152421383/6d4ec0a5-1a8f-44a8-9a9d-d03c21610b13)

Figure 2: Illustrates the amount of donations donors in different job fields/Industries donated.
![image](https://github.com/VictoryOfejiro-O/education-for-all-analysis/assets/152421383/eec1799b-f926-4ffa-829f-e93d66352991)

Figure 3: This shows the number of donors by their shirt size.
![image](https://github.com/VictoryOfejiro-O/education-for-all-analysis/assets/152421383/6343ce36-f375-4e03-9c34-87ee5d39f8b5)

Figure 4: Shows donations by their car owned, it is seen that most donations came from donors with the Ford car model.
![image](https://github.com/VictoryOfejiro-O/education-for-all-analysis/assets/152421383/ac5f89e9-0b32-48a4-9542-d3b95d0e523e)

Figure 5: Shows the state with the highest donations and the state with the highest number of donors. 
![image](https://github.com/VictoryOfejiro-O/education-for-all-analysis/assets/152421383/7639428b-aaca-445a-bc30-1067c7a39a68)
![image](https://github.com/VictoryOfejiro-O/education-for-all-analysis/assets/152421383/f48e8b96-fd82-4a9c-89e2-dd05cf1b64cc)

### Findings
- The total amount of donations was 249085.
- The number count of donations that came in was 1000.
- The number of donors that donate the highest donated either yearly or once than weekly or monthly as shown in Figure 1. Also, the males gave higher than the females.
- Most donations came from those in universities and even though others weren’t, it did not affect the donations ratio much. Most of the higher donations came from donors who reside either in California, Texas, or Florida respectively as seen in Figure 5.
- Donors in the research and development, legal and training industries respectively gave higher donations as shown in Figure 2.

### Recommendation/Conclusion
- To overcome the problem of low donations because people are unable to give or continue giving much, the data should show the organization's reach and success outcome as a motivation to loyal and intending donors. 
This can be achieved when we place more focus on large-scale global advertisement marketing in donor states and especially in states that had not gotten awareness of the charity program, thereby bringing awareness to the public on what people face without proper education and what measures have been successfully carried out to provide education to those that either cannot afford or access it. This would help in bringing more donors from different states, even states that had not participated in the donations before.
- Proper measures must also be taken to improve the database, for instance; movie genre, favorite color, car, and even shirt size data collected are not necessary, we need to create a database that provides the age group of donors as this will help us narrow down our market target, giving a clear picture of where our market target focus should be when carrying out our market strategy.





