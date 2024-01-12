# Filtros de Correlação (Correlations Filters)

****
Nome: Gustavo Costa

Curso: Ciências da Computação

Artigo Científico de Referência: Face Recognition Systems: A Survey; Yassin Kortli, Maher Jridi, Ayman Al Falou e Mohamed Atri

****

Sistemas de reconhecimento facial baseados nos *filtros de correlação (CF)* ultimamente vem gerando bons resultados de robustez, acurácia local, eficiência e discriminação. Essas técnicas concedem as seguintes vantagens:

- Alta capacidade para discriminação/diferenciação;
- Robustez de ruído desejada;
- Invariância de deslocamento;
- Paralelismo Inerente.

****

## Sistema Óptico de Fourier "4F"🔍
Para as duas técnicas que utilizam os filtros de correlação a seguir, elas utilizam a configuração óptica "4F" que é um tipo de sistema óptico usando em processamento de imagens e recebe esse nome devido à sua configuração que envolve
quatro distâncias focais (4f)

**Como funciona?**

O sistema "4F" é composto por duas lentes convergentes, cada uma com distância focal ' f ' dos 3 planos existentes, e são separadas entre si por uma distância focal ' 2f', formando a seguinte sequência:

**P1 (plano de entrada) - ' f ' - L1 (lente 1) - ' f ' - P2 (plano de interferência) -' f ' - L2 (lente 2) - ' f ' - P3 (plano de saída)**

- *P1:* Chamado de Plano de Entrada, o objeto ou imagem a ser processado é colocado no primeiro plano, na frente da primeira lente.
- *P2:* Chamado de Plano de Frequência, está localizado à uma distância ' f ' de ambas as lentes, é onde o objeto de entrada sofrerá a *transformada de Fourier* e passará a ser um espectro.
- *P3:* Chamado de Plano de Saída, está localizado na distância focal ' f ' após a segunda lente, É onde acontece a inversa da transformada de Fourier do objeto de entrada e o espectro volta ao domínio do espaço/tempo. O processamento da imagem
ocorre aqui.


<img src="https://i.ibb.co/vkDLSnh/optica-fourier-4f.png">

## ⚙️Joint Transform Correlator (JTC)⚙️
No JTC, é dada uma imagem de referência que será utilizada no processo de reconhecimento facial e a imagem de entrada são colocadas lado a lado no *Plano de Entrada (P1)* do sistema óptico. A primeira 
<a href="https://pt.wikipedia.org/wiki/Transformada_de_Fourier" target=_blank> transformada de Fourier</a>  é aplicada a essa combinação, produzindo um padrão de interferência no *Plano de Frequência (P2)*. Após isso, a segunda lente realizará 
a segunda transformada de Fourier ou a transformada inversa, formando a correlação no *Plano de Saída (P3)*.

<img src="https://i.ibb.co/LCpRfmF/JTC.jpg">

*fonte da imagem: http://www.optique-ingenieur.org/en/courses/OPI_ang_M02_C02/co/Contenu_09.html*

## ⚙️VanderLugt Correlator (VLC)⚙️
No VLC, a imagem de entrada é colocada no *Plano de Entrada (P1)*, logo após isso, a primeira lente *L1* realiza a transformada de Fourier no *Plano de Frequência (P2)* que contém o **filtro holográfico, gerado a partir da imagem de referência 
que já havia passado pelo filtro de correlação anteriormente e gravada em um holograma ou filtro espacial**. A segunda lente *L2*, inverte a transformada de Fourier, e a correlação de saída é formada no *Plano de Saída (P3)*.

- **Fórmula de Correlação:**
<img src="https://i.ibb.co/NNt2Wb7/Captura-de-tela-2024-01-12-015935.png">

- **Fórmula do Filtro Óptico Otimizado:**
<img src="https://i.ibb.co/92TTFC8/Captura-de-tela-2024-01-12-015919.png">


<img src="https://i.ibb.co/ZfqBp5q/VLC.png">

*VLC*

****

Além disso, para as duas técnicas, há o *Pico de Correlação de Energia (PCE)* que é utilizado para avaliar a eficácia da correlação. Esse índice é particularmente útil para quantificar a qualidade da correlação em termos de quão 
distintamente o pico de correlação se destaca do fundo ou ruído.

**Função do PCE**🔢

- *Medir a Qualidade da Correlação:* O PCE é uma métrica que ajuda a determinar quão bem um padrão específico é detectado em uma imagem de entrada. Um PCE alto indica que o pico de correlação é muito distinto e, portanto, o padrão de
referência é facilmente identificável na imagem de entrada.

- *Equilíbrio entre Pico e Energia:* O PCE equilibra a altura do pico de correlação com a energia total (ou distribuição de intensidade) da resposta de correlação. Isso ajuda a discernir entre verdadeiros positivos (correlações fortes e claras)
e falsos positivos (onde um pico pode ser alto, mas não claramente distinguível do fundo).

- **FÓRMULA:**
<img src="https://i.ibb.co/W3tfBWx/Captura-de-tela-2024-01-12-010902.png">

- **Epeak** é a energia do pico de correlação, ou seja, o valor do pico mais alto dentro da função de correlação.

- **Epeak(i,j)** representa a energia de cada ponto na função de correlação dentro de uma janela definida, com 'i' e 'j' variando sobre todos os pontos dessa janela.

- **N** é o número total de pontos na janela de correlação.

****
## ⬇️Vantagens e Desvantagens dos Filtros de Correlação⬇️

### ✅ Vantagens

- **Facilidade de Implementação:** Filtros de correlação podem ser mais simples de implementar em comparação com outros métodos mais complexos de reconhecimento de padrões. Essa simplicidade facilita a integração em diferentes
tipos de sistemas.

- **Análise em Tempo Real:** Devido à sua natureza menos complexa, esses filtros podem permitir a análise de imagens em tempo real, o que é essencial em aplicações como vigilância, segurança e interações humanas-computador.

- **Invariância a Transformações Geométricas e de Iluminação:** Filtros de correlação podem ser desenhados para serem invariantes a mudanças de tamanho, orientação e variações de iluminação. Isso os torna robustos em ambientes onde essas
variações são comuns.

### ❌ Desvantagens

- Falta de Capacidade de Discriminação: Uma limitação importante é a dificuldade em distinguir entre características muito semelhantes ou sutis. Isso pode ser um problema em aplicações onde é essencial diferenciar entre padrões ou texturas 
muito próximas.

- Dificuldade de Automatização na Detecção de Características: Automatizar a identificação e seleção de características relevantes para a correlação pode ser desafiador, exigindo frequentemente ajustes manuais ou dependendo da
qualidade das imagens de treinamento.

### ⌛ Performance

- **Alta Performance em Tempo de Processamento e Taxa de Reconhecimento:** Apesar das desvantagens, os filtros de correlação geralmente oferecem uma boa performance em termos de velocidade de processamento e eficácia na taxa de reconhecimento, 
especialmente em cenários controlados ou quando as variações nas imagens de entrada não são extremas.
