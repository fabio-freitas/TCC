# TCC
# Abrir bibliotecas
library(BatchGetSymbols)

# Selecao de acoes
my.tickers <- c("SBSP3.SA")

# Selecao de todos os dados disponiveis desde 01/01/2005 ate o ultimo dia de 2018
first.date <- as.Date(c("2005-01-01"))
last.date <- as.Date(c("2018-12-31"))

# Busca dos dados das acoes aglomerados com informacoes da fonte de dados
l.out <- BatchGetSymbols(tickers = my.tickers, first.date = first.date, 
                         last.date = last.date)
                         
# Seleciona apenas a parte dos dados financeiros
dados <- l.out[["df.tickers"]]


my.idx <- dados$ticker == "SBSP3.SA"
my.df.bovespa <- dados[my.idx, ]

SABESP <- my.df.bovespa$ref.date 
