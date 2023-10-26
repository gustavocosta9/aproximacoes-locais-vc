# Análise ROC (Receiver Operating Characteristic)

****
Nome: Gustavo Costa
Curso: Ciências da Computação
****

# Classificação da Verificação Facial pelo ROC (Receiver Operating Characteristic)

Durante o processo de detecção facial, foi visto que durante a análise de uma imagem pelo classificador pode haver a detecção excessiva ou a detecção ausente de faces:

- *Falsos Positivos*: É quando o classificador subentende que em algum lugar da imagem há um indivíduo/objeto presente mas não é verdade, é um erro.

- *Verdadeiros Positivos*: É quando, de fato, o classificador acerta na detecção do indivíduo/objeto na imagem.

- *Falsos Negativos*: É quando o classificador não realiza a classificação correta e deixa um indivíduo/objeto passar despercebido.

- *Verdadeiros Negativos*: É quando o classificador acerta em dizer que não há um indivíduo/objeto a ser classificado na imagem.

## ❌Primeiro erro: Taxa de Aceitação Verdadeira (True Accept Rate TAR)❌

<img src="https://i.ibb.co/Dt9X4nK/Captura-de-Tela-106.png">

Quando vamos quantificar os acertos de um classificador, precisamos dividir os *Verdadeiros Positivos* pela **soma** dos *Verdadeiros Positivos* mais os *Falsos Negativos*

Isso se dá pelo fato de quando o classificador traz o resultado de um FALSO negativo, quer dizer que há ali uma classificação que passou despercebida. Essa soma equivale ao TOTAL de indivíduos/objetos a serem classificados.

Logo, se temos 10 pessoas na foto:

- 7 pessoas foram classificadas de forma correta = Verdadeiros Positivos
- 3 pessoas não foram classificadas = Falsos Negativos
- TAR = 0,7

## ❌Segundo erro: Taxa de Aceitação Falsa (False Accept Rate FAR)❌

<img src="https://i.ibb.co/5n8SsNx/Captura-de-Tela-107.png">

Se é importante sabermos a taxa de acertos verdadeiros de um classificador, é de suma importância que tenhamos consciência da situação contrária: a taxa de acertos falsos.

A importância de saber essa informação é para ajustar o classificador para que eventualmente não ocorram mais acertos que sejam falsos.

precisamos dividir os *Falsos Positivos*, pelos próprios *Falsos Positivos* mais a **correção** que inclui os *Negativos Verdadeiros*. Ou seja, temos as análises que resultam em falsos positivos e análises que resultam em verdadeiros negativos. Oque no final das contas são todas as análises que retornam uma "negação" na identificação.


# 📉Equação Simplificada: Estimated Mean Accuracy (ACC)

<img src="https://i.ibb.co/BCqp5PB/Captura-de-Tela-108.png">

Trata-se de uma métrica que nos retorna qual é a porcentagem das classificações corretas.

Somamos os *Verdadeiros Positivos* mais os *Verdadeiros Negativos* e dividimos pela soma de TODAS as classificações.
