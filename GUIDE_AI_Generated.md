# Writer's Guide for LaTeX Thesis Template by Github Copilot

This guide provides best practices and patterns for using this thesis template effectively.

It is generated using github copilot on 01.12.2025.
The content is checked and some misleading or wrong things got deleted.

## Section Writing Patterns

### Starting a New Section

```latex
\section{Your Section Title}\label{sec:your_section}

\subsection{First Subsection}
Your content here.

\subsection{Second Subsection}
More content.
```

### Including Images

Always use relative paths and reference figures:

```latex
\begin{figure}
  \centering
  \includegraphics[width=0.8\textwidth]{assets/my-image.pdf}
  \caption{Description of your image}\label{fig:my_image}
\end{figure}

See \autoref{fig:my_image} for details.
```

**Image Tips**:

- Use PDF for vector graphics (diagrams, plots)
- Use PNG/JPG for photographs
- Width should be 0.6-0.8 of `\textwidth`
- Always include descriptive captions
- Always use `\autoref{}` not hardcoded numbers

### Creating Tables

Use `booktabs` for professional looking tables:

```latex
\begin{table}
  \centering
  \caption{Your table title}\label{tab:my_table}
  \begin{tabular}{lrc}  % l=left, r=right, c=center
    \toprule
    Header 1 & Header 2 & Header 3 \\
    \midrule
    Row 1 & 100 & \SI{50}{\percent} \\
    Row 2 & 200 & \SI{75}{\percent} \\
    \bottomrule
  \end{tabular}
\end{table}

See \autoref{tab:my_table} for comparison.
```

**Table Tips**:

- Use `\toprule`, `\midrule`, `\bottomrule` (not `\hline`)
- Use `\SI{}{}` for units and percentages
- Keep tables concise
- Always reference with `\autoref{}`

### Code Listings

For code examples (there is a better option in the [`sections/abstract.tex`](sections/abstract.tex)):

```latex
\begin{verbatim}
def hello_world():
    print("Hello, World!")
\end{verbatim}
```

For better formatting with syntax highlighting, add to `setup.tex`:

```latex
\usepackage{listings}
\lstset{
  language=Python,
  basicstyle=\ttfamily\small,
  keywordstyle=\bfseries,
  commentstyle=\itshape\gray,
  breaklines=true
}
```

Then use:

```latex
\begin{lstlisting}
def hello_world():
    print("Hello, World!")
\end{lstlisting}
```

## Citation Patterns

### Adding Bibliography Files

Add your `.bib` files to the `references/` directory. At the end of your thesis (in `sections/140_references.tex`), include:

```latex
\bibliographystyle{plainnat}
\bibliography{references/fundamentals,references/motivation}
```

### Citing Sources

In your text, use one of these citation styles:

```latex
% Parenthetical citation
Research shows \cite{AuthorYear} that...

% Narrative citation (Author mentioned in text)
\citet{AuthorYear} discovered that...

% Multiple citations
Multiple studies \cite{Author1Year,Author2Year} suggest...

% Citation with page
\cite[p.~42]{AuthorYear} states that...
```

### Bibliography File Format

Create `.bib` files in `references/` following this format:

```bibtex
@article{Smith2020,
  author = {Smith, John and Jones, Mary},
  title = {Title of the article},
  journal = {Journal Name},
  volume = {42},
  pages = {100--115},
  year = {2020}
}

@book{Doe2019,
  author = {Doe, Jane},
  title = {Complete Book Title},
  publisher = {Publisher Name},
  year = {2019},
  edition = {2nd}
}
```

## Math & Units

### Writing Equations

Inline math uses single `$`:

```latex
The formula $E = mc^2$ shows...
```

Display equations use `equation` environment:

Or with labels for reference:

```latex
\begin{equation}\label{eq:my_equation}
  F = ma
\end{equation}

According to \autoref{eq:my_equation}, force equals...
```

### SI Units

Always use `\SI{}{}` for physical quantities:

```latex
% Correct
The speed is \SI{50}{\meter\per\second}.
The energy is \SI{100}{\joule}.
The efficiency is \SI{85}{\percent}.

% Avoid
The speed is 50 m/s.
The energy is 100 J.
```

## Cross-References

