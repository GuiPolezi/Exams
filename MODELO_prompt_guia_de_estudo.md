# Modelo de prompt: guia de estudo enxuto para provas (qualquer disciplina)

> **Como usar**
> 1. Copie este arquivo e preencha a seção 0 (tudo entre `[colchetes]`).
> 2. Na seção 0, escolha o **modo**: `COMPLETO` (primeira prova ou prova sem guia anterior) ou
>    `INCREMENTAL` (já existe guia de uma prova anterior e só o conteúdo novo interessa).
> 3. Cole o arquivo no chat e anexe o material: zip das aulas, plano de ensino, suas anotações e,
>    no modo INCREMENTAL, o(s) guia(s) anterior(es) (o HTML é melhor que o PDF, porque é mais completo).
> 4. Apague as seções marcadas como "só INCREMENTAL" quando usar o modo COMPLETO, se quiser.

---

## 0. Parâmetros (preencha)

| Parâmetro | Valor |
|---|---|
| Disciplina | [nome] |
| Curso / instituição / semestre | [ex.: Ciência da Computação · EEP · 2º sem. 2026] |
| Prova | [P1 / P2 / Sub / Exame] · data [dd/mm/aaaa] · peso [x% da média] |
| Formato provável da prova | [dissertativa / múltipla escolha / cálculo / código / desenho de diagrama / misto / não sei] |
| Recorte oficial | [temas do cronograma até a prova, copie do plano de ensino, ou "deduza do plano de ensino anexo"] |
| Tempo de estudo disponível | [ex.: 2 h] → orçamento de leitura ativa ≈ [mesmo valor] |
| Versão expressa | [ex.: 30 min] |
| Tamanho máximo | [ex.: 8 páginas A4 impressas] (referência: ~1 página por módulo + 2 de elementos transversais) |
| Modo | [COMPLETO / INCREMENTAL] |
| Guia(s) anterior(es) | [nome do arquivo, só INCREMENTAL] |
| A prova é cumulativa? | [sim / não / não sei] (só INCREMENTAL; se "sim" ou "não sei", ver seção 2.4) |
| Prática/código na matéria? | [sim: linguagem/ferramenta / não] |
| Identidade visual | [cor de destaque e fonte; ou "mesma do guia anterior, trocando só a cor de destaque"] |

**Restrição principal:** concisão vale mais que completude. O guia precisa caber no orçamento acima. O que não
couber sai do guia e vai para a lista "cortado por tempo", em uma linha cada.

---

## 1. Fase A: auditoria do material (subagente "auditor")

Antes de escrever qualquer parte do guia, **lance um subagente** com a tarefa abaixo. Ele não escreve o guia.

### 1.1 Inventário
Para cada arquivo: tipo (teoria / prática / apostila / lista de exercícios / prova antiga), páginas, tema e se é legível.
- **PDF com pouco texto** (menos de ~80 palavras por página no `pdftotext`) provavelmente é slide em imagem: rasterize
  (`pdftoppm -r 80 -png`) e **olhe as páginas** ou rode OCR (`tesseract -l por`). Diagramas, tabelas e fórmulas em imagem
  são frequentemente o que mais cai.
- **Material com anotações do aluno** (grifos, setas, comentários à mão, "cai na prova"): examine as páginas como imagem.
  **As anotações são o sinal mais forte de prioridade.**
- **Notebooks e código**: extraia as células (`jupyter nbconvert --to script`) e guarde as saídas reais (números, formatos).
- **Provas antigas e listas**: valem ouro; registre cada questão e o tema dela.
- Ignore atalhos (`.url`) e manuais de ferramenta, a menos que o recorte peça uso da ferramenta.

### 1.2 Recorte
Cruze **ementa × cronograma × material** e classifique cada tema:
- **Núcleo**: tem material + exemplo/exercício ou anotação → estudar a fundo.
- **Conceitual**: só definição no material → saber definir e comparar.
- **Lacuna**: no cronograma, mas sem material → "mínimo defensável" + aviso para confirmar com o professor.
- **Fora**: só na ementa, ou de outra prova → listar em "o que não cai".

