<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Visualize data with QuickSight

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-analytics-quicksight)

**Author:** Abegail Manalac  
**Email:** abby.manalac@gmail.com

---

![Image](http://learn.nextwork.org/excited_gray_zealous_miracle_fruit/uploads/aws-analytics-quicksight_6c7f7ef0)

---

## Introducing Today's Project!

In this project, I will demonstrate how to use Amazon QuickSight to analyze Netflix data and generate visualizations. This project demonstrates how to use cloud data services for data analysis.

### Tools and concepts

The services I used were QuickSight and S3. Key concepts I learned include working with manifest.json files, applying data visualization techniques such as charts and filters, and performing data refresh.

### Project reflection

The project took around 2 hours, including time spent on the demo. The biggest challenge was grasping how the manifest.json file functions. The most satisfying part was exporting the final visualizations as a PDF.

After completing this project, I plan to begin Day Three of the AWS Beginners Challenge. I’ll be starting that project tomorrow.

---

## Upload project files into S3

n this project, S3 is used to store two files: manifest.json, which informs QuickSight about the structure of the data, and netflix_titles.csv, which contains the raw data we’ll analyze.

I modified the manifest.json file by updating the S3 URI to point to the correct location of the dataset. This step is crucial because it enables QuickSight to locate and analyze the data properly.

![Image](http://learn.nextwork.org/excited_gray_zealous_miracle_fruit/uploads/aws-analytics-quicksight_3c3cd85a)

---

## Create QuickSight account

Creating a QuickSight account costs $0 as it comes with a 30 day free trial. Make sure to uncheck an add-on in the sign up flow called Pixel-Perfect Reports so you don't get charged.

Creating an account took me 5 minutes including setting up the S3 bucket permissions

![Image](http://learn.nextwork.org/excited_gray_zealous_miracle_fruit/uploads/aws-analytics-quicksight_f4ab4214)

---

## Download the Dataset

I connected the S3 bucket to QuickSight through the Datasets page. While there were many available data source options, I specifically chose S3.

The manifest.json file tells QuickSight how the dataset is structured, helping it interpret the data correctly for visualizations like charts and graphs. Without this file, QuickSight might misread the data and display it inaccurately.

![Image](http://learn.nextwork.org/excited_gray_zealous_miracle_fruit/uploads/aws-analytics-quicksight_6f874996)

---

## My first visualization

To create visualizations in QuickSight, I clicked a data field and it will auto-generate a suitable chart. You can also drag fields to the X or Y axis sections to control how the data is displayed.

The chart shows a breakdown of Netflix content by release year—how many shows or movies came out each year. It highlights over 8,800 total titles, with 2019 being the year that had the highest number of releases.

I created this graph by dragging the 'release_year' data label and then switching the default bar chart to a donut chart.

![Image](http://learn.nextwork.org/excited_gray_zealous_miracle_fruit/uploads/aws-analytics-quicksight_aff3aad7)

---

## Using filters

Filters are helpful for narrowing data to specific subsets you want to analyze. In this case, I used filters to focus on content released from 2015 onward, specifically in the categories of Action and Adventure, Thriller, and TV Comedies.

This visualization shows a breakdown of TV shows and movies that fall under three categories: Action & Adventure, TV Comedies, and Thrillers. I applied a filter using the "listed_in" data label to display only these specific genres.

![Image](http://learn.nextwork.org/excited_gray_zealous_miracle_fruit/uploads/aws-analytics-quicksight_c32248c5)

---

## Setting up a dashboard

As a final touch, I updated the chart titles in the dashboard to make them more readable and meaningful. Instead of the default titles that just listed data labels, the new titles clearly communicate the purpose of each chart.

Did you know you could export your dashboard as PDFs too? I did this by clicking Publish, then selecting Generate PDF from the top-right corner of the QuickSight analysis.

![Image](http://learn.nextwork.org/excited_gray_zealous_miracle_fruit/uploads/aws-analytics-quicksight_6c7f7ef0)

---

## Refreshing source data

---

---
