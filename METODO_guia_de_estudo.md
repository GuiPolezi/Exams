# Método para construir um guia de estudo de prova (modelo replicável)

Este documento registra o planejamento e a lógica usados para criar o guia
`guia_estudo_AM_P1.html` (Aprendizado de Máquina, P1). Ele foi escrito para ser
reaproveitado: troque a matéria, os arquivos e as anotações, mantenha o processo.

Use-o de duas formas:

1. Como **checklist pessoal** ao montar um guia por conta própria.
2. Como **prompt de contexto** para uma IA: cole este arquivo junto com os
   materiais da nova prova e peça "siga o método descrito".

---

## 1. Entradas necessárias

Reúna antes de começar. Quanto mais completo, mais preciso o recorte da prova.

| Entrada | Para que serve | Exemplo da P1 de AM |
|---|---|---|
| Ementa oficial da disciplina | Universo total de temas | 6 blocos (KDD, supervisionado, associação, classificação, agrupamento, outliers) |
| Temas efetivamente dados até a prova (planilha/cronograma do professor) | Recorte do que cai | 4 temas marcados até a P1 |
| Slides teóricos | Conceitos e definições exatas do professor | aula_02t, 03t, 04t, 06t (PDF) |
| Notebooks / código de aula | Funções e sintaxe cobradas | aula2, aula3, aula5, aula6, aula7 (.ipynb e PDF) |
| Anotações próprias | Ênfases orais do professor, avisos ("focar em conceito") | Notas das aulas 1 a 5 |
| Formato da avaliação | Decide o tipo de exercício a treinar | P1 = 50%, provável escrita de código |

Regra: **o que o professor mostrou vale mais que a ementa**. A ementa define o
teto; o material dado define o que estudar.

---

## 2. Processo em 7 etapas

### Etapa 1 — Inventário do material

Para cada arquivo, registrar: tipo (teoria/prática), tema, se está legível.

- PDFs de slides muitas vezes são **imagens sem camada de texto**: verificar com
  `pdffonts`; se vazio, rasterizar (`pdftoppm -r 60 -png`) e OCR (`tesseract`).
- Notebooks: extrair células (`extract-text arquivo.ipynb` ou `jupyter nbconvert --to script`).
- Anotar o que **não** está no material (ex.: "regras de associação: nenhum slide").

Saída: uma tabela "arquivo → tema → módulo do guia".

### Etapa 2 — Recorte da prova

Cruzar três listas: ementa × cronograma × material. Classificar cada tema em:

- **Núcleo**: tem slide E código E anotação → estudar a fundo.
- **Conceitual**: só slide → saber definir e comparar.
- **Lacuna**: na ementa/cronograma mas sem material → módulo "mínimo defensável" e
  aviso explícito para o aluno confirmar com o professor.
- **Fora**: só na ementa, para provas futuras → listar em "o que não cai".

### Etapa 3 — Encontrar o fio condutor

Todo conjunto de aulas tem uma narrativa. Em AM foi um **pipeline**
(dados → explorar → limpar → reduzir → classificar). Em outras matérias pode ser:
uma linha do tempo (história), uma hierarquia (redes: camadas), um ciclo (engenharia
de software), uma cadeia de dependências matemáticas (cálculo).

O fio condutor define:
- a **ordem dos módulos** (cada um usa vocabulário do anterior);
- o **eixo do mapa mental**;
- a **frase de abertura** do guia ("Do dado bruto ao classificador…").

### Etapa 4 — Estrutura fixa de cada módulo

Cada módulo segue o mesmo esqueleto, sempre nesta ordem:

1. **Título** com número e nome do tema.
2. **Bloco "Por que estudar"** (2–3 linhas): finalidade, onde aparece na prova, o
   que o aluno ganha sabendo. Responde "por que perder tempo com isso?".
3. **Conteúdo**: definições nas palavras do professor, tabelas comparativas para
   qualquer par/trinca de conceitos (tipo × operação × exemplo; técnica × fórmula ×
   resultado × função), listas curtas para enumerações.
4. **Exemplo resolvido** com números pequenos e conta aberta (média, distância,
   normalização, autovalor 2×2). Sempre um exemplo que caberia numa prova escrita.
5. **Bloco "Como fica no código"** quando há prática: apenas o trecho essencial,
   comentado linha a linha.
