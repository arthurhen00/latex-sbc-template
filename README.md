# Template LaTeX SBC

Base para artigos da Sociedade Brasileira de Computação (SBC), com pdfLaTeX e BibTeX.

## 1. Prepare o WSL

No Ubuntu do WSL, instale o Git e os pacotes do TeX Live.

```bash
sudo apt update
sudo apt install git latexmk texlive-latex-base texlive-latex-recommended \
  texlive-latex-extra texlive-fonts-recommended texlive-lang-portuguese
```

No VS Code do Windows, instale a extensão da Microsoft para abrir projetos no WSL. [WSL](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-wsl)

## 2. Clone o repositório

No terminal do WSL, substitua `URL_DO_REPOSITORIO` pelo endereço do modelo.

```bash
git clone URL_DO_REPOSITORIO meu-artigo
cd meu-artigo
code .
```

Confira se o canto inferior esquerdo do VS Code mostra **WSL: Ubuntu** ou o nome da sua distribuição. Instale a extensão recomendada na janela conectada ao WSL. [LaTeX Workshop](https://marketplace.visualstudio.com/items?itemName=James-Yu.latex-workshop)

## 3. Compile o artigo

Compile pelo terminal a partir da raiz do projeto.

```bash
latexmk
```

O PDF fica em `build/main.pdf`. O `latexmk` roda o pdfLaTeX e chama o BibTeX quando há referências a processar. Para remover os arquivos gerados, rode `latexmk -C`.

A linha `\typeout{}` antes da bibliografia separa mensagens do log e permite que o `latexmk 4.76` detecte a etapa do BibTeX.

Use estes atalhos com `main.tex` aberto no VS Code.

| Ação | Atalho |
| --- | --- |
| Compilar com LaTeX Workshop | `Ctrl+Alt+B` |
| Abrir a prévia do PDF no editor | `Ctrl+Alt+V` |

## 4. Edite o artigo

| Arquivo ou pasta | O que contém |
| --- | --- |
| `main.tex` | Título, autores, afiliação, abstract, resumo e inclusão das seções. |
| `secoes/` | Introdução, metodologia, resultados e conclusão. |
| `figs/` | Imagens usadas no artigo. |
| `referencias.bib` | Referências no formato BibTeX, com uma entrada de exemplo. |
| `sbc-template.sty` e `sbc.bst` | Estilos de artigo e bibliografia da SBC. |
| `.latexmkrc` | Arquivo principal, compilador e pasta de saída para o terminal. |
| `.vscode/` | Recomendação da extensão e pasta de saída para o editor. |
| `.gitignore` | Regras para ignorar os arquivos de compilação. |

Ao adicionar uma figura, salve-a em `figs/` e use o caminho a partir da raiz, como `\includegraphics{figs/experimento.png}`. Para citar uma entrada de `referencias.bib`, use sua chave em `\cite{chave}`.
