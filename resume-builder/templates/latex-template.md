# LaTeX Resume Template

Use this template when the student chooses Option 2 (LaTeX ATS resume).
Replace all placeholder values with the student's actual details.
Remind the student to paste the code at overleaf.com and click Compile.

---

## main.tex

```latex
%-------------------------
% ATS-Friendly Resume in LaTeX
% Based on Jake Gutierrez's template (MIT License)
% Compile on: overleaf.com (free, no install needed)
%-------------------------

\documentclass[letterpaper,11pt]{article}

\usepackage{latexsym}
\usepackage[empty]{fullpage}
\usepackage{titlesec}
\usepackage{marvosym}
\usepackage[usenames,dvipsnames]{color}
\usepackage{verbatim}
\usepackage{enumitem}
\usepackage[hidelinks]{hyperref}
\usepackage{fancyhdr}
\usepackage[english]{babel}
\usepackage{tabularx}
\input{glyphtounicode}

\pagestyle{fancy}
\fancyhf{}
\fancyfoot{}
\renewcommand{\headrulewidth}{0pt}
\renewcommand{\footrulewidth}{0pt}

\addtolength{\oddsidemargin}{-0.5in}
\addtolength{\evensidemargin}{-0.5in}
\addtolength{\textwidth}{1in}
\addtolength{\topmargin}{-.5in}
\addtolength{\textheight}{1.0in}

\urlstyle{same}
\raggedbottom
\raggedright
\setlength{\tabcolsep}{0in}

\titleformat{\section}{
  \vspace{-4pt}\scshape\raggedright\large
}{}{0em}{}[\color{black}\titlerule \vspace{-5pt}]

\pdfgentounicode=1

%--- Custom Commands ---
\newcommand{\resumeItem}[1]{
  \item\small{{#1 \vspace{-2pt}}}
}

\newcommand{\resumeSubheading}[4]{
  \vspace{-2pt}\item
    \begin{tabular*}{0.97\textwidth}[t]{l@{\extracolsep{\fill}}r}
      \textbf{#1} & #2 \\
      \textit{\small#3} & \textit{\small #4} \\
    \end{tabular*}\vspace{-7pt}
}

\newcommand{\resumeProjectHeading}[2]{
    \item
    \begin{tabular*}{0.97\textwidth}{l@{\extracolsep{\fill}}r}
      \small#1 & #2 \\
    \end{tabular*}\vspace{-7pt}
}

\newcommand{\resumeSubItem}[1]{\resumeItem{#1}\vspace{-4pt}}
\renewcommand\labelitemii{$\vcenter{\hbox{\tiny$\bullet$}}$}
\newcommand{\resumeSubHeadingListStart}{\begin{itemize}[leftmargin=0.15in, label={}]}
\newcommand{\resumeSubHeadingListEnd}{\end{itemize}}
\newcommand{\resumeItemListStart}{\begin{itemize}}
\newcommand{\resumeItemListEnd}{\end{itemize}\vspace{-5pt}}

%==========================================
%           RESUME STARTS HERE
%==========================================

\begin{document}

%----------HEADING----------
\begin{center}
    \textbf{\Huge \scshape {{FULL_NAME}}} \\ \vspace{1pt}
    \small {{PHONE}} $|$
    \href{mailto:{{EMAIL}}}{\underline{{EMAIL}}} $|$
    \href{{{LINKEDIN_URL}}}{\underline{linkedin.com/in/{{LINKEDIN_HANDLE}}}} $|$
    \href{{{GITHUB_URL}}}{\underline{github.com/{{GITHUB_HANDLE}}}}
\end{center}

%-----------EDUCATION-----------
\section{Education}
  \resumeSubHeadingListStart
    \resumeSubheading
      {{{COLLEGE_NAME}}}{{{CITY}}, {{STATE}}}
      {{{DEGREE}} -- CGPA: {{CGPA}}}{{{START_YEAR}} -- {{END_YEAR}}}
  \resumeSubHeadingListEnd

%-----------EXPERIENCE (remove this section if no internship)-----------
\section{Experience}
  \resumeSubHeadingListStart

    \resumeSubheading
      {{{JOB_TITLE}}}{{{JOB_START}} -- {{JOB_END}}}
      {{{COMPANY_NAME}}}{{{COMPANY_CITY}}}
      \resumeItemListStart
        \resumeItem{{{JOB_BULLET_1}}}
        \resumeItem{{{JOB_BULLET_2}}}
        \resumeItem{{{JOB_BULLET_3}}}
      \resumeItemListEnd

  \resumeSubHeadingListEnd

%-----------PROJECTS-----------
\section{Projects}
    \resumeSubHeadingListStart

      \resumeProjectHeading
          {\textbf{{{PROJECT_1_NAME}}} $|$ \emph{{{PROJECT_1_TECH}}}}{{{PROJECT_1_DATE}}}
          \resumeItemListStart
            \resumeItem{{{PROJECT_1_BULLET_1}}}
            \resumeItem{{{PROJECT_1_BULLET_2}}}
            \resumeItem{{{PROJECT_1_BULLET_3}}}
          \resumeItemListEnd

      \resumeProjectHeading
          {\textbf{{{PROJECT_2_NAME}}} $|$ \emph{{{PROJECT_2_TECH}}}}{{{PROJECT_2_DATE}}}
          \resumeItemListStart
            \resumeItem{{{PROJECT_2_BULLET_1}}}
            \resumeItem{{{PROJECT_2_BULLET_2}}}
            \resumeItem{{{PROJECT_2_BULLET_3}}}
          \resumeItemListEnd

      \resumeProjectHeading
          {\textbf{{{PROJECT_3_NAME}}} $|$ \emph{{{PROJECT_3_TECH}}}}{{{PROJECT_3_DATE}}}
          \resumeItemListStart
            \resumeItem{{{PROJECT_3_BULLET_1}}}
            \resumeItem{{{PROJECT_3_BULLET_2}}}
          \resumeItemListEnd

    \resumeSubHeadingListEnd

%-----------TECHNICAL SKILLS-----------
\section{Technical Skills}
\begin{itemize}[leftmargin=0.15in, label={}]
  \small{\item{
    \textbf{Languages}{: {{LANGUAGES}}} \\
    \textbf{Frameworks}{: {{FRAMEWORKS}}} \\
    \textbf{Databases}{: {{DATABASES}}} \\
    \textbf{Developer Tools}{: {{TOOLS}}}
  }}
\end{itemize}

%-----------ACHIEVEMENTS (remove if none)-----------
\section{Achievements \& Certifications}
\begin{itemize}[leftmargin=0.15in, label={}]
  \small{\item{
    \textbf{{{ACHIEVEMENT_1}}} \\
    \textbf{{{ACHIEVEMENT_2}}} \\
    \textbf{{{ACHIEVEMENT_3}}}
  }}
\end{itemize}

\end{document}
```

---

## Special Character Escaping Rules

When filling in the student's details, always escape these characters in LaTeX:

| Character | Replace with |
|---|---|
| & | \& |
| % | \% |
| # | \# |
| _ | \_ |
| $ | \$ |
| { } | \{ \} |
| ~ | \textasciitilde |
| ^ | \textasciicircum |

Example: "React & Node.js" becomes "React \& Node.js"

---

## Instructions to give the student

1. Go to **overleaf.com** and create a free account
2. Click **New Project** then **Blank Project**
3. Delete everything in the editor and paste this code
4. Click **Recompile** and your resume will appear on the right
5. Click the **Download PDF** button to save it
6. To update anything, just edit the text and recompile