6. **Perguntas que o leitor faria** (4–7 pares pergunta/resposta): dúvidas que
   surgem ao ler, confusões clássicas, "e se…", diferenças entre termos parecidos.
7. **Bloco "Provável na prova"**: 2–4 formatos de questão concretos, de preferência
   reaproveitando exercícios que o professor deixou nos slides.

Cores/rótulos fixos ajudam a varrer o guia: amarelo = por que, vermelho = prova,
verde = código, caixa tracejada = exemplo resolvido, caixa branca = perguntas.

### Etapa 5 — Elementos transversais

Produzidos depois dos módulos, porque dependem deles:

- **Mapa mental**: raiz = disciplina; 1 ramo por módulo; 3–4 folhas por ramo com
  os termos-chave. Ler da esquerda para a direita segue o fio condutor. Formato:
  SVG simples (retângulo raiz + linhas + textos) ou lista aninhada em texto.
- **Ordem de estudo**: lista numerada com tempo sugerido e justificativa de
  dependência ("sem X você não lê a questão de Y").
- **Colinha de código**: tabela função → o que responde, agrupada por notebook;
  depois os scripts completos (EDA, transformação, algoritmo) e uma seção de erros
  frequentes (warnings, dimensões, NaN).
- **Fórmulas que caem**: só as que o professor mostrou, em uma página, com um
  exemplo numérico resolvido logo abaixo.
- **Flashcards**: 20–30 perguntas de resposta curta, cada uma marcada com o
  módulo de origem para o aluno saber onde voltar. Misturar definição, comparação,
  cálculo e código.
- **"O que não cai / lacunas"**: transparência sobre o que ficou de fora e o que
  foi inferido.

### Etapa 6 — Critérios de qualidade do texto

- Definições fiéis aos slides (mesmos termos que o professor usará na prova).
- Toda comparação em tabela; toda sequência em lista numerada; nunca parede de texto.
- Todo conceito abstrato ganha um exemplo com os datasets das aulas (aqui: cardekho,
  iris, commodities CEPEA). Números reais das saídas dos notebooks (r = 0,9994,
  167 duplicatas, PC1 = 92,5%) ancoram a memória.
- Explicar o "porquê" além do "o quê": por que n−1, por que padronizar antes do
  PCA, por que k ímpar.
- Marcar o que é inferência do autor ("provável na prova") e o que é fato do material.

### Etapa 7 — Revisão final

Checklist antes de entregar:

- [ ] Cada tema do cronograma tem um módulo ou está na seção de lacunas.
- [ ] Cada notebook tem suas funções na colinha.
- [ ] Cada exercício deixado nos slides está respondido em algum "Provável na prova".
- [ ] Cada módulo tem pelo menos um exemplo resolvido e um bloco de perguntas.
- [ ] Flashcards cobrem todos os módulos.
- [ ] HTML válido (tags balanceadas), navegação funciona, responsivo.

---

## 3. Lógica do site estático

O guia é **um único arquivo HTML** sem dependências obrigatórias (fontes do Google
são opcionais; há fallback). Motivos: abre em qualquer dispositivo, funciona
offline, é fácil de versionar e de copiar para a próxima prova.

### Layout

```
+-----------+----------------------------------------+
| nav fixa  | hero: título-frase + parágrafo + fatos |
| (sumário) |----------------------------------------|
| módulos   | #mapa    mapa mental (SVG)             |
| ferramen. | #ordem   ordem de estudo               |
| legenda   | #m1..#mN módulos (esqueleto da etapa 4)|
|           | #codigo  colinha + scripts + erros     |
|           | #formulas                              |
|           | #quiz    flashcards (<details>)        |
|           | #ementa  lacunas e o que não cai       |
+-----------+----------------------------------------+
```

- Grid de duas colunas (260px + 1fr); em telas < 900px a nav vira um bloco no topo.
- Conteúdo alinhado à esquerda, largura máxima de leitura ~72 caracteres.
- Um `IntersectionObserver` realça no sumário a seção visível.

### Tokens de design (trocar por matéria para dar identidade própria)