### 1.3 Cobertura contra o guia anterior (só INCREMENTAL)
Leia o(s) guia(s) anterior(es) inteiro(s) e classifique cada tópico do material:

| Status | Significado | Vai para o guia novo? |
|---|---|---|
| **COBERTO** | já explicado no guia anterior | Não |
| **NOVO** | não aparece no guia anterior | Sim |
| **EXPANSÃO** | o guia anterior só cita o nome, sem explicar | Só a parte nova |
| **PONTE** | conceito anterior necessário para entender um tópico novo | Lembrete de no máximo 1 linha: "ver guia [Px], módulo X" |

Arquivos que misturam temas de provas diferentes devem ser classificados **slide a slide**, não pelo arquivo inteiro.
Busque ativamente termos que o guia anterior só menciona de passagem: eles são os melhores candidatos a EXPANSÃO.

### 1.4 Prioridade
Para cada tópico que entra no guia:
- **A (essencial)**: aparece em vários slides, tem anotação, tem exercício/exemplo do professor, caiu em prova antiga ou é tema nominal do cronograma.
- **B (importante)**: definição ou lista que aparece uma vez, com destaque.
- **C (detalhe)**: menção solta, histórico, curiosidade → **"cortado por tempo"**, fora do guia.

### 1.5 Entrega do auditor
1. Tabela `arquivo/páginas → tópico → recorte → status (INCREMENTAL) → prioridade → justificativa`.
2. Lista de exercícios, exemplos e casos deixados pelo professor.
3. Lacunas.

Mostre-me um resumo da tabela (contagem por status e prioridade) antes de seguir. Se eu não responder, siga com ela.

---

## 2. Fase B: escrita do guia

### 2.1 Fio condutor
Encontre a narrativa do conjunto de aulas: pipeline (dados → modelo), linha do tempo (história), hierarquia (camadas de rede),
ciclo (engenharia de software, gestão), cadeia de dependências (cálculo), do geral ao específico (frameworks). O fio define a
**ordem dos módulos**, o **eixo do mapa mental** e a **frase de abertura** do guia.

### 2.2 Orçamento (obrigatório)
- Total ≤ [tamanho máximo]. Por módulo, cerca de 1 página impressa.
- Prioridade A ganha tabela + exemplo; prioridade B ganha uma linha de tabela ou um item de lista.
- Se estourar, corte nesta ordem: pegadinhas → segundo exemplo → itens B → texto corrido.
- **Nunca corte:** definições A, listas que a prova pode pedir de cor, fórmulas usadas nos exercícios, exercícios do professor.

### 2.3 Esqueleto de cada módulo
1. **Título** com número e tema.
2. **Por que estudar**: 1 frase (onde aparece na prova, o que destrava).
3. **Núcleo**: definições nas palavras do material (com o termo original em inglês, se for o caso); **toda comparação em tabela**;
   toda enumeração em lista curta; siglas expandidas na primeira vez.
4. **Exemplo resolvido** (1, só se houver conta, classificação, desenho ou caso): números pequenos, conta aberta, cabe numa prova escrita.
   Prefira os exemplos do professor.
5. **Como fica no código/ferramenta** (só se a matéria tiver prática): apenas o trecho essencial, comentado.
6. **Pegadinhas** (no máximo 3 pares pergunta/resposta): só confusões reais entre termos parecidos.
7. **Provável na prova** (2 a 4 itens): formatos concretos de questão, coerentes com o formato provável da seção 0.

### 2.4 Prova cumulativa (só INCREMENTAL)
Se a prova for cumulativa ou se não houver certeza, acrescente **uma caixa "Revisão relâmpago da prova anterior"** de no
máximo meia página: só os itens A do guia anterior, em formato de lista, sem explicação. Se a prova não for cumulativa, use apenas as pontes.

