# Github CI

Coba compile latex dokumen dengan Github CI. 

## Github Action File

Buatlah file di folder .github/workflows/docker-image.yml

```
name: Build LaTeX document
on:
  push:
    paths:
    - '**.tex'
jobs:
  build_latex:
    runs-on: ubuntu-latest
    steps:
      - name: Set up Git repository
        uses: actions/checkout@v1
      - name: Compile LaTeX document
        uses: xu-cheng/latex-action@master
        with:
          root_file: main.tex
      - name: Uplod PDF 
        uses: actions/upload-artifact@v1
        with:
          name: PDF
          path: main.pdf
```          
