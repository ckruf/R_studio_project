#print(getwd())
churn <- read.csv(file="./churn.txt", stringsAsFactors = FALSE)
#churn
#typeof(churn)
#summary(churn)
na_count <- sapply(churn, function(value) sum(length(which(is.na(value)))))
na_count <- data.frame(na_count)
na_count

table(churn$State)
length(unique(churn$State))

table(churn$Area.Code)
length(unique(churn$Area.Code))

barplot(table(churn$State), las=2, cex.names=0.5)
barplot(table(churn$Area.Code))

par(mfrow=c(1, 1))
hist(churn$CustServ.Calls,
     breaks=10,
     col="blue",
     border="black",
     xlab="Calls to customer service",
     ylab="counts",
     ylim=c(0,100),
     main="Histogram of customer service calls")
box(which="plot", lty="solid", col="black")
summary(churn$CustServ.Calls)

sd(churn$CustServ.Calls)

zscore_day_mins <- ((churn$Day.Mins-mean(churn$Day.Mins))/sd(churn$Day.Mins))
zscore_day_mins

day_mins_skew <- ((3*(mean(churn$Day.Mins) - median(churn$Day.Mins)))/sd(churn$Day.Mins))
day_mins_skew

zscore_day_mins_skew <- ((3*(mean(zscore_day_mins) - median(zscore_day_mins)))/sd(zscore_day_mins))
zscore_day_mins_skew

par(mfrow = c(1, 1))
qqnorm(churn$Day.Mins,
       datax=TRUE,
       col="red",
       main="Normal Q-Q Plot of Day Minutes")
qqline(churn$Day.Mins,
      col="blue",
      datax=TRUE)

par(mfrow = c(1, 1))
qqnorm(churn$Intl.Mins,
       datax=TRUE,
       col="red",
       main="Normal Q-Q Plot of International Minutes")
qqline(churn$Intl.Mins,
       col="blue",
       datax=TRUE)

table(churn$Intl.Mins)

hist(churn$Intl.Mins,
     breaks=10,
     col="blue",
     border="black",
     xlab="International Minutes",
     ylab="Number of customers",
     main="Histogram of International Minutes calls")
box(which="plot", lty="solid", col="black")

churn["has_international_minutes"] <- unlist(lapply(churn$Intl.Mins, function(x) as.numeric(x > 0)))

churn["non_zero_international_minutes"] <-unlist(lapply(churn$Intl.Mins, function(x) if (x>0) x else NA))

churn$non_zero_international_minutes

hist(churn$non_zero_international_minutes,
     breaks=10,
     col="blue",
     border="black",
     xlab="International Minutes",
     ylab="Number of customers",
     main="Histogram of International Minutes calls")
box(which="plot", lty="solid", col="black")

par(mfrow = c(1, 1))
qqnorm(churn$non_zero_international_minutes,
       datax=TRUE,
       col="red",
       main="Normal Q-Q Plot of Non-zero International Minutes")
qqline(churn$Intl.Mins,
       col="blue",
       datax=TRUE)