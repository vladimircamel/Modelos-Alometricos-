# Modelos-Alometricos-
Modelos de crecimiento de arboles
##Elpresente proyecto ayudara a  desarrollar 
## modelos no lineales para estimar el crecimiento de Arboles
## El lenguage es R project.


####Modelo Logistico
logistico<- nls(DAC~ (a/(1+b*exp(-c*Edad))), start=list(a=23.0191, b=6.9325, c= 0.0808),trace=T)
summary(logistico)
anova(logistico, gompertz)
AIC(logistico)
BIC(logistico)
(coefic1<-(coef(logistico)))
(a1<-as.numeric(coefic1[1:1]))
(b1<-as.numeric(coefic1[2:2]))
(c1<-as.numeric(coefic1[3:3]))
logis <- (DAC~ (a/(1+b*exp(-c*Edad))))
plot(DAC~Edad, main="Modelo Alometrico Logistico (Prunus serotina)", ylab="Diametro acumulado (cm)", xlab="Edad (Años)",lwd="0.1", bg="cornsilk3",ylim=c(0, 120),xlim=c(0,170),sub="Logistico",pch=21,col="gray1")
curve(a1/(1+b1*exp(-c1*x)), add=T, col="darkblue", lwd="3")
abline(h=a1,col="gray25",lwd="0.7", lty=c(9))
abline(h=a1/2,col="gray34",lwd="1", lty=c(9))
abline(v=b1/c1,col="gray34",lwd="1", lty=c(9))
abline(v=23, col="gray30", lwd="1", lty=c(9))
