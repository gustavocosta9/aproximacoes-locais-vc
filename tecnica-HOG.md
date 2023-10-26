# Técnica Histogram Of Oriented Gradients (HOG)

****
Nome: Gustavo Costa

Curso: Ciências da Computação

Artigo Científico de Referência: Face Recognition Systems: A Survey; Yassin Kortli, Maher Jridi, Ayman Al Falou e Mohamed Atri
****

A técnica HOG (Histogram Of Oriented Gradients) é uma técnica de reconhecimento facial que se encaixa nas **Aproximações Locais**. Além disso, o HOG é um dos melhores descritores usados para construir descrições de formas e bordas.

Algumas de suas aplicações são:
  - Detecção de Pessoas;
  - Detecção de Veículos;
  - Reconhecimento de Gestos;
  - Reconhecimento de Objetos;
  - Rastreamento de Objetos;
  - Reconhecimento de faces;
  - Detecção de Bordas e Contornos;
  - Reconhecimento de Texturas;
  - Contagem de Objetos;
  - Detecção de Movimento;
  - Realidade Aumentada;
  - Detecção de Anomalias.

<img src="https://i.ibb.co/KF65Gt0/hog.png">

****
## ⚙️Funcionamento do HOG⚙️

A técnica HOG funciona da seguinte maneira:

**Passo 1:** Pré-processamento da imagem
  - O primeiro passo envolve o pré-processamento da imagem. Normalmente, a imagem é *convertida para a escala de cinza para simplificar o processamento*, reduzindo-a a uma única dimensão de intensidade de pixel.

**Passo 2:** Divisão da Imagem em Células
  - A imagem inteira é divida em células retangulares e, em cada uma delas, o histograma de gradiente será calculado. A escolha da célula depende da aplicação (geralmente varia de 6x6 a 8x8 pixels)

**Passo 3:** Cálculo dos gradientes
  - A técnica HOG se concentra na orientação das mudanças de intensidade de pixel na imagem. Para capturar essas mudanças, os gradientes da imagem são calculados. Isso envolve a aplicação de operadores de gradiente para determinar a direção e magnitude das mudanças de intensidade em cada pixel.

**Passo 4:** Cálculo dos histogramas de gradientes
  - Para cada célula, o histograma de gradientes são calculados e, todos os histogramas de todas as células da imagem são combinados para extrair a característica da imagem facial

**Passo 5:** Normalização de blocos
  - Consiste em melhorar a invariância de iluminação e contraste, os histogramas são normalizados em blocos, isso ajuda o descritor HOG a ficar mais *robusto a variações locais como iluminação e intensidade* da imagem.

**Passo 6:** Criação do vetor de características HOG
  - Finalmente, com os histogramas concatenados e normalizados um vetor de características HOG é formado. Ele é utilizado para treinar classificadores, como SVMs (Support Vector Machines), para a detecção.

****

## ⚠️Atenção: Entendendo melhor o Passo 2 (Cálculo dos Gradientes)⚠️

Para calcular os gradientes, é de suma importância realizar os cálculos em ambas direções, na horizontal (Gx) e na vertical (Gy), porque esses gradientes serão os responsáveis por detectar as mudanças de intensidade de pixel na imagem.

Geralmente é utilizado uma máscara 1D (matriz) [-1 0 1] e é utilizada para realizar operações de convolução na imagem.

**Convolução**: processo matemático que envolve a aplicação de uma máscara deslizante sobre a imagem, multiplicando os valores da máscara com os valores dos pixels da imagem e, em seguida, somando esses produtos. O resultado é colocado em um novo local, formando uma nova imagem que destaca alguns itens: bordas ou gradientes na imagem original.

<img src="https://i.ibb.co/0mZBrLP/Captura-de-Tela-134.png">

**Exemplo**

Dado uma matriz de intensidade de pixels de uma imagem, cada valor dessa matriz (i,j) será aplicado tanto na fórmula do gradiente horizontal (Gx) quanto no gradiente vertical (Gy)

Máscara = [-1 0 1]


Considere a seguinte matriz de intensidade de pixels de uma suposta imagem:

[100, 150, 200]

[50, 100, 150]

[25, 50, 75]

Para calcular os Gradientes Gx e Gy do pixel central pC(2,2) = '100' vamos utilizar as fórmulas dos gradientes.

Gx(2, 2) = I(2, 1) * (-1) + I(2, 2) * (0) + I(2, 3) * (1)

Gx(2, 2) = 50 * (-1) + 100 * (0) + 150 * (1)

Gx(2, 2) = -50 + 0 + 150

**Gx(2, 2) = 100**. Isso significa que há um **aumento na intensidade** dos pixels da esquerda para a direita.

Gy(2, 2) = I(1, 2) * (-1) + I(2, 2) * (0) + I(3, 2) * (1)

Gy(2, 2) = 50 * (-1) + 100 * (0) + 50 * (1)

Gy(2, 2) = -50 + 0 + 50

**Gy(2, 2) = 0**. Isso significa que no eixo vertical **não há um aumento** nem diminuição na intensidade dos pixels.

**Magnitude do Gradiente**

<img src="https://i.ibb.co/31wBDff/Captura-de-Tela-137.png">

A magnitude do gradiente é calculada usando o teorema de Pitágoras para *combinar os gradientes* nas direções horizontal (Gx) e vertical (Gy).

Onde:

  - G(x, y) é a magnitude do gradiente no ponto (x, y).
  - Gx(x, y) é o valor do gradiente na direção horizontal no ponto (x, y).
  - Gy(x, y) é o valor do gradiente na direção vertical no ponto (x, y).

  Para cada célula retangular na imagem, a magnitude do gradiente representa a intensidade das mudanças na intensidade dos pixels. Isso é útil porque informa quão acentuada é a transição de intensidade em qualquer direção.

**Orientação do Gradiente**

<img src="https://i.ibb.co/y6h0SwS/Captura-de-Tela-136.png">

A orientação do gradiente é calculada usando a função trigonométrica "tan^-1", que fornece a orientação do gradiente em radianos.

Onde:

  - θ(x, y) é a orientação do gradiente no ponto (x, y).
  - Gx(x, y) é o valor do gradiente na direção horizontal no ponto (x, y).
  - Gy(x, y) é o valor do gradiente na direção vertical no ponto (x, y).

  Em grande parte das aplicações, a variação da orientação é de 0°-180°.

   A orientação dos gradientes é uma característica valiosa para a análise de imagens, permitindo a detecção de bordas, texturas, formas e a extração de informações úteis para várias tarefas em visão computacional e processamento de imagem. Ela desempenha um papel fundamental na captura de informações relacionadas à direção das mudanças de intensidade nos pixels de uma imagem.


<img src="https://i.ibb.co/H2cBzz6/hog-ex.png">

*fonte da imagem: A Framework for Instantaneous Driver Drowsiness Detection Based on Improved HOG Features and Naïve Bayesian Classification*


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
