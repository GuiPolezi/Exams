# Guias de estudo para provas

Repositório de guias de estudo em HTML, um por prova, gerados a partir do material
das aulas (slides, notebooks, anotações). O método de construção está em
[`METODO_guia_de_estudo.md`](./METODO_guia_de_estudo.md).

## Estrutura

```
.
├── README.md
├── METODO_guia_de_estudo.md       # como montar um guia (modelo replicável)
└── <disciplina>/
    └── <prova>/
        ├── guia_estudo_<sigla>_<prova>.html   # o guia (abrir no navegador)
        ├── material/                          # slides, notebooks, PDFs das aulas
        └── anotacoes.md                       # notas próprias de aula
```

Exemplo: `aprendizado-de-maquina/P1/guia_estudo_AM_P1.html`.

## Como criar um novo guia

1. **Reúna o material** em `<disciplina>/<prova>/material/`: ementa, cronograma
   do professor com os temas dados até a prova, slides, notebooks e suas anotações.
2. **Gere o guia** com uma IA usando o prompt da seção 4 do `METODO_guia_de_estudo.md`,
   anexando o método e todo o material. Ou monte manualmente seguindo as 7 etapas
   da seção 2.
3. **Confira o checklist** da etapa 7 do método (todo tema tem módulo, todo
   notebook está na colinha, todo exercício dos slides está respondido).
4. **Salve** o HTML na pasta da prova e registre abaixo.

## Como estudar com um guia

Abra o HTML no navegador e siga a seção **Ordem de estudo**. Cada módulo tem
cinco marcações fixas:

| Marcação | Significado |
|---|---|
| amarelo | por que estudar aquilo |
| tabela / lista | conteúdo com as definições do professor |
| caixa tracejada | exemplo resolvido com conta aberta |
| verde | código cobrado |
| branco (perguntas) | dúvidas que surgem ao ler, já respondidas |
| vermelho | formatos prováveis de questão |

Termine pelas **flashcards**: se errar uma, o rótulo `[M#]` indica o módulo para revisar.

## Guias disponíveis

| Disciplina | Prova | Guia | Temas |
|---|---|---|---|
| Aprendizado de Máquina | P1 | `Aprendizado Máquina/P1.html` | KDD, dados, exploração, pré-processamento, PCA, KNN, associação |
| Redes de Computadores II | P1 | `Redes de Computadores 2/P1.html` | Camada de transporte, portas, UDP, TCP, controle de fluxo e congestionamento, Telnet/SSH/FTP, DNS, SMTP/MIME/POP3/IMAP, HTTP e Proxy |
