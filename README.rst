Github CI
===========================

.. contents:: **Daftar Isi**

Compile latex dokumen dengan Github CI. 

Tutorial
---------------------------

- `Github documentation: Github Actions`_
- `Docker blog: Github Actions`_ 

Github Actions File
---------------------------

Buatlah file .github/workflows/compile.yml. Isinya sebagai berikut:

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

.. Referensi

.. _`Github documentation: Github Actions`: https://docs.github.com/en/free-pro-team@latest/actions
.. _`Docker blog: Github Actions`: https://www.docker.com/blog/docker-github-actions/
