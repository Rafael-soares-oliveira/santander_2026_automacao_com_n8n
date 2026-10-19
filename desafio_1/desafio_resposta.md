# ⋒ Inferência Causal na era da IA - Guia e Documentação do Notebook

>"Estudar e dominar os conceitos, métodos e ferramentas de Inferência Causal na era da IA, fazendo a transição fundamentada da modelagem preditiva tradicional (associação) para a modelagem causal e de contrafactuais (intervenção e raciocínio contrafactual), seguindo um plano de estudos estruturados por fases e validado empiricamente em Python".

Para acessar este ambiente interativo de estudos e acompanhar a evolução dos scripts e documentos:

🔗 [Link para o Gemini Notebook: Inferência Causal na era da IA](https://notebook.google.com/notebook/f911a1f7-340e-444f-ad62-336203c17314)

---

## 1. Fontes Integradas e Justificativa de Confiança

O notebook reúne 18 fontes criteriosamente selecionadas, abrangendo literatura científica internacional, livros texto de referência acadêmica e documentações oficiais das principais bibliotecas de código aberto:

| Categoria | Fonte/Título | Por que confiamos |
| --- | --- | --- |
| Artigos Científicos | *Double/Debiased Machine Learning* ([arXiv:1608.00060](https://www.google.com/url?sa=E&amp;q=https%3A%2F%2Farxiv.org%2Fpdf%2F1608.00060)) | Paper seminal de Chernozhukov et al. (publicado no *Econometrica*), base de todo o Causal Machine Learning moderno. |
| Artigos Científicos | *Causal Inference and Machine Learning* ([arXiv:2403.02467](https://www.google.com/url?sa=E&amp;q=https%3A%2F%2Farxiv.org%2Fpdf%2F2403.02467)) | Roadmap recente sobre ortogonalidade de Neyman, regressão não-linear e amostragem cruzada (cross-fitting). |
| Diretrizes Médicas | *The TARGET Statement* ([BMJ 2025;390](https://www.google.com/url?sa=E&amp;q=https%3A%2F%2Fwww.bmj.com%2Fcontent%2Fbmj%2F390%2Fbmj-2025-087179.full.pdf)) | Diretriz internacional publicada no *British Medical Journal* para o relato transparente de *Target Trial Emulation*. |
| Autores de Referência | *Miguel Hernán* | Harvard T.H. Chan School of Public Health |
| Livros Acadêmicos | *Causal Inference: The Mixtape* (Scott Cunningham) | Livro de econometria e inferência causal adotado nas principais universidades mundiais. |
| Documentação Oficial | DoWhy / PyWhy GitHub Repository | Biblioteca oficial mantida pela PyWhy/Microsoft Research para modelagem baseada em DAGs e testes de refutação. |
| Documentação Oficial | EconML Documentation | Biblioteca oficial desenvolvida pela Microsoft Research para estimativa de CATE e Double Machine Learning. |
| Manuais Técnicos | Causal Inference and Discovery in Python | Guia especializado (Packt Publishing) focado em descoberta causal e aplicação prática em código. |
| Fundamentos Matemáticos | *Essential Math for Data Science*, *Bayesian Analysis with Python*, *Mastering PyTorch*, *Graph Machine Learning*, *Pandas Cookbook* | O'Reilly e Packt: livros de base para suporte em álgebra, probabilidade, estatística bayesiana e aprendizado de máquina. |
| Materiais do Estudante | `Planos_de_Estudo.md` e `Conteúdo.md` | O roteiro pedagógico original e o caderno de anotações pessoal mantido e expandido ao longo do curso. |

---

## 2. Diretrizes de Comportamento dadas ao Notebook (System Directives)

Para garantir o máximo rigor conceitual e metodológico, o assistente opera sob as seguintes diretrizes fundamentais:

1. **Rigor de Fundamentação (*Grounding First*):** Toda afirmação factual e fórmula estatística deve ser rastreável às fontes do notebook, sem preencher lacunas com conhecimento superficial não verificado.
2. **Separação Rígida entre Predição e Causalidade:** Reforçar continuamente a diferença entre o Machine Learning Preditivo (Degrau 1 da Escada da Causalidade de Pearl — Observação/Associação) e a Inferência Causal (Degraus 2 e 3 — Intervenção e Contrafactuais).
3. **Progressão Pedagógica Estruturada:** Conduzir o aprendizado respeitando rigorosamente as fases estabelecidas em `Planos_de_Estudo.md` (Fases 0 a 5).
4. **Falsificação Popperiana:** Abordar modelos causais não sob a perspectiva de "provar que estão certos", mas submetendo-os a estressores, testes de sensibilidade e refutação (*nullifying* e *invariant transformations*).
5. **Orientação Prática e Executável:** Traduzir teorias abstratas em implementações funcionais de código em Python (`statsmodels`, `scikit-learn`, `DoWhy`/`EconML`), fornecendo diagnósticos estatísticos completos.

---

## 3. Perguntas Realizadas, Respostas Geradas e Fontes Utilizadas

Abaixo está o registro sequencial das principais interações desenvolvidas neste notebook:

### 📍 Pergunta 1: Estruturação Inicial da Fase 0 (Mentalidade e Vocabulário Causal)

* **Pergunta do Usuário:** *"Vamos estudar seguindo as etapas do arquivo Plano de Estudo.md. Vamos começar com a Fase 0... O que acha que devemos abordar nessa fase 0?"* e posterior solicitação de detalhamento sobre ATE, ATT, ATC, CATE, SUTVA e Rubin/Neyman.
* **O que o Notebook Respondeu:** Redigiu o texto completo e reestruturado para a Fase 0, cobrindo a Escada da Causalidade de Pearl, o Problema Fundamental da Inferência Causal, o Modelo de Resultados Potenciais, as métricas de efeito (ATE, ATT, ATC, CATE), a suposição SUTVA (não-interferência e consistência), a lógica dos RCTs e o Paradoxo de Simpson.
* **Fontes Utilizadas:** `Conteúdo.md`, `Planos_de_Estudo.md`, *Causal Inference: The Mixtape*, *Causal Inference and Discovery in Python*, arXiv:2403.02467, arXiv:1608.00060.

### 📍 Pergunta 2: Esclarecimento Conceitual sobre Viés de Seleção vs. Collider Bias

* **Pergunta do Usuário:** *"Viés de seleção e collider bias são duas coisas diferentes, não era para ser viés de colisor?"* e *"mas viés de seleção não seria quando ocorre a escolha enviesada da amostragem e viés de colisor quando cria uma falsa correlação?"*
* **O que o Notebook Respondeu:** Explicou que o *Viés de Colisor* é a estrutura gráfica e matemática (condicionar em uma consequência comum), enquanto o *Viés de Seleção* é a manifestação prática desse fenômeno no processo de amostragem (exilando subpopulações). Iluminou a questão com o histórico Exemplo dos Aviões de Abraham Wald (Viés de Sobrevivência) e o Viés de Seleção de Heckman na econometria.
* **Fontes Utilizadas:** *Causal Inference and Discovery in Python*, *Miguel Hernán | Harvard CAUSALab*, *Causal Inference: The Mixtape*, `Conteúdo.md`.

### 📍 Pergunta 3: Aprofundamento na Fase 2 (Desenhos Experimentais, Quase-Experimentais e TTE)

* **Pergunta do Usuário:** *"Vamos avançar para a Fase 2... apresentar abordagens utilizadas em 2026"* e *"Em Estudos Observacionais e Ignorabilidade Condicional, o correto seria isolar o efeito ou ajustar o X?"*
* **O que o Notebook Respondeu:** Apresentou o ecossistema completo da Fase 2: RCTs, Target Trial Emulation (TTE) baseado nas diretrizes internacionais **TARGET**, Ignorabilidade Condicional, PSM, IPW, Estimadores Duplamente Robustos, DiD (incluindo adoção escalonada de Callaway &amp; Sant'Anna), RDD, Variáveis Instrumentais (2SLS) e Controle Sintético com CausalPy. Esclareceu que "ajustar por $X$" é precisamente a operação matemática para "isolar o efeito".
* **Fontes Utilizadas:** BMJ 2025 (TARGET Statement), *Miguel Hernán | Harvard*, `Planos_de_Estudo.md`, `Conteúdo.md`, *Causal Inference: The Mixtape*.

### 📍 Pergunta 4: Construção de Exemplos Práticos da Fase 2

* **Pergunta do Usuário:** *"Atualizei a Fase 2 adicionando sobre Efeitos Fixos e Efeitos Aleatórios. Quais exemplos práticos podemos construir para aplicar os conceitos da Fase 2?"*
* **O que o Notebook Respondeu:** Formulou 5 projetos práticos aplicados em Python: (1) Lalonde NSW com PSM/IPW e AIPW; (2) DiD e Efeitos Fixos de Duas Vias (TWFE) para Salário Mínimo; (3) Variáveis Instrumentais com Instituições (AJR) em 2SLS; (4) RDD no programa social Progresa com teste de McCrary; (5) Controle Sintético Bayesiano para impacto de marketing.
* **Fontes Utilizadas:** `Conteúdo.md`, `Planos_de_Estudo.md`, *Causal Inference: The Mixtape*.

### 📍 Pergunta 5: Fase 3 — Robustez, Validade, Testes de Refutação e Código Prático

* **Pergunta do Usuário:** *"Vamos avançar para a Fase 3 - Robustez, Validade e Testes de Refutação"* com posterior expansão para Overlap, Balanço de Covariáveis (SMD/KS), SUTVA, Transportabilidade, d-separação empírica, Bootstrap, E-value, Sensemakr (Cinelli) e refutadores DoWhy.
* **O que o Notebook Respondeu:** Elaborou o compêndio completo da Fase 3, explicando por que a Validação Cruzada Preditiva falha para Causalidade (devido a Classes de Equivalência de Markov) e aplicando a filosofia Popperiana de falsificação. Além da teoria, **gerou e executou um script Python completo (`validacao_causal.py`)** e um gráfico de suporte comum (`overlap_plot.png`), aplicando testes empíricos de Overlap, SMD, KS, Random Common Cause, Placebo Treatment, Data Subsets, E-value e $R^2$ parcial de sensibilidade.
* **Fontes Utilizadas:** *DoWhy GitHub / PyWhy*, *EconML Documentation*, arXiv:1608.00060, BMJ 2025 (TARGET), `Conteúdo.md`, `Planos_de_Estudo.md`.
