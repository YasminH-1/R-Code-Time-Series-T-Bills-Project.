# R-Code-Time-Series-T-Bills-Project.
Time series project for attempting to model 3-month TB rates of daily frequency, with data from the Federal Reserve. 
x=read.csv("TB Rates.csv")
x=ts(x,frequency = 365,start = c(2000,5))
plot.ts(x)
x=ts(x,frequency = 1,start = c(2000,5)) #to make calculations easier
xdiff1=diff(x)
plot.ts(xdiff1)
acf(x)
pacf(x)
acf(xdiff1)
pacf(xdiff1)
model1diff=arima(xdiff1,order=c(3,1,0))
model1diff
model2diff=arima(xdiff1,order=c(4,1,0))
model2diff
qqnorm(model2diff$residuals)
qqline(model2diff$residuals)
acf(model2diff$residuals)
pacf(model2diff$residuals)
Box.test(model2diff$residuals,lag=20)
plot(model2diff$residuals)
predict(model2diff, n.ahead=1)
