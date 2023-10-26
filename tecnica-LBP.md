# Local Binary Pattern (LBP)
****
Nome: Gustavo Costa

Curso: Ciências da Computação

Artigo Científico de Referência: Face Recognition Systems: A Survey; Yassin Kortli, Maher Jridi, Ayman Al Falou e Mohamed Atri
****

A técnica LBP faz parte das **aproximações locais** dentro do reconhecimento facial. Ademais, essa técnica de texturas é ótima para extrair características de qualquer objeto.

Algumas de suas aplicações são:

- Reconhecimento Facial
- Reconhecimento de expressões faciais
- Segmentação de texturas
- Classificação de texturas

<img src="https://i.ibb.co/1drm0Mp/lbp.webp">

*fonte da imagem: Local Binary Patterns (LBP) Mapping*

## 🔬**Afinal, como a LBP funciona?**

Como melhor entendimento, vamos mostrar o funcionamento da técnica LBP por um algoritmo.


**Passo 1:** Divisão da Imagem em Vetores Espaciais
  - A LBP começa com uma imagem de entrada, que é uma matrix de pixels.
  - A imagem é dividida em regiões menores chamadas de quadrados ou células.
  - Cada célula é uma área de interesse onde o LBP será calculado, o tamanho da célula é setado pelo autor do algoritmo, geralmente é 3x3, 5x5 ou 7x7.

**Passo 2:** Cálculo do LBP em Cada Quadrado
  - Escolha um pixel central no quadrado p0, será o pixel de referência.
  - Crie uma vizinhança ao redor do p0, geralmente é uma matriz 3x3.
  - Compare a intensidade do p0 com a intensidade de cada pixel vizinho.
  - Se a intensidade do vizinho >= intensidade p0, atribua 1 a esse pixel na representação binária do LBP. Caso seja menor, atribua o valor 0.
  -Concatene os valores binários dos pixels vizinhos.
  -Converta o número binário formado para decimal, esse valor representa o LBP para o p0.

**Passo 3:** Repetição para todos os Quadrados
  - Repita o passo 3 para toda célula/quadrado da imagem.
  - Após isso, cada LBP de cada célula representa a **textura local** da área coberta por essa célula.

**Passo 4:** Construção de um Mapa de Textura
  - Após obtermos o LBP para todas as células, podemos organizar esse conjunto de valores em uma **matriz** criando um **mapa de textura** ou uma nova imagem

**Passo 5:** Análise ou Uso dos Valores LBP
  - Esses valores são de extrema importância na visão computacional para reconhecimento de objetos, detecção de texturas, segmentação de imagens,etc.

**Passo 6:** Construção do Histograma
  - Com os valores do LBP é possível construir um histograma (estatística) para resumir a textura geral da imagem, útil para classificação e detecção.

<img src="https://i.ibb.co/rFpzLYv/Captura-de-Tela-132.png">

****
##**Exemplo do LBP**

<img src="https://i.ibb.co/61Wh7ZT/lbp-ex.png">

*fonte da imagem: Semantic Scholar The Local Binary Pattern Approach and its Applications to Face Analysis A. Hadid Published in First Workshops on Image… 1 November 2008 Computer Science 2008 First Workshops on Image Processing Theory, Tools and Applications*

****

## ⬇️**Vantagens e Desvantagens da técnica LBP**⬇️

A técnica LBP por pertencer ao que chamamos de Aproximações Locais, possui vantagens e desvantagens que são:

### ✅**Vantagens**
- Fácil de implementar, permite a análise de imagens em tempo real mesmo com ambientes desafiadores;
- Invariante em relação ao tamanho, orientação e iluminação.

### ❌**Desvantagens**
- Falta de capacidade de discriminação, isto é, a dificuldade de diferenciar detalhes muito sutis ou nuances em texturas e padrões de imagens;
- É difícil automatizar a detecção de características nessa aproximação.

### ⌛**Performance**
- Alta performance em termos de tempo de processamento e taxa de reconhecimento.
