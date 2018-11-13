# FGV_Numerical_Analysis

Exercícios e anotações do curso de Análise Numérica da graduação em Matemática Aplicada @ FGV/EMAp.

**Livro**: [Cheney, W. & Kincaid, D. *Numerical Mathematics and Computing*, 6th edition](https://www.amazon.com/Numerical-Mathematics-Computing-Ward-Cheney/dp/1133103715/ref=dp_ob_title_bk)

**Ementa**\*: Aritmética numérica. Álgebra linear numérica: sistemas lineares, minimos quadrados,
problemas de autovalores; fatorizações LU, Cholesky, QR e SVD. Otimização: método do gradiente
conjugado e de Lanczos. Interpolação por polinômios, splines; métodos de integração (Gauss,
Chebyshev, Romberg). Sistemas de equações não lineares. Métodos numéricos em EDOS: RungeKutta,
métodos multipasso, convergência e estabilidade. Métodos numéricos em EDPs (parabólicas
elípticas e hiperbólicas): diferenças finitas e elementos finitos. ([Plano de ensino](https://emap.fgv.br/sites/emap.fgv.br/files/u77/8o_periodo_-_analise_numerica-paulo_cezar_e_moacyr.pdf))

\*ordem das matérias vai seguir o livro

**Conteúdo:**

    ├── README.md          <- this file :)
    ├── material           <- Jupyter notebooks with material and exercises solutions
      └── images           <- images used in notebook files
    ├── exercises          <- exercises enunciates
    └── project            <- project developed in the course


Notebook | Capítulos
---|---
[Pontos Flutuantes](material/08-02_floating_points.ipynb) | Cap. 1.1 + 1.3
[Sitemas Lineares: métodos iterativos](material/08-07_09_linear_sys.ipynb) | Cap. 8.1 + 8.2 + 8.4
[Sitemas Não Lineares: métodos iterativos](material/08-14_16_non_linear_sys.ipynb) | Cap 3
[Interpolação e diferenciação numérica](material/08-28_30_numerical_interpolation_diff.ipynb) | Cap. 4
[Função Spline](material/09-06_spline_function.ipynb) | Cap. 6
[Problemas de valores iniciais: Método de Euler](material/09-11_13_initial_value_problems_pt1.ipynb) | Cap. 7.1
[Problemas de valores iniciais: Método de Euler Implícito e Método de Heun](material/09-25_initial_value_problems_pt2.ipynb) | Cap. 7.2
[Resolvendo exercícios da lista 25-09](material/09_27_solving_exercises.ipnb) | -
[Métodos de integração numérica: Regra do Trapezio, Simpson e Algoritmo de Romberg](material/10-02_04_numerical_integration_pt1.ipynb) | Cap. 4.3 + 5.1-3
[Métodos de integração numérica: Quadratura Gaussiana e Monte Carlo](material/10-18_numerical_integration_pt2.ipynb) | Cap. 5.4 + 10
[Métodos numéricos de resolução de EDPs](material/10_30_partial_diff_equations.ipynb) | Cap. 12.1 + 12.2