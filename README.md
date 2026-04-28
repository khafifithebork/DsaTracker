Here's the prompt
You are a senior software engineer and LaTeX expert. I will provide a code repository. Generate a complete, compilable LaTeX document that serves as exhaustive, interview-ready technical documentation.

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
DOCUMENT STRUCTURE
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Produce a single .tex file using the preamble template provided. The document must contain ALL of the following sections in order:

1. COVER PAGE
   - Project name (large, bold), subtitle, author, date
   - A one-sentence abstract
   - Technology badges as colored \tcbox pills (one per major tech)

2. TABLE OF CONTENTS (auto-generated with \tableofcontents)

3. PROJECT OVERVIEW & MOTIVATION
   - Executive summary paragraph
   - Problem statement, target users, core value
   - Developer role and key contributions
   - What makes this project non-trivial

4. ARCHITECTURE & STRUCTURE
   - Annotated directory tree using the \dirtree package (3 levels deep)
     Format: \dirtree{.1 root/. .2 src/. .3 ....}
   - Architectural pattern (MVC / hexagonal / microservices / etc.) with justification
   - Component interaction diagram using TikZ (see TikZ schemas tab for template)
   - Data flow description as a numbered list

5. TECHNOLOGY DEEP-DIVE
   - One \subsection per major technology
   - For each: purpose in project, why chosen over alternatives, key files/classes
   - Use \texttt{} for all file/class/function names
   - Use a \begin{tabular} comparison table showing the chosen tech vs 2 alternatives

6. TECHNICAL ARCHITECTURE Q&A
   Generate concrete answers to each question BASED ON THE ACTUAL REPO:
   Q1. How does [ComponentA] communicate with [ComponentB]?
   Q2. How is the database schema designed?
   Q3. How is authentication implemented end-to-end?
   Q4. How is the API designed? (REST/GraphQL, versioning, error contracts)
   Q5. How is configuration managed across environments?
   Q6. How does the system handle failures and retries?
   Format each as \paragraph{Qn — question text} followed by the answer.

7. CHALLENGES & PROBLEM-SOLVING
   - Hardest technical problem: describe it, the failed approaches, and the solution
   - Performance-sensitive paths: use \begin{lstlisting} for relevant code snippets
   - Non-obvious design decisions with justification
   - Edge cases explicitly handled in code

8. DESIGN & QUALITY
   - Security posture table: \begin{tabular}{lll} with columns: Concern | Approach | Gap
   - Testing strategy: what exists, coverage estimate, what is untested
   - Code quality assessment with \begin{enumerate} of specific examples

9. REFLECTIONS & FUTURE IMPROVEMENTS
   - Top 3 things done differently with more time
   - Scaling strategy for 10× load (use TikZ scaling diagram from schemas tab)
   - Technical debt inventory as \begin{itemize} with \item[\textbf{P1}] priority tags

10. ONE-PAGE CHEAT SHEET (last page)
    - \begin{tcolorbox} with \begin{multicols}{2}
    - ≤20 bullet points optimized for verbal recall in an interview
    - Key stats, patterns, decisions, tradeoffs

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
DIAGRAM REQUIREMENTS
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
You MUST generate the following TikZ diagrams (use the templates in the TikZ schemas tab):

  [A] Component Architecture Diagram — boxes for each major module with arrows
       showing data flow. Color-code by layer (presentation/service/data).

  [B] Sequence Diagram (using tikz-uml or manual tikz) — the most important
       request flow (e.g., user auth, or the core business operation).

  [C] Entity-Relationship Diagram — for each database entity, show fields and
       relationships using TikZ entities.

  [D] Scaling Architecture Diagram — current state vs. proposed 10× state,
       side by side using \begin{subfigure}.

Each diagram must have a \caption{} and be inside a \begin{figure}[H] environment.

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
CODE LISTING RULES
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
- Use \begin{lstlisting}[language=X, caption=Y] for all code
- Include 2-4 representative code excerpts from the actual repo
- Each listing must have a caption explaining what it demonstrates
- Supported languages: Java, Python, JavaScript, SQL, YAML, Bash, Go, etc.

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
STYLE & PRECISION RULES
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
- Prefix speculative content with [Inferred]: in the text
- Never hallucinate file names, class names, or config values
- Use \texttt{} for all identifiers, \textit{} for emphasis, \textbf{} for key terms
- All tables must use \toprule / \midrule / \bottomrule (booktabs style)
- Every section must cite actual files/classes found in the repo
- Output ONLY valid LaTeX — no markdown, no explanation, just the .tex file

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
COMPILATION NOTES
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
The output must compile cleanly with: pdflatex → biber (if refs) → pdflatex x2
Use \usepackage{float} and [H] for all figures to prevent float drift.

--- REPOSITORY INPUT BELOW ---
