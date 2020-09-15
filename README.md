  Math2200 Discrete Mathematics $\LaTeX$ HW Template
======================================================
_UofU Fall 2020 - Prof. Vaibhav Pandey_

<!-- 
 !-- This is a Markdown File!
 !-- It is meant to be viewed in a markdown viewer.
 !-- However, it is meant to be human readable as well.
 !-- So if you do not know how to work with markdown files you can just read is as is,
 !--    with very little difficulty.
 !-- It is just easier to read if viewed in a markdown editor/viewer.
 !--
 !-- Suggested Markdown Editors/Readers:
 !--   - dillinger.io :: A website for editing and viewing markdown (supper easy to use).
 !--       - Link: https://dillinger.io/
 !--   - vs-code :: A lightweight code editor that is highly extensible.
 !--       - Download: https://code.visualstudio.com/download
 !--   - Markdown Viewer :: A browser extension for Chromium based browsers and Firefox, fairly easy to use.
 !--       - Download - Chrome: https://chrome.google.com/webstore/detail/markdown-viewer?hl=en
 !--       - Download - Firefox: https://addons.mozilla.org/en-US/firefox/addon/markdown-viewer-chrome/
  -->

This is a $\LaTeX$ template system for doing the assignments for the Math2200 Discrete Mathematics course.
It is a modular file template, with many features and a fairly straight forward organizational structure.
It is set up in a way to hade most of the verbose and complicated header section of the document, 
    that is emissary to make the document work and look pretty.

It is fairly straight forward to use but I will include some pointers and best practices, 
    along with the basic instructions of how to do your work in the template.
One of the main things done in these templates are all of the problems form the book are already inputted into $\LaTeX$ for you
    _(If you downloaded a template for a specific HW assignment)_.
That way you can see some of the latex commands & environments used in the problems to get decent formatting,
    and use some of the more obscure symbols.

