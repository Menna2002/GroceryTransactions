##### let the user input his csv file
datasetPath2<-readline("Dataset path :")
datasetpath<-read.csv(datasetPath2)
str(datasetpath) #data= 9835 obs of 8 variables
###### checking if the data clean or not
library(tidyr)
clean<-drop_na(datasetpath)#drop_na:Drop rows
#containing missing values
str(clean) #data= 9835 obs of 8 variables
library(janitor)
clean2<-clean_names(clean)
colnames(clean2)
x<-data.frame(colnames(datasetpath),colnames(clean2))
x ## now All the col names are lower case 
clean3<-remove_empty(clean2,which = c("rows","cols"),quiet = FALSE)
# no empty rows , no empty columns
library(dplyr)
data_cleaned<-distinct(clean3) # to remove duplicate rows
str(data_cleaned) 
class(data_cleaned)
#after removing duplicate rows number of obs 9833 of 8 variable

#step 2 data visualization
par(mfrow=c(2,3))
#####comparing total spending of cash and credit
total_Per_paymentType<-group_by(data_cleaned,payment_type)#dplyr
total_Per_paymentType<-
  summarise(total_Per_paymentType,totalSpending=sum(total))
total_Per_paymentType
pie(x=total_Per_paymentType$totalSpending,
    labels = total_Per_paymentType$payment_type,
    main = "comparing total spending cash vs credit" )
##### comparing number of transactions by cash vs credit
table(data_cleaned$payment_type)
pie(x=table(data_cleaned$payment_type),
    main = "Compare cash and credit totales")
library(dplyr)
SpendingPerAge<-group_by(data_cleaned,age)#dyplyr
SpendingPerAge<-summarise(SpendingPerAge,totalSpending =sum(total))#dyplyr
SpendingPerAge
plot(x= SpendingPerAge$age,y= SpendingPerAge$totalSpending,
     main = "Spending vs Age",xlab = "Age",ylab = "Total spending",)
city_vs_spending<-group_by(data_cleaned,city)#dplyr
city_vs_spending<-summarise(city_vs_spending,totalspending=sum(total))#dplyr
city_vs_spending<-arrange(city_vs_spending,desc(totalspending))#dplyr
city_vs_spending
barplot( height = city_vs_spending$totalspending
         ,name =city_vs_spending$city
         ,col = "skyblue"
         ,main = "city VS. total spending"
         ,xlab = "Total spending"
         ,horiz = TRUE
         ,las = 1 )
boxplot(x = data_cleaned$total
        ,main = "Distribution of total spending"
        ,xlab = "Spending")

#ask user
numberOfClusters<-as.numeric(readline("Number of clusters:")) 
rawdata<-cbind(data_cleaned$age,data_cleaned$total)
rownames(rawdata)<-data_cleaned$customer
colnames(rawdata)<-c("age","total")
rawdata
#k-means
if(numberOfClusters<4&numberOfClusters>2){
  
  customers<-kmeans(rawdata,centers = numberOfClusters )#stats
  customers
}else
  print("Enter Number of clusters between (2:4)")
##table
customer_name<-c(data_cleaned$customer)
customer_age<-c(data_cleaned$age)
customer_totalSpending<-c(data_cleaned$total)
customer_cluster<-c(customers$cluster)
customer_table<-
  data.frame(customer_name,customer_age,customer_totalSpending,customer_cluster)
print(customer_table)

# Association rules
#ask user
minSupport<-as.numeric(readline("Minimum Apriori support: "))
minConfidence<-as.numeric(readline("Minimum Apriori confidence:"))

library(arules)
#saving cleaned data set 
write.csv(data_cleaned,datasetPath2)

#Apriori algorithm
if(minSupport > 0.001 & minSupport < 1 & minConfidence > 0.001 & minConfidence
   < 1){
  transactions1<-read.transactions("transactions.txt",sep = ",")
  class(transactions1)
  inspect(transactions1)
  rules<-apriori(transactions1,
                 parameter = list(supp = minSupport,conf = minConfidence))
  inspect(rules)
  
}else 
  print("Enter minsupport & minconfidence between (0.001:1)!")