Always use LaTeX cross-references, never hardcode numbers:

```latex
\section{Introduction}\label{sec:intro}
% ... content ...

\section{Methods}\label{sec:methods}
As discussed in \autoref{sec:intro}...

\begin{figure}
  \includegraphics{...}
  \label{fig:example}
\end{figure}

\autoref{fig:example} shows...

\begin{table}
  \label{tab:results}
  ...
\end{table}

\autoref{tab:results} indicates...
```

## Structuring Complex Sections

For large sections, break them into subsections and subsubsections:

```latex
\section{Fundamentals}\label{sec:fundamentals}

\subsection{Background}\label{subsec:background}
Historical context...

\subsection{Core Concepts}\label{subsec:concepts}

\subsubsection{First Concept}
Details about first concept...

\subsubsection{Second Concept}
Details about second concept...

\subsection{Current State}\label{subsec:current}
Recent developments...
```

## Creating Lists

### Bullet Lists

```latex
\begin{itemize}
  \item First point
  \item Second point
    \begin{itemize}
      \item Nested point
      \item Another nested point
    \end{itemize}
  \item Third point
\end{itemize}
```

### Numbered Lists

```latex
\begin{enumerate}
  \item First step
  \item Second step
  \item Third step
\end{enumerate}
```

### Description Lists

```latex
\begin{description}
  \item[Term 1:] Definition of term 1
  \item[Term 2:] Definition of term 2
\end{description}
```

## Special Characters & Formatting

| Want               | Use             | Output     |
| ------------------ | --------------- | ---------- |
| Emphasis           | `\emph{text}`   | _text_     |
| Bold               | `\textbf{text}` | **text**   |
| Typewriter         | `\texttt{code}` | `code`     |
| Small caps         | `\textsc{text}` | SMALL CAPS |
| Dash               | `--`            | –          |
| Hyphen             | `-`             | -          |
| Em-dash            | `---`           | —          |
| Non-breaking space | `~`             | (space)    |
| Ellipsis           | `\ldots`        | …          |

## Common Mistakes to Avoid

### Spacing Issues

```latex
% Wrong: No space before citation
The result (Smith2020) shows...

% Correct: Space and proper citation
The result~\cite{Smith2020} shows...

% Wrong: Hardcoded references
See Figure 5 for...

% Correct: Automatic references
See \autoref{fig:example} for...
```

### Math Mode Issues

```latex
% Wrong: Plain text in math
The area is 50 m^2.

% Correct: Proper math and units
The area is \SI{50}{\meter\squared}.
```

### Citation Issues

```latex
% Wrong: Citation outside sentence
(Smith 2020) showed that...

% Correct: Citation integrated
\citet{Smith2020} showed that...

% Or
Studies~\cite{Smith2020} show that...
```

## Debugging Compilation Errors

### "Undefined control sequence"

- Check spelling of commands
- Ensure package is imported in `setup.tex`

### "Undefined reference"

- Make sure you compiled the full thesis (not using `\includeonly`)
- Run compile again after adding new `\label{}` commands

### "Missing file"

- Check file paths are correct
- Use relative paths from `main.tex` directory
- Avoid spaces in filenames

### "Overfull hbox"

- Lines are too long or words too big
- Add `\allowbreak` or rewrite the sentence
- Use `sloppy` mode (already enabled in setup.tex)

## TODO Reminders

Use margin notes during writing:

```latex
\todo{Fix this citation}
\todo[inline]{This section needs more evidence}
\todo[color=yellow]{Check if this is correct}
```

These appear in the PDF.

## Best Practices Summary

1. **Always use labels**: `\label{sec:...}`, `\label{fig:...}`, `\label{tab:...}`, `\label{eq:...}`
2. **Always reference**: `\autoref{}`, `\cite{}` - never hardcode numbers
3. **Use SI units**: `\SI{}{}` for all quantities
4. **Include FloatBarrier**: At the start of each section
5. **Descriptive captions**: For all figures and tables
6. **Consistent style**: Match the structure of other sections
7. **Test compilation**: Compile frequently to catch errors early
8. **Full compile regularly**: At least before finalizing, to update all references

---

For more help, see the main `README.md` or the [LaTeX Wikibook](https://en.wikibooks.org/wiki/LaTeX).
