# Guias de estudo para provas

Repositório de guias de estudo em HTML, um por prova, gerados a partir do material das aulas
(slides, apostilas, notebooks, anotações). Os guias são **enxutos por projeto**: cabem no tempo
de estudo disponível, com uma versão expressa no topo. Quando já existe guia de uma prova anterior,
o guia novo traz **só o conteúdo novo**.

O guia é gerado pelo prompt [`MODELO_prompt_guia_de_estudo.md`](./MODELO_prompt_guia_de_estudo.md).

## Estrutura

```
.
├── README.md
├── MODELO_prompt_guia_de_estudo.md     # prompt-modelo (preencher e colar na IA)
└── <disciplina>/
    └── <prova>/
        ├── guia_estudo_<sigla>_<prova>.html   # o guia (abrir no navegador)
        ├── guia_estudo_<sigla>_<prova>.pdf    # versão impressa (opcional)
        ├── prompt_<prova>.md                  # cópia preenchida do modelo usada nesta prova
        ├── material/                          # slides, apostilas, notebooks, plano de ensino
        └── anotacoes.md                       # notas próprias de aula
```

Exemplo: `aprendizado-de-maquina/P1/guia_estudo_AM_P1.html`.

## Como criar um novo guia

1. **Reúna o material** em `<disciplina>/<prova>/material/`: plano de ensino (ementa e cronograma),
   slides, apostilas, notebooks, provas antigas e listas. Material com anotações à mão também entra:
   ele é o sinal mais forte de prioridade.
2. **Copie o modelo** para `<disciplina>/<prova>/prompt_<prova>.md` e preencha a tabela de parâmetros
   (seção 0): data e peso da prova, formato provável, tempo de estudo, tamanho máximo e identidade visual.
3. **Escolha o modo:**

   | Modo | Quando usar | O que anexar além do material |
   |---|---|---|
   | `COMPLETO` | Primeira prova da disciplina ou prova sem guia anterior | — |
   | `INCREMENTAL` | Já existe guia da prova anterior | O(s) guia(s) anterior(es), de preferência o HTML |

   No modo `INCREMENTAL`, informe se a prova é cumulativa. Se for, ou se não souber, o guia ganha uma
   caixa curta de "revisão relâmpago" da prova anterior.
4. **Gere o guia** colando o prompt preenchido na IA com o material anexado. O processo tem três fases:
   - **A · Auditoria** (subagente): inventário do material (com OCR se os slides forem imagem), recorte,
     comparação com o guia anterior (no modo incremental) e prioridade A/B/C de cada tópico.
   - **B · Escrita**: guia dentro do tamanho máximo; tópicos C vão para "cortado por tempo".
   - **C · Revisão** (subagente independente): fidelidade aos slides, contas refeitas, nada repetido da prova anterior, tamanho respeitado.
5. **Salve** o HTML (e o PDF, se gerar) na pasta da prova e registre na tabela abaixo.

## Como estudar com um guia

Abra o HTML no navegador:

1. Comece pela **Versão expressa** se o tempo estiver curto; senão, siga a **Ordem de estudo**.
2. No modo incremental, leia antes a caixa **Pontes com a prova anterior** (lembretes de uma linha).
3. Estude os módulos. Cada um usa as marcações fixas:

   | Marcação | Significado |
   |---|---|
   | amarelo | por que estudar aquilo (1 frase) |
   | tabela / lista | definições nas palavras do professor |
   | caixa tracejada | exemplo resolvido com conta aberta |
   | verde | código ou ferramenta (só em matérias com prática) |
   | branco (perguntas) | pegadinhas: confusões entre termos parecidos |
   | vermelho | formatos prováveis de questão |
   | etiqueta cinza `inferência` | interpretação do guia, não está no material |

4. Termine pelos **flashcards**: se errar um, o rótulo `[M#]` indica o módulo para revisar.
5. Confira a seção **Lacunas e cortado por tempo** para saber o que ficou de fora.

Para imprimir, use "Imprimir → Salvar como PDF" no navegador: o CSS de impressão esconde a navegação,
quebra página entre módulos e abre todos os flashcards.

## Guias disponíveis

| Disciplina | Prova | Modo | Guia | Temas |
|---|---|---|---|---|
| Aprendizado de Máquina | P1 | completo | `Aprendizado Máquina/P1.html` | KDD, dados, exploração, pré-processamento, PCA, KNN, associação |
| Redes de Computadores II | P1 | completo | `Redes de Computadores 2/P1.html` | Camada de transporte, portas, UDP, TCP, controle de fluxo e congestionamento, Telnet/SSH/FTP, DNS, SMTP/MIME/POP3/IMAP, HTTP e Proxy |
| Governança e Gestão de TI | P1 | completo | `Governança e Gestão de TI/P1.html` | Governança × gestão, COBIT (princípios, cascata, domínios), arquitetura corporativa e TOGAF, BPMN, CEP e Seis Sigma |
| Governança e Gestão de TI | P2 | incremental | `Governança e Gestão de TI/P2.html` | ITIL (gestão de serviços de TI), gestão de dados: COBIT APO14 e DMBOK (perfilamento, qualidade, ciclo de vida) |
