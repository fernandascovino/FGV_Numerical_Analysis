## Projeto: Transformada de Hilbert-Huang

---

#### Por [Beatriz Coimbra](https://github.com/beatrizmcoimbra) e [Fernanda Scovino](https://github.com/fernandascovino)

#### Resumo

Implementação da transformada de Hilbert-Huang para identificação de sons e expansão do [verbete na *Wikipédia*](https://pt.wikipedia.org/wiki/Transformada_de_Hilbert-Huang).

A transformada de Hilbert-Huang é uma técnica de decomposição de sinais em tempo-frequência em duas fases (EMD - Método de decomposição do modo empírico, e HSA - Análise espectral de Hilbert). Esta técnica foi desenvolvida num dos organismos da NASA por Northen E. Huang em 1998, e tem sido aplicada a sinais nos mais variados ramos da ciência, que vão desde a engenharia à medicina.<sup>1</sup>

O método de decomposição do modo empírico (EMD) nos permite decompor um conjunto de dados em um número
finito de componentes mais simples, chamados de funções do modo intrínseco (IMF).<sup>2</sup> Uma função de modo intrínseco é definida como qualquer função que tenha o mesmo, ou diferindo no máximo por um, números de zeros (cruzam o eixo x) e extremos, e também ter "envelopes simétricos" definidos pelos máximos e mínimos locais, respectivamente (os dados devem se localizar entre essas funções).<sup>3</sup>. As splines cúbicas são utilizadas para traçarmos esses envelopes, conectando os máximos/mínimos locais.<sup>4</sup>

#### Referências

1: [Hilbert-Huang transform - Wikipédia](https://en.wikipedia.org/wiki/Hilbert%E2%80%93Huang_transform)

2: [Tese *Utilização do método de decomposição empírico no processamento de dados de mobilidade urbana*, de Juliana Crespo (EMAp)](https://emap.fgv.br/dissertacao/utilizacao-metodo-de-decomposicao-empirico-processamento-de-dados-de-mobilidade-urbana)

3: [Hilbert-Huang transform - Scholarpedia](http://www.scholarpedia.org/article/Hilbert-Huang_transform)

4: [Spline - Wikipédia](https://pt.wikipedia.org/wiki/Spline)

5: [Cheney, W. & Kincaid, D. *Numerical Mathematics and Computing*](https://www.amazon.com/Numerical-Mathematics-Computing-Ward-Cheney/dp/1133103715/ref=dp_ob_title_bk)