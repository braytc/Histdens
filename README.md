# Histdens
something quick for looking at q and t density plots from Ima2 output
setwd('C:/2015TIM/Analysis/IMa2_8_27_12/Finalouts_to_use')

q_values.txt
t_values.txt

qdat<-read.table('q_values.txt', header =TRUE)
df= as.data.frame(qdat)
  dfq0.freq= as.vector(rep(df$q0, df$P0))#THIS CREATES SOEMTHIGN TO USE IN THE DENSITY PLOT
dfq1.freq= as.vector(rep(df$q1, df$P1))
dfq2.freq= as.vector(rep(df$q2, df$P2))
dfq3.freq= as.vector(rep(df$q3, df$P3))


#hist(dfq0.freq, nclass=1000, xlim=c(0,2))
hist(dfq3.freq, nclass=10000, xlim=c(0,2))
densq0 <- density(dfq0.freq)
densq1 <- density(dfq1.freq)#Not sure why these don't work, something about the shape of the distribution
densq2 <- density(dfq2.freq)
densq3 <- density(dfq3.freq)



plot(densq0, xlim=c(0,2))#THE DENSITY PLOT ITSELF
lines(densq3)
plot(densq1, xlim=c(0,2))
abline(b=0, v=0.223, col="red", lwd=2)



maybe a density function is better?
library(locfit)

m1.p1.fit <- locfit(~df$P0, xlim=c(0,2)) # to create density
dev.off()

#par(mfrow=c(4,4))  # to get multiple figures on one plot
hist(df.freq, nclass=1000, xlim=c(0,2))
lines(m1.p1.fit, col="red", lwd=2)
hist(m1[,3], freq=F, nclass=100, xlim=c(0,1))
lines(m1.p1.fit, col="red", lwd=2)
abline(b=0, v=0.223, col="red", lwd=2)
