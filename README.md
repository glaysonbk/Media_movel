# Media_movel


Média Móvel com uso do RCloud

A base de dados abaixo é relativa ao número diário de veículos acessando um shopping center, medido em milhares. 

Deseja-se construir uma média móvel de três dias para essa série e apresentar os resultados em um gráfico. 

Definição de dataset

dias <- c(1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12)
veiculos <- c(188, 272, 170, 256, 204, 248, 256, 233, 178, 175, 168, 166)

Instalar e executar bibliotecas

install.packages("zoo")
library(zoo)
media_movel <- rollmean(veiculos, k = 3, align = "right", fill = NA)

Plotagem 

plot(dias, veiculos, type = "l", ylim = c(0, max(veiculos, media_movel, na.rm = TRUE)),
     xlab = "Dia", ylab = "Número de Veículos", main = "Média Móvel de 3 dias")
lines(dias, media_movel, col = "red")
legend("topleft", legend = c("Veículos", "Média Móvel"), col = c("black", "red"), lty = 1)
