# Unofficial Uni Freiburg Thesis-Template

This is a minimal template for a [german or english bachelor's or master's thesis](output/main.pdf).

It uses the Corporate Design of the University of Freiburg and fulfills the requirements for the technical faculty (e.g. the supervisor is only mentioned in the acknowledgments not in the [sections/information.tex](sections/information.tex)).

**I wish you all the best and let me know about any issues!**

## Prerequisites

This [Video-Explanation](https://www.youtube.com/watch?v=vIImoKpKWIo) gives an overview of the used programs:

### Visual Studio Code (VSC)

[Visual Studio Code (VSC)](https://code.visualstudio.com/)

### TeX Live and LaTeX-Formatter

[TeX Live](https://www.tug.org/texlive/) and the optional [LaTeX-Formatter](https://github.com/cmhughes/latexindent.pl)

install on Linux Mint:

```bash
sudo apt update && sudo apt install texlive-full texlive-extra-utils
```

### VSC Extension LaTeX-Workshop

[VSC Extension LaTeX-Workshop](https://github.com/James-Yu/LaTeX-Workshop)

VSC should ask you to install it.
If not, go to Extensions by pressing CTRL + SHIFT + X and search @recommended.

## Usage

### AI Declaration

There is currently a debate among professors on the AI declaration
(both if it should be added and if you are allowed to use AI). It is
important to discuss this early -- most professors are fine with it,
but you don't wont to discover that one of them is not after writing
your thesis. We have included an example, which you need to update to
match the AI declaration.

You should update the declaration to match your usage of AI.

The AI declaration is a way to make sure that if in the future it
turns to be possible to detect AI usage, you have properly declared it
(unlike various German politicians).

You can also delete the line if your supervisor does not want it
(search for `AI declaration` in `main.tex`).

### Cover

#### Get Cover

The official template for the cover is from the Corporate Design of the University of Freiburg:

<https://cd.uni-freiburg.de/buerovorlagen/#latex-vorlagen>

1. Download it.
2. Extract it.
3. Open it in VSC.
4. Delete the german or english directory that you don't want to use.
5. Compile it.

If you have any issues, make it one single file:
Open the .tex-file that is not `setup.tex`, replace

```TeX
\input{setup}
```

with the content of `setup.tex` and delete `setup.tex`.

#### Insert Cover

1. Rename the compiled PDF to `cover.pdf`.
2. Copy it into the `assets` directory.
3. Compile the thesis.
4. Check the cover in the PDF.

### Hints

Sometimes there is no PDF generated, especially when you open the project for the first time.
Just wait a few seconds, recompile and if it still doesn't work, restart VSC or your computer.

More hints and examples are given in the file [sections/conclusion.tex](sections/conclusion.tex).

There is also a Guide written by the Github Copilot, checked by hand:
[GUIDE_AI_Generated.md](GUIDE_AI_Generated.md)
Everything else in this archive is not written by AI.
