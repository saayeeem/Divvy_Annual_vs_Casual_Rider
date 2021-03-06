---
title: 'Cyclistic Company: A Case Study between Annual Member vs. Casual Rider 2021'
author: "Mohammad Sayem Chowdhury"
date: "2/01/2022"

---
https://saayeeem.github.io/Divvy_Annual_vs_Casual_Rider/

https://www.kaggle.com/saayem/divvy-annual-vs-casual-rider
## Introduction 

Welcome to the Cyclistic bike-share analysis case study! In this case study, I am performing many real-world tasks of a junior data analyst. I am working for a fictional company, Cyclistic, and meet different characters and team members. In order to answer the key business questions, I am following the steps of the data analysis process: **ask**, **prepare**, **process**, **analyze**, **share**, and **act**. 

## Scenario

I am a junior data analyst working in the marketing analyst team at Cyclistic, a bike-share company in Chicago. The director of marketing believes the company’s future success depends on maximizing the number of annual memberships. Therefore, me and my team wants to understand how casual riders and annual members use Cyclistic bikes differently. From these insights, me and my team will design a new marketing strategy to convert casual riders into annual members. But first, Cyclistic executives must approve my recommendations, so they must be backed up with compelling data insights and professional data visualizations.

## About the company
In 2016, Cyclistic launched a successful bike-share offering. Since then, the program has grown to a fleet of 5,824 bicycles that are geotracked and locked into a network of 692 stations across Chicago. The bikes can be unlocked from one station and returned to any other station in the system anytime.

Until now, Cyclistic’s marketing strategy relied on building general awareness and appealing to broad consumer segments. One approach that helped make these things possible was the flexibility of its pricing plans: single-ride passes, full-day passes, and annual memberships. Customers who purchase single-ride or full-day passes are referred to as casual riders. Customers who purchase annual memberships are Cyclistic members.

Cyclistic’s finance analysts have concluded that annual members are much more profitable than casual riders. Although the pricing flexibility helps Cyclistic attract more customers, Moreno believes that maximizing the number of annual members will be key to future growth. Rather than creating a marketing campaign that targets all-new customers, Moreno believes there is a very good chance to convert casual riders into members. She notes that casual riders are already aware of the Cyclistic program and have chosen Cyclistic for their mobility needs.

Moreno has set a clear goal: Design marketing strategies aimed at converting casual riders into annual members. In order to do that, however, the marketing analyst team needs to better understand how annual members and casual riders differ, why casual riders would buy a membership, and how digital media could affect their marketing tactics. Moreno and her team are interested in analyzing the Cyclistic historical bike trip data to identify trends.

## Ask Phase

From the company description we already know that there is two types of users: Casual riders and Annual members.Now my task is: "How do annual members and casual riders use Cyclistic bikes differently?". Here we will go through the usage data of casual riders and annual members then try to find out their using behaviour and why the differences between them in different metrics.

We are using facts to guide the business of our company strategy which also known as data-driven decision.Data is everywhere in today's world and the evolving of technology increasing it more and more.So making a decision based on data is the best option rather than making a decision from gut instinct. By solving this problem or gain insights from data we can use it for our membership advertisement to specific people or we could use this insights to see which membership are giving us more profit. 

## Prepare Phase


