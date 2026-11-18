# Template LaTeX SBC

Repositório base para artigos da Sociedade Brasileira de Computação (SBC), com pdfLaTeX e BibTeX.

## 1. Instale as dependências

- **TeX Live** fornece o pdfLaTeX para gerar o PDF e o BibTeX para montar a bibliografia. O template também usa as coleções LaTeX básica, recomendada e extra, as fontes recomendadas e o suporte ao português.
- **`latexmk`** automatiza a compilação. Ele executa o pdfLaTeX e chama o BibTeX quando há referências a processar.

No Debian e no Ubuntu, execute os comandos abaixo.

```bash
sudo apt update
sudo apt install latexmk texlive-latex-base texlive-latex-recommended \
  texlive-latex-extra texlive-fonts-recommended texlive-lang-portuguese
```

## 2. Clone o repositório

```bash
git clone https://github.com/arthurhen00/latex-sbc-template.git meu-artigo
cd meu-artigo
```

## 3. Compile pelo terminal

Na raiz do projeto, execute o comando abaixo.

```bash
latexmk
```

O PDF fica em `build/main.pdf`. O `latexmk` roda o pdfLaTeX e chama o BibTeX quando há referências a processar. Para remover os arquivos gerados, rode `latexmk -C`.

A linha `\typeout{}` antes da bibliografia separa mensagens do log e permite que o `latexmk 4.76` detecte a etapa do BibTeX.

## 4. Edite o artigo

| Arquivo ou pasta | O que contém |
| --- | --- |
| `main.tex` | Título, autores, afiliação, abstract, resumo e inclusão das seções. |
| `secoes/` | Introdução, metodologia, resultados e conclusão. |
| `figs/` | Imagens do artigo. |
| `referencias.bib` | Referências no formato BibTeX, com uma entrada de exemplo. |
| `sbc-template.sty` e `sbc.bst` | Estilos de artigo e bibliografia da SBC. |
| `.latexmkrc` | Arquivo principal, compilador e pasta de saída. |
| `.vscode/` | Configuração opcional para o VS Code. |
| `.gitignore` | Regras para ignorar os arquivos de compilação. |

Ao adicionar uma figura, salve-a em `figs/` e use o caminho a partir da raiz, como `\includegraphics{figs/experimento.png}`. Para citar uma entrada de `referencias.bib`, use sua chave em `\cite{chave}`.

## Integração opcional com o VS Code

Abra a pasta do projeto no VS Code e instale a extensão recomendada pelo repositório. [LaTeX Workshop](https://marketplace.visualstudio.com/items?itemName=James-Yu.latex-workshop)

Com `main.tex` aberto, use os atalhos abaixo.

| Ação | Atalho |
| --- | --- |
| Compilar com LaTeX Workshop | `Ctrl+Alt+B` |
| Abrir a prévia do PDF no editor | `Ctrl+Alt+V` |