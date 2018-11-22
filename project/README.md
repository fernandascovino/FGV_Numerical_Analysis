## Projeto: Transformada de Hilbert-Huang

---

#### Por [Beatriz Coimbra](https://github.com/beatrizmcoimbra) e [Fernanda Scovino](https://github.com/fernandascovino)

Implementação da transformada de Hilbert-Huang para identificação de sons e expansão do [verbete na *Wikipédia*](https://pt.wikipedia.org/wiki/Transformada_de_Hilbert-Huang).


### O que é HHT?

A transformada de Hilbert-Huang é uma técnica adaptativa de decomposição de sinais em tempo-frequência. Esta técnica foi desenvolvida num dos organismos da NASA por Northen E. Huang em 1998, e tem sido aplicada a sinais nos mais variados ramos da ciência, que vão desde a engenharia à medicina.<sup>1</sup> 

#### Qual a sua vantagem?

Em relação aos demais métodos para reconhecimento de pitch (frequência fundamental) de um som, como trasformada de Fourier, é que a transformada HHT toma como input dados e não uma função, é um método empírico e não teórico. 

Além disso, os demais métodos assumem que o processo de produção do som é linear e que os sinais são localmente estacionários (variância e média constantes no tempo) - por causa disso, análises com esses métodos só são possíveis em trechos curtos de tempo, logo o som deve ser trabalhando separadamente em diferentes intervalos, o que prejudica a estimação final. Por outro lado, o método empírico da HHT nos permite analisar sinais não-lineares e não-estacionários!<sup>3</sup>

Ela é realizada em duas etapas: **EMD - Método de decomposição do modo empírico, e HSA - Análise espectral de Hilbert**. 

### O que é EMD?

O método de decomposição do modo empírico (EMD) nos permite decompor sinais (para o som, amplitudes no tempo) em um número finito de componentes mais simples, chamados de funções do modo intrínseco (IMF).<sup>3</sup>

#### O que são IMFs?

Uma função de modo intrínseco é definida como qualquer função que tenha os mesmos, ou diferindo no máximo por um, números de zeros (cruzam o eixo x) e extremos, e também ter "envelopes simétricos" definidos pelos máximos e mínimos locais, respectivamente.<sup>1</sup>. Em qualquer, os dados podem envolver mais de um modo oscilatório, por isso que a transformação simples de Hilbert não pode fornecer a descrição completa do conteúdo de frequência para os dados gerais e é necessária a decomposição em IMFs para identificação dos modos<sup>5</sup>.

O processo de geração das IMFs é chamado de *sifting process*, ou "processo de peneiração", que busca suavizar as amplitudes desiguais. A essência do método é identificar os modos oscilatórios intrínsecos a partir das escalas de tempo dos dados empiricamente, e assim decompor os modos<sup>5</sup>.

As splines cúbicas são utilizadas para traçarmos os envelopes, conectando os máximos/mínimos locais.<sup>2</sup> Vale ressaltar que não existe um embasamento teórico para a utilização da spline em relação a outras técnicas de interpolação, um dos motivos pelo qual o EMD é dito empírico. Adaptações já foram feitas, como a utilização de funções radiais para a interpolação<sup>4</sup>, mas a spline continua sendo a mais difundida.

#### Algoritmo

1. Identificação os mínimos e máximos do sinal $x(t)$
2. Geração dos envelope superior e inferior de $x(t)$, passando um spline cúbico através dos máximos e mínimos respectivamente
3. Cálculo da média dos envelopes superior e inferior como $m(t)$
4. Obtenção de um candidato do FMI usando a fórmula  $h_{k}(t) = x(t)−m(t)$ 
5. Verificação das propriedades  de uma função do modo intrínseco (IMF) para $h_{k}(t)$
Se $h_{k}(t)$ não é uma IMF, repetimos o processo a partir do passo 1 com $x(t)=h_{k}(t)$. Se for, obtemos o resíduo $r(t) = x(t) - h_{k}(t)$ e repetimos o processo com $x(t) = r(t)$. 

No geral, sendo $h_1(t)$ a 1ª IMF, deve conter o componente de período mais curto do sinal. Como o resíduo contém ainda informação de componentes com período mais longo, refazemos o *sifting* como descrito no passo 5. 

Um critério de parada utilizado para o algoritmo é que o resíduo $r(t)$ se torne uma função monótona.

#### Como identificar uma IMF?

Existem alguns critérios possíveis de serem seguidos, vamos enumerar 2 deles aqui: *Nũmero S* e *Desvio Padrão*. Para fins práticos, utilizaremos o *Desvio Padrão* como critério.

##### Número S

Este critério baseia-se no chamado número S, que é definido como o número de *siftings* consecutivos para os quais o número de zero crossings e extremos são iguais ou no máximo diferentes por um.

O processo só é interrompido se, para S *siftings* consecutivos, os números de cruzamentos nulos e extremos permanecerem iguais e forem iguais ou no máximo diferentes por um.

##### Desvio padrão 

Foi proposto por Huang et al. (1998). Definimos uma soma das diferenças dos *siftings*, ou desvio padrão, como $SD$ da seguinte forma:

$$ SD_{k}=\sum_{{t=0}}^{{T}}{\frac  {|h_{{k-1}}(t)-h_{k}(t)|^{2}}{h_{{k-1}}^{2}(t)}} $$ e estabelecemos um limite para seu tamanho, recomendado no intervalo de 0.2 e 0.3 por Huang et al. (1998).


### O que é HSA?




### Referências

1: [Hilbert-Huang transform - Wikipédia](https://en.wikipedia.org/wiki/Hilbert%E2%80%93Huang_transform)

2: [Spline - Wikipédia](https://pt.wikipedia.org/wiki/Spline)

3: [Speech pitch determination based on Hilbert-Huang transform - Huang, H.; Pan, J. (2006)](https://www.sciencedirect.com/science/article/pii/S0165168405002367)

4: [Bidimensional Empirical Mode Decomposition Modified for Texture Analysis - Nunes, J.C. et all. (2003)](https://pdfs.semanticscholar.org/4cfd/e80b1f8284e35d7544e84172c95a5d7527fd.pdf)

5: [The empirical mode decomposition and the Hilbert spectrum for nonlinear and non-stationary time series analysis - Huang, N. et all. (1998)](http://rspa.royalsocietypublishing.org/content/454/1971/903)

6: [Pitch Detection Method Based on Hilbert-Huang Transform for Erhu Music](http://umir.umac.mo/jspui/handle/123456789/14152)