### 2.5 Elementos transversais (ordem no documento)
1. **Hero**: frase-fio + parágrafo de contexto + fatos (n módulos, casos-âncora) + alerta com data, peso e recorte.
2. **Versão expressa**: 4 a 6 itens A, com tempo de cada um, somando o tempo da seção 0.
3. **Ordem de estudo**: lista numerada com tempo e justificativa de dependência ("sem X você não lê a questão de Y").
4. **Mapa mental** em SVG: raiz = disciplina; 1 ramo por módulo; 3–4 folhas por ramo.
5. **Pontes com a prova anterior** (só INCREMENTAL): caixa única, no máximo 6 linhas.
6. **Módulos.**
7. **Colinha**: siglas, listas de cor, símbolos ou funções de código (tabela função → o que faz), conforme a matéria.
8. **Fórmulas**: só as do material, com um exemplo numérico. Se não houver, omita a seção.
9. **Flashcards**: 15 a 20 (ajuste ao tamanho), cada um com a tag [M#]; misture definição, diferença, lista, cálculo e código.
10. **Lacunas, o que não cai e cortado por tempo**: uma linha cada; diga o que é inferência.

### 2.6 Critérios de qualidade
- Definições fiéis ao material (os mesmos termos que o professor usará na prova).
- Marque com `<span class="infer">inferência</span>` tudo o que não está no material.
- Ancore conceitos em números e casos reais do material (saídas de notebooks, exemplos dos slides). Não invente caso se o professor deu um.
- Explique o "porquê" em meia frase quando ajudar a lembrar.
- Parágrafos de no máximo 3 linhas; nenhuma parede de texto.

---

## 3. Formato de saída

**Um único arquivo HTML** autocontido (funciona offline; fontes do Google opcionais, com fallback).

- **Layout:** grid de 2 colunas (nav fixa de 260px + conteúdo); abaixo de 900px a nav vira bloco no topo; largura de leitura de cerca de 72 caracteres;
  `IntersectionObserver` realça no sumário a seção visível; botão "Fechar todas" nos flashcards. Todo o resto em HTML nativo (`<details>`).
- **Componentes (classes):** `.why` (amarelo, por que estudar) · `.prova` (vermelho, provável na prova) · `.ex` (caixa tracejada, exemplo) ·
  `.faq` + `<dl>` (pegadinhas) · `.code` (verde, código) · `.tool` (ferramenta) · `.steps` (ordem numerada) · `.map` + `<svg>` (mapa) ·
  `.card` com `<details>` (flashcard) · `.infer` (inferência) · `table` (toda comparação). Legenda das cores na nav.
- **Identidade visual:** a da seção 0. Em modo INCREMENTAL, mantenha layout, classes e tipografia do guia anterior e troque só a cor de
  destaque, para que os guias formem uma coleção. Evite os visuais genéricos "creme + terracota" e "preto + verde neon".
- **CSS de impressão** (`@media print`): esconde a nav, quebra página entre módulos e expande os flashcards, para que "Imprimir → PDF"
  gere o resumo dentro do tamanho máximo.
- Valide as tags (script Python com `html.parser`) e renderize uma vez para conferir.

---

## 4. Fase C: revisão independente (subagente "revisor")

Lance um segundo subagente, que **não viu a produção**, com o guia, o material e (INCREMENTAL) o guia anterior. Ele confere:

- [ ] Todo tema do cronograma tem módulo ou está em lacunas.
- [ ] Todo tópico A está no guia; nenhum tópico C entrou.
- [ ] Amostra de pelo menos 10 definições conferidas na fonte: todas fiéis.
- [ ] Todo exercício/exemplo do professor aparece resolvido em um módulo ou em "Provável na prova".
- [ ] Todas as contas do guia foram refeitas (rodando o cálculo) e batem.
- [ ] As anotações do aluno estão refletidas nas prioridades.
- [ ] (INCREMENTAL) Nada repete o guia anterior além das pontes e da revisão relâmpago.
- [ ] Tamanho máximo e versão expressa respeitados.
- [ ] Flashcards cobrem todos os módulos; HTML válido; navegação e impressão funcionam.

Corrija o que o revisor apontar antes de entregar.

---

## 5. Entrega
1. O HTML do guia.
2. No chat: o resumo da auditoria (contagem por status/prioridade), a versão expressa em texto e a lista "cortado por tempo".
