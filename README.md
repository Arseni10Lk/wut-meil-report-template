# WUT MEiL: Intermediate Project & Report Template

LaTeX template for **intermediate projects** (praca przejściowa) and **course reports** at the
Faculty of Power and Aeronautical Engineering (MEiL), Warsaw University of Technology.

It is a modified version of [WUT-Thesis](https://github.com/ArturB/WUT-Thesis) by Artur M. Brodzki
and Piotr Woźniak, which covers Bachelor's and Master's theses only.

## 1. Download the template

You don't need a GitHub account.

1. At the top of this page, click the green **Code** button.
2. Click **Download ZIP**.

The ZIP contains two ready-to-use documents:

- `intermediate-project.tex`: intermediate project, one author
- `report.tex`: course report, written by a group

## 2. Open it

### Option A: Overleaf (easiest, nothing to install)

1. Sign in at [overleaf.com](https://www.overleaf.com). A free account is enough.
2. Click **New Project → Upload Project** and choose the ZIP file. You don't need to unzip it.
3. Open **Menu** (top left) and set **Main document** to `intermediate-project.tex` or `report.tex`.
4. Click **Recompile**.

### Option B: TeXstudio on your computer

**Install once:**

1. A LaTeX distribution:
   - Windows: [MiKTeX](https://miktex.org/download). The first time you compile, it asks to install
     missing packages. Click **Install**.
   - macOS: [MacTeX](https://www.tug.org/mactex/)
   - Ubuntu: run `sudo apt install texlive-full` in a terminal
2. [TeXstudio](https://www.texstudio.org/)

**Every time:**

1. Unzip the ZIP file (Windows: right-click it → **Extract All**). Keep the files together: the
   `src` and `img` folders must stay next to the `.tex` file.
2. In TeXstudio, open `intermediate-project.tex` or `report.tex` with **File → Open**.
3. Press **F5** (Build & View). The PDF appears on the right.

**If something goes wrong:**

- Citations show up as bold names like **[lamport1994latex]** instead of numbers: press **F8**
  (builds the reference list) and then **F5** again.
- TeXstudio says `I found no \citation commands`: it is using BibTeX instead of Biber. Close and
  reopen the `.tex` file, or go to **Options → Configure TeXstudio → Build** and set
  **Default Bibliography Tool** to **Biber**.

### Option C: command line

```bash
latexmk -pdf intermediate-project.tex
```

## 3. Fill in the title page

Near the top of the `.tex` file, below the `Title page` comment, replace the example text:

| Command | Printed as |
|---|---|
| `\facultymeil` / `\facultyeiti` | Faculty header |
| `\langeng` / `\langpol` | Language of the document and title page |
| `\institute{...}` | "Institute of ..." |
| `\worktype{...}` | Type of work, large and bold. Defaults to "Intermediate Project" / "Praca przejściowa" |
| `\fieldofstudy{...}` | Free-text line under the type of work: field of study, laboratory or course name |
| `\title{...}` | Title |
| `\author{...}` | Name and student ID; separate group members with `\\` |
| `\supervisor{...}` | Supervisor, under "Project supervisor:" / "Opiekun projektu:" |

## 4. Write

- **Figures:** put the image file in the `img` folder and replace `example-image` with its name,
  e.g. `\includegraphics[width=0.6\textwidth]{my-plot.png}`.
- **References:** add entries to `references.bib`. Google Scholar gives them ready-made: click
  **Cite** under a search result, then **BibTeX**, and paste the text into the file. Cite it in the
  text with `\cite{key}`, where `key` is the first word after `@article{` (or `@book{`, ...).
- **Code:** see the listings in the examples. MATLAB uses `style=Matlab-editor`, other languages
  use `style=code, language=Python` (or `C`, `C++`, `Java`, ...).

## Optional: nicer code highlighting with minted

The examples use `listings`, which works everywhere. To use [minted](https://ctan.org/pkg/minted)
instead:

1. In the preamble, remove the `%` in front of `\usepackage{minted}` and `\setminted{...}`.
2. Write code as `\begin{minted}{python} ... \end{minted}`.

On Overleaf this works as is. On your own computer minted needs Python, and TeXstudio may need
`-shell-escape` added to the PdfLaTeX command (**Options → Configure TeXstudio → Commands**).

## Files

| File | Purpose |
|---|---|
| `intermediate-project.tex` | Intermediate project, single author |
| `report.tex` | Course report, group of authors |
| `references.bib` | Bibliography (biblatex + biber, IEEE style) |
| `img/` | Your figures |
| `src/wut-thesis.cls` | Document class |
| `src/{en,pl}/header/` | Faculty header used on the title page |

## Changes from WUT-Thesis

- Student groups are supported.
- The title is flexible.
- Commands have English names. Polish-language documents (`\langpol`) are still supported.

## License

GPL-3.0, the same as WUT-Thesis; see [LICENSE](LICENSE). Documents you write with this template
are your own and are not covered by the GPL.

The Warsaw University of Technology logo and the faculty header PDFs in `src/` are university
materials, included as in WUT-Thesis. The GPL does not cover them.