_**Please note:**_ 
  - _These are not set up instructions for the template or $\LaTeX$._
  - _Instructions on how to set up the template for [Overleaf](https://www.overleaf.com/projects) are in the [Discussion post](https://utah.instructure.com/courses/638114/discussion_topics/3804116) on canvas, where you likely got this template from._
  - _This template includes the vs-code files necessary for plugging and playing with an existing $\LaTeX$ setup in vs-code using the [$\LaTeX$ Workshop](https://marketplace.visualstudio.com/items?itemName=James-Yu.latex-workshop) vs-code Extension._


## First Things to Do:
Fill in the requisite information in [`main.tex`](./main.tex), this includes setting up your name and u# to be auto filled in the correct locations throughout the document.
(_**Note:** These felids are filled with place holders that will cause your document to fail to compile if you do not change them._)
These felids are located on lines 6 & 7 respectively in [`main.tex`](./main.tex).

 > #### [`main.tex`](./main.tex) _(pre-changes)_
 > ```latex
 > \def\yourName{<Your-Name>}           % - Your name to be put on the paper.
 > \def\yourUNum{u<Your-u#>}             % - Your u# to be put on the paper.
 > ```

 > #### [`main.tex`](./main.tex) _(post-changes)_
 > ```latex
 > \def\yourName{Jane Doe}           % - Your name to be put on the paper.
 > \def\yourUNum{u1234567}             % - Your u# to be put on the paper.
 > ```

After these changes have been made the document should compile just fine.
(in Overleaf press the "Compile" button or press <kbd>ctrl</kbd>+<kbd>Enter</kbd> (Mac OS: <kbd>⌘Cmd</kbd>+<kbd>return</kbd>)).


## Basic Usage:
To do the work for an exercise, 
 1. Navigate to the appropriate location in the project:
     1. Expand the `tex/` directory.
     2. Expand the directory labeled as the proper section (`s#-#/`).
          _i.e._ If the exercise you want to work on is in section 1.2 expand the `s1-2/` directory.
     3. Select the `.tex` file labeled with the desired exercise number (`e#.tex`).
          _i.e._ If the exercise you wan tto work on is numbered 22 open the file labeled `e22.tex`.
 2. Locate the appropriate location to start inputting your work in the file.
      - If the exercise you are working on has no parts just start your work under the "My Work" comment block.
      - If the exercise you are working on has parts they should be split up inside the `\begin{exercise}...\end{exercise}` environment that is in the proper order and should have the premise of the exercise part as it's first line already.
 3. _"TeX-up"_ your work in $\LaTeX$!
      - This part is very subjective to what you are doing and will very greatly on what you are doing.
 4. Make sure to denote your answer!
     1. Create a solution environment:
        ```latex
        \begin{solution}
            ...
        \end{solution}
        ```
     2. Type your solution on the inside of it.


## The File Structure:
This template uses a modular file structure with an organized structure.
This is done because it helps hide some of the mess involved in $\LaTeX$,
    it allows you to only have to see what is really important for the exercise you are working on without the destructions from other problems and document structure,
    and far easier to navigate and find things in the document, because otherwise $\LaTeX$ documents tend to all be pne file that is thousands of lines long & therefore a pain to scroll through and find anything.

To that effect these templates are built for the following structure:
```
./
│ main.tex
│ workspace.code-workspace
│
├─.vscode/
│   settings.json
│
├─code/
├─comm/
│   gen.bib
│   header.tex
│
├───fig
└─┬─tex
  │ s#-#.tex
  │
  └─s#-#
      e#.tex
```
  - `main.tex` :: is the primary compile point of the document, 
       it is where Chapter Headers reside, and the individual section documents are included from.
      - You can also create an external reference section by un-commenting out the code and including whatever you like to there.
      - The [`header.tex`](./comm/header.tex) file with most of the technical code is provided.
      - The Bibliography/Citation section is also generated from here, using the [Bib TeX (`.bib`)](https://en.wikipedia.org/wiki/BibTeX#Bibliographic_information_file) info from the [`gen.bib`](./comm/gen.bib) file.
  - `tex/` :: This is the directory where your $\LaTeX$ code is located in.
  - `tex/s#-#.tex` :: Files that follow this naming format are Section Files.
      - They contain the Section headers, 
          the `\begin{exercise} ... \end{exercise}` environment declarations for labeling the Exercises & providing references to them,
          the `\input{...}` statements for including the files for the individual Exercises,
          and any instructions that encompass multiple exercises.
  - `tex/s#-#/` :: The directory for exercise files for the specified chapter and section. 
  - `tex/s#-#/e#.tex` :: Files that are where you do your work for your exercises, 
       and the $\LaTeX$ code for the Exercise premise are.
      - If you have sub-exercises (Especially those denoted by letters) their work should be done in the appropriate `begin{exercise} ... \end{exercise}` environment inside the `\begin{subthm}{exercise} ... \end{subthm}` environment.
  - `fig/` :: This is a directory where you should put any pictures, or standalone $\LaTeX$ files that contain any Tikz pictures, $\LaTeX$ tables, or code snippets, you want to have in your document.
      - These files should be given descriptive names that do not contain spaces _(use `-` & `_` instead of spaces)_.
      - They can be included in your document using either the `\includegraphics[width=.6\textwidth]{./fig/...}` for pictures/images & documents, `\include{./fig/...}` for the stand alone $\LaTeX$ files, or `\lstinputlisting[language=...]{./fig/...}` for .
      - Supported picture/image formats: `.png`, `.jpg`, `.pdf`, & `.eps`
  - `comm/` :: This is where the technical files for the the $\LaTeX$ document reside.
      - Use Caution when making changes to files in this directory.
  - `comm/header.tex` :: This is the most technical file in the template, and everything possible has been done so that you don't ever have to make any changes to this file _**ever!**_
      - If you need to add a package to your document,
          create your own TeX macro (`\def...{}`),
          define a custom $\LaTeX$ commands (`\newcommand{...}[...]{...}`),
          or define default parameters for some utility,
          do it in the labeled section in [`main.tex`](./main.tex) and _**NOT**_ in the [`headers.tex`](./comm/header.tex) file!
  - `comm/gen.bib` :: This is a [Bib TeX](https://en.wikipedia.org/wiki/BibTeX) information [file](https://en.wikipedia.org/wiki/BibTeX#Bibliographic_information_file).
      - You can add any references you want to this just follow the Bib-TeX format.