As our company is fictional, we are working with a real-world data company for the purpose of our case study and answer our business question.The data has been made and available by Motivate International Inc. under this [license](https://www.ride.divvybikes.com/data-license-agreement).


For the capstone project, i download the relevant data and store the data in the subfolder of our capstone project folder called data. We took 12 months data of 2021 and all data in csv format.Now first start

### Setting up my environment
Note: Setting up my R environment by installing "tidyverse" and "lubridate" packages
```{r}
library("tidyverse")
library("lubridate")
```

```{r}
january_df <- read_csv("Data/202101-divvy-tripdata/202101-divvy-tripdata.csv")
glimpse(january_df)
row_january <- nrow(january_df)
as_data_frame(january_df)
```

```{r}
february_df <- read_csv("Data/202102-divvy-tripdata/202102-divvy-tripdata.csv")
row_february <- nrow(february_df)
as_data_frame(february_df)

```

```{r}
march_df <- read_csv("Data/202103-divvy-tripdata/202103-divvy-tripdata.csv")
row_march <- nrow(march_df)
as_data_frame(march_df)
```

```{r}
april_df <- read_csv("Data/202104-divvy-tripdata/202104-divvy-tripdata.csv")
row_april <- nrow(april_df)
as_data_frame(april_df)
```

```{r}
may_df <- read_csv("Data/202105-divvy-tripdata/202105-divvy-tripdata.csv")
row_may <- nrow(may_df)
glimpse(may_df)
as_data_frame(may_df)
```

```{r}
june_df <- read_csv("Data/202106-divvy-tripdata/202106-divvy-tripdata.csv")
row_june <- nrow(june_df)
glimpse(june_df)
as_data_frame(june_df)
```

```{r}
july_df <- read_csv("Data/202107-divvy-tripdata/202107-divvy-tripdata.csv")
row_july <- nrow(july_df)
glimpse(july_df)
as_data_frame(july_df)
```

```{r}
august_df <- read_csv("Data/202108-divvy-tripdata/202108-divvy-tripdata.csv")
row_august <- nrow(august_df)
glimpse(august_df)
as_data_frame(august_df)
```

```{r}
september_df <- read_csv("Data/202109-divvy-tripdata/202109-divvy-tripdata.csv")
row_september <- nrow(september_df)
glimpse(september_df)
as_data_frame(september_df)
```

```{r}
october_df <- read_csv("Data/202110-divvy-tripdata/202110-divvy-tripdata.csv")
row_october <- nrow(october_df)
glimpse(october_df)
as_data_frame(october_df)
```

```{r}

november_df <- read_csv("Data/202111-divvy-tripdata/202111-divvy-tripdata.csv")
row_november <- nrow(november_df)
glimpse(november_df)
as_data_frame(november_df)
```

```{r}
december_df <- read_csv("Data/202112-divvy-tripdata/202112-divvy-tripdata.csv")
row_december <- nrow(december_df)
glimpse(december_df)
as_data_frame(december_df)
```

There is no issues with data bias and credibility because it is a Reliable,Original,Comprehensive,Current and Cited.

The data has proper license, does not contain the Personal Identifiable Information (PII) so privacy and security properly maintained. It is a open source data so it has free access, usage and sharing of data for all.

Data integrity means the accuracy,completeness,consistency, and trustworthiness of data throughtout it's life-cycle. For verify this, we research about the company and the data lives within the company's own systems.

The data has following variables/columns Trip start day and time,Trip end day and time,Trip start station,Trip end station,Rider type (Member, Single Ride, and Day Pass) so it will help answer our questions by process, analyze and making visualization from those data.

The data is in raw format so i need to clean the data then i could perform the analysis.

## Process Phase 


I choose to work with R and Tableau because the data is too large for working with Google Sheets or Excel.Also,with R it's easy to reproduce analysis, processing lots of data and creating data viz.

Here,I have a data of different months in different csv files. Now, I want to merge all data in one place. To do that:
```{r}
cyclist_2021_raw_data <- rbind(january_df,february_df,march_df,april_df,may_df,june_df,
                           july_df,august_df,september_df,october_df,november_df,december_df)

glimpse(cyclist_2021_raw_data)
as_tibble(cyclist_2021_raw_data)
```


To ensure that the data is valid and data integrity is in good form, i perform a logical condition to
see the condition of data after merging and before merging.

```{r}
cyclist_row <- nrow(cyclist_2021_raw_data)
print(cyclist_row)
all_month_row <- (row_january + row_february+ row_march + row_april + row_may + row_june +
                   row_july + row_august + row_september + row_october + row_november + row_december)
print(all_month_row)
if (cyclist_row == all_month_row){
  print("Data Merged Successful")
}else{
  print("There is a probelm with data merging")
}
as_tibble(cyclist_2021_raw_data)
glimpse(cyclist_2021_raw_data)
```


We use "drop_na()" functions to clean na value so that the na value cannot hamper in our analysis. Also, we add "distinct()" function to remove duplicate values and a new column "ride_length" by subtracting 'started_at' column value from 'ended_at' column. I also ensure that there is no negative value in our dataset by filter-out all the 'started_at' value which is greater than 'ended_at' value

```{r}
cyclist_2021_cleaned_data <- cyclist_2021_raw_data %>%
  drop_na() %>% 
  filter(ended_at>started_at) %>% 
  distinct() %>% 
  mutate(ride_length=ended_at - started_at)
as_tibble(cyclist_2021_cleaned_data)
```

Convert the ride-length in 'hms' by hms function.

```{r}
cyclist_2021_cleaned_data$ride_length <- hms::hms(seconds_to_period(cyclist_2021_cleaned_data$ride_length))
as_tibble(cyclist_2021_cleaned_data)
```

Add another column "day_of_week" to see which day they are starting the ride. Here, I use 1=Sunday and 7 = Saturday.

```{r}
cyclist_2021_cleaned_data <- cyclist_2021_cleaned_data %>%
  mutate(day_of_week=wday(started_at)) %>% 
  arrange(started_at)
as_tibble(cyclist_2021_cleaned_data)
```


To verify the cleaning process, i tried to discover the value is in right form or not by checking there 
positive or negative value validation.

```{r}
if ((cyclist_2021_cleaned_data$start_lat && cyclist_2021_cleaned_data$end_lat && 
    cyclist_2021_cleaned_data$ride_length >0) &&(cyclist_2021_cleaned_data$start_lng &&
      cyclist_2021_cleaned_data$end_lng < 0)){
  print("Data Cleaned Successful")
}else{
  print("Still need some cleaning")
}

glimpse(cyclist_2021_cleaned_data)
as_tibble(cyclist_2021_cleaned_data)
```

## Analyze

To analyze the data we organize it in our project as our requirements.We prepare the data and process it in our previous phase. Now, it's time to analyze the data.

To format the data, I perform a research on datasets there i found that if any "ride_length" is less 60 seconds than it should be a false data so i filter-out those data by "filter" function.Also, sorted the data with 'started_at' column by 'arrange' function.

```{r}
cyclist_2021_cleaned_data <- cyclist_2021_cleaned_data %>%
  rename(member_type=member_casual) %>% 
  mutate(day_of_week=wday(started_at)) %>% 
  arrange(started_at) %>% 
  filter(ride_length > hms::hms(seconds_to_period(60)))
as_tibble(cyclist_2021_cleaned_data)
```


As earlier, we knew that there is three packages for users: single-ride passes, full-day passes, and annual memberships. The first tow types of packages for casual riders and they only allowed to take passes for 24-hours but in our data it's extended sometimes. For that reason i filter-out those data which is extended 24-hours for casual riders.

```{r}
summary1_df <-cyclist_2021_cleaned_data %>% 
  group_by(member_type) %>% 
  summarise(min_ride_length =hms::hms(seconds_to_period(min(ride_length))),
            average_ride_length =hms::hms(round(seconds_to_period(mean(ride_length)))),
            max_ride_length =hms::hms(seconds_to_period(max(ride_length))))

as_tibble(summary1_df)

cyclist_2021_cleaned_data <- cyclist_2021_cleaned_data %>%
  filter(!(member_type=="casual" & ride_length > hms::hms(seconds_to_period(86400))))

View(cyclist_2021_cleaned_data)
```


We need to use 'mode' function in our analysis. Though i thought there will be a package for that i could not find any so i use a manual mode function which i took from this [site](https://www.statology.org/mode-in-r/). With 'mode' function we could find the *most* occured value. 
```{r}
#define function to calculate mode
mode<- function(x) {
  u <- unique(x)
  tab <- tabulate(match(x, u))
  u[tab == max(tab)]
}
```

Now, it is time for analyzing data.First try to do a descriptive analysis by finding the minimum,average,and maximum of ride_length with each type of member.Also,I convert the ride_length in 'hms' format and grouped all the same type of member with "group_by" function.
```{r}
summary2_df <-cyclist_2021_cleaned_data %>% 
  group_by(member_type) %>% 
  summarise(min_ride_length =hms::hms(seconds_to_period(min(ride_length))),
            average_ride_length =hms::hms(round(seconds_to_period(mean(ride_length)))),
            max_ride_length=hms::hms(seconds_to_period(max(ride_length))),most_ride_length=hms::hms(seconds_to_period(mode(ride_length))))
as_tibble(summary2_df)

```

From the summary, the average ride_length of casual rider is *00:28:30* which is greater than annual member's average ride_length *00:13:23* and the maximum,minimum ride_length is almost *same*.The interesting thing is most of ride legth for casual meber is *00:08:32* and annual member is *00:05:52* so both of riders took short-time ride. Now, let's find most_trips_day_of_the_week,most_used_bike,most_trips_started_station,,most_trips_ended_station,most_trips_started_month,most_trips_ended_month with the help of our mode function and total_trips.

```{r}
summary2_df <-cyclist_2021_cleaned_data %>% 
  group_by(member_type) %>% 
  summarise(min_ride_length =hms::hms(seconds_to_period(min(ride_length))),
            average_ride_length =hms::hms(round(seconds_to_period(mean(ride_length)))),
            max_ride_length =hms::hms(seconds_to_period(max(ride_length))),
            most_ride_length=hms::hms(seconds_to_period(mode(ride_length))),
            most_trips_day_of_the_week=mode(day_of_week),most_used_bike=mode(rideable_type),
            most_trips_started_station=mode(start_station_name),most_trips_ended_station=mode(end_station_name),most_trips_started_month = mode(months(as.Date(started_at))),most_trips_ended_month = mode(months(as.Date(ended_at))),total_trips = n())
as_tibble(summary2_df)
```

Most of the casual rider took their trips in *7th day of week(saturday)* where annual member took their rides in *4th day of week(thrusday)*.The total trips comes from annual member riders are *2500603* and casual riders are *2026429*.Annual member rider took their trips in *august* month most of the time and *july* for casual riders. Casual rider start and end their ride in *Streeter Dr & Grand Ave* station and Annual member riders start and end their rides in 	*Clark St & Elm St* station. Both type of riders most used *classic bike* most of the time.

Now see what we find if we group together the member type value and day of week. Let's find average_ride_length and total_trips.Sort the value with "total_trips"

```{r message=FALSE}
summary3_df <- cyclist_2021_cleaned_data %>% 
  group_by(member_type,day_of_week) %>%
  summarize(average_ride_length =hms::hms(round(seconds_to_period(mean(ride_length)))),
  total_trips=n()) %>%
  arrange(-total_trips)
as_tibble(summary3_df)
```
So the highest trips in the 7th day of week for casual member which is 463358 and for annual member it's 4th day and 391943 trips.Now Sort the value with "average_ride_length"

```{r}
summary3_df <- cyclist_2021_cleaned_data %>% 
  group_by(member_type,day_of_week) %>%
  summarize(average_ride_length =hms::hms(round(seconds_to_period(mean(ride_length)))),
  total_trips=n()) %>%
  arrange(-average_ride_length)
as_tibble(summary3_df)
```
Here, the average_ride_length shows that the casual member took most lengthy ride than the annual member rider.Let's find out about round trip. Round trip is a trip where start and end station is same in a single ride.

```{r}
round_trip_df <- cyclist_2021_cleaned_data %>% 
  filter(start_station_name==end_station_name) %>% 
  mutate(month = months(as.Date(started_at))) 
round_trip_summary <- round_trip_df  %>% 
  group_by(member_type) %>% 
  summarise(min_ride_length =hms::hms(seconds_to_period(min(ride_length))),
            average_ride_length =hms::hms(round(seconds_to_period(mean(ride_length)))),
            max_ride_length =hms::hms(seconds_to_period(max(ride_length))),
            most_ride_length=hms::hms(seconds_to_period(mode(ride_length))),
            most_trips_day_of_the_week=mode(day_of_week),most_used_bike=mode(rideable_type),
            most_trips_started_station=mode(start_station_name),most_trips_ended_station=mode(end_station_name),most_trips_started_month = mode(months(as.Date(started_at))),most_trips_ended_month = mode(months(as.Date(ended_at))),total_trips = n())
as_tibble(round_trip_df)

```


## Share

Make a dataframe for visualization. Here, we add a month column and convert the ride length into seconds for making a good visualization.Now, we make another column for calculating month.As the maximum ride length is in 24hrs so we can calculate start or end month same.

```{r}
viz_df <- cyclist_2021_cleaned_data %>% 
  mutate(month = months(as.Date(started_at))) 

viz_df$ride_length <- period_to_seconds(hms(viz_df$ride_length))

as.tibble(viz_df)

```

To save the dataframe in local computer:

```{r}
#write.csv(viz_df, file ='Data/cyclist_2021_cleaned_data.csv')
```

First, see the initial ride trips of both type of member.
```{r}
ggplot(data = viz_df) +
  geom_bar(mapping = aes(x = member_type))+
  scale_y_continuous(labels = function(x) format(x, scientific = FALSE)) +
  labs(title="Comparison of trips by member type",
       caption=paste0("Data of 2021 by DivvyBikes"),
       x="Member Type",
       y="Number of Trips")


```
The viz shows that member type riders took most trips than casual rider.


### Visualize trips in week 

Now, let's see it in the week day and the use of rideable_type.
```{r}
p <- ggplot(data = viz_df) +
  geom_bar(mapping = aes(x = member_type,fill=rideable_type))+
  facet_wrap(~day_of_week,scales = "free_x")
p + scale_y_continuous(labels = function(x) format(x, scientific = FALSE)) +
  labs(title="Comparison of trips of each day in week by member type for ride trips",
       caption=paste0("Data of 2021 by DivvyBikes"),
       x="Member Type",
       y="Number of Trips")+scale_fill_brewer(direction = -1, palette = "Purples")

```

From the viz, we can see no. of trips of member and casual riders and their used bike in each day of week.Casual riders took their rides in Saturday(7) and Sunday(1) which indicates they took their rides most in weekend. For member it's all most same in each day but they they prefer to use only classic bike and electric bike.

```{r}
w <- ggplot(data = viz_df) +
  geom_bar(mapping = aes(x = member_type,y=ride_length,fill=rideable_type),stat = "identity")+
  facet_wrap(~day_of_week,scales = "free_x")
w + scale_y_continuous(labels = function(x) format(x, scientific = FALSE)) +
  labs(title="Comparison of ride length of each day in week by member type",
       caption=paste0("Data of 2021 by DivvyBikes"),
       x="Member Type",
       y="Ride Length(seconds)")+scale_fill_brewer(direction = -1, palette = "Blues")
```
Most of the casual rider took their ride length constantly higher in every week day than member rider. 

### Visualize trips in month 

Let's see the total trips in each month.

```{r}
ggplot(data = viz_df) +
  geom_bar(mapping = aes(x = member_type,fill=rideable_type))+
  facet_wrap(~fct_inorder(month),scales = "free_x") + 
   scale_y_continuous(labels = function(x) format(x, scientific = FALSE)) +
  labs(title="Comparison of trips of each day in week by member type for ride trips",
       caption=paste0("Data of 2021 by DivvyBikes"),
       x="Member Type",
       y="Number of Trips")+scale_fill_brewer(direction = -1, palette = "Purples")
```

Most of the trips took in June,July,August and Semptember. Though, In July, casual rider took highest trips and member rider took their highest trips in semptember.Now see the ride length difference in month.

```{r}
m <- ggplot(data = viz_df) +
  geom_bar(mapping = aes(x = member_type,y=ride_length,fill=rideable_type),stat = "identity")+
  facet_wrap(~fct_inorder(month),scales = "free_x")
m + scale_y_continuous(labels = function(x) format(x, scientific = FALSE)) +
  labs(title="Comparison of ride length of each month by member type",
       caption=paste0("Data of 2021 by DivvyBikes"),
       x="Member Type",
       y="Ride Length(seconds)")+scale_fill_brewer(direction = -1, palette = "Blues")

```
Most of the rides taken in May to Semptember. Though casual rider took lenghtier rides than member rider.

### Round Trips

```{r}
r <- ggplot(data = round_trip_df) +
  geom_bar(mapping = aes(x = member_type,fill=rideable_type))+
  facet_wrap(~day_of_week,scales = "free_x")
r + scale_y_continuous(labels = function(x) format(x, scientific = FALSE)) +
  labs(title="Comparison of round trips each day in week by member type",
       caption=paste0("Data of 2021 by DivvyBikes"),
       x="Member Type",
       y="Number of Round Trips")+scale_fill_brewer(direction = -1, palette = "Purples")
```

Casual rider loves round trip most than member. 

## ACT


There is lot's of differnce with member and annual riders using their trips based on that i am going to give some recommendation.

### Recommendation

* *Advertisement*

From the analysis, it's better to do more advertisement in Saturday and Sunday becuase casual riders took their highest trips those days and May to September is the time when most of trips taken.

* *New Package*

Most of the casual riders loves to take round trip so a new package of round trip could attract them more to purchase annual membership.

* *Offer*

Casual riders loves to take lenghty ride so we could offer them for it if they took their annual membership.

Here, i used all the data of 2021 and based on that data i give my recommendation but further analysis and accurate result might come if we analyze data from previous years also.

## Conclusions

Thank you for reading the whole case study of mine. This is my first case study so there might be some mistakes,feel free to give me any suggestion.