| Token | Valor usado | Papel |
|---|---|---|
| `--paper` | #F3F5F8 | fundo da página |
| `--ink` | #14213D | texto e nav |
| `--navy` | #1D3F8C | títulos de seção, botões, raiz do mapa |
| `--mustard` | #E0A526 | "por que estudar", números da ordem, foco |
| `--coral` | #D2553E | "provável na prova" |
| `--mint` | #2C8C6A | blocos de código |
| Tipografia | IBM Plex Sans + IBM Plex Mono | texto + código/fórmulas |

Sugestão para outras disciplinas: manter a estrutura e trocar a paleta e a fonte
(ex.: matéria de redes em tons frios com fonte geométrica; história em serifada).
Evitar o padrão "creme + terracota" e "preto + verde neon", que soam genéricos.

### Componentes reutilizáveis (classes CSS)

| Classe | Uso |
|---|---|
| `.why` | bloco amarelo "Por que estudar" |
| `.prova` | bloco vermelho "Provável na prova" |
| `.code` | bloco verde com `<pre>` para código |
| `.ex` | caixa tracejada de exemplo resolvido |
| `.faq` + `<dl><dt><dd>` | perguntas que o leitor faria |
| `.steps` (`<ol>`) | sequência numerada (ordem de estudo, passos de algoritmo) |
| `.map` + `<svg>` | mapa mental |
| `.card` (`<details>`) | flashcard com resposta oculta |
| `details.snip` | trecho de código recolhido |
| `table` | qualquer comparação |

Realce de sintaxe no `<pre>`: `<span class="c">` comentário, `.k` palavra-chave,
`.s` string. Sem biblioteca externa.

### Interatividade mínima (JavaScript de ~8 linhas)

- Sumário ativo por rolagem.
- Botão "Fechar todas" nos flashcards.
- Tudo o mais é HTML nativo (`<details>`), o que garante acessibilidade por teclado.

### Como gerar para uma nova prova

1. Copiar o HTML, apagar as seções `#m1..#mN`, manter hero, nav, `#mapa`, `#ordem`,
   `#codigo`, `#formulas`, `#quiz`, `#ementa` como esqueleto.
2. Preencher os módulos com o esqueleto da etapa 4.
3. Redesenhar o SVG do mapa (1 ramo por módulo; y dos ramos espaçados igualmente).
4. Atualizar a nav e os "fatos" do hero (n módulos, n notebooks, datasets).
5. Trocar os tokens de cor/fonte.
6. Validar tags (script Python com `html.parser`) e abrir no navegador.

---

## 4. Prompt-modelo para pedir a uma IA

> Tenho a prova [P2] de [disciplina] em [data]. Anexo: ementa, cronograma do
> professor com os temas dados até a prova, slides (PDF), notebooks e minhas
> anotações. Siga o arquivo `METODO_guia_de_estudo.md`: faça o inventário do
> material (com OCR se os slides forem imagem), recorte os temas em núcleo /
> conceitual / lacuna / fora, identifique o fio condutor, e produza um único HTML
> com nav lateral, mapa mental em SVG, ordem de estudo, um módulo por tema seguindo
> o esqueleto (por que estudar, conteúdo em tabelas, exemplo resolvido, código,
> perguntas que o leitor faria, provável na prova), colinha de código, fórmulas,
> 20–30 flashcards e a seção de lacunas. Use definições fiéis aos slides e números
> reais das saídas dos notebooks. Troque a paleta para [cores] e a fonte para [fonte].
> Ao final, valide o HTML e me entregue também um resumo em texto no chat.

---

## 5. Registro do que foi feito na P1 de AM (para referência)

- 13 arquivos: 8 PDFs (4 de slides teóricos em imagem → OCR; 4 exportações de
  Colab com texto) e 3 notebooks; mais anotações do aluno.
- Recorte: 6 módulos núcleo/conceitual (KDD, dados, exploração, pré-processamento,
  PCA, KNN) + 1 lacuna (associação) + lista de temas de P2.
- Fio condutor: pipeline de dados.
- Datasets-âncora: cardekho (EDA), iris (PCA e KNN), séries de commodities (aula 7).
- Elementos: mapa SVG com 6 ramos, ordem de estudo de 6 passos (~10 h), 5 blocos
  de código (EDA, distâncias, PCA, KNN, erros), 12 fórmulas, 28 flashcards, 8 blocos
  de perguntas do leitor, 9 exemplos resolvidos.
