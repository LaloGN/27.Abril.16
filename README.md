# 27.Abril.16
###Residuos de los pronosticos
install.packages("foreign")
install.packages("fpp")
require(foreign)
require(fpp)
pib<-read.csv("C:\\Users\\SALA-C16\\Downloads\\pib.csv", header=T, dec=".")
pibts<-ts(pib[,2],start=1993, frequency=4)
View(pibts)
plot(pibts)
Acf(pibts)

###Pronosticos
pibtspro<-meanf(pibts,4)
pibtsnai<-naive(pibts,4)
pibtssnai<-snaive(pibts,4)
pibtsder<-rwf(pibts,4,drift=TRUE)

plot(pibtspro)
plot(pibtsnai)
plot(pibtssnai)
plot(pibtsder)

evalmed  <- accuracy(pibtspro)
evaling  <- accuracy(pibtsnai)
evalsnai <- accuracy(pibtssnai)
evalder  <- accuracy(pibtsder)
evalmed
evaling
evalsnai
evalder
