\documentclass[11pt]{article}

    \usepackage[breakable]{tcolorbox}
    \usepackage{parskip} % Stop auto-indenting (to mimic markdown behaviour)
    
    \usepackage{iftex}
    \ifPDFTeX
    	\usepackage[T1]{fontenc}
    	\usepackage{mathpazo}
    \else
    	\usepackage{fontspec}
    \fi

    % Basic figure setup, for now with no caption control since it's done
    % automatically by Pandoc (which extracts ![](path) syntax from Markdown).
    \usepackage{graphicx}
    % Maintain compatibility with old templates. Remove in nbconvert 6.0
    \let\Oldincludegraphics\includegraphics
    % Ensure that by default, figures have no caption (until we provide a
    % proper Figure object with a Caption API and a way to capture that
    % in the conversion process - todo).
    \usepackage{caption}
    \DeclareCaptionFormat{nocaption}{}
    \captionsetup{format=nocaption,aboveskip=0pt,belowskip=0pt}

    \usepackage{float}
    \floatplacement{figure}{H} % forces figures to be placed at the correct location
    \usepackage{xcolor} % Allow colors to be defined
    \usepackage{enumerate} % Needed for markdown enumerations to work
    \usepackage{geometry} % Used to adjust the document margins
    \usepackage{amsmath} % Equations
    \usepackage{amssymb} % Equations
    \usepackage{textcomp} % defines textquotesingle
    % Hack from http://tex.stackexchange.com/a/47451/13684:
    \AtBeginDocument{%
        \def\PYZsq{\textquotesingle}% Upright quotes in Pygmentized code
    }
    \usepackage{upquote} % Upright quotes for verbatim code
    \usepackage{eurosym} % defines \euro
    \usepackage[mathletters]{ucs} % Extended unicode (utf-8) support
    \usepackage{fancyvrb} % verbatim replacement that allows latex
    \usepackage{grffile} % extends the file name processing of package graphics 
                         % to support a larger range
    \makeatletter % fix for old versions of grffile with XeLaTeX
    \@ifpackagelater{grffile}{2019/11/01}
    {
      % Do nothing on new versions
    }
    {
      \def\Gread@@xetex#1{%
        \IfFileExists{"\Gin@base".bb}%
        {\Gread@eps{\Gin@base.bb}}%
        {\Gread@@xetex@aux#1}%
      }
    }
    \makeatother
    \usepackage[Export]{adjustbox} % Used to constrain images to a maximum size
    \adjustboxset{max size={0.9\linewidth}{0.9\paperheight}}

    % The hyperref package gives us a pdf with properly built
    % internal navigation ('pdf bookmarks' for the table of contents,
    % internal cross-reference links, web links for URLs, etc.)
    \usepackage{hyperref}
    % The default LaTeX title has an obnoxious amount of whitespace. By default,
    % titling removes some of it. It also provides customization options.
    \usepackage{titling}
    \usepackage{longtable} % longtable support required by pandoc >1.10
    \usepackage{booktabs}  % table support for pandoc > 1.12.2
    \usepackage[inline]{enumitem} % IRkernel/repr support (it uses the enumerate* environment)
    \usepackage[normalem]{ulem} % ulem is needed to support strikethroughs (\sout)
                                % normalem makes italics be italics, not underlines
    \usepackage{mathrsfs}
    

    
    % Colors for the hyperref package
    \definecolor{urlcolor}{rgb}{0,.145,.698}
    \definecolor{linkcolor}{rgb}{.71,0.21,0.01}
    \definecolor{citecolor}{rgb}{.12,.54,.11}

    % ANSI colors
    \definecolor{ansi-black}{HTML}{3E424D}
    \definecolor{ansi-black-intense}{HTML}{282C36}
    \definecolor{ansi-red}{HTML}{E75C58}
    \definecolor{ansi-red-intense}{HTML}{B22B31}
    \definecolor{ansi-green}{HTML}{00A250}
    \definecolor{ansi-green-intense}{HTML}{007427}
    \definecolor{ansi-yellow}{HTML}{DDB62B}
    \definecolor{ansi-yellow-intense}{HTML}{B27D12}
    \definecolor{ansi-blue}{HTML}{208FFB}
    \definecolor{ansi-blue-intense}{HTML}{0065CA}
    \definecolor{ansi-magenta}{HTML}{D160C4}
    \definecolor{ansi-magenta-intense}{HTML}{A03196}
    \definecolor{ansi-cyan}{HTML}{60C6C8}
    \definecolor{ansi-cyan-intense}{HTML}{258F8F}
    \definecolor{ansi-white}{HTML}{C5C1B4}
    \definecolor{ansi-white-intense}{HTML}{A1A6B2}
    \definecolor{ansi-default-inverse-fg}{HTML}{FFFFFF}
    \definecolor{ansi-default-inverse-bg}{HTML}{000000}

    % common color for the border for error outputs.
    \definecolor{outerrorbackground}{HTML}{FFDFDF}

    % commands and environments needed by pandoc snippets
    % extracted from the output of `pandoc -s`
    \providecommand{\tightlist}{%
      \setlength{\itemsep}{0pt}\setlength{\parskip}{0pt}}
    \DefineVerbatimEnvironment{Highlighting}{Verbatim}{commandchars=\\\{\}}
    % Add ',fontsize=\small' for more characters per line
    \newenvironment{Shaded}{}{}
    \newcommand{\KeywordTok}[1]{\textcolor[rgb]{0.00,0.44,0.13}{\textbf{{#1}}}}
    \newcommand{\DataTypeTok}[1]{\textcolor[rgb]{0.56,0.13,0.00}{{#1}}}
    \newcommand{\DecValTok}[1]{\textcolor[rgb]{0.25,0.63,0.44}{{#1}}}
    \newcommand{\BaseNTok}[1]{\textcolor[rgb]{0.25,0.63,0.44}{{#1}}}
    \newcommand{\FloatTok}[1]{\textcolor[rgb]{0.25,0.63,0.44}{{#1}}}
    \newcommand{\CharTok}[1]{\textcolor[rgb]{0.25,0.44,0.63}{{#1}}}
    \newcommand{\StringTok}[1]{\textcolor[rgb]{0.25,0.44,0.63}{{#1}}}
    \newcommand{\CommentTok}[1]{\textcolor[rgb]{0.38,0.63,0.69}{\textit{{#1}}}}
    \newcommand{\OtherTok}[1]{\textcolor[rgb]{0.00,0.44,0.13}{{#1}}}
    \newcommand{\AlertTok}[1]{\textcolor[rgb]{1.00,0.00,0.00}{\textbf{{#1}}}}
    \newcommand{\FunctionTok}[1]{\textcolor[rgb]{0.02,0.16,0.49}{{#1}}}
    \newcommand{\RegionMarkerTok}[1]{{#1}}
    \newcommand{\ErrorTok}[1]{\textcolor[rgb]{1.00,0.00,0.00}{\textbf{{#1}}}}
    \newcommand{\NormalTok}[1]{{#1}}
    
    % Additional commands for more recent versions of Pandoc
    \newcommand{\ConstantTok}[1]{\textcolor[rgb]{0.53,0.00,0.00}{{#1}}}
    \newcommand{\SpecialCharTok}[1]{\textcolor[rgb]{0.25,0.44,0.63}{{#1}}}
    \newcommand{\VerbatimStringTok}[1]{\textcolor[rgb]{0.25,0.44,0.63}{{#1}}}
    \newcommand{\SpecialStringTok}[1]{\textcolor[rgb]{0.73,0.40,0.53}{{#1}}}
    \newcommand{\ImportTok}[1]{{#1}}
    \newcommand{\DocumentationTok}[1]{\textcolor[rgb]{0.73,0.13,0.13}{\textit{{#1}}}}
    \newcommand{\AnnotationTok}[1]{\textcolor[rgb]{0.38,0.63,0.69}{\textbf{\textit{{#1}}}}}
    \newcommand{\CommentVarTok}[1]{\textcolor[rgb]{0.38,0.63,0.69}{\textbf{\textit{{#1}}}}}
    \newcommand{\VariableTok}[1]{\textcolor[rgb]{0.10,0.09,0.49}{{#1}}}
    \newcommand{\ControlFlowTok}[1]{\textcolor[rgb]{0.00,0.44,0.13}{\textbf{{#1}}}}
    \newcommand{\OperatorTok}[1]{\textcolor[rgb]{0.40,0.40,0.40}{{#1}}}
    \newcommand{\BuiltInTok}[1]{{#1}}
    \newcommand{\ExtensionTok}[1]{{#1}}
    \newcommand{\PreprocessorTok}[1]{\textcolor[rgb]{0.74,0.48,0.00}{{#1}}}
    \newcommand{\AttributeTok}[1]{\textcolor[rgb]{0.49,0.56,0.16}{{#1}}}
    \newcommand{\InformationTok}[1]{\textcolor[rgb]{0.38,0.63,0.69}{\textbf{\textit{{#1}}}}}
    \newcommand{\WarningTok}[1]{\textcolor[rgb]{0.38,0.63,0.69}{\textbf{\textit{{#1}}}}}
    
    
    % Define a nice break command that doesn't care if a line doesn't already
    % exist.
    \def\br{\hspace*{\fill} \\* }
    % Math Jax compatibility definitions
    \def\gt{>}
    \def\lt{<}
    \let\Oldtex\TeX
    \let\Oldlatex\LaTeX
    \renewcommand{\TeX}{\textrm{\Oldtex}}
    \renewcommand{\LaTeX}{\textrm{\Oldlatex}}
    % Document parameters
    % Document title
    \title{DADS5001\_E-commerce\_mini\_project}
    
    
    
    
    
% Pygments definitions
\makeatletter
\def\PY@reset{\let\PY@it=\relax \let\PY@bf=\relax%
    \let\PY@ul=\relax \let\PY@tc=\relax%
    \let\PY@bc=\relax \let\PY@ff=\relax}
\def\PY@tok#1{\csname PY@tok@#1\endcsname}
\def\PY@toks#1+{\ifx\relax#1\empty\else%
    \PY@tok{#1}\expandafter\PY@toks\fi}
\def\PY@do#1{\PY@bc{\PY@tc{\PY@ul{%
    \PY@it{\PY@bf{\PY@ff{#1}}}}}}}
\def\PY#1#2{\PY@reset\PY@toks#1+\relax+\PY@do{#2}}

\@namedef{PY@tok@w}{\def\PY@tc##1{\textcolor[rgb]{0.73,0.73,0.73}{##1}}}
\@namedef{PY@tok@c}{\let\PY@it=\textit\def\PY@tc##1{\textcolor[rgb]{0.24,0.48,0.48}{##1}}}
\@namedef{PY@tok@cp}{\def\PY@tc##1{\textcolor[rgb]{0.61,0.40,0.00}{##1}}}
\@namedef{PY@tok@k}{\let\PY@bf=\textbf\def\PY@tc##1{\textcolor[rgb]{0.00,0.50,0.00}{##1}}}
\@namedef{PY@tok@kp}{\def\PY@tc##1{\textcolor[rgb]{0.00,0.50,0.00}{##1}}}
\@namedef{PY@tok@kt}{\def\PY@tc##1{\textcolor[rgb]{0.69,0.00,0.25}{##1}}}
\@namedef{PY@tok@o}{\def\PY@tc##1{\textcolor[rgb]{0.40,0.40,0.40}{##1}}}
\@namedef{PY@tok@ow}{\let\PY@bf=\textbf\def\PY@tc##1{\textcolor[rgb]{0.67,0.13,1.00}{##1}}}
\@namedef{PY@tok@nb}{\def\PY@tc##1{\textcolor[rgb]{0.00,0.50,0.00}{##1}}}
\@namedef{PY@tok@nf}{\def\PY@tc##1{\textcolor[rgb]{0.00,0.00,1.00}{##1}}}
\@namedef{PY@tok@nc}{\let\PY@bf=\textbf\def\PY@tc##1{\textcolor[rgb]{0.00,0.00,1.00}{##1}}}
\@namedef{PY@tok@nn}{\let\PY@bf=\textbf\def\PY@tc##1{\textcolor[rgb]{0.00,0.00,1.00}{##1}}}
\@namedef{PY@tok@ne}{\let\PY@bf=\textbf\def\PY@tc##1{\textcolor[rgb]{0.80,0.25,0.22}{##1}}}
\@namedef{PY@tok@nv}{\def\PY@tc##1{\textcolor[rgb]{0.10,0.09,0.49}{##1}}}
\@namedef{PY@tok@no}{\def\PY@tc##1{\textcolor[rgb]{0.53,0.00,0.00}{##1}}}
\@namedef{PY@tok@nl}{\def\PY@tc##1{\textcolor[rgb]{0.46,0.46,0.00}{##1}}}
\@namedef{PY@tok@ni}{\let\PY@bf=\textbf\def\PY@tc##1{\textcolor[rgb]{0.44,0.44,0.44}{##1}}}
\@namedef{PY@tok@na}{\def\PY@tc##1{\textcolor[rgb]{0.41,0.47,0.13}{##1}}}
\@namedef{PY@tok@nt}{\let\PY@bf=\textbf\def\PY@tc##1{\textcolor[rgb]{0.00,0.50,0.00}{##1}}}
\@namedef{PY@tok@nd}{\def\PY@tc##1{\textcolor[rgb]{0.67,0.13,1.00}{##1}}}
\@namedef{PY@tok@s}{\def\PY@tc##1{\textcolor[rgb]{0.73,0.13,0.13}{##1}}}
\@namedef{PY@tok@sd}{\let\PY@it=\textit\def\PY@tc##1{\textcolor[rgb]{0.73,0.13,0.13}{##1}}}
\@namedef{PY@tok@si}{\let\PY@bf=\textbf\def\PY@tc##1{\textcolor[rgb]{0.64,0.35,0.47}{##1}}}
\@namedef{PY@tok@se}{\let\PY@bf=\textbf\def\PY@tc##1{\textcolor[rgb]{0.67,0.36,0.12}{##1}}}
\@namedef{PY@tok@sr}{\def\PY@tc##1{\textcolor[rgb]{0.64,0.35,0.47}{##1}}}
\@namedef{PY@tok@ss}{\def\PY@tc##1{\textcolor[rgb]{0.10,0.09,0.49}{##1}}}
\@namedef{PY@tok@sx}{\def\PY@tc##1{\textcolor[rgb]{0.00,0.50,0.00}{##1}}}
\@namedef{PY@tok@m}{\def\PY@tc##1{\textcolor[rgb]{0.40,0.40,0.40}{##1}}}
\@namedef{PY@tok@gh}{\let\PY@bf=\textbf\def\PY@tc##1{\textcolor[rgb]{0.00,0.00,0.50}{##1}}}
\@namedef{PY@tok@gu}{\let\PY@bf=\textbf\def\PY@tc##1{\textcolor[rgb]{0.50,0.00,0.50}{##1}}}
\@namedef{PY@tok@gd}{\def\PY@tc##1{\textcolor[rgb]{0.63,0.00,0.00}{##1}}}
\@namedef{PY@tok@gi}{\def\PY@tc##1{\textcolor[rgb]{0.00,0.52,0.00}{##1}}}
\@namedef{PY@tok@gr}{\def\PY@tc##1{\textcolor[rgb]{0.89,0.00,0.00}{##1}}}
\@namedef{PY@tok@ge}{\let\PY@it=\textit}
\@namedef{PY@tok@gs}{\let\PY@bf=\textbf}
\@namedef{PY@tok@gp}{\let\PY@bf=\textbf\def\PY@tc##1{\textcolor[rgb]{0.00,0.00,0.50}{##1}}}
\@namedef{PY@tok@go}{\def\PY@tc##1{\textcolor[rgb]{0.44,0.44,0.44}{##1}}}
\@namedef{PY@tok@gt}{\def\PY@tc##1{\textcolor[rgb]{0.00,0.27,0.87}{##1}}}
\@namedef{PY@tok@err}{\def\PY@bc##1{{\setlength{\fboxsep}{\string -\fboxrule}\fcolorbox[rgb]{1.00,0.00,0.00}{1,1,1}{\strut ##1}}}}
\@namedef{PY@tok@kc}{\let\PY@bf=\textbf\def\PY@tc##1{\textcolor[rgb]{0.00,0.50,0.00}{##1}}}
\@namedef{PY@tok@kd}{\let\PY@bf=\textbf\def\PY@tc##1{\textcolor[rgb]{0.00,0.50,0.00}{##1}}}
\@namedef{PY@tok@kn}{\let\PY@bf=\textbf\def\PY@tc##1{\textcolor[rgb]{0.00,0.50,0.00}{##1}}}
\@namedef{PY@tok@kr}{\let\PY@bf=\textbf\def\PY@tc##1{\textcolor[rgb]{0.00,0.50,0.00}{##1}}}
\@namedef{PY@tok@bp}{\def\PY@tc##1{\textcolor[rgb]{0.00,0.50,0.00}{##1}}}
\@namedef{PY@tok@fm}{\def\PY@tc##1{\textcolor[rgb]{0.00,0.00,1.00}{##1}}}
\@namedef{PY@tok@vc}{\def\PY@tc##1{\textcolor[rgb]{0.10,0.09,0.49}{##1}}}
\@namedef{PY@tok@vg}{\def\PY@tc##1{\textcolor[rgb]{0.10,0.09,0.49}{##1}}}
\@namedef{PY@tok@vi}{\def\PY@tc##1{\textcolor[rgb]{0.10,0.09,0.49}{##1}}}
\@namedef{PY@tok@vm}{\def\PY@tc##1{\textcolor[rgb]{0.10,0.09,0.49}{##1}}}
\@namedef{PY@tok@sa}{\def\PY@tc##1{\textcolor[rgb]{0.73,0.13,0.13}{##1}}}
\@namedef{PY@tok@sb}{\def\PY@tc##1{\textcolor[rgb]{0.73,0.13,0.13}{##1}}}
\@namedef{PY@tok@sc}{\def\PY@tc##1{\textcolor[rgb]{0.73,0.13,0.13}{##1}}}
\@namedef{PY@tok@dl}{\def\PY@tc##1{\textcolor[rgb]{0.73,0.13,0.13}{##1}}}
\@namedef{PY@tok@s2}{\def\PY@tc##1{\textcolor[rgb]{0.73,0.13,0.13}{##1}}}
\@namedef{PY@tok@sh}{\def\PY@tc##1{\textcolor[rgb]{0.73,0.13,0.13}{##1}}}
\@namedef{PY@tok@s1}{\def\PY@tc##1{\textcolor[rgb]{0.73,0.13,0.13}{##1}}}
\@namedef{PY@tok@mb}{\def\PY@tc##1{\textcolor[rgb]{0.40,0.40,0.40}{##1}}}
\@namedef{PY@tok@mf}{\def\PY@tc##1{\textcolor[rgb]{0.40,0.40,0.40}{##1}}}
\@namedef{PY@tok@mh}{\def\PY@tc##1{\textcolor[rgb]{0.40,0.40,0.40}{##1}}}
\@namedef{PY@tok@mi}{\def\PY@tc##1{\textcolor[rgb]{0.40,0.40,0.40}{##1}}}
\@namedef{PY@tok@il}{\def\PY@tc##1{\textcolor[rgb]{0.40,0.40,0.40}{##1}}}
\@namedef{PY@tok@mo}{\def\PY@tc##1{\textcolor[rgb]{0.40,0.40,0.40}{##1}}}
\@namedef{PY@tok@ch}{\let\PY@it=\textit\def\PY@tc##1{\textcolor[rgb]{0.24,0.48,0.48}{##1}}}
\@namedef{PY@tok@cm}{\let\PY@it=\textit\def\PY@tc##1{\textcolor[rgb]{0.24,0.48,0.48}{##1}}}
\@namedef{PY@tok@cpf}{\let\PY@it=\textit\def\PY@tc##1{\textcolor[rgb]{0.24,0.48,0.48}{##1}}}
\@namedef{PY@tok@c1}{\let\PY@it=\textit\def\PY@tc##1{\textcolor[rgb]{0.24,0.48,0.48}{##1}}}
\@namedef{PY@tok@cs}{\let\PY@it=\textit\def\PY@tc##1{\textcolor[rgb]{0.24,0.48,0.48}{##1}}}

\def\PYZbs{\char`\\}
\def\PYZus{\char`\_}
\def\PYZob{\char`\{}
\def\PYZcb{\char`\}}
\def\PYZca{\char`\^}
\def\PYZam{\char`\&}
\def\PYZlt{\char`\<}
\def\PYZgt{\char`\>}
\def\PYZsh{\char`\#}
\def\PYZpc{\char`\%}
\def\PYZdl{\char`\$}
\def\PYZhy{\char`\-}
\def\PYZsq{\char`\'}
\def\PYZdq{\char`\"}
\def\PYZti{\char`\~}
% for compatibility with earlier versions
\def\PYZat{@}
\def\PYZlb{[}
\def\PYZrb{]}
\makeatother


    % For linebreaks inside Verbatim environment from package fancyvrb. 
    \makeatletter
        \newbox\Wrappedcontinuationbox 
        \newbox\Wrappedvisiblespacebox 
        \newcommand*\Wrappedvisiblespace {\textcolor{red}{\textvisiblespace}} 
        \newcommand*\Wrappedcontinuationsymbol {\textcolor{red}{\llap{\tiny$\m@th\hookrightarrow$}}} 
        \newcommand*\Wrappedcontinuationindent {3ex } 
        \newcommand*\Wrappedafterbreak {\kern\Wrappedcontinuationindent\copy\Wrappedcontinuationbox} 
        % Take advantage of the already applied Pygments mark-up to insert 
        % potential linebreaks for TeX processing. 
        %        {, <, #, %, $, ' and ": go to next line. 
        %        _, }, ^, &, >, - and ~: stay at end of broken line. 
        % Use of \textquotesingle for straight quote. 
        \newcommand*\Wrappedbreaksatspecials {% 
            \def\PYGZus{\discretionary{\char`\_}{\Wrappedafterbreak}{\char`\_}}% 
            \def\PYGZob{\discretionary{}{\Wrappedafterbreak\char`\{}{\char`\{}}% 
            \def\PYGZcb{\discretionary{\char`\}}{\Wrappedafterbreak}{\char`\}}}% 
            \def\PYGZca{\discretionary{\char`\^}{\Wrappedafterbreak}{\char`\^}}% 
            \def\PYGZam{\discretionary{\char`\&}{\Wrappedafterbreak}{\char`\&}}% 
            \def\PYGZlt{\discretionary{}{\Wrappedafterbreak\char`\<}{\char`\<}}% 
            \def\PYGZgt{\discretionary{\char`\>}{\Wrappedafterbreak}{\char`\>}}% 
            \def\PYGZsh{\discretionary{}{\Wrappedafterbreak\char`\#}{\char`\#}}% 
            \def\PYGZpc{\discretionary{}{\Wrappedafterbreak\char`\%}{\char`\%}}% 
            \def\PYGZdl{\discretionary{}{\Wrappedafterbreak\char`\$}{\char`\$}}% 
            \def\PYGZhy{\discretionary{\char`\-}{\Wrappedafterbreak}{\char`\-}}% 
            \def\PYGZsq{\discretionary{}{\Wrappedafterbreak\textquotesingle}{\textquotesingle}}% 
            \def\PYGZdq{\discretionary{}{\Wrappedafterbreak\char`\"}{\char`\"}}% 
            \def\PYGZti{\discretionary{\char`\~}{\Wrappedafterbreak}{\char`\~}}% 
        } 
        % Some characters . , ; ? ! / are not pygmentized. 
        % This macro makes them "active" and they will insert potential linebreaks 
        \newcommand*\Wrappedbreaksatpunct {% 
            \lccode`\~`\.\lowercase{\def~}{\discretionary{\hbox{\char`\.}}{\Wrappedafterbreak}{\hbox{\char`\.}}}% 
            \lccode`\~`\,\lowercase{\def~}{\discretionary{\hbox{\char`\,}}{\Wrappedafterbreak}{\hbox{\char`\,}}}% 
            \lccode`\~`\;\lowercase{\def~}{\discretionary{\hbox{\char`\;}}{\Wrappedafterbreak}{\hbox{\char`\;}}}% 
            \lccode`\~`\:\lowercase{\def~}{\discretionary{\hbox{\char`\:}}{\Wrappedafterbreak}{\hbox{\char`\:}}}% 
            \lccode`\~`\?\lowercase{\def~}{\discretionary{\hbox{\char`\?}}{\Wrappedafterbreak}{\hbox{\char`\?}}}% 
            \lccode`\~`\!\lowercase{\def~}{\discretionary{\hbox{\char`\!}}{\Wrappedafterbreak}{\hbox{\char`\!}}}% 
            \lccode`\~`\/\lowercase{\def~}{\discretionary{\hbox{\char`\/}}{\Wrappedafterbreak}{\hbox{\char`\/}}}% 
            \catcode`\.\active
            \catcode`\,\active 
            \catcode`\;\active
            \catcode`\:\active
            \catcode`\?\active
            \catcode`\!\active
            \catcode`\/\active 
            \lccode`\~`\~ 	
        }
    \makeatother

    \let\OriginalVerbatim=\Verbatim
    \makeatletter
    \renewcommand{\Verbatim}[1][1]{%
        %\parskip\z@skip
        \sbox\Wrappedcontinuationbox {\Wrappedcontinuationsymbol}%
        \sbox\Wrappedvisiblespacebox {\FV@SetupFont\Wrappedvisiblespace}%
        \def\FancyVerbFormatLine ##1{\hsize\linewidth
            \vtop{\raggedright\hyphenpenalty\z@\exhyphenpenalty\z@
                \doublehyphendemerits\z@\finalhyphendemerits\z@
                \strut ##1\strut}%
        }%
        % If the linebreak is at a space, the latter will be displayed as visible
        % space at end of first line, and a continuation symbol starts next line.
        % Stretch/shrink are however usually zero for typewriter font.
        \def\FV@Space {%
            \nobreak\hskip\z@ plus\fontdimen3\font minus\fontdimen4\font
            \discretionary{\copy\Wrappedvisiblespacebox}{\Wrappedafterbreak}
            {\kern\fontdimen2\font}%
        }%
        
        % Allow breaks at special characters using \PYG... macros.
        \Wrappedbreaksatspecials
        % Breaks at punctuation characters . , ; ? ! and / need catcode=\active 	
        \OriginalVerbatim[#1,codes*=\Wrappedbreaksatpunct]%
    }
    \makeatother

    % Exact colors from NB
    \definecolor{incolor}{HTML}{303F9F}
    \definecolor{outcolor}{HTML}{D84315}
    \definecolor{cellborder}{HTML}{CFCFCF}
    \definecolor{cellbackground}{HTML}{F7F7F7}
    
    % prompt
    \makeatletter
    \newcommand{\boxspacing}{\kern\kvtcb@left@rule\kern\kvtcb@boxsep}
    \makeatother
    \newcommand{\prompt}[4]{
        {\ttfamily\llap{{\color{#2}[#3]:\hspace{3pt}#4}}\vspace{-\baselineskip}}
    }
    

    
    % Prevent overflowing lines due to hard-to-break entities
    \sloppy 
    % Setup hyperref package
    \hypersetup{
      breaklinks=true,  % so long urls are correctly broken across lines
      colorlinks=true,
      urlcolor=urlcolor,
      linkcolor=linkcolor,
      citecolor=citecolor,
      }
    % Slightly bigger margins than the latex defaults
    
    \geometry{verbose,tmargin=1in,bmargin=1in,lmargin=1in,rmargin=1in}
    
    

\begin{document}
    
    \maketitle
    
    

    
    \hypertarget{e-commerce-mini-project}{%
\section{E-commerce-Mini-Project}\label{e-commerce-mini-project}}

\hypertarget{uxe1cuxe08uxe14uxe17uxe33}{%
\subsubsection{ผู้จัดทำ}\label{uxe1cuxe08uxe14uxe17uxe33}}

\hypertarget{unyawee-phanburananont}{%
\paragraph{- 6510400004 Unyawee
Phanburananont}\label{unyawee-phanburananont}}

\hypertarget{phanuphong-siriphongwatana}{%
\paragraph{- 6510400003 Phanuphong
Siriphongwatana}\label{phanuphong-siriphongwatana}}

\hypertarget{uxe02uxe2duxe21uxe25}{%
\subsubsection{ข้อมูล}\label{uxe02uxe2duxe21uxe25}}

ชุดข้อมูลเป็น Transaction ของข้อมูลสินค้าบนแพลตฟอร์ม E-commerce ที่เก็บเป็นรายชั่วโมง
มีข้อมูลเกี่ยวกับ \%ส่วนลด, ราคาสินค้า, ยี่ห้อสินค้า, การทำแฟลชเซล(Flash sale),
จำนวนสินค้าในคลังสินค้า(Stock) เป็นต้น

ระยะเวลาของข้อมูล: 2022-09 ถึง 2023-03

\hypertarget{uxe04uxe33uxe16uxe32uxe21}{%
\subsubsection{คำถาม}\label{uxe04uxe33uxe16uxe32uxe21}}

สำรวจเกี่ยวกับการทำแฟลชเซลของสินค้า แคมเปญการขาย สินค้าแต่ละเเบรนด์
และการลดราคากับสต็อกสินค้า

\begin{enumerate}
\def\labelenumi{\arabic{enumi}.}
\tightlist
\item
  วันและเวลา 10 อันดับแรกที่มีการทำแฟลชเซลบ่อยที่สุด
\item
  เปรียบเทียบ 3 แคมเปญลดราคาสินค้า ว่าแคมเปญไหนมีการทำแฟลชเซลบ่อยที่สุด
\item
  PayDay แคมเปญมีระยะเวลาที่จัดแคมเปญหลายวันกว่าแคมเปญอื่นๆ จึงดูเพิ่มว่า
  ช่วงวันและเวลาไหนที่นิยมทำแฟลชเซล
\item
  แต่ละแคมเปญส่วนมากทำแฟลชเซลกี่ชั่วโมงโดยเฉลี่ย
\item
  แต่ละแคมเปญมีพฤติกรรมการทำแฟลชเซลช่วงเวลาไหนเท่าไหร่บ้าง
\item
  สำรวจแบรนด์สินค้าที่เป็นร้านค้าทางการเทียบกับร้านค้าไม่ทางการว่ามีพฤติกรรมการลดราคาในแต่ละแคมเปญแตกต่างกันหรือไม่
\item
  ความสัมพันธ์ของการลดราคากับจำนวนสินค้าที่ขายได้
\end{enumerate}

    \begin{tcolorbox}[breakable, size=fbox, boxrule=1pt, pad at break*=1mm,colback=cellbackground, colframe=cellborder]
\prompt{In}{incolor}{1}{\boxspacing}
\begin{Verbatim}[commandchars=\\\{\}]
\PY{k+kn}{import} \PY{n+nn}{pandas} \PY{k}{as} \PY{n+nn}{pd}
\PY{k+kn}{import} \PY{n+nn}{numpy} \PY{k}{as} \PY{n+nn}{np}
\PY{k+kn}{from} \PY{n+nn}{datetime} \PY{k+kn}{import} \PY{n}{datetime}
\PY{k+kn}{import} \PY{n+nn}{matplotlib}\PY{n+nn}{.}\PY{n+nn}{pyplot} \PY{k}{as} \PY{n+nn}{plt}
\PY{k+kn}{import} \PY{n+nn}{seaborn} \PY{k}{as} \PY{n+nn}{sns}
\end{Verbatim}
\end{tcolorbox}

    \begin{tcolorbox}[breakable, size=fbox, boxrule=1pt, pad at break*=1mm,colback=cellbackground, colframe=cellborder]
\prompt{In}{incolor}{85}{\boxspacing}
\begin{Verbatim}[commandchars=\\\{\}]
\PY{n}{df} \PY{o}{=} \PY{n}{pd}\PY{o}{.}\PY{n}{read\PYZus{}csv}\PY{p}{(}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{Ecommerce\PYZus{}mini\PYZus{}project.csv}\PY{l+s+s1}{\PYZsq{}}\PY{p}{)}
\end{Verbatim}
\end{tcolorbox}

    \begin{tcolorbox}[breakable, size=fbox, boxrule=1pt, pad at break*=1mm,colback=cellbackground, colframe=cellborder]
\prompt{In}{incolor}{86}{\boxspacing}
\begin{Verbatim}[commandchars=\\\{\}]
\PY{n}{df}\PY{o}{.}\PY{n}{info}\PY{p}{(}\PY{p}{)}
\end{Verbatim}
\end{tcolorbox}

    \begin{Verbatim}[commandchars=\\\{\}]
<class 'pandas.core.frame.DataFrame'>
RangeIndex: 316949 entries, 0 to 316948
Data columns (total 84 columns):
 \#   Column                                  Non-Null Count   Dtype
---  ------                                  --------------   -----
 0   item\_type                               316949 non-null  int64
 1   discount                                303991 non-null  object
 2   price\_min                               316949 non-null  int64
 3   item\_has\_video                          316949 non-null  object
 4   userid                                  316949 non-null  int64
 5   liked                                   316949 non-null  object
 6   is\_pre\_order                            316949 non-null  object
 7   is\_adult                                316949 non-null  object
 8   scraped\_datetime                        316949 non-null  object
 9   model\_name                              289103 non-null  object
 10  price                                   316949 non-null  int64
 11  is\_infant\_milk\_formula\_product          316949 non-null  object
 12  ctime                                   316949 non-null  object
 13  should\_show\_amp\_tag                     316949 non-null  object
 14  stock                                   316949 non-null  int64
 15  price\_min\_before\_discount               304653 non-null  float64
 16  brand                                   309731 non-null  object
 17  is\_service\_by\_shopee                    316949 non-null  object
 18  image                                   316949 non-null  object
 19  price\_before\_discount                   316949 non-null  int64
 20  is\_preferred\_plus\_seller                316949 non-null  object
 21  show\_official\_shop\_label\_in\_title       316949 non-null  object
 22  cod\_flag                                316949 non-null  int64
 23  modelid                                 316949 non-null  int64
 24  price\_max\_before\_discount               304653 non-null  float64
 25  label\_ids                               316502 non-null  object
 26  is\_official\_shop                        316949 non-null  object
 27  global\_sold                             203029 non-null  float64
 28  show\_shopee\_verified\_label              316949 non-null  object
 29  item\_status                             316949 non-null  object
 30  brand\_id                                316949 non-null  int64
 31  cb\_option                               316949 non-null  int64
 32  condition                               316949 non-null  int64
 33  shipping\_icon\_type                      316949 non-null  int64
 34  cmt\_count                               316949 non-null  int64
 35  name                                    316949 non-null  object
 36  reference\_item\_id                       0 non-null       float64
 37  shopid                                  316949 non-null  int64
 38  show\_best\_price\_guarantee               316949 non-null  object
 39  shopee\_verified                         316949 non-null  object
 40  estimated\_days                          316949 non-null  int64
 41  has\_low\_fulfillment\_rate                316949 non-null  object
 42  price\_max                               316949 non-null  int64
 43  has\_lowest\_price\_guarantee              316949 non-null  object
 44  status                                  316949 non-null  int64
 45  bundle\_deal\_id                          316949 non-null  int64
 46  is\_alcohol\_product                      316949 non-null  object
 47  show\_discount                           316949 non-null  int64
 48  liked\_count                             316949 non-null  int64
 49  flag                                    316949 non-null  int64
 50  welcome\_package\_type                    316949 non-null  int64
 51  can\_use\_bundle\_deal                     316949 non-null  object
 52  is\_non\_cc\_installment\_payment\_eligible  316829 non-null  float64
 53  is\_prescription\_item                    316949 non-null  object
 54  normal\_stock                            316949 non-null  int64
 55  min\_purchase\_limit                      316949 non-null  int64
 56  itemid                                  316949 non-null  int64
 57  catid                                   316949 non-null  int64
 58  show\_recycling\_info                     316949 non-null  object
 59  is\_mart                                 316949 non-null  object
 60  item\_has\_post                           316949 non-null  object
 61  historical\_sold                         316949 non-null  int64
 62  shop\_location                           316949 non-null  object
 63  current\_promotion\_reserved\_stock        316949 non-null  int64
 64  scraped\_start\_date                      316949 non-null  object
 65  is\_cc\_installment\_payment\_eligible      316829 non-null  float64
 66  class\_name                              316949 non-null  object
 67  sold                                    316949 non-null  int64
 68  discount\_stock                          316949 non-null  int64
 69  show\_free\_shipping                      316949 non-null  object
 70  other\_stock                             316949 non-null  int64
 71  show\_original\_guarantee                 316949 non-null  object
 72  raw\_discount                            316949 non-null  int64
 73  promotionid                             316949 non-null  int64
 74  url                                     316949 non-null  object
 75  badge\_icon\_type                         316949 non-null  int64
 76  can\_use\_wholesale                       316949 non-null  object
 77  is\_partial\_fulfilled                    316949 non-null  object
 78  current\_promotion\_has\_reserve\_stock     316949 non-null  object
 79  upcoming\_flash\_sale                     22274 non-null   object
 80  bundle\_deal\_info                        45186 non-null   object
 81  flash\_sale                              11240 non-null   object
 82  exclusive\_price\_info                    5158 non-null    object
 83  ingest\_date                             316949 non-null  object
dtypes: float64(6), int64(34), object(44)
memory usage: 203.1+ MB
    \end{Verbatim}

    \begin{tcolorbox}[breakable, size=fbox, boxrule=1pt, pad at break*=1mm,colback=cellbackground, colframe=cellborder]
\prompt{In}{incolor}{87}{\boxspacing}
\begin{Verbatim}[commandchars=\\\{\}]
\PY{n}{df}\PY{o}{.}\PY{n}{describe}\PY{p}{(}\PY{p}{)}
\end{Verbatim}
\end{tcolorbox}

            \begin{tcolorbox}[breakable, size=fbox, boxrule=.5pt, pad at break*=1mm, opacityfill=0]
\prompt{Out}{outcolor}{87}{\boxspacing}
\begin{Verbatim}[commandchars=\\\{\}]
       item\_type      price\_min    userid          price          stock  \textbackslash{}
count   316949.0  316949.000000  316949.0  316949.000000  316949.000000
mean         0.0    5826.871629       0.0    6842.930992     231.559229
std          0.0    7304.720851       0.0    8015.321658     804.860872
min          0.0     131.000000       0.0     131.000000       0.000000
25\%          0.0    1359.000000       0.0    1699.000000       1.000000
50\%          0.0    3489.000000       0.0    4499.000000      23.000000
75\%          0.0    7610.000000       0.0    9490.000000     194.000000
max          0.0  114642.000000       0.0  122842.000000   67029.000000

       price\_min\_before\_discount  price\_before\_discount       cod\_flag  \textbackslash{}
count              304653.000000          316949.000000  316949.000000
mean                 8929.532304            8110.809812       0.682763
std                 12014.080406           12023.332042       0.465401
min                   230.000000               0.000000       0.000000
25\%                  1999.000000            1899.000000       0.000000
50\%                  5990.000000            3499.000000       1.000000
75\%                  9999.000000            9999.000000       1.000000
max                125310.000000          134274.000000       1.000000

            modelid  price\_max\_before\_discount  {\ldots}          catid  \textbackslash{}
count  3.169490e+05              304653.000000  {\ldots}  316949.000000
mean   1.168458e+11               10908.731698  {\ldots}  100215.086799
std    4.989618e+10               13552.015133  {\ldots}     290.707979
min    3.471427e+09                 230.000000  {\ldots}  100001.000000
25\%    8.036762e+10                2990.000000  {\ldots}  100010.000000
50\%    1.231928e+11                6999.000000  {\ldots}  100013.000000
75\%    1.526733e+11               13086.000000  {\ldots}  100631.000000
max    2.307300e+11              134274.000000  {\ldots}  100637.000000

       historical\_sold  current\_promotion\_reserved\_stock  \textbackslash{}
count    316949.000000                     316949.000000
mean       5087.556067                          6.562964
std       13890.012883                         48.039579
min           0.000000                          0.000000
25\%         219.000000                          0.000000
50\%        1168.000000                          0.000000
75\%        3976.000000                          0.000000
max      102765.000000                       1179.000000

       is\_cc\_installment\_payment\_eligible           sold  discount\_stock  \textbackslash{}
count                       316829.000000  316949.000000   316949.000000
mean                             0.390766     221.332684     2589.093356
std                              0.487923     538.543273     6834.859107
min                              0.000000       0.000000        0.000000
25\%                              0.000000      12.000000       51.000000
50\%                              0.000000      45.000000      234.000000
75\%                              1.000000     142.000000      811.000000
max                              1.000000    3719.000000   263871.000000

         other\_stock   raw\_discount   promotionid  badge\_icon\_type
count  316949.000000  316949.000000  3.169490e+05    316949.000000
mean      173.168989      39.384343  4.862378e+14         0.233470
std      1520.610166      17.383550  2.981477e+14         1.430638
min         0.000000       0.000000  0.000000e+00         0.000000
25\%         0.000000      26.000000  1.141186e+14         0.000000
50\%         0.000000      44.000000  6.677588e+14         0.000000
75\%         0.000000      54.000000  6.802253e+14         0.000000
max     31439.000000      94.000000  7.089141e+14         9.000000

[8 rows x 40 columns]
\end{Verbatim}
\end{tcolorbox}
        
    \hypertarget{type-campaign}{%
\subsection{3 Type campaign}\label{type-campaign}}

campaign คือมหกรรมการลดราคาของ platform ที่การให้โค้ดส่วนลดมากมายและการทำ
flash sale ของร้านค้า

Shopee มีทั้งหมด 3 แคมเปญหลักๆ ดังนี้

\hypertarget{mega-sale}{%
\subsubsection{1. Mega Sale}\label{mega-sale}}

วันที่ วันกับเดือนตรงกัน เช่น 11.11 , 12.12 เป็นต้น

\hypertarget{mid-month-sale}{%
\subsubsection{2. Mid Month Sale}\label{mid-month-sale}}

แคมเปญทุกกลางเดือน จัดทุกวันที่ 15 ของเดือน

\hypertarget{pay-day-sale}{%
\subsubsection{3. Pay Day Sale}\label{pay-day-sale}}

แคมเปญปลายเดือน ส่วนมากจะจัดหลายวันตั้งแต่วันที่ 25-สิ้นเดือน

ทุกเดือนจะทำทั้ง 3 campaign แตกต่างกันที่วันที่ และจะมีร้านค้าการทำ flash sale ร่วมด้วย
(Flash sale ไม่จำเป็นต้องทำภายใน 3 campaign นี้แต่สามารถทำได้ตลอดเวลาและทุกๆวัน)

    \hypertarget{understand-and-prepare-data-part}{%
\section{Understand and prepare Data
Part}\label{understand-and-prepare-data-part}}

itemid = id ของสินค้าใน 1 url สินค้า modelid = id ของตัวเลือกสินค้าใน itemid

itemid มีได้หลาย modelid เพราะ 1 สินค้าสามารถมีได้หลายตัวเลือกสินค้า

    \begin{tcolorbox}[breakable, size=fbox, boxrule=1pt, pad at break*=1mm,colback=cellbackground, colframe=cellborder]
\prompt{In}{incolor}{88}{\boxspacing}
\begin{Verbatim}[commandchars=\\\{\}]
\PY{n}{df}\PY{p}{[}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{itemid}\PY{l+s+s1}{\PYZsq{}}\PY{p}{,}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{modelid}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{p}{]}
\end{Verbatim}
\end{tcolorbox}

            \begin{tcolorbox}[breakable, size=fbox, boxrule=.5pt, pad at break*=1mm, opacityfill=0]
\prompt{Out}{outcolor}{88}{\boxspacing}
\begin{Verbatim}[commandchars=\\\{\}]
             itemid       modelid
0       13374366434  134017795683
1       13374366434  134017795684
2       11385534326  134017787145
3       11385534326  134017787146
4        4950629721   58328468873
{\ldots}             {\ldots}           {\ldots}
316944   9723579733  142390562339
316945   9723579733  142390562340
316946   9723579733   48355102339
316947   9723579733   48355102340
316948   9723579733   48355102341

[316949 rows x 2 columns]
\end{Verbatim}
\end{tcolorbox}
        
    จากคำถามเราต้องการวิเคราะห์เกี่ยวกับการทำแฟลชเซลสินค้า เนื่องจาก API ของ Shopee
มีการ return ค่าของแฟลชเซลออกมาตาม itemid ทำให้ ทุก modelid
จะถูกเหมาะรวมว่าทำแฟลชเซลถึงแม้ modelid นั้นจะไม่ได้มีการทำแฟลชเซลก็ตาม
ดังนั้นเราจึงทำการเลือกเฉพาะข้อมูล itemid ที่มีเฉพาะ modelid
เดียวมาทำการวิเคราะห์ต่อเท่านั้น

    \begin{tcolorbox}[breakable, size=fbox, boxrule=1pt, pad at break*=1mm,colback=cellbackground, colframe=cellborder]
\prompt{In}{incolor}{89}{\boxspacing}
\begin{Verbatim}[commandchars=\\\{\}]
\PY{n+nb}{list}\PY{p}{(}\PY{n}{df}\PY{o}{.}\PY{n}{sort\PYZus{}values}\PY{p}{(}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{brand}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{p}{)}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{brand}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{o}{.}\PY{n}{unique}\PY{p}{(}\PY{p}{)}\PY{p}{)}
\end{Verbatim}
\end{tcolorbox}

            \begin{tcolorbox}[breakable, size=fbox, boxrule=.5pt, pad at break*=1mm, opacityfill=0]
\prompt{Out}{outcolor}{89}{\boxspacing}
\begin{Verbatim}[commandchars=\\\{\}]
['Amazfit (อเมซฟิต)',
 'Baseus(เบซิอัส)',
 'Ecovacs(อีโคแวคส์)',
 'Haier(ไฮเออร์)',
 'Life Space (ไลฟ์สเปซ)',
 'Mister Robot(มิสเตอร์โรบอต)',
 'Pando(แพนโด้)',
 'Papifeed(ปาปิฟีด)',
 'Petkit(เพ็ทคิต)',
 'Petkit(เพ็ทคิท)',
 'Redmi(เรดมี่)',
 'Roborock(โรโบร็อค)',
 'Xiaomi(เสี่ยวมี่)',
 'iRobot(ไอโรบอท)',
 nan]
\end{Verbatim}
\end{tcolorbox}
        
    \begin{tcolorbox}[breakable, size=fbox, boxrule=1pt, pad at break*=1mm,colback=cellbackground, colframe=cellborder]
\prompt{In}{incolor}{90}{\boxspacing}
\begin{Verbatim}[commandchars=\\\{\}]
\PY{n}{unique\PYZus{}id} \PY{o}{=} \PY{p}{[}\PY{p}{]}
\PY{k}{for} \PY{n}{i} \PY{o+ow}{in} \PY{n}{df}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{itemid}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{o}{.}\PY{n}{unique}\PY{p}{(}\PY{p}{)}\PY{o}{.}\PY{n}{tolist}\PY{p}{(}\PY{p}{)}\PY{p}{:}
    \PY{k}{if} \PY{n+nb}{len}\PY{p}{(}\PY{n}{df}\PY{p}{[}\PY{n}{df}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{itemid}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{o}{==}\PY{n}{i}\PY{p}{]}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{modelid}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{o}{.}\PY{n}{unique}\PY{p}{(}\PY{p}{)}\PY{p}{)} \PY{o}{==} \PY{l+m+mi}{1}\PY{p}{:}
\PY{c+c1}{\PYZsh{}         print(i)}
        \PY{n}{unique\PYZus{}id}\PY{o}{.}\PY{n}{append}\PY{p}{(}\PY{n}{i}\PY{p}{)}
\PY{n}{df}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{brand}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]} \PY{o}{=} \PY{n}{df}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{brand}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{o}{.}\PY{n}{replace}\PY{p}{(}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{Petkit(เพ็ทคิต)}\PY{l+s+s1}{\PYZsq{}}\PY{p}{,}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{Petkit(เพ็ทคิท)}\PY{l+s+s1}{\PYZsq{}}\PY{p}{)}
\PY{n}{df} \PY{o}{=} \PY{n}{df}\PY{p}{[}\PY{n}{df}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{itemid}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{o}{.}\PY{n}{isin}\PY{p}{(}\PY{n}{unique\PYZus{}id}\PY{p}{)}\PY{p}{]}\PY{o}{.}\PY{n}{reset\PYZus{}index}\PY{p}{(}\PY{n}{drop}\PY{o}{=}\PY{k+kc}{True}\PY{p}{)}
\PY{n}{df} \PY{o}{=} \PY{n}{df}\PY{o}{.}\PY{n}{sort\PYZus{}values}\PY{p}{(}\PY{n}{by}\PY{o}{=}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{ingest\PYZus{}date}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{p}{,}\PY{n}{ascending}\PY{o}{=}\PY{k+kc}{True}\PY{p}{)}
\PY{n}{df} \PY{o}{=} \PY{n}{df}\PY{o}{.}\PY{n}{drop\PYZus{}duplicates}\PY{p}{(}\PY{p}{)}
\end{Verbatim}
\end{tcolorbox}

    \begin{tcolorbox}[breakable, size=fbox, boxrule=1pt, pad at break*=1mm,colback=cellbackground, colframe=cellborder]
\prompt{In}{incolor}{91}{\boxspacing}
\begin{Verbatim}[commandchars=\\\{\}]
\PY{k}{def} \PY{n+nf}{extract\PYZus{}date\PYZus{}hour}\PY{p}{(}\PY{n}{row}\PY{p}{)}\PY{p}{:}
    \PY{n}{date} \PY{o}{=} \PY{n}{datetime}\PY{o}{.}\PY{n}{strptime}\PY{p}{(}\PY{n}{row}\PY{p}{,} \PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{\PYZpc{}}\PY{l+s+s1}{Y\PYZhy{}}\PY{l+s+s1}{\PYZpc{}}\PY{l+s+s1}{m\PYZhy{}}\PY{l+s+si}{\PYZpc{}d}\PY{l+s+s1}{ }\PY{l+s+s1}{\PYZpc{}}\PY{l+s+s1}{H:}\PY{l+s+s1}{\PYZpc{}}\PY{l+s+s1}{M:}\PY{l+s+s1}{\PYZpc{}}\PY{l+s+s1}{S}\PY{l+s+s1}{\PYZsq{}}\PY{p}{)}
    \PY{k}{return} \PY{n}{date}\PY{o}{.}\PY{n}{strftime}\PY{p}{(}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+si}{\PYZpc{}d}\PY{l+s+s1}{\PYZhy{}}\PY{l+s+s1}{\PYZpc{}}\PY{l+s+s1}{H}\PY{l+s+s1}{\PYZsq{}}\PY{p}{)}

\PY{k}{def} \PY{n+nf}{extract\PYZus{}year}\PY{p}{(}\PY{n}{row}\PY{p}{)}\PY{p}{:}
    \PY{n}{date} \PY{o}{=} \PY{n}{datetime}\PY{o}{.}\PY{n}{strptime}\PY{p}{(}\PY{n}{row}\PY{p}{,} \PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{\PYZpc{}}\PY{l+s+s1}{Y\PYZhy{}}\PY{l+s+s1}{\PYZpc{}}\PY{l+s+s1}{m\PYZhy{}}\PY{l+s+si}{\PYZpc{}d}\PY{l+s+s1}{ }\PY{l+s+s1}{\PYZpc{}}\PY{l+s+s1}{H:}\PY{l+s+s1}{\PYZpc{}}\PY{l+s+s1}{M:}\PY{l+s+s1}{\PYZpc{}}\PY{l+s+s1}{S}\PY{l+s+s1}{\PYZsq{}}\PY{p}{)}
    \PY{k}{return} \PY{n}{date}\PY{o}{.}\PY{n}{strftime}\PY{p}{(}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{\PYZpc{}}\PY{l+s+s1}{Y}\PY{l+s+s1}{\PYZsq{}}\PY{p}{)}

\PY{k}{def} \PY{n+nf}{extract\PYZus{}mega\PYZus{}sale}\PY{p}{(}\PY{n}{row}\PY{p}{)}\PY{p}{:}
    \PY{n}{date} \PY{o}{=} \PY{n}{datetime}\PY{o}{.}\PY{n}{strptime}\PY{p}{(}\PY{n}{row}\PY{p}{,} \PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{\PYZpc{}}\PY{l+s+s1}{Y\PYZhy{}}\PY{l+s+s1}{\PYZpc{}}\PY{l+s+s1}{m\PYZhy{}}\PY{l+s+si}{\PYZpc{}d}\PY{l+s+s1}{ }\PY{l+s+s1}{\PYZpc{}}\PY{l+s+s1}{H:}\PY{l+s+s1}{\PYZpc{}}\PY{l+s+s1}{M:}\PY{l+s+s1}{\PYZpc{}}\PY{l+s+s1}{S}\PY{l+s+s1}{\PYZsq{}}\PY{p}{)}
    \PY{k}{if} \PY{n}{date}\PY{o}{.}\PY{n}{strftime}\PY{p}{(}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{\PYZpc{}}\PY{l+s+s1}{m}\PY{l+s+s1}{\PYZsq{}}\PY{p}{)} \PY{o}{==} \PY{n}{date}\PY{o}{.}\PY{n}{strftime}\PY{p}{(}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+si}{\PYZpc{}d}\PY{l+s+s1}{\PYZsq{}}\PY{p}{)}\PY{p}{:}
        \PY{k}{return} \PY{k+kc}{True}
    \PY{k}{else}\PY{p}{:}
        \PY{k}{return} \PY{k+kc}{False}
\end{Verbatim}
\end{tcolorbox}

    \begin{tcolorbox}[breakable, size=fbox, boxrule=1pt, pad at break*=1mm,colback=cellbackground, colframe=cellborder]
\prompt{In}{incolor}{92}{\boxspacing}
\begin{Verbatim}[commandchars=\\\{\}]
\PY{n}{df}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{year}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]} \PY{o}{=} \PY{n}{df}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{ingest\PYZus{}date}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{o}{.}\PY{n}{apply}\PY{p}{(}\PY{n}{extract\PYZus{}year}\PY{p}{)}
\PY{n}{df}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{day\PYZus{}hour}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]} \PY{o}{=} \PY{n}{df}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{ingest\PYZus{}date}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{o}{.}\PY{n}{apply}\PY{p}{(}\PY{n}{extract\PYZus{}date\PYZus{}hour}\PY{p}{)}
\PY{n}{df}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{mega\PYZus{}sale}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]} \PY{o}{=} \PY{n}{df}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{ingest\PYZus{}date}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{o}{.}\PY{n}{apply}\PY{p}{(}\PY{n}{extract\PYZus{}mega\PYZus{}sale}\PY{p}{)}
\end{Verbatim}
\end{tcolorbox}

    ตรวจจสอบพฤติกรรมของข้อมูลในแต่ละปี เพื่อดูคุณภาพของข้อมูลก่อนการทำไปวิเคราะห์

    \begin{tcolorbox}[breakable, size=fbox, boxrule=1pt, pad at break*=1mm,colback=cellbackground, colframe=cellborder]
\prompt{In}{incolor}{93}{\boxspacing}
\begin{Verbatim}[commandchars=\\\{\}]
\PY{n}{df}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{year}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{o}{.}\PY{n}{unique}\PY{p}{(}\PY{p}{)}
\end{Verbatim}
\end{tcolorbox}

            \begin{tcolorbox}[breakable, size=fbox, boxrule=.5pt, pad at break*=1mm, opacityfill=0]
\prompt{Out}{outcolor}{93}{\boxspacing}
\begin{Verbatim}[commandchars=\\\{\}]
array(['2022', '2023'], dtype=object)
\end{Verbatim}
\end{tcolorbox}
        
    \begin{tcolorbox}[breakable, size=fbox, boxrule=1pt, pad at break*=1mm,colback=cellbackground, colframe=cellborder]
\prompt{In}{incolor}{94}{\boxspacing}
\begin{Verbatim}[commandchars=\\\{\}]
\PY{n+nb}{print}\PY{p}{(}\PY{n+nb}{len}\PY{p}{(}\PY{n}{df}\PY{p}{[}\PY{n}{df}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{year}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{o}{==}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{2022}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{p}{)}\PY{p}{)}
\PY{n}{df}\PY{p}{[}\PY{n}{df}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{year}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{o}{==}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{2022}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{p}{[}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{itemid}\PY{l+s+s1}{\PYZsq{}}\PY{p}{,}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{modelid}\PY{l+s+s1}{\PYZsq{}}\PY{p}{,}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{ingest\PYZus{}date}\PY{l+s+s1}{\PYZsq{}}\PY{p}{,}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{day\PYZus{}hour}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{p}{]}\PY{o}{.}\PY{n}{sort\PYZus{}values}\PY{p}{(}\PY{n}{by}\PY{o}{=}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{itemid}\PY{l+s+s1}{\PYZsq{}}\PY{p}{,}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{ingest\PYZus{}date}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{p}{)}\PY{p}{[}\PY{p}{:}\PY{l+m+mi}{10}\PY{p}{]}
\end{Verbatim}
\end{tcolorbox}

    \begin{Verbatim}[commandchars=\\\{\}]
30679
    \end{Verbatim}

            \begin{tcolorbox}[breakable, size=fbox, boxrule=.5pt, pad at break*=1mm, opacityfill=0]
\prompt{Out}{outcolor}{94}{\boxspacing}
\begin{Verbatim}[commandchars=\\\{\}]
          itemid      modelid          ingest\_date day\_hour
2987   845016064  42157405015  2022-10-07 10:00:01    07-10
4622   845016064  42157405015  2022-10-07 12:00:01    07-12
6063   845016064  42157405015  2022-10-07 13:00:02    07-13
7668   845016064  42157405015  2022-10-07 14:00:01    07-14
11112  845016064  42157405015  2022-10-07 15:00:01    07-15
13232  845016064  42157405015  2022-10-07 16:00:02    07-16
18257  845016064  42157405015  2022-10-07 17:00:01    07-17
22276  845016064  42157405015  2022-10-07 18:00:02    07-18
16966  845016064  42157405015  2022-10-07 19:00:01    07-19
18085  845016064  42157405015  2022-10-07 20:00:02    07-20
\end{Verbatim}
\end{tcolorbox}
        
    \begin{tcolorbox}[breakable, size=fbox, boxrule=1pt, pad at break*=1mm,colback=cellbackground, colframe=cellborder]
\prompt{In}{incolor}{95}{\boxspacing}
\begin{Verbatim}[commandchars=\\\{\}]
\PY{n+nb}{print}\PY{p}{(}\PY{n+nb}{len}\PY{p}{(}\PY{n}{df}\PY{p}{[}\PY{n}{df}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{year}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{o}{==}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{2023}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{p}{)}\PY{p}{)}
\PY{n}{df}\PY{p}{[}\PY{n}{df}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{year}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{o}{==}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{2023}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{p}{[}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{itemid}\PY{l+s+s1}{\PYZsq{}}\PY{p}{,}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{modelid}\PY{l+s+s1}{\PYZsq{}}\PY{p}{,}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{ingest\PYZus{}date}\PY{l+s+s1}{\PYZsq{}}\PY{p}{,}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{day\PYZus{}hour}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{p}{]}\PY{o}{.}\PY{n}{sort\PYZus{}values}\PY{p}{(}\PY{n}{by}\PY{o}{=}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{itemid}\PY{l+s+s1}{\PYZsq{}}\PY{p}{,}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{ingest\PYZus{}date}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{p}{)}\PY{p}{[}\PY{p}{:}\PY{l+m+mi}{10}\PY{p}{]}
\end{Verbatim}
\end{tcolorbox}

    \begin{Verbatim}[commandchars=\\\{\}]
1194
    \end{Verbatim}

            \begin{tcolorbox}[breakable, size=fbox, boxrule=.5pt, pad at break*=1mm, opacityfill=0]
\prompt{Out}{outcolor}{95}{\boxspacing}
\begin{Verbatim}[commandchars=\\\{\}]
           itemid      modelid          ingest\_date day\_hour
36417   845016064  42157405015  2023-01-19 09:21:47    19-09
36419  2177325629  22934228784  2023-01-19 09:21:47    19-09
28899  2177325629  22934228784  2023-01-19 12:00:01    19-12
24336  2177325629  22934228784  2023-01-19 15:00:05    19-15
24339  2177325629  22934228784  2023-01-20 09:00:08    20-09
26153  2177325629  22934228784  2023-01-20 12:00:07    20-12
24573  2177325629  22934228784  2023-01-20 15:00:07    20-15
24389  2177325629  22934228784  2023-01-23 15:00:01    23-15
32660  2177325629  22934228784  2023-01-23 18:00:02    23-18
32666  2177325629  22934228784  2023-01-23 21:00:01    23-21
\end{Verbatim}
\end{tcolorbox}
        
    จากการดูแยกปี 2022 กับ 2023 จะพบว่า 2022 มี transaction ทุกๆ1 ชั่วโมง ส่วน 2023
จะเป็น transaction ทุกๆ3ชั่วโมง ทำให้ข้อมูลปี 2023
อาจจะข้ามช่วงเวลาการทำแฟลชเซลไปอาจจะทำให้ข้อมูลคลาดเคลื่อนกันของทั้ง2ปี
เราจึงเลือกที่จะตัดข้อมูลของปี 2023
ออกเนื่องจากเราต้องการนำแฟลชเซลมาวิเคราะห์ถึงระยะเวลาและจำนวน trnsasction
ที่เกิดขึ้น

    \begin{tcolorbox}[breakable, size=fbox, boxrule=1pt, pad at break*=1mm,colback=cellbackground, colframe=cellborder]
\prompt{In}{incolor}{12}{\boxspacing}
\begin{Verbatim}[commandchars=\\\{\}]
\PY{n}{fig} \PY{o}{=} \PY{n}{plt}\PY{o}{.}\PY{n}{figure}\PY{p}{(}\PY{n}{figsize} \PY{o}{=} \PY{p}{(}\PY{l+m+mi}{15}\PY{p}{,} \PY{l+m+mi}{7}\PY{p}{)}\PY{p}{)}
\PY{n}{freq} \PY{o}{=} \PY{n}{plt}\PY{o}{.}\PY{n}{bar}\PY{p}{(}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{All data}\PY{l+s+s1}{\PYZsq{}}\PY{p}{,}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{After removing 2023}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{p}{,} \PY{p}{[}\PY{n+nb}{len}\PY{p}{(}\PY{n}{df}\PY{p}{)}\PY{p}{,}\PY{n+nb}{len}\PY{p}{(}\PY{n}{df}\PY{p}{[}\PY{n}{df}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{year}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{o}{!=}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{2023}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{p}{)}\PY{p}{]}\PY{p}{,} \PY{n}{color} \PY{o}{=}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{c}\PY{l+s+s1}{\PYZsq{}}\PY{p}{,}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{green}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{p}{)}

\PY{k}{for} \PY{n}{f} \PY{o+ow}{in} \PY{n}{freq}\PY{p}{:}
    \PY{n}{height} \PY{o}{=} \PY{n}{f}\PY{o}{.}\PY{n}{get\PYZus{}height}\PY{p}{(}\PY{p}{)}
    \PY{n}{plt}\PY{o}{.}\PY{n}{annotate}\PY{p}{(}\PY{l+s+sa}{f}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+si}{\PYZob{}}\PY{n}{height}\PY{l+s+si}{:}\PY{l+s+s1}{.0f}\PY{l+s+si}{\PYZcb{}}\PY{l+s+s1}{\PYZsq{}}\PY{p}{,}
                \PY{n}{xy}\PY{o}{=}\PY{p}{(}\PY{n}{f}\PY{o}{.}\PY{n}{get\PYZus{}x}\PY{p}{(}\PY{p}{)} \PY{o}{+} \PY{n}{f}\PY{o}{.}\PY{n}{get\PYZus{}width}\PY{p}{(}\PY{p}{)} \PY{o}{/} \PY{l+m+mi}{2}\PY{p}{,} \PY{n}{height}\PY{o}{/}\PY{l+m+mi}{2}\PY{p}{)}\PY{p}{,}
                \PY{n}{xytext}\PY{o}{=}\PY{p}{(}\PY{l+m+mi}{0}\PY{p}{,} \PY{l+m+mi}{3}\PY{p}{)}\PY{p}{,}
                \PY{n}{textcoords}\PY{o}{=}\PY{l+s+s2}{\PYZdq{}}\PY{l+s+s2}{offset points}\PY{l+s+s2}{\PYZdq{}}\PY{p}{,}
                \PY{n}{ha}\PY{o}{=}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{center}\PY{l+s+s1}{\PYZsq{}}\PY{p}{,} \PY{n}{va}\PY{o}{=}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{bottom}\PY{l+s+s1}{\PYZsq{}}\PY{p}{,} \PY{n}{fontsize}\PY{o}{=}\PY{l+m+mi}{15}\PY{p}{,}\PY{n}{color}\PY{o}{=}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{white}\PY{l+s+s1}{\PYZsq{}}\PY{p}{,} \PY{n}{weight}\PY{o}{=}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{bold}\PY{l+s+s1}{\PYZsq{}}\PY{p}{)}
    
\PY{n}{fig}\PY{o}{.}\PY{n}{suptitle}\PY{p}{(}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{Number of data Before and After remove 2023}\PY{l+s+s1}{\PYZsq{}}\PY{p}{,} \PY{n}{fontsize}\PY{o}{=}\PY{l+m+mi}{15}\PY{p}{)}
\PY{n}{plt}\PY{o}{.}\PY{n}{ylabel}\PY{p}{(}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{Count row of data}\PY{l+s+s1}{\PYZsq{}}\PY{p}{,} \PY{n}{fontsize}\PY{o}{=}\PY{l+m+mi}{15}\PY{p}{)}
\end{Verbatim}
\end{tcolorbox}

            \begin{tcolorbox}[breakable, size=fbox, boxrule=.5pt, pad at break*=1mm, opacityfill=0]
\prompt{Out}{outcolor}{12}{\boxspacing}
\begin{Verbatim}[commandchars=\\\{\}]
Text(0, 0.5, 'Count row of data')
\end{Verbatim}
\end{tcolorbox}
        
    \begin{center}
    \adjustimage{max size={0.9\linewidth}{0.9\paperheight}}{output_18_1.png}
    \end{center}
    { \hspace*{\fill} \\}
    
    \begin{tcolorbox}[breakable, size=fbox, boxrule=1pt, pad at break*=1mm,colback=cellbackground, colframe=cellborder]
\prompt{In}{incolor}{13}{\boxspacing}
\begin{Verbatim}[commandchars=\\\{\}]
\PY{n}{df} \PY{o}{=} \PY{n}{df}\PY{p}{[}\PY{n}{df}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{year}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{o}{!=}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{2023}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}
\end{Verbatim}
\end{tcolorbox}

    \hypertarget{top-10-flash-sale-frequency-by-day_hour}{%
\subsection{1.Top 10 flash sale frequency by
day\_hour}\label{top-10-flash-sale-frequency-by-day_hour}}

วันและเวลา 10 อันดับแรกใดที่มีการทำแฟลชเซลบ่อยที่สุด

    \hypertarget{filter-only-transaction-that-have-flash-sale}{%
\paragraph{Filter only transaction that have flash
sale}\label{filter-only-transaction-that-have-flash-sale}}

เตรียมข้อมูลเพื่อวิเคราะห์สินค้าที่ทำแฟลชเซล โดยสินค้าที่มีการทำแฟลชเซล ดูจากคอลัมน์
Flash\_sale ที่ค่าไม่ใช่ค่าว่าง

    \begin{tcolorbox}[breakable, size=fbox, boxrule=1pt, pad at break*=1mm,colback=cellbackground, colframe=cellborder]
\prompt{In}{incolor}{14}{\boxspacing}
\begin{Verbatim}[commandchars=\\\{\}]
\PY{n}{df}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{flash\PYZus{}sale}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{o}{.}\PY{n}{unique}\PY{p}{(}\PY{p}{)}\PY{p}{[}\PY{p}{:}\PY{l+m+mi}{10}\PY{p}{]}
\end{Verbatim}
\end{tcolorbox}

            \begin{tcolorbox}[breakable, size=fbox, boxrule=.5pt, pad at break*=1mm, opacityfill=0]
\prompt{Out}{outcolor}{14}{\boxspacing}
\begin{Verbatim}[commandchars=\\\{\}]
array([nan,
       "\{'price\_before\_discount': 1999900000, 'hidden\_price\_display': None,
'end\_time': 1662663600, 'flash\_sale\_stock': 100, 'promotionid': 107390517342208,
'lowest\_past\_price': None, 'promo\_images': ['60aaea4fe52b112fca2bf6c02bf52da8'],
'start\_time': 1662656400, 'promo\_overlay\_image':
'f85173f31d3776172d6999ad5a8d39e4', 'extra\_discount\_info': None,
'flash\_sale\_type': 0, 'price': 1499000000, 'stock': 100\}",
       "\{'price\_before\_discount': 2141900000, 'hidden\_price\_display': None,
'end\_time': 1662663600, 'flash\_sale\_stock': 30, 'promotionid': 674535842344547,
'lowest\_past\_price': None, 'promo\_images': None, 'start\_time': 1662656400,
'promo\_overlay\_image': None, 'extra\_discount\_info': None, 'flash\_sale\_type': 2,
'price': 1190000000, 'stock': 30\}",
       "\{'price\_before\_discount': 1700000000, 'hidden\_price\_display': None,
'end\_time': 1662663600, 'flash\_sale\_stock': 50, 'promotionid': 108652700917760,
'lowest\_past\_price': None, 'promo\_images': ['4be03248bfbc47be3234d3a451b79f25'],
'start\_time': 1662656400, 'promo\_overlay\_image': None, 'extra\_discount\_info':
None, 'flash\_sale\_type': 1, 'price': 1150000000, 'stock': 50\}",
       "\{'price\_before\_discount': 1890000000, 'hidden\_price\_display': None,
'end\_time': 1662663600, 'flash\_sale\_stock': 40, 'promotionid': 108652700917760,
'lowest\_past\_price': None, 'promo\_images': ['61a2ee81dd0020fa6fdce5b3e2b7cef5'],
'start\_time': 1662656400, 'promo\_overlay\_image': None, 'extra\_discount\_info':
None, 'flash\_sale\_type': 1, 'price': 1400000000, 'stock': 40\}",
       "\{'price\_before\_discount': 1499000000, 'hidden\_price\_display': None,
'end\_time': 1662663600, 'flash\_sale\_stock': 30, 'promotionid': 107390517342208,
'lowest\_past\_price': None, 'promo\_images': ['db1455ff51f4185d24ebdf8475dd1ecd'],
'start\_time': 1662656400, 'promo\_overlay\_image': None, 'extra\_discount\_info':
None, 'flash\_sale\_type': 0, 'price': 1149000000, 'stock': 30\}",
       "\{'price\_before\_discount': 1700000000, 'hidden\_price\_display': None,
'end\_time': 1662663600, 'flash\_sale\_stock': 50, 'promotionid': 108652700917760,
'lowest\_past\_price': None, 'promo\_images': ['4be03248bfbc47be3234d3a451b79f25'],
'start\_time': 1662656400, 'promo\_overlay\_image': None, 'extra\_discount\_info':
None, 'flash\_sale\_type': 1, 'price': 1150000000, 'stock': 34\}",
       "\{'price\_before\_discount': 1499000000, 'hidden\_price\_display': None,
'end\_time': 1662663600, 'flash\_sale\_stock': 30, 'promotionid': 107390517342208,
'lowest\_past\_price': None, 'promo\_images': ['db1455ff51f4185d24ebdf8475dd1ecd'],
'start\_time': 1662656400, 'promo\_overlay\_image': None, 'extra\_discount\_info':
None, 'flash\_sale\_type': 0, 'price': 1149000000, 'stock': 6\}",
       "\{'price\_before\_discount': 1999900000, 'hidden\_price\_display': None,
'end\_time': 1662663600, 'flash\_sale\_stock': 100, 'promotionid': 107390517342208,
'lowest\_past\_price': None, 'promo\_images': ['60aaea4fe52b112fca2bf6c02bf52da8'],
'start\_time': 1662656400, 'promo\_overlay\_image':
'f85173f31d3776172d6999ad5a8d39e4', 'extra\_discount\_info': None,
'flash\_sale\_type': 0, 'price': 1499000000, 'stock': 63\}",
       "\{'price\_before\_discount': 2141900000, 'hidden\_price\_display': None,
'end\_time': 1662663600, 'flash\_sale\_stock': 10, 'promotionid': 674491900713811,
'lowest\_past\_price': None, 'promo\_images': None, 'start\_time': 1662656400,
'promo\_overlay\_image': None, 'extra\_discount\_info': None, 'flash\_sale\_type': 2,
'price': 1190000000, 'stock': 9\}"],
      dtype=object)
\end{Verbatim}
\end{tcolorbox}
        
    เราจะเลือกเฉพาะ Transaction ที่มีการทำแฟลชเซล

    \begin{tcolorbox}[breakable, size=fbox, boxrule=1pt, pad at break*=1mm,colback=cellbackground, colframe=cellborder]
\prompt{In}{incolor}{15}{\boxspacing}
\begin{Verbatim}[commandchars=\\\{\}]
\PY{n}{flash\PYZus{}sale} \PY{o}{=} \PY{n}{df}\PY{p}{[}\PY{n}{df}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{flash\PYZus{}sale}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{o}{.}\PY{n}{notnull}\PY{p}{(}\PY{p}{)}\PY{p}{]}
\PY{n+nb}{print}\PY{p}{(}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{Number of records:}\PY{l+s+s1}{\PYZsq{}}\PY{p}{,}\PY{n+nb}{len}\PY{p}{(}\PY{n}{df}\PY{p}{)}\PY{p}{)}
\PY{n+nb}{print}\PY{p}{(}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{Number of records after filter only flash sale:}\PY{l+s+s1}{\PYZsq{}}\PY{p}{,}\PY{n+nb}{len}\PY{p}{(}\PY{n}{flash\PYZus{}sale}\PY{p}{)}\PY{p}{)}
\end{Verbatim}
\end{tcolorbox}

    \begin{Verbatim}[commandchars=\\\{\}]
Number of records: 30679
Number of records after filter only flash sale: 1197
    \end{Verbatim}

    \begin{tcolorbox}[breakable, size=fbox, boxrule=1pt, pad at break*=1mm,colback=cellbackground, colframe=cellborder]
\prompt{In}{incolor}{16}{\boxspacing}
\begin{Verbatim}[commandchars=\\\{\}]
\PY{n}{flash\PYZus{}sale} \PY{o}{=} \PY{n}{df}\PY{o}{.}\PY{n}{drop\PYZus{}duplicates}\PY{p}{(}\PY{n}{subset}\PY{o}{=}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{flash\PYZus{}sale}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{p}{)}
\PY{n}{fs\PYZus{}groupby\PYZus{}DH} \PY{o}{=} \PY{n}{flash\PYZus{}sale}\PY{o}{.}\PY{n}{groupby}\PY{p}{(}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{modelid}\PY{l+s+s1}{\PYZsq{}}\PY{p}{,}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{day\PYZus{}hour}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{p}{)}\PY{p}{[}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{day\PYZus{}hour}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{p}{]}\PY{o}{.}\PY{n}{count}\PY{p}{(}\PY{p}{)}
\end{Verbatim}
\end{tcolorbox}

    \begin{tcolorbox}[breakable, size=fbox, boxrule=1pt, pad at break*=1mm,colback=cellbackground, colframe=cellborder]
\prompt{In}{incolor}{17}{\boxspacing}
\begin{Verbatim}[commandchars=\\\{\}]
\PY{n}{fs\PYZus{}groupby\PYZus{}DH} \PY{o}{=} \PY{n}{fs\PYZus{}groupby\PYZus{}DH}\PY{o}{.}\PY{n}{rename}\PY{p}{(}\PY{n}{columns} \PY{o}{=} \PY{p}{\PYZob{}}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{day\PYZus{}hour}\PY{l+s+s1}{\PYZsq{}}\PY{p}{:}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{count\PYZus{}dh}\PY{l+s+s1}{\PYZsq{}}\PY{p}{\PYZcb{}}\PY{p}{)}
\end{Verbatim}
\end{tcolorbox}

    \begin{tcolorbox}[breakable, size=fbox, boxrule=1pt, pad at break*=1mm,colback=cellbackground, colframe=cellborder]
\prompt{In}{incolor}{18}{\boxspacing}
\begin{Verbatim}[commandchars=\\\{\}]
\PY{n}{fs\PYZus{}groupby\PYZus{}DH} \PY{o}{=} \PY{n}{fs\PYZus{}groupby\PYZus{}DH}\PY{o}{.}\PY{n}{reset\PYZus{}index}\PY{p}{(}\PY{p}{)}
\end{Verbatim}
\end{tcolorbox}

    \begin{tcolorbox}[breakable, size=fbox, boxrule=1pt, pad at break*=1mm,colback=cellbackground, colframe=cellborder]
\prompt{In}{incolor}{20}{\boxspacing}
\begin{Verbatim}[commandchars=\\\{\}]
\PY{n}{most\PYZus{}flash\PYZus{}sale} \PY{o}{=} \PY{n}{fs\PYZus{}groupby\PYZus{}DH}\PY{o}{.}\PY{n}{groupby}\PY{p}{(}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{day\PYZus{}hour}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{p}{)}\PY{p}{[}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{count\PYZus{}dh}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{p}{]}\PY{o}{.}\PY{n}{sum}\PY{p}{(}\PY{p}{)}\PY{o}{.}\PY{n}{reset\PYZus{}index}\PY{p}{(}\PY{p}{)}
\end{Verbatim}
\end{tcolorbox}

    \begin{tcolorbox}[breakable, size=fbox, boxrule=1pt, pad at break*=1mm,colback=cellbackground, colframe=cellborder]
\prompt{In}{incolor}{22}{\boxspacing}
\begin{Verbatim}[commandchars=\\\{\}]
\PY{n}{most\PYZus{}flash\PYZus{}sale} \PY{o}{=} \PY{n}{most\PYZus{}flash\PYZus{}sale}\PY{o}{.}\PY{n}{sort\PYZus{}values}\PY{p}{(}\PY{n}{by}\PY{o}{=}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{count\PYZus{}dh}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{p}{,}\PY{n}{ascending}\PY{o}{=}\PY{k+kc}{False}\PY{p}{)}\PY{o}{.}\PY{n}{reset\PYZus{}index}\PY{p}{(}\PY{p}{)}
\PY{n}{most\PYZus{}flash\PYZus{}sale}
\end{Verbatim}
\end{tcolorbox}

            \begin{tcolorbox}[breakable, size=fbox, boxrule=.5pt, pad at break*=1mm, opacityfill=0]
\prompt{Out}{outcolor}{22}{\boxspacing}
\begin{Verbatim}[commandchars=\\\{\}]
     index day\_hour  count\_dh
0      206    25-00        10
1      113    15-00        10
2      129    15-21         9
3      263    30-12         9
4       93    11-00         8
..     {\ldots}      {\ldots}       {\ldots}
276    136    16-15         1
277    138    17-00         1
278    139    17-01         1
279      1    01-04         1
280    280    31-16         1

[281 rows x 3 columns]
\end{Verbatim}
\end{tcolorbox}
        
    \begin{tcolorbox}[breakable, size=fbox, boxrule=1pt, pad at break*=1mm,colback=cellbackground, colframe=cellborder]
\prompt{In}{incolor}{23}{\boxspacing}
\begin{Verbatim}[commandchars=\\\{\}]
\PY{n}{fig} \PY{o}{=} \PY{n}{plt}\PY{o}{.}\PY{n}{figure}\PY{p}{(}\PY{n}{figsize} \PY{o}{=} \PY{p}{(}\PY{l+m+mi}{15}\PY{p}{,} \PY{l+m+mi}{6}\PY{p}{)}\PY{p}{)}
\PY{n}{freq} \PY{o}{=} \PY{n}{plt}\PY{o}{.}\PY{n}{bar}\PY{p}{(}\PY{n}{most\PYZus{}flash\PYZus{}sale}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{day\PYZus{}hour}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{p}{[}\PY{p}{:}\PY{l+m+mi}{10}\PY{p}{]}\PY{p}{,} \PY{n}{most\PYZus{}flash\PYZus{}sale}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{count\PYZus{}dh}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{p}{[}\PY{p}{:}\PY{l+m+mi}{10}\PY{p}{]}\PY{p}{,} \PY{n}{color} \PY{o}{=}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{c}\PY{l+s+s1}{\PYZsq{}}\PY{p}{,}
        \PY{n}{width} \PY{o}{=} \PY{l+m+mf}{0.4}\PY{p}{)}

\PY{k}{for} \PY{n}{f} \PY{o+ow}{in} \PY{n}{freq}\PY{p}{:}
    \PY{n}{height} \PY{o}{=} \PY{n}{f}\PY{o}{.}\PY{n}{get\PYZus{}height}\PY{p}{(}\PY{p}{)}
    \PY{n}{plt}\PY{o}{.}\PY{n}{annotate}\PY{p}{(}\PY{l+s+sa}{f}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+si}{\PYZob{}}\PY{n}{height}\PY{l+s+si}{:}\PY{l+s+s1}{.0f}\PY{l+s+si}{\PYZcb{}}\PY{l+s+s1}{\PYZsq{}}\PY{p}{,}
                \PY{n}{xy}\PY{o}{=}\PY{p}{(}\PY{n}{f}\PY{o}{.}\PY{n}{get\PYZus{}x}\PY{p}{(}\PY{p}{)} \PY{o}{+} \PY{n}{f}\PY{o}{.}\PY{n}{get\PYZus{}width}\PY{p}{(}\PY{p}{)} \PY{o}{/} \PY{l+m+mi}{2}\PY{p}{,} \PY{n}{height}\PY{p}{)}\PY{p}{,}
                \PY{n}{xytext}\PY{o}{=}\PY{p}{(}\PY{l+m+mi}{0}\PY{p}{,} \PY{l+m+mi}{3}\PY{p}{)}\PY{p}{,}
                \PY{n}{textcoords}\PY{o}{=}\PY{l+s+s2}{\PYZdq{}}\PY{l+s+s2}{offset points}\PY{l+s+s2}{\PYZdq{}}\PY{p}{,}
                \PY{n}{ha}\PY{o}{=}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{center}\PY{l+s+s1}{\PYZsq{}}\PY{p}{,} \PY{n}{va}\PY{o}{=}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{bottom}\PY{l+s+s1}{\PYZsq{}}\PY{p}{)}
    
\PY{n}{fig}\PY{o}{.}\PY{n}{suptitle}\PY{p}{(}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{Top 10 flash sale frequency by day\PYZus{}hour}\PY{l+s+s1}{\PYZsq{}}\PY{p}{)}
\PY{n}{plt}\PY{o}{.}\PY{n}{xlabel}\PY{p}{(}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{day\PYZus{}hour of flash sale}\PY{l+s+s1}{\PYZsq{}}\PY{p}{)}
\PY{n}{plt}\PY{o}{.}\PY{n}{ylabel}\PY{p}{(}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{count transaction of flash sale}\PY{l+s+s1}{\PYZsq{}}\PY{p}{)}
\end{Verbatim}
\end{tcolorbox}

            \begin{tcolorbox}[breakable, size=fbox, boxrule=.5pt, pad at break*=1mm, opacityfill=0]
\prompt{Out}{outcolor}{23}{\boxspacing}
\begin{Verbatim}[commandchars=\\\{\}]
Text(0, 0.5, 'count transaction of flash sale')
\end{Verbatim}
\end{tcolorbox}
        
    \begin{center}
    \adjustimage{max size={0.9\linewidth}{0.9\paperheight}}{output_30_1.png}
    \end{center}
    { \hspace*{\fill} \\}
    
    วันและเวลาที่มีการทำแฟลชเซลบ่อยที่สุดโดยนับจาก Transaction ของสินค้าที่มีการทำแฟลชเซล
คือวันที่ 25 เที่ยงคืนกับ 15 เที่ยงคืน (เนื่องจาก 25 เป็นวันที่จัด PayDay campaign และ 15
เป็นวันที่จัด Mid month campaign)

    \hypertarget{compare-3-sales-campaigns}{%
\subsection{2. Compare 3 sales
campaigns}\label{compare-3-sales-campaigns}}

เปรียบเทียบ 3 แคมเปญลดราคาสินค้า หาว่าแคมเปญไหนมีการทำแฟลชเซลบ่อยที่สุด

    \begin{tcolorbox}[breakable, size=fbox, boxrule=1pt, pad at break*=1mm,colback=cellbackground, colframe=cellborder]
\prompt{In}{incolor}{24}{\boxspacing}
\begin{Verbatim}[commandchars=\\\{\}]
\PY{c+c1}{\PYZsh{} Extract day and hour from day\PYZus{}hour}
\PY{n}{df}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{day}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]} \PY{o}{=} \PY{n}{df}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{day\PYZus{}hour}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{o}{.}\PY{n}{apply}\PY{p}{(}\PY{k}{lambda} \PY{n}{x} \PY{p}{:} \PY{n}{x}\PY{o}{.}\PY{n}{split}\PY{p}{(}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{\PYZhy{}}\PY{l+s+s1}{\PYZsq{}}\PY{p}{)}\PY{p}{[}\PY{l+m+mi}{0}\PY{p}{]}\PY{p}{)}\PY{o}{.}\PY{n}{astype}\PY{p}{(}\PY{n+nb}{int}\PY{p}{)}
\PY{n}{df}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{hour}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]} \PY{o}{=} \PY{n}{df}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{day\PYZus{}hour}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{o}{.}\PY{n}{apply}\PY{p}{(}\PY{k}{lambda} \PY{n}{x} \PY{p}{:} \PY{n}{x}\PY{o}{.}\PY{n}{split}\PY{p}{(}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{\PYZhy{}}\PY{l+s+s1}{\PYZsq{}}\PY{p}{)}\PY{p}{[}\PY{l+m+mi}{1}\PY{p}{]}\PY{p}{)}\PY{o}{.}\PY{n}{astype}\PY{p}{(}\PY{n+nb}{int}\PY{p}{)}
\end{Verbatim}
\end{tcolorbox}

    \hypertarget{create-3-new-dataframe-by-sale-campaign}{%
\subsubsection{Create 3 new dataframe by sale
campaign}\label{create-3-new-dataframe-by-sale-campaign}}

    \begin{tcolorbox}[breakable, size=fbox, boxrule=1pt, pad at break*=1mm,colback=cellbackground, colframe=cellborder]
\prompt{In}{incolor}{25}{\boxspacing}
\begin{Verbatim}[commandchars=\\\{\}]
\PY{n}{mega\PYZus{}sale\PYZus{}df} \PY{o}{=} \PY{n}{df}\PY{p}{[}\PY{p}{(}\PY{n}{df}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{mega\PYZus{}sale}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{o}{==}\PY{k+kc}{True}\PY{p}{)}\PY{o}{\PYZam{}}\PY{p}{(}\PY{n}{df}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{flash\PYZus{}sale}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{o}{.}\PY{n}{notna}\PY{p}{(}\PY{p}{)}\PY{p}{)}\PY{p}{]}\PY{o}{.}\PY{n}{drop\PYZus{}duplicates}\PY{p}{(}\PY{n}{subset}\PY{o}{=}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{flash\PYZus{}sale}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{p}{,}\PY{n}{keep}\PY{o}{=}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{first}\PY{l+s+s1}{\PYZsq{}}\PY{p}{)}\PY{o}{.}\PY{n}{reset\PYZus{}index}\PY{p}{(}\PY{n}{drop}\PY{o}{=}\PY{k+kc}{True}\PY{p}{)}
\PY{n}{mega\PYZus{}sale\PYZus{}fr} \PY{o}{=} \PY{n+nb}{len}\PY{p}{(}\PY{n}{mega\PYZus{}sale\PYZus{}df}\PY{p}{)}
\PY{n}{mega\PYZus{}sale\PYZus{}fr}
\end{Verbatim}
\end{tcolorbox}

            \begin{tcolorbox}[breakable, size=fbox, boxrule=.5pt, pad at break*=1mm, opacityfill=0]
\prompt{Out}{outcolor}{25}{\boxspacing}
\begin{Verbatim}[commandchars=\\\{\}]
98
\end{Verbatim}
\end{tcolorbox}
        
    \begin{tcolorbox}[breakable, size=fbox, boxrule=1pt, pad at break*=1mm,colback=cellbackground, colframe=cellborder]
\prompt{In}{incolor}{26}{\boxspacing}
\begin{Verbatim}[commandchars=\\\{\}]
\PY{n}{mid\PYZus{}month\PYZus{}sale\PYZus{}df} \PY{o}{=} \PY{n}{df}\PY{p}{[}\PY{p}{(}\PY{n}{df}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{day}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{o}{==}\PY{l+m+mi}{15}\PY{p}{)}\PY{o}{\PYZam{}}\PY{p}{(}\PY{n}{df}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{flash\PYZus{}sale}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{o}{.}\PY{n}{notna}\PY{p}{(}\PY{p}{)}\PY{p}{)}\PY{p}{]}\PY{o}{.}\PY{n}{drop\PYZus{}duplicates}\PY{p}{(}\PY{n}{subset}\PY{o}{=}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{flash\PYZus{}sale}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{p}{,}\PY{n}{keep}\PY{o}{=}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{first}\PY{l+s+s1}{\PYZsq{}}\PY{p}{)}\PY{o}{.}\PY{n}{reset\PYZus{}index}\PY{p}{(}\PY{n}{drop}\PY{o}{=}\PY{k+kc}{True}\PY{p}{)}
\PY{n}{mid\PYZus{}month\PYZus{}sale\PYZus{}fr} \PY{o}{=} \PY{n+nb}{len}\PY{p}{(}\PY{n}{mid\PYZus{}month\PYZus{}sale\PYZus{}df}\PY{p}{)}
\PY{n}{mid\PYZus{}month\PYZus{}sale\PYZus{}fr}
\end{Verbatim}
\end{tcolorbox}

            \begin{tcolorbox}[breakable, size=fbox, boxrule=.5pt, pad at break*=1mm, opacityfill=0]
\prompt{Out}{outcolor}{26}{\boxspacing}
\begin{Verbatim}[commandchars=\\\{\}]
60
\end{Verbatim}
\end{tcolorbox}
        
    \begin{tcolorbox}[breakable, size=fbox, boxrule=1pt, pad at break*=1mm,colback=cellbackground, colframe=cellborder]
\prompt{In}{incolor}{27}{\boxspacing}
\begin{Verbatim}[commandchars=\\\{\}]
\PY{n}{pay\PYZus{}day\PYZus{}sale\PYZus{}df} \PY{o}{=} \PY{n}{df}\PY{p}{[}\PY{p}{(}\PY{n}{df}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{day}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{o}{\PYZgt{}}\PY{o}{=}\PY{l+m+mi}{25}\PY{p}{)}\PY{o}{\PYZam{}}\PY{p}{(}\PY{n}{df}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{flash\PYZus{}sale}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{o}{.}\PY{n}{notna}\PY{p}{(}\PY{p}{)}\PY{p}{)}\PY{p}{]}\PY{o}{.}\PY{n}{drop\PYZus{}duplicates}\PY{p}{(}\PY{n}{subset}\PY{o}{=}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{flash\PYZus{}sale}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{p}{,}\PY{n}{keep}\PY{o}{=}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{first}\PY{l+s+s1}{\PYZsq{}}\PY{p}{)}\PY{o}{.}\PY{n}{reset\PYZus{}index}\PY{p}{(}\PY{n}{drop}\PY{o}{=}\PY{k+kc}{True}\PY{p}{)}
\PY{n}{pay\PYZus{}day\PYZus{}sale\PYZus{}fr} \PY{o}{=} \PY{n+nb}{len}\PY{p}{(}\PY{n}{pay\PYZus{}day\PYZus{}sale\PYZus{}df}\PY{p}{)}
\PY{n}{pay\PYZus{}day\PYZus{}sale\PYZus{}fr}
\end{Verbatim}
\end{tcolorbox}

            \begin{tcolorbox}[breakable, size=fbox, boxrule=.5pt, pad at break*=1mm, opacityfill=0]
\prompt{Out}{outcolor}{27}{\boxspacing}
\begin{Verbatim}[commandchars=\\\{\}]
151
\end{Verbatim}
\end{tcolorbox}
        
    \begin{tcolorbox}[breakable, size=fbox, boxrule=1pt, pad at break*=1mm,colback=cellbackground, colframe=cellborder]
\prompt{In}{incolor}{28}{\boxspacing}
\begin{Verbatim}[commandchars=\\\{\}]
\PY{n}{fig} \PY{o}{=} \PY{n}{plt}\PY{o}{.}\PY{n}{figure}\PY{p}{(}\PY{n}{figsize} \PY{o}{=} \PY{p}{(}\PY{l+m+mi}{15}\PY{p}{,} \PY{l+m+mi}{6}\PY{p}{)}\PY{p}{)}
\PY{n}{freq} \PY{o}{=} \PY{n}{plt}\PY{o}{.}\PY{n}{bar}\PY{p}{(}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{Mega campaign}\PY{l+s+s1}{\PYZsq{}}\PY{p}{,}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{Mid Month campaign}\PY{l+s+s1}{\PYZsq{}}\PY{p}{,}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{PayDay campaign}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{p}{,} \PY{p}{[}\PY{n}{mega\PYZus{}sale\PYZus{}fr}\PY{p}{,}\PY{n}{mid\PYZus{}month\PYZus{}sale\PYZus{}fr}\PY{p}{,}\PY{n}{pay\PYZus{}day\PYZus{}sale\PYZus{}fr}\PY{p}{]}\PY{p}{,} \PY{n}{color} \PY{o}{=}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{c}\PY{l+s+s1}{\PYZsq{}}\PY{p}{,}
        \PY{n}{width} \PY{o}{=} \PY{l+m+mf}{0.4}\PY{p}{)}
\PY{n}{all\PYZus{}freq} \PY{o}{=} \PY{l+m+mi}{0}   \PY{c+c1}{\PYZsh{}mega\PYZus{}sale\PYZus{}fr+mid\PYZus{}month\PYZus{}sale\PYZus{}fr+pay\PYZus{}day\PYZus{}sale\PYZus{}fr}
\PY{k}{for} \PY{n}{i} \PY{o+ow}{in} \PY{n}{freq}\PY{p}{:}
    \PY{n}{height} \PY{o}{=} \PY{n}{i}\PY{o}{.}\PY{n}{get\PYZus{}height}\PY{p}{(}\PY{p}{)}
\PY{c+c1}{\PYZsh{}     print(height)}
    \PY{n}{all\PYZus{}freq}\PY{o}{+}\PY{o}{=} \PY{n}{height}
    
\PY{c+c1}{\PYZsh{} print(all\PYZus{}freq)}
\PY{k}{for} \PY{n}{f} \PY{o+ow}{in} \PY{n}{freq}\PY{p}{:}
    \PY{n}{height} \PY{o}{=} \PY{n}{f}\PY{o}{.}\PY{n}{get\PYZus{}height}\PY{p}{(}\PY{p}{)}
    \PY{n}{plt}\PY{o}{.}\PY{n}{annotate}\PY{p}{(}\PY{l+s+sa}{f}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+si}{\PYZob{}}\PY{n}{height}\PY{l+s+si}{:}\PY{l+s+s1}{.0f}\PY{l+s+si}{\PYZcb{}}\PY{l+s+s1}{\PYZsq{}}\PY{p}{,}
                \PY{n}{xy}\PY{o}{=}\PY{p}{(}\PY{n}{f}\PY{o}{.}\PY{n}{get\PYZus{}x}\PY{p}{(}\PY{p}{)} \PY{o}{+} \PY{n}{f}\PY{o}{.}\PY{n}{get\PYZus{}width}\PY{p}{(}\PY{p}{)} \PY{o}{/} \PY{l+m+mi}{2}\PY{p}{,} \PY{n}{height}\PY{p}{)}\PY{p}{,}
                \PY{n}{xytext}\PY{o}{=}\PY{p}{(}\PY{l+m+mi}{0}\PY{p}{,} \PY{l+m+mi}{3}\PY{p}{)}\PY{p}{,}
                \PY{n}{textcoords}\PY{o}{=}\PY{l+s+s2}{\PYZdq{}}\PY{l+s+s2}{offset points}\PY{l+s+s2}{\PYZdq{}}\PY{p}{,}
                \PY{n}{ha}\PY{o}{=}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{center}\PY{l+s+s1}{\PYZsq{}}\PY{p}{,} \PY{n}{va}\PY{o}{=}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{bottom}\PY{l+s+s1}{\PYZsq{}}\PY{p}{)}
    
    \PY{n}{plt}\PY{o}{.}\PY{n}{annotate}\PY{p}{(}\PY{l+s+sa}{f}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+si}{\PYZob{}}\PY{p}{(}\PY{p}{(}\PY{n}{height}\PY{p}{)}\PY{o}{/}\PY{n}{all\PYZus{}freq}\PY{o}{*}\PY{l+m+mi}{100}\PY{p}{)}\PY{l+s+si}{:}\PY{l+s+s1}{.0f}\PY{l+s+si}{\PYZcb{}}\PY{l+s+s1}{\PYZpc{}}\PY{l+s+s1}{\PYZsq{}}\PY{p}{,}
                \PY{n}{xy}\PY{o}{=}\PY{p}{(}\PY{n}{f}\PY{o}{.}\PY{n}{get\PYZus{}x}\PY{p}{(}\PY{p}{)} \PY{o}{+} \PY{n}{f}\PY{o}{.}\PY{n}{get\PYZus{}width}\PY{p}{(}\PY{p}{)} \PY{o}{/} \PY{l+m+mi}{2}\PY{p}{,} \PY{n}{height}\PY{o}{/}\PY{l+m+mi}{2}\PY{p}{)}\PY{p}{,}
                \PY{n}{xytext}\PY{o}{=}\PY{p}{(}\PY{l+m+mi}{0}\PY{p}{,} \PY{l+m+mi}{3}\PY{p}{)}\PY{p}{,}
                \PY{n}{textcoords}\PY{o}{=}\PY{l+s+s2}{\PYZdq{}}\PY{l+s+s2}{offset points}\PY{l+s+s2}{\PYZdq{}}\PY{p}{,}
                \PY{n}{ha}\PY{o}{=}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{center}\PY{l+s+s1}{\PYZsq{}}\PY{p}{,} \PY{n}{va}\PY{o}{=}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{bottom}\PY{l+s+s1}{\PYZsq{}}\PY{p}{)}
    
\PY{n}{fig}\PY{o}{.}\PY{n}{suptitle}\PY{p}{(}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{Frequency transaction product of each sales campaign}\PY{l+s+s1}{\PYZsq{}}\PY{p}{,} \PY{n}{fontsize}\PY{o}{=}\PY{l+m+mi}{17}\PY{p}{)}
\PY{n}{plt}\PY{o}{.}\PY{n}{xlabel}\PY{p}{(}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{Sales campaigns}\PY{l+s+s1}{\PYZsq{}}\PY{p}{,} \PY{n}{fontsize}\PY{o}{=}\PY{l+m+mi}{15}\PY{p}{)}
\PY{n}{plt}\PY{o}{.}\PY{n}{ylabel}\PY{p}{(}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{Count transaction of flash sale}\PY{l+s+s1}{\PYZsq{}}\PY{p}{,} \PY{n}{fontsize}\PY{o}{=}\PY{l+m+mi}{15}\PY{p}{)}
\end{Verbatim}
\end{tcolorbox}

            \begin{tcolorbox}[breakable, size=fbox, boxrule=.5pt, pad at break*=1mm, opacityfill=0]
\prompt{Out}{outcolor}{28}{\boxspacing}
\begin{Verbatim}[commandchars=\\\{\}]
Text(0, 0.5, 'Count transaction of flash sale')
\end{Verbatim}
\end{tcolorbox}
        
    \begin{center}
    \adjustimage{max size={0.9\linewidth}{0.9\paperheight}}{output_38_1.png}
    \end{center}
    { \hspace*{\fill} \\}
    
    ภาพรวมของแต่ละแคมเปญที่มีการทำแฟลชเซล Payday
แคมเปญมีการทำแฟลชเซลเยอะที่สุดเนื่องจากมีการจัดแคมเปญหลายวัน รองลงมาคือ Mega sale
แคมเปญ

    \hypertarget{details-of-payday-campaign-payday-campaign-has-several-campaign-periods.}{%
\subsection{3. Details of Payday campaign (Payday campaign has several
campaign
periods.)}\label{details-of-payday-campaign-payday-campaign-has-several-campaign-periods.}}

PayDay แคมเปญมีระยะเวลาที่จัดแคมเปญหลายวันกว่าแคมเปญอื่นๆ
จึงดูเพิ่มว่าช่วงวันและเวลาไหนที่นิยมทำแฟลชเซล

    \hypertarget{frequency-by-hour}{%
\subsubsection{3.1 Frequency by hour}\label{frequency-by-hour}}

    \begin{tcolorbox}[breakable, size=fbox, boxrule=1pt, pad at break*=1mm,colback=cellbackground, colframe=cellborder]
\prompt{In}{incolor}{29}{\boxspacing}
\begin{Verbatim}[commandchars=\\\{\}]
\PY{n}{pay\PYZus{}day\PYZus{}sale} \PY{o}{=} \PY{n}{df}\PY{p}{[}\PY{p}{(}\PY{n}{df}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{day}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{o}{\PYZgt{}}\PY{o}{=}\PY{l+m+mi}{25}\PY{p}{)}\PY{o}{\PYZam{}}\PY{p}{(}\PY{n}{df}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{flash\PYZus{}sale}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{o}{.}\PY{n}{notna}\PY{p}{(}\PY{p}{)}\PY{p}{)}\PY{p}{]}\PY{o}{.}\PY{n}{drop\PYZus{}duplicates}\PY{p}{(}\PY{n}{subset}\PY{o}{=}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{flash\PYZus{}sale}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{p}{,}\PY{n}{keep}\PY{o}{=}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{first}\PY{l+s+s1}{\PYZsq{}}\PY{p}{)}\PY{o}{.}\PY{n}{groupby}\PY{p}{(}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{hour}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{p}{)}\PY{p}{[}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{hour}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{p}{]}\PY{o}{.}\PY{n}{count}\PY{p}{(}\PY{p}{)}\PY{o}{.}\PY{n}{rename}\PY{p}{(}\PY{n}{columns}\PY{o}{=}\PY{p}{\PYZob{}}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{hour}\PY{l+s+s1}{\PYZsq{}}\PY{p}{:}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{count}\PY{l+s+s1}{\PYZsq{}}\PY{p}{\PYZcb{}}\PY{p}{)}\PY{o}{.}\PY{n}{reset\PYZus{}index}\PY{p}{(}\PY{p}{)}
\PY{n}{pay\PYZus{}day\PYZus{}sale} \PY{o}{=} \PY{n}{pay\PYZus{}day\PYZus{}sale}\PY{o}{.}\PY{n}{sort\PYZus{}values}\PY{p}{(}\PY{n}{by}\PY{o}{=}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{count}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{p}{,}\PY{n}{ascending}\PY{o}{=}\PY{k+kc}{False}\PY{p}{)}\PY{o}{.}\PY{n}{reset\PYZus{}index}\PY{p}{(}\PY{p}{)}
\PY{n}{pay\PYZus{}day\PYZus{}sale}

\PY{n}{fig} \PY{o}{=} \PY{n}{plt}\PY{o}{.}\PY{n}{figure}\PY{p}{(}\PY{n}{figsize} \PY{o}{=} \PY{p}{(}\PY{l+m+mi}{15}\PY{p}{,} \PY{l+m+mi}{6}\PY{p}{)}\PY{p}{)}
\PY{n}{freq} \PY{o}{=} \PY{n}{plt}\PY{o}{.}\PY{n}{bar}\PY{p}{(}\PY{n}{pay\PYZus{}day\PYZus{}sale}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{hour}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{p}{[}\PY{p}{:}\PY{l+m+mi}{10}\PY{p}{]}\PY{p}{,} \PY{n}{pay\PYZus{}day\PYZus{}sale}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{count}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{p}{[}\PY{p}{:}\PY{l+m+mi}{10}\PY{p}{]}\PY{p}{,} \PY{n}{color} \PY{o}{=}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{c}\PY{l+s+s1}{\PYZsq{}}\PY{p}{,}
        \PY{n}{width} \PY{o}{=} \PY{l+m+mf}{0.4}\PY{p}{)}

\PY{k}{for} \PY{n}{f} \PY{o+ow}{in} \PY{n}{freq}\PY{p}{:}
    \PY{n}{height} \PY{o}{=} \PY{n}{f}\PY{o}{.}\PY{n}{get\PYZus{}height}\PY{p}{(}\PY{p}{)}
    \PY{n}{plt}\PY{o}{.}\PY{n}{annotate}\PY{p}{(}\PY{l+s+sa}{f}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+si}{\PYZob{}}\PY{n}{height}\PY{l+s+si}{:}\PY{l+s+s1}{.0f}\PY{l+s+si}{\PYZcb{}}\PY{l+s+s1}{\PYZsq{}}\PY{p}{,}
                \PY{n}{xy}\PY{o}{=}\PY{p}{(}\PY{n}{f}\PY{o}{.}\PY{n}{get\PYZus{}x}\PY{p}{(}\PY{p}{)} \PY{o}{+} \PY{n}{f}\PY{o}{.}\PY{n}{get\PYZus{}width}\PY{p}{(}\PY{p}{)} \PY{o}{/} \PY{l+m+mi}{2}\PY{p}{,} \PY{n}{height}\PY{p}{)}\PY{p}{,}
                \PY{n}{xytext}\PY{o}{=}\PY{p}{(}\PY{l+m+mi}{0}\PY{p}{,} \PY{l+m+mi}{3}\PY{p}{)}\PY{p}{,}
                \PY{n}{textcoords}\PY{o}{=}\PY{l+s+s2}{\PYZdq{}}\PY{l+s+s2}{offset points}\PY{l+s+s2}{\PYZdq{}}\PY{p}{,}
                \PY{n}{ha}\PY{o}{=}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{center}\PY{l+s+s1}{\PYZsq{}}\PY{p}{,} \PY{n}{va}\PY{o}{=}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{bottom}\PY{l+s+s1}{\PYZsq{}}\PY{p}{)}
    
\PY{n}{\PYZus{}} \PY{o}{=} \PY{n}{plt}\PY{o}{.}\PY{n}{xticks}\PY{p}{(}\PY{n}{pay\PYZus{}day\PYZus{}sale}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{hour}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{p}{)}
\PY{n}{fig}\PY{o}{.}\PY{n}{suptitle}\PY{p}{(}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{Frequency transaction product of PayDay sales campaign}\PY{l+s+s1}{\PYZsq{}}\PY{p}{,} \PY{n}{fontsize}\PY{o}{=}\PY{l+m+mi}{17}\PY{p}{)}
\PY{n}{plt}\PY{o}{.}\PY{n}{xlabel}\PY{p}{(}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{Hour}\PY{l+s+s1}{\PYZsq{}}\PY{p}{,} \PY{n}{fontsize}\PY{o}{=}\PY{l+m+mi}{15}\PY{p}{)}
\PY{n}{plt}\PY{o}{.}\PY{n}{ylabel}\PY{p}{(}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{Count transaction of flash sale}\PY{l+s+s1}{\PYZsq{}}\PY{p}{,} \PY{n}{fontsize}\PY{o}{=}\PY{l+m+mi}{15}\PY{p}{)}
\end{Verbatim}
\end{tcolorbox}

            \begin{tcolorbox}[breakable, size=fbox, boxrule=.5pt, pad at break*=1mm, opacityfill=0]
\prompt{Out}{outcolor}{29}{\boxspacing}
\begin{Verbatim}[commandchars=\\\{\}]
Text(0, 0.5, 'Count transaction of flash sale')
\end{Verbatim}
\end{tcolorbox}
        
    \begin{center}
    \adjustimage{max size={0.9\linewidth}{0.9\paperheight}}{output_42_1.png}
    \end{center}
    { \hspace*{\fill} \\}
    
    \hypertarget{frequency-by-day}{%
\subsubsection{3.2 Frequency by day}\label{frequency-by-day}}

    \begin{tcolorbox}[breakable, size=fbox, boxrule=1pt, pad at break*=1mm,colback=cellbackground, colframe=cellborder]
\prompt{In}{incolor}{30}{\boxspacing}
\begin{Verbatim}[commandchars=\\\{\}]
\PY{n}{pay\PYZus{}day\PYZus{}sale} \PY{o}{=} \PY{n}{df}\PY{p}{[}\PY{p}{(}\PY{n}{df}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{day}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{o}{\PYZgt{}}\PY{o}{=}\PY{l+m+mi}{25}\PY{p}{)}\PY{o}{\PYZam{}}\PY{p}{(}\PY{n}{df}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{flash\PYZus{}sale}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{o}{.}\PY{n}{notna}\PY{p}{(}\PY{p}{)}\PY{p}{)}\PY{p}{]}\PY{o}{.}\PY{n}{drop\PYZus{}duplicates}\PY{p}{(}\PY{n}{subset}\PY{o}{=}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{flash\PYZus{}sale}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{p}{,}\PY{n}{keep}\PY{o}{=}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{first}\PY{l+s+s1}{\PYZsq{}}\PY{p}{)}\PY{o}{.}\PY{n}{groupby}\PY{p}{(}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{day}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{p}{)}\PY{p}{[}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{day}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{p}{]}\PY{o}{.}\PY{n}{count}\PY{p}{(}\PY{p}{)}\PY{o}{.}\PY{n}{rename}\PY{p}{(}\PY{n}{columns}\PY{o}{=}\PY{p}{\PYZob{}}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{day}\PY{l+s+s1}{\PYZsq{}}\PY{p}{:}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{count}\PY{l+s+s1}{\PYZsq{}}\PY{p}{\PYZcb{}}\PY{p}{)}\PY{o}{.}\PY{n}{reset\PYZus{}index}\PY{p}{(}\PY{p}{)}
\PY{n}{pay\PYZus{}day\PYZus{}sale} \PY{o}{=} \PY{n}{pay\PYZus{}day\PYZus{}sale}\PY{o}{.}\PY{n}{sort\PYZus{}values}\PY{p}{(}\PY{n}{by}\PY{o}{=}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{count}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{p}{,}\PY{n}{ascending}\PY{o}{=}\PY{k+kc}{False}\PY{p}{)}\PY{o}{.}\PY{n}{reset\PYZus{}index}\PY{p}{(}\PY{p}{)}
\PY{n}{pay\PYZus{}day\PYZus{}sale}

\PY{n}{fig} \PY{o}{=} \PY{n}{plt}\PY{o}{.}\PY{n}{figure}\PY{p}{(}\PY{n}{figsize} \PY{o}{=} \PY{p}{(}\PY{l+m+mi}{15}\PY{p}{,} \PY{l+m+mi}{6}\PY{p}{)}\PY{p}{)}
\PY{n}{freq} \PY{o}{=} \PY{n}{plt}\PY{o}{.}\PY{n}{bar}\PY{p}{(}\PY{n}{pay\PYZus{}day\PYZus{}sale}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{day}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{p}{[}\PY{p}{:}\PY{l+m+mi}{10}\PY{p}{]}\PY{p}{,} \PY{n}{pay\PYZus{}day\PYZus{}sale}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{count}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{p}{[}\PY{p}{:}\PY{l+m+mi}{10}\PY{p}{]}\PY{p}{,} \PY{n}{color} \PY{o}{=}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{c}\PY{l+s+s1}{\PYZsq{}}\PY{p}{,}
        \PY{n}{width} \PY{o}{=} \PY{l+m+mf}{0.4}\PY{p}{)}

\PY{k}{for} \PY{n}{f} \PY{o+ow}{in} \PY{n}{freq}\PY{p}{:}
    \PY{n}{height} \PY{o}{=} \PY{n}{f}\PY{o}{.}\PY{n}{get\PYZus{}height}\PY{p}{(}\PY{p}{)}
    \PY{n}{plt}\PY{o}{.}\PY{n}{annotate}\PY{p}{(}\PY{l+s+sa}{f}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+si}{\PYZob{}}\PY{n}{height}\PY{l+s+si}{:}\PY{l+s+s1}{.0f}\PY{l+s+si}{\PYZcb{}}\PY{l+s+s1}{\PYZsq{}}\PY{p}{,}
                \PY{n}{xy}\PY{o}{=}\PY{p}{(}\PY{n}{f}\PY{o}{.}\PY{n}{get\PYZus{}x}\PY{p}{(}\PY{p}{)} \PY{o}{+} \PY{n}{f}\PY{o}{.}\PY{n}{get\PYZus{}width}\PY{p}{(}\PY{p}{)} \PY{o}{/} \PY{l+m+mi}{2}\PY{p}{,} \PY{n}{height}\PY{p}{)}\PY{p}{,}
                \PY{n}{xytext}\PY{o}{=}\PY{p}{(}\PY{l+m+mi}{0}\PY{p}{,} \PY{l+m+mi}{3}\PY{p}{)}\PY{p}{,}
                \PY{n}{textcoords}\PY{o}{=}\PY{l+s+s2}{\PYZdq{}}\PY{l+s+s2}{offset points}\PY{l+s+s2}{\PYZdq{}}\PY{p}{,}
                \PY{n}{ha}\PY{o}{=}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{center}\PY{l+s+s1}{\PYZsq{}}\PY{p}{,} \PY{n}{va}\PY{o}{=}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{bottom}\PY{l+s+s1}{\PYZsq{}}\PY{p}{)}
    
\PY{n}{\PYZus{}} \PY{o}{=} \PY{n}{plt}\PY{o}{.}\PY{n}{xticks}\PY{p}{(}\PY{n}{pay\PYZus{}day\PYZus{}sale}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{day}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{p}{)}
\PY{n}{fig}\PY{o}{.}\PY{n}{suptitle}\PY{p}{(}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{Frequency transaction product of PayDay sales campaign}\PY{l+s+s1}{\PYZsq{}}\PY{p}{,} \PY{n}{fontsize}\PY{o}{=}\PY{l+m+mi}{17}\PY{p}{)}
\PY{n}{plt}\PY{o}{.}\PY{n}{xlabel}\PY{p}{(}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{Day}\PY{l+s+s1}{\PYZsq{}}\PY{p}{,} \PY{n}{fontsize}\PY{o}{=}\PY{l+m+mi}{15}\PY{p}{)}
\PY{n}{plt}\PY{o}{.}\PY{n}{ylabel}\PY{p}{(}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{Count transaction of flash sale}\PY{l+s+s1}{\PYZsq{}}\PY{p}{,} \PY{n}{fontsize}\PY{o}{=}\PY{l+m+mi}{15}\PY{p}{)}
\end{Verbatim}
\end{tcolorbox}

            \begin{tcolorbox}[breakable, size=fbox, boxrule=.5pt, pad at break*=1mm, opacityfill=0]
\prompt{Out}{outcolor}{30}{\boxspacing}
\begin{Verbatim}[commandchars=\\\{\}]
Text(0, 0.5, 'Count transaction of flash sale')
\end{Verbatim}
\end{tcolorbox}
        
    \begin{center}
    \adjustimage{max size={0.9\linewidth}{0.9\paperheight}}{output_44_1.png}
    \end{center}
    { \hspace*{\fill} \\}
    
    \hypertarget{frequency-by-day-and-hour}{%
\subsubsection{3.3 Frequency by day and
hour}\label{frequency-by-day-and-hour}}

    \begin{tcolorbox}[breakable, size=fbox, boxrule=1pt, pad at break*=1mm,colback=cellbackground, colframe=cellborder]
\prompt{In}{incolor}{31}{\boxspacing}
\begin{Verbatim}[commandchars=\\\{\}]
\PY{n}{pay\PYZus{}day\PYZus{}sale} \PY{o}{=} \PY{n}{df}\PY{p}{[}\PY{p}{(}\PY{n}{df}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{day}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{o}{\PYZgt{}}\PY{o}{=}\PY{l+m+mi}{25}\PY{p}{)}\PY{o}{\PYZam{}}\PY{p}{(}\PY{n}{df}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{flash\PYZus{}sale}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{o}{.}\PY{n}{notna}\PY{p}{(}\PY{p}{)}\PY{p}{)}\PY{p}{]}\PY{o}{.}\PY{n}{drop\PYZus{}duplicates}\PY{p}{(}\PY{n}{subset}\PY{o}{=}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{flash\PYZus{}sale}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{p}{,}\PY{n}{keep}\PY{o}{=}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{first}\PY{l+s+s1}{\PYZsq{}}\PY{p}{)}\PY{o}{.}\PY{n}{groupby}\PY{p}{(}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{day}\PY{l+s+s1}{\PYZsq{}}\PY{p}{,}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{hour}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{p}{)}\PY{p}{[}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{hour}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{p}{]}\PY{o}{.}\PY{n}{count}\PY{p}{(}\PY{p}{)}\PY{o}{.}\PY{n}{rename}\PY{p}{(}\PY{n}{columns}\PY{o}{=}\PY{p}{\PYZob{}}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{hour}\PY{l+s+s1}{\PYZsq{}}\PY{p}{:}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{count}\PY{l+s+s1}{\PYZsq{}}\PY{p}{\PYZcb{}}\PY{p}{)}\PY{o}{.}\PY{n}{reset\PYZus{}index}\PY{p}{(}\PY{p}{)}
\PY{n}{pay\PYZus{}day\PYZus{}sale}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{day\PYZus{}hour}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]} \PY{o}{=} \PY{n}{pay\PYZus{}day\PYZus{}sale}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{day}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{o}{.}\PY{n}{astype}\PY{p}{(}\PY{n+nb}{str}\PY{p}{)} \PY{o}{+}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{\PYZhy{}}\PY{l+s+s1}{\PYZsq{}} \PY{o}{+}\PY{n}{pay\PYZus{}day\PYZus{}sale}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{hour}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{o}{.}\PY{n}{astype}\PY{p}{(}\PY{n+nb}{str}\PY{p}{)}
\PY{n}{pay\PYZus{}day\PYZus{}sale} \PY{o}{=} \PY{n}{pay\PYZus{}day\PYZus{}sale}\PY{o}{.}\PY{n}{sort\PYZus{}values}\PY{p}{(}\PY{n}{by}\PY{o}{=}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{count}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{p}{,}\PY{n}{ascending}\PY{o}{=}\PY{k+kc}{False}\PY{p}{)}\PY{o}{.}\PY{n}{reset\PYZus{}index}\PY{p}{(}\PY{p}{)}

\PY{n}{fig} \PY{o}{=} \PY{n}{plt}\PY{o}{.}\PY{n}{figure}\PY{p}{(}\PY{n}{figsize} \PY{o}{=} \PY{p}{(}\PY{l+m+mi}{15}\PY{p}{,} \PY{l+m+mi}{6}\PY{p}{)}\PY{p}{)}
\PY{n}{freq} \PY{o}{=} \PY{n}{plt}\PY{o}{.}\PY{n}{bar}\PY{p}{(}\PY{n}{pay\PYZus{}day\PYZus{}sale}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{day\PYZus{}hour}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{p}{[}\PY{p}{:}\PY{l+m+mi}{10}\PY{p}{]}\PY{p}{,} \PY{n}{pay\PYZus{}day\PYZus{}sale}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{count}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{p}{[}\PY{p}{:}\PY{l+m+mi}{10}\PY{p}{]}\PY{p}{,} \PY{n}{color} \PY{o}{=}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{c}\PY{l+s+s1}{\PYZsq{}}\PY{p}{,}
        \PY{n}{width} \PY{o}{=} \PY{l+m+mf}{0.4}\PY{p}{)}

\PY{k}{for} \PY{n}{f} \PY{o+ow}{in} \PY{n}{freq}\PY{p}{:}
    \PY{n}{height} \PY{o}{=} \PY{n}{f}\PY{o}{.}\PY{n}{get\PYZus{}height}\PY{p}{(}\PY{p}{)}
    \PY{n}{plt}\PY{o}{.}\PY{n}{annotate}\PY{p}{(}\PY{l+s+sa}{f}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+si}{\PYZob{}}\PY{n}{height}\PY{l+s+si}{:}\PY{l+s+s1}{.0f}\PY{l+s+si}{\PYZcb{}}\PY{l+s+s1}{\PYZsq{}}\PY{p}{,}
                \PY{n}{xy}\PY{o}{=}\PY{p}{(}\PY{n}{f}\PY{o}{.}\PY{n}{get\PYZus{}x}\PY{p}{(}\PY{p}{)} \PY{o}{+} \PY{n}{f}\PY{o}{.}\PY{n}{get\PYZus{}width}\PY{p}{(}\PY{p}{)} \PY{o}{/} \PY{l+m+mi}{2}\PY{p}{,} \PY{n}{height}\PY{p}{)}\PY{p}{,}
                \PY{n}{xytext}\PY{o}{=}\PY{p}{(}\PY{l+m+mi}{0}\PY{p}{,} \PY{l+m+mi}{3}\PY{p}{)}\PY{p}{,}
                \PY{n}{textcoords}\PY{o}{=}\PY{l+s+s2}{\PYZdq{}}\PY{l+s+s2}{offset points}\PY{l+s+s2}{\PYZdq{}}\PY{p}{,}
                \PY{n}{ha}\PY{o}{=}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{center}\PY{l+s+s1}{\PYZsq{}}\PY{p}{,} \PY{n}{va}\PY{o}{=}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{bottom}\PY{l+s+s1}{\PYZsq{}}\PY{p}{)}
    
\PY{n}{fig}\PY{o}{.}\PY{n}{suptitle}\PY{p}{(}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{Frequency transaction product of PayDay sales campaign}\PY{l+s+s1}{\PYZsq{}}\PY{p}{,} \PY{n}{fontsize}\PY{o}{=}\PY{l+m+mi}{17}\PY{p}{)}
\PY{n}{plt}\PY{o}{.}\PY{n}{xlabel}\PY{p}{(}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{Day and hour}\PY{l+s+s1}{\PYZsq{}}\PY{p}{,} \PY{n}{fontsize}\PY{o}{=}\PY{l+m+mi}{15}\PY{p}{)}
\PY{n}{plt}\PY{o}{.}\PY{n}{ylabel}\PY{p}{(}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{Count transaction of flash sale}\PY{l+s+s1}{\PYZsq{}}\PY{p}{,} \PY{n}{fontsize}\PY{o}{=}\PY{l+m+mi}{15}\PY{p}{)}
\end{Verbatim}
\end{tcolorbox}

            \begin{tcolorbox}[breakable, size=fbox, boxrule=.5pt, pad at break*=1mm, opacityfill=0]
\prompt{Out}{outcolor}{31}{\boxspacing}
\begin{Verbatim}[commandchars=\\\{\}]
Text(0, 0.5, 'Count transaction of flash sale')
\end{Verbatim}
\end{tcolorbox}
        
    \begin{center}
    \adjustimage{max size={0.9\linewidth}{0.9\paperheight}}{output_46_1.png}
    \end{center}
    { \hspace*{\fill} \\}
    
    แคมเปญการขาย PayDay

3.1 ชั่วโมงที่นิยมทำแฟลชเซลคือ 12:00 น. 00:00 น. 18:00 น. และ 15:00 น. ตามลำดับ
พฤติกรรมการขายส่วนใหญ่จะห่างกันทุกสามชั่วโมง

3.2 วันที่ขายแฟลชสูงสุดในช่วง Payday คือวันที่ 25 (วันแรกของแคมเปญการขาย PayDay),
30, 27 ตามลำดับ

3.3 วันและชั่วโมงการขายแฟลชสูงสุดในช่วง Payday คือ 25-00:00 น., 30-12:00 น.,
25-12:00 น., 27-12:00 น. ตามลำดับ

    \hypertarget{flash-sale-duration-time}{%
\section{4. Flash sale duration time}\label{flash-sale-duration-time}}

แต่ละแคมเปญส่วนมากทำแฟลชเซลกี่ชั่วโมงโดยเฉลี่ย

    \begin{tcolorbox}[breakable, size=fbox, boxrule=1pt, pad at break*=1mm,colback=cellbackground, colframe=cellborder]
\prompt{In}{incolor}{32}{\boxspacing}
\begin{Verbatim}[commandchars=\\\{\}]
\PY{k}{def} \PY{n+nf}{extract\PYZus{}duration}\PY{p}{(}\PY{n}{row}\PY{p}{)}\PY{p}{:}
    \PY{n}{flash\PYZus{}sale\PYZus{}dict} \PY{o}{=} \PY{n+nb}{eval}\PY{p}{(}\PY{n}{row}\PY{p}{)}
    \PY{n}{temp} \PY{o}{=} \PY{n}{datetime}\PY{o}{.}\PY{n}{fromtimestamp}\PY{p}{(}\PY{n}{flash\PYZus{}sale\PYZus{}dict}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{end\PYZus{}time}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{p}{)} \PY{o}{\PYZhy{}} \PY{n}{datetime}\PY{o}{.}\PY{n}{fromtimestamp}\PY{p}{(}\PY{n}{flash\PYZus{}sale\PYZus{}dict}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{start\PYZus{}time}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{p}{)}
    \PY{k}{return} \PY{n}{temp}\PY{o}{.}\PY{n}{seconds}\PY{o}{/}\PY{o}{/}\PY{l+m+mi}{3600}
\end{Verbatim}
\end{tcolorbox}

    \begin{tcolorbox}[breakable, size=fbox, boxrule=1pt, pad at break*=1mm,colback=cellbackground, colframe=cellborder]
\prompt{In}{incolor}{33}{\boxspacing}
\begin{Verbatim}[commandchars=\\\{\}]
\PY{n}{mega\PYZus{}sale\PYZus{}df}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{duration}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]} \PY{o}{=} \PY{n}{mega\PYZus{}sale\PYZus{}df}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{flash\PYZus{}sale}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{o}{.}\PY{n}{apply}\PY{p}{(}\PY{n}{extract\PYZus{}duration}\PY{p}{)}
\PY{n}{mega\PYZus{}sale\PYZus{}df}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{duration}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{o}{.}\PY{n}{mean}\PY{p}{(}\PY{p}{)}
\end{Verbatim}
\end{tcolorbox}

            \begin{tcolorbox}[breakable, size=fbox, boxrule=.5pt, pad at break*=1mm, opacityfill=0]
\prompt{Out}{outcolor}{33}{\boxspacing}
\begin{Verbatim}[commandchars=\\\{\}]
2.693877551020408
\end{Verbatim}
\end{tcolorbox}
        
    \begin{tcolorbox}[breakable, size=fbox, boxrule=1pt, pad at break*=1mm,colback=cellbackground, colframe=cellborder]
\prompt{In}{incolor}{34}{\boxspacing}
\begin{Verbatim}[commandchars=\\\{\}]
\PY{n}{mid\PYZus{}month\PYZus{}sale\PYZus{}df}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{duration}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]} \PY{o}{=} \PY{n}{mid\PYZus{}month\PYZus{}sale\PYZus{}df}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{flash\PYZus{}sale}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{o}{.}\PY{n}{apply}\PY{p}{(}\PY{n}{extract\PYZus{}duration}\PY{p}{)}
\PY{n}{mid\PYZus{}month\PYZus{}sale\PYZus{}df}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{duration}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{o}{.}\PY{n}{mean}\PY{p}{(}\PY{p}{)}
\end{Verbatim}
\end{tcolorbox}

            \begin{tcolorbox}[breakable, size=fbox, boxrule=.5pt, pad at break*=1mm, opacityfill=0]
\prompt{Out}{outcolor}{34}{\boxspacing}
\begin{Verbatim}[commandchars=\\\{\}]
3.5166666666666666
\end{Verbatim}
\end{tcolorbox}
        
    \begin{tcolorbox}[breakable, size=fbox, boxrule=1pt, pad at break*=1mm,colback=cellbackground, colframe=cellborder]
\prompt{In}{incolor}{35}{\boxspacing}
\begin{Verbatim}[commandchars=\\\{\}]
\PY{n}{pay\PYZus{}day\PYZus{}sale\PYZus{}df}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{duration}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]} \PY{o}{=} \PY{n}{pay\PYZus{}day\PYZus{}sale\PYZus{}df}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{flash\PYZus{}sale}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{o}{.}\PY{n}{apply}\PY{p}{(}\PY{n}{extract\PYZus{}duration}\PY{p}{)}
\PY{n}{pay\PYZus{}day\PYZus{}sale\PYZus{}df}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{duration}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{o}{.}\PY{n}{mean}\PY{p}{(}\PY{p}{)}
\end{Verbatim}
\end{tcolorbox}

            \begin{tcolorbox}[breakable, size=fbox, boxrule=.5pt, pad at break*=1mm, opacityfill=0]
\prompt{Out}{outcolor}{35}{\boxspacing}
\begin{Verbatim}[commandchars=\\\{\}]
7.529801324503311
\end{Verbatim}
\end{tcolorbox}
        
    \begin{tcolorbox}[breakable, size=fbox, boxrule=1pt, pad at break*=1mm,colback=cellbackground, colframe=cellborder]
\prompt{In}{incolor}{36}{\boxspacing}
\begin{Verbatim}[commandchars=\\\{\}]
\PY{n}{fig} \PY{o}{=} \PY{n}{plt}\PY{o}{.}\PY{n}{figure}\PY{p}{(}\PY{n}{figsize} \PY{o}{=} \PY{p}{(}\PY{l+m+mi}{15}\PY{p}{,} \PY{l+m+mi}{6}\PY{p}{)}\PY{p}{)}
\PY{n}{freq} \PY{o}{=} \PY{n}{plt}\PY{o}{.}\PY{n}{bar}\PY{p}{(}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{Mega campaign}\PY{l+s+s1}{\PYZsq{}}\PY{p}{,}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{Mid month campaign}\PY{l+s+s1}{\PYZsq{}}\PY{p}{,}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{PayDay campaign}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{p}{,}
        \PY{p}{[}\PY{n}{mega\PYZus{}sale\PYZus{}df}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{duration}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{o}{.}\PY{n}{mean}\PY{p}{(}\PY{p}{)}\PY{p}{,}\PY{n}{mid\PYZus{}month\PYZus{}sale\PYZus{}df}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{duration}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{o}{.}\PY{n}{mean}\PY{p}{(}\PY{p}{)}\PY{p}{,}\PY{n}{pay\PYZus{}day\PYZus{}sale\PYZus{}df}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{duration}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{o}{.}\PY{n}{mean}\PY{p}{(}\PY{p}{)}\PY{p}{]}\PY{p}{,} 
        \PY{n}{color} \PY{o}{=}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{c}\PY{l+s+s1}{\PYZsq{}}\PY{p}{,}
        \PY{n}{width} \PY{o}{=} \PY{l+m+mf}{0.4}\PY{p}{)}

\PY{k}{for} \PY{n}{f} \PY{o+ow}{in} \PY{n}{freq}\PY{p}{:}
    \PY{n}{height} \PY{o}{=} \PY{n}{f}\PY{o}{.}\PY{n}{get\PYZus{}height}\PY{p}{(}\PY{p}{)}
    \PY{n}{plt}\PY{o}{.}\PY{n}{annotate}\PY{p}{(}\PY{l+s+sa}{f}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+si}{\PYZob{}}\PY{n}{height}\PY{l+s+si}{:}\PY{l+s+s1}{.2f}\PY{l+s+si}{\PYZcb{}}\PY{l+s+s1}{ Hour}\PY{l+s+s1}{\PYZsq{}}\PY{p}{,}
                \PY{n}{xy}\PY{o}{=}\PY{p}{(}\PY{n}{f}\PY{o}{.}\PY{n}{get\PYZus{}x}\PY{p}{(}\PY{p}{)} \PY{o}{+} \PY{n}{f}\PY{o}{.}\PY{n}{get\PYZus{}width}\PY{p}{(}\PY{p}{)} \PY{o}{/} \PY{l+m+mi}{2}\PY{p}{,} \PY{n}{height}\PY{p}{)}\PY{p}{,}
                \PY{n}{xytext}\PY{o}{=}\PY{p}{(}\PY{l+m+mi}{0}\PY{p}{,} \PY{l+m+mi}{3}\PY{p}{)}\PY{p}{,}
                \PY{n}{textcoords}\PY{o}{=}\PY{l+s+s2}{\PYZdq{}}\PY{l+s+s2}{offset points}\PY{l+s+s2}{\PYZdq{}}\PY{p}{,}
                \PY{n}{ha}\PY{o}{=}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{center}\PY{l+s+s1}{\PYZsq{}}\PY{p}{,} \PY{n}{va}\PY{o}{=}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{bottom}\PY{l+s+s1}{\PYZsq{}}\PY{p}{)}
    
\PY{n}{fig}\PY{o}{.}\PY{n}{suptitle}\PY{p}{(}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{Duration times of Flash sale by sales campaign}\PY{l+s+s1}{\PYZsq{}}\PY{p}{,} \PY{n}{fontsize}\PY{o}{=}\PY{l+m+mi}{17}\PY{p}{)}
\PY{n}{plt}\PY{o}{.}\PY{n}{xlabel}\PY{p}{(}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{Sales Campaigns}\PY{l+s+s1}{\PYZsq{}}\PY{p}{,} \PY{n}{fontsize}\PY{o}{=}\PY{l+m+mi}{15}\PY{p}{)}
\PY{n}{plt}\PY{o}{.}\PY{n}{ylabel}\PY{p}{(}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{Duration time (Hours)}\PY{l+s+s1}{\PYZsq{}}\PY{p}{,} \PY{n}{fontsize}\PY{o}{=}\PY{l+m+mi}{15}\PY{p}{)}
\end{Verbatim}
\end{tcolorbox}

            \begin{tcolorbox}[breakable, size=fbox, boxrule=.5pt, pad at break*=1mm, opacityfill=0]
\prompt{Out}{outcolor}{36}{\boxspacing}
\begin{Verbatim}[commandchars=\\\{\}]
Text(0, 0.5, 'Duration time (Hours)')
\end{Verbatim}
\end{tcolorbox}
        
    \begin{center}
    \adjustimage{max size={0.9\linewidth}{0.9\paperheight}}{output_53_1.png}
    \end{center}
    { \hspace*{\fill} \\}
    
    PayDay มีการทำแฟลชเซลระยะเวลานานที่สุดคือประมาณ 8 ชั่วโมงต่อการทำแฟลชเซล1ครั้ง
รองลงมาด้วย Mid month แคมเปญ คือ4 ชั่วโมงและ Mega 3ชั่วโมง

จากการสำรวจข้อมูลพบว่า Mega sale
จะแฟลชเซลในระยะสั้นกว่าและมีจำนวนการแฟลชเซลบ่อยกว่า Mid month sale

    \hypertarget{pattern-of-the-flash-sale-hour-of-each-campaign.}{%
\subsection{5. Pattern of the flash sale hour of each
campaign.}\label{pattern-of-the-flash-sale-hour-of-each-campaign.}}

แต่ละแคมเปญมีพฤติกรรมการทำแฟลชเซลช่วงเวลาไหนเท่าไหร่บ้าง

    \begin{tcolorbox}[breakable, size=fbox, boxrule=1pt, pad at break*=1mm,colback=cellbackground, colframe=cellborder]
\prompt{In}{incolor}{37}{\boxspacing}
\begin{Verbatim}[commandchars=\\\{\}]
\PY{k}{def} \PY{n+nf}{groupby\PYZus{}time\PYZus{}series}\PY{p}{(}\PY{n}{df}\PY{p}{)}\PY{p}{:}
    \PY{n}{flash\PYZus{}hour\PYZus{}df}\PY{o}{=} \PY{n}{pd}\PY{o}{.}\PY{n}{DataFrame}\PY{p}{(}\PY{p}{)}
    \PY{n}{hour} \PY{o}{=} \PY{p}{[}\PY{p}{]}
    \PY{n}{modelid} \PY{o}{=} \PY{p}{[}\PY{p}{]}
    \PY{k}{for} \PY{n}{i} \PY{o+ow}{in} \PY{n+nb}{range}\PY{p}{(}\PY{n+nb}{len}\PY{p}{(}\PY{n}{df}\PY{p}{)}\PY{p}{)} \PY{p}{:}
        \PY{n}{fs\PYZus{}dict} \PY{o}{=} \PY{n+nb}{eval}\PY{p}{(}\PY{n}{df}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{flash\PYZus{}sale}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{o}{.}\PY{n}{loc}\PY{p}{[}\PY{n}{i}\PY{p}{]}\PY{p}{)}
        \PY{n}{fs\PYZus{}dict}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{start\PYZus{}time}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}
        \PY{k}{for} \PY{n}{h} \PY{o+ow}{in} \PY{n+nb}{range}\PY{p}{(}\PY{n+nb}{int}\PY{p}{(}\PY{n}{datetime}\PY{o}{.}\PY{n}{fromtimestamp}\PY{p}{(}\PY{n}{fs\PYZus{}dict}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{start\PYZus{}time}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{p}{)}\PY{o}{.}\PY{n}{strftime}\PY{p}{(}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{\PYZpc{}}\PY{l+s+s1}{H}\PY{l+s+s1}{\PYZsq{}}\PY{p}{)}\PY{p}{)}\PY{p}{,}\PY{n+nb}{int}\PY{p}{(}\PY{n}{datetime}\PY{o}{.}\PY{n}{fromtimestamp}\PY{p}{(}\PY{n}{fs\PYZus{}dict}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{end\PYZus{}time}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{p}{)}\PY{o}{.}\PY{n}{strftime}\PY{p}{(}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{\PYZpc{}}\PY{l+s+s1}{H}\PY{l+s+s1}{\PYZsq{}}\PY{p}{)}\PY{p}{)}\PY{o}{+}\PY{l+m+mi}{1}\PY{p}{)}\PY{p}{:}
            \PY{n}{modelid}\PY{o}{.}\PY{n}{append}\PY{p}{(}\PY{n}{df}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{modelid}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{o}{.}\PY{n}{loc}\PY{p}{[}\PY{n}{i}\PY{p}{]}\PY{p}{)}
            \PY{n}{hour}\PY{o}{.}\PY{n}{append}\PY{p}{(}\PY{n}{h}\PY{p}{)}
    \PY{n}{flash\PYZus{}hour\PYZus{}df}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{modelid}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]} \PY{o}{=} \PY{n}{modelid}
    \PY{n}{flash\PYZus{}hour\PYZus{}df}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{hour}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]} \PY{o}{=} \PY{n}{hour}
    \PY{n}{flash\PYZus{}hour\PYZus{}groupby} \PY{o}{=} \PY{n}{flash\PYZus{}hour\PYZus{}df}\PY{o}{.}\PY{n}{groupby}\PY{p}{(}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{hour}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{p}{)}\PY{p}{[}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{modelid}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{p}{]}\PY{o}{.}\PY{n}{count}\PY{p}{(}\PY{p}{)}\PY{o}{.}\PY{n}{reset\PYZus{}index}\PY{p}{(}\PY{p}{)}
    \PY{k}{for} \PY{n}{i} \PY{o+ow}{in} \PY{n+nb}{range}\PY{p}{(}\PY{l+m+mi}{0}\PY{p}{,}\PY{l+m+mi}{24}\PY{p}{)}\PY{p}{:}
        \PY{k}{if} \PY{n}{i} \PY{o+ow}{not} \PY{o+ow}{in} \PY{n}{flash\PYZus{}hour\PYZus{}groupby}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{hour}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{o}{.}\PY{n}{unique}\PY{p}{(}\PY{p}{)}\PY{o}{.}\PY{n}{tolist}\PY{p}{(}\PY{p}{)}\PY{p}{:}
\PY{c+c1}{\PYZsh{}             print(i)}
            \PY{n}{flash\PYZus{}hour\PYZus{}groupby} \PY{o}{=} \PY{n}{flash\PYZus{}hour\PYZus{}groupby}\PY{o}{.}\PY{n}{append}\PY{p}{(}\PY{n}{pd}\PY{o}{.}\PY{n}{Series}\PY{p}{(}\PY{p}{\PYZob{}}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{hour}\PY{l+s+s1}{\PYZsq{}}\PY{p}{:} \PY{n}{i}\PY{p}{,} \PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{modelid}\PY{l+s+s1}{\PYZsq{}}\PY{p}{:}\PY{l+m+mi}{0}\PY{p}{\PYZcb{}}\PY{p}{)}\PY{p}{,}\PY{n}{ignore\PYZus{}index}\PY{o}{=}\PY{k+kc}{True}\PY{p}{)}
    \PY{k}{return} \PY{n}{flash\PYZus{}hour\PYZus{}groupby}
\end{Verbatim}
\end{tcolorbox}

    \begin{tcolorbox}[breakable, size=fbox, boxrule=1pt, pad at break*=1mm,colback=cellbackground, colframe=cellborder]
\prompt{In}{incolor}{38}{\boxspacing}
\begin{Verbatim}[commandchars=\\\{\}]
\PY{n}{mega\PYZus{}sale\PYZus{}timeseries} \PY{o}{=}  \PY{n}{groupby\PYZus{}time\PYZus{}series}\PY{p}{(}\PY{n}{mega\PYZus{}sale\PYZus{}df}\PY{p}{)}
\PY{n}{mid\PYZus{}month\PYZus{}timeseries} \PY{o}{=}  \PY{n}{groupby\PYZus{}time\PYZus{}series}\PY{p}{(}\PY{n}{mid\PYZus{}month\PYZus{}sale\PYZus{}df}\PY{p}{)}
\PY{n}{pay\PYZus{}day\PYZus{}timeseries} \PY{o}{=}  \PY{n}{groupby\PYZus{}time\PYZus{}series}\PY{p}{(}\PY{n}{pay\PYZus{}day\PYZus{}sale\PYZus{}df}\PY{p}{)}
\end{Verbatim}
\end{tcolorbox}

    \begin{tcolorbox}[breakable, size=fbox, boxrule=1pt, pad at break*=1mm,colback=cellbackground, colframe=cellborder]
\prompt{In}{incolor}{39}{\boxspacing}
\begin{Verbatim}[commandchars=\\\{\}]
\PY{n}{fig} \PY{o}{=} \PY{n}{plt}\PY{o}{.}\PY{n}{figure}\PY{p}{(}\PY{n}{figsize} \PY{o}{=} \PY{p}{(}\PY{l+m+mi}{20}\PY{p}{,} \PY{l+m+mi}{10}\PY{p}{)}\PY{p}{)}
\PY{n}{plt}\PY{o}{.}\PY{n}{plot}\PY{p}{(}\PY{n}{mega\PYZus{}sale\PYZus{}timeseries}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{hour}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{p}{,} \PY{n}{mega\PYZus{}sale\PYZus{}timeseries}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{modelid}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{p}{,}\PY{n}{label}\PY{o}{=}\PY{l+s+s2}{\PYZdq{}}\PY{l+s+s2}{Mega campaign}\PY{l+s+s2}{\PYZdq{}}\PY{p}{)}
\PY{n}{plt}\PY{o}{.}\PY{n}{plot}\PY{p}{(}\PY{n}{mid\PYZus{}month\PYZus{}timeseries}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{hour}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{p}{,} \PY{n}{mid\PYZus{}month\PYZus{}timeseries}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{modelid}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{p}{,}\PY{n}{label}\PY{o}{=}\PY{l+s+s2}{\PYZdq{}}\PY{l+s+s2}{Mid month campaign}\PY{l+s+s2}{\PYZdq{}}\PY{p}{)}
\PY{n}{plt}\PY{o}{.}\PY{n}{plot}\PY{p}{(}\PY{n}{pay\PYZus{}day\PYZus{}timeseries}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{hour}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{p}{,} \PY{n}{pay\PYZus{}day\PYZus{}timeseries}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{modelid}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{p}{,}\PY{n}{label}\PY{o}{=}\PY{l+s+s2}{\PYZdq{}}\PY{l+s+s2}{PayDay campaign}\PY{l+s+s2}{\PYZdq{}}\PY{p}{)}
\PY{n}{\PYZus{}} \PY{o}{=} \PY{n}{plt}\PY{o}{.}\PY{n}{xticks}\PY{p}{(}\PY{n}{mega\PYZus{}sale\PYZus{}timeseries}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{hour}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{p}{)}
\PY{n}{plt}\PY{o}{.}\PY{n}{legend}\PY{p}{(}\PY{n}{loc}\PY{o}{=}\PY{l+s+s2}{\PYZdq{}}\PY{l+s+s2}{upper left}\PY{l+s+s2}{\PYZdq{}}\PY{p}{,}\PY{n}{prop}\PY{o}{=}\PY{p}{\PYZob{}}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{size}\PY{l+s+s1}{\PYZsq{}}\PY{p}{:}\PY{l+m+mi}{15}\PY{p}{\PYZcb{}}\PY{p}{)}
    
\PY{n}{fig}\PY{o}{.}\PY{n}{suptitle}\PY{p}{(}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{The frequency of flash sales in each hour by sales campaign}\PY{l+s+s1}{\PYZsq{}}\PY{p}{,} \PY{n}{fontsize}\PY{o}{=}\PY{l+m+mi}{17}\PY{p}{)}
\PY{n}{plt}\PY{o}{.}\PY{n}{xlabel}\PY{p}{(}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{Hours of the day}\PY{l+s+s1}{\PYZsq{}}\PY{p}{,} \PY{n}{fontsize}\PY{o}{=}\PY{l+m+mi}{15}\PY{p}{)}
\PY{n}{plt}\PY{o}{.}\PY{n}{ylabel}\PY{p}{(}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{Number of transactions}\PY{l+s+s1}{\PYZsq{}}\PY{p}{,} \PY{n}{fontsize}\PY{o}{=}\PY{l+m+mi}{15}\PY{p}{)}
\end{Verbatim}
\end{tcolorbox}

            \begin{tcolorbox}[breakable, size=fbox, boxrule=.5pt, pad at break*=1mm, opacityfill=0]
\prompt{Out}{outcolor}{39}{\boxspacing}
\begin{Verbatim}[commandchars=\\\{\}]
Text(0, 0.5, 'Number of transactions')
\end{Verbatim}
\end{tcolorbox}
        
    \begin{center}
    \adjustimage{max size={0.9\linewidth}{0.9\paperheight}}{output_58_1.png}
    \end{center}
    { \hspace*{\fill} \\}
    
    ภาพรวมของการขายแฟลชเป็นที่นิยมในช่วงเวลา 02:00 น.
(อาจเริ่มขายแฟลชเซลตั้งแต่เที่ยงคืนหรือ 01.00 น.) รองลงมาคือ 9.00 น., 12.00 น.,
14.00 น., 16.00 น., 18.00 น. ตามลำดับ

ตามแคมเปญ Mega Campaign และ Mid month Campaign จะมี flash sale
ในแต่ละช่วงใกล้เคียงกันและเน้นทำแฟลชเซลช่วงกลางคืน. สำหรับแคมเปญ Payday
จะมีรูปแบบที่แตกต่างไปคือจะมีการขายแฟลชมากที่สุดในตอนกลางวัน ที่เวลา 12:00 น.
และอีกครั้งเวลา 18:00 น.

    \hypertarget{explore-by-brand}{%
\section{6. Explore by Brand}\label{explore-by-brand}}

สำรวจแบรนด์สินค้าที่เป็น Official เทียบกับแบรนด์ Unofficial
ว่ามีพฤติกรรมการลดราคาในแต่ละแคมเปญแตกต่างกันหรือไม่

Explore the discounting behavior of brands selling on the platform.

    \begin{tcolorbox}[breakable, size=fbox, boxrule=1pt, pad at break*=1mm,colback=cellbackground, colframe=cellborder]
\prompt{In}{incolor}{40}{\boxspacing}
\begin{Verbatim}[commandchars=\\\{\}]
\PY{n}{brand} \PY{o}{=} \PY{p}{[}\PY{n}{i} \PY{k}{for} \PY{n}{i} \PY{o+ow}{in} \PY{n}{df}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{brand}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{o}{.}\PY{n}{dropna}\PY{p}{(}\PY{p}{)}\PY{o}{.}\PY{n}{unique}\PY{p}{(}\PY{p}{)}\PY{o}{.}\PY{n}{tolist}\PY{p}{(}\PY{p}{)}\PY{p}{]}

\PY{n}{brand\PYZus{}count} \PY{o}{=} \PY{p}{[}\PY{n+nb}{len}\PY{p}{(}\PY{n}{df}\PY{p}{[}\PY{n}{df}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{brand}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{o}{==}\PY{n}{i}\PY{p}{]}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{shopid}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{o}{.}\PY{n}{unique}\PY{p}{(}\PY{p}{)}\PY{p}{)} \PY{k}{for} \PY{n}{i} \PY{o+ow}{in} \PY{n}{brand}\PY{p}{]}
\PY{n}{brand\PYZus{}count}
\end{Verbatim}
\end{tcolorbox}

            \begin{tcolorbox}[breakable, size=fbox, boxrule=.5pt, pad at break*=1mm, opacityfill=0]
\prompt{Out}{outcolor}{40}{\boxspacing}
\begin{Verbatim}[commandchars=\\\{\}]
[9, 4, 3, 1, 1, 3, 2, 1]
\end{Verbatim}
\end{tcolorbox}
        
    \begin{tcolorbox}[breakable, size=fbox, boxrule=1pt, pad at break*=1mm,colback=cellbackground, colframe=cellborder]
\prompt{In}{incolor}{41}{\boxspacing}
\begin{Verbatim}[commandchars=\\\{\}]
\PY{n}{df\PYZus{}brand} \PY{o}{=} \PY{n}{pd}\PY{o}{.}\PY{n}{DataFrame}\PY{p}{(}\PY{p}{)}
\PY{n}{df\PYZus{}brand}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{brand}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]} \PY{o}{=} \PY{n}{brand}
\PY{n}{df\PYZus{}brand}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{countd\PYZus{}shopid}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]} \PY{o}{=} \PY{p}{[}\PY{n+nb}{len}\PY{p}{(}\PY{n}{df}\PY{p}{[}\PY{n}{df}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{brand}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{o}{==}\PY{n}{i}\PY{p}{]}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{shopid}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{o}{.}\PY{n}{unique}\PY{p}{(}\PY{p}{)}\PY{p}{)} \PY{k}{for} \PY{n}{i} \PY{o+ow}{in} \PY{n}{brand}\PY{p}{]}
\PY{n}{df\PYZus{}brand}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{count\PYZus{}shopid}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}  \PY{o}{=} \PY{p}{[}\PY{n+nb}{len}\PY{p}{(}\PY{n}{df}\PY{p}{[}\PY{n}{df}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{brand}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{o}{==}\PY{n}{i}\PY{p}{]}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{shopid}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{p}{)} \PY{k}{for} \PY{n}{i} \PY{o+ow}{in} \PY{n}{brand}\PY{p}{]}
\PY{n}{df\PYZus{}brand}
\end{Verbatim}
\end{tcolorbox}

            \begin{tcolorbox}[breakable, size=fbox, boxrule=.5pt, pad at break*=1mm, opacityfill=0]
\prompt{Out}{outcolor}{41}{\boxspacing}
\begin{Verbatim}[commandchars=\\\{\}]
                         brand  countd\_shopid  count\_shopid
0              Petkit(เพ็ทคิท)              9         11140
1            Amazfit (อเมซฟิต)              4          4417
2            Xiaomi(เสี่ยวมี่)              3          6529
3              iRobot(ไอโรบอท)              1          1082
4                Pando(แพนโด้)              1          2234
5               Haier(ไฮเออร์)              3          3027
6           Ecovacs(อีโคแวคส์)              2          1493
7  Mister Robot(มิสเตอร์โรบอต)              1           756
\end{Verbatim}
\end{tcolorbox}
        
    \begin{tcolorbox}[breakable, size=fbox, boxrule=1pt, pad at break*=1mm,colback=cellbackground, colframe=cellborder]
\prompt{In}{incolor}{42}{\boxspacing}
\begin{Verbatim}[commandchars=\\\{\}]
\PY{n}{fig} \PY{o}{=} \PY{n}{plt}\PY{o}{.}\PY{n}{figure}\PY{p}{(}\PY{n}{figsize} \PY{o}{=} \PY{p}{(}\PY{l+m+mi}{15}\PY{p}{,} \PY{l+m+mi}{10}\PY{p}{)}\PY{p}{)}
\PY{n}{label} \PY{o}{=} \PY{p}{[}\PY{n}{i}\PY{o}{.}\PY{n}{split}\PY{p}{(}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{(}\PY{l+s+s1}{\PYZsq{}}\PY{p}{)}\PY{p}{[}\PY{l+m+mi}{0}\PY{p}{]}\PY{o}{+}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{ (}\PY{l+s+s1}{\PYZsq{}}\PY{o}{+}\PY{n+nb}{str}\PY{p}{(}\PY{n}{brand\PYZus{}count}\PY{p}{[}\PY{n}{index}\PY{p}{]}\PY{p}{)}\PY{o}{+}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{)}\PY{l+s+s1}{\PYZsq{}} \PY{k}{for} \PY{n}{index}\PY{p}{,}\PY{n}{i} \PY{o+ow}{in} \PY{n+nb}{enumerate}\PY{p}{(}\PY{n}{brand}\PY{p}{)}\PY{p}{]}

\PY{n}{\PYZus{}} \PY{o}{=} \PY{n}{plt}\PY{o}{.}\PY{n}{pie}\PY{p}{(}\PY{n}{brand\PYZus{}count}\PY{p}{,} \PY{n}{labels} \PY{o}{=} \PY{n}{label} \PY{p}{,} \PY{n}{autopct}\PY{o}{=}\PY{k}{lambda} \PY{n}{p}\PY{p}{:} \PY{l+s+s1}{\PYZsq{}}\PY{l+s+si}{\PYZob{}:.2f\PYZcb{}}\PY{l+s+s1}{\PYZpc{}}\PY{l+s+s1}{\PYZsq{}}\PY{o}{.}\PY{n}{format}\PY{p}{(}\PY{n}{p}\PY{p}{)}\PY{p}{,} \PY{n}{textprops}\PY{o}{=}\PY{p}{\PYZob{}}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{fontsize}\PY{l+s+s1}{\PYZsq{}}\PY{p}{:} \PY{l+m+mi}{10}\PY{p}{\PYZcb{}}\PY{p}{,} \PY{n}{wedgeprops} \PY{o}{=} \PY{p}{\PYZob{}} \PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{linewidth}\PY{l+s+s1}{\PYZsq{}} \PY{p}{:} \PY{l+m+mi}{1}\PY{p}{,} \PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{edgecolor}\PY{l+s+s1}{\PYZsq{}} \PY{p}{:} \PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{white}\PY{l+s+s1}{\PYZsq{}} \PY{p}{\PYZcb{}}\PY{p}{,}\PY{n}{colors}\PY{o}{=}\PY{n}{sns}\PY{o}{.}\PY{n}{color\PYZus{}palette}\PY{p}{(}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{Set2}\PY{l+s+s1}{\PYZsq{}}\PY{p}{)}\PY{p}{)}
\end{Verbatim}
\end{tcolorbox}

    \begin{center}
    \adjustimage{max size={0.9\linewidth}{0.9\paperheight}}{output_63_0.png}
    \end{center}
    { \hspace*{\fill} \\}
    
    แบรนด์ Petkit มีจำนวนร้านค้ามากที่สุด (มีการแข่งขันที่สูง) รองลงมาคือ Amazfit

    \hypertarget{compare-between-official-shop-and-unofficial-shop}{%
\subsubsection{Compare between official shop and unofficial
shop}\label{compare-between-official-shop-and-unofficial-shop}}

    \begin{tcolorbox}[breakable, size=fbox, boxrule=1pt, pad at break*=1mm,colback=cellbackground, colframe=cellborder]
\prompt{In}{incolor}{43}{\boxspacing}
\begin{Verbatim}[commandchars=\\\{\}]
\PY{n}{official} \PY{o}{=} \PY{n}{df}\PY{p}{[}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{brand}\PY{l+s+s1}{\PYZsq{}}\PY{p}{,}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{shopid}\PY{l+s+s1}{\PYZsq{}}\PY{p}{,}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{is\PYZus{}official\PYZus{}shop}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{p}{]}\PY{o}{.}\PY{n}{drop\PYZus{}duplicates}\PY{p}{(}\PY{p}{)}
\PY{n}{official} \PY{o}{=} \PY{n}{official}\PY{o}{.}\PY{n}{groupby}\PY{p}{(}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{brand}\PY{l+s+s1}{\PYZsq{}}\PY{p}{,}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{is\PYZus{}official\PYZus{}shop}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{p}{)}\PY{p}{[}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{is\PYZus{}official\PYZus{}shop}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{p}{]}\PY{o}{.}\PY{n}{count}\PY{p}{(}\PY{p}{)}
\end{Verbatim}
\end{tcolorbox}

    \begin{tcolorbox}[breakable, size=fbox, boxrule=1pt, pad at break*=1mm,colback=cellbackground, colframe=cellborder]
\prompt{In}{incolor}{44}{\boxspacing}
\begin{Verbatim}[commandchars=\\\{\}]
\PY{n}{official} \PY{o}{=} \PY{n}{official}\PY{o}{.}\PY{n}{rename}\PY{p}{(}\PY{n}{columns}\PY{o}{=}\PY{p}{\PYZob{}}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{is\PYZus{}official\PYZus{}shop}\PY{l+s+s1}{\PYZsq{}}\PY{p}{:}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{count\PYZus{}ofiicial}\PY{l+s+s1}{\PYZsq{}}\PY{p}{\PYZcb{}}\PY{p}{)}\PY{o}{.}\PY{n}{reset\PYZus{}index}\PY{p}{(}\PY{p}{)}
\end{Verbatim}
\end{tcolorbox}

    \begin{tcolorbox}[breakable, size=fbox, boxrule=1pt, pad at break*=1mm,colback=cellbackground, colframe=cellborder]
\prompt{In}{incolor}{45}{\boxspacing}
\begin{Verbatim}[commandchars=\\\{\}]
\PY{n}{official}
\end{Verbatim}
\end{tcolorbox}

            \begin{tcolorbox}[breakable, size=fbox, boxrule=.5pt, pad at break*=1mm, opacityfill=0]
\prompt{Out}{outcolor}{45}{\boxspacing}
\begin{Verbatim}[commandchars=\\\{\}]
                          brand is\_official\_shop  count\_ofiicial
0             Amazfit (อเมซฟิต)                f               1
1             Amazfit (อเมซฟิต)                t               3
2            Ecovacs(อีโคแวคส์)                t               2
3                Haier(ไฮเออร์)                f               1
4                Haier(ไฮเออร์)                t               2
5   Mister Robot(มิสเตอร์โรบอต)                t               1
6                 Pando(แพนโด้)                t               1
7               Petkit(เพ็ทคิท)                f               5
8               Petkit(เพ็ทคิท)                t               4
9             Xiaomi(เสี่ยวมี่)                f               1
10            Xiaomi(เสี่ยวมี่)                t               2
11              iRobot(ไอโรบอท)                t               1
\end{Verbatim}
\end{tcolorbox}
        
    \begin{tcolorbox}[breakable, size=fbox, boxrule=1pt, pad at break*=1mm,colback=cellbackground, colframe=cellborder]
\prompt{In}{incolor}{46}{\boxspacing}
\begin{Verbatim}[commandchars=\\\{\}]
\PY{c+c1}{\PYZsh{} Fill null value of is\PYZus{}official\PYZus{}shop}
\PY{k}{for} \PY{n}{i} \PY{o+ow}{in} \PY{n}{official}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{brand}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{o}{.}\PY{n}{unique}\PY{p}{(}\PY{p}{)}\PY{o}{.}\PY{n}{tolist}\PY{p}{(}\PY{p}{)}\PY{p}{:}
    \PY{k}{if} \PY{n+nb}{len}\PY{p}{(}\PY{n}{official}\PY{p}{[}\PY{n}{official}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{brand}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{o}{==}\PY{n}{i}\PY{p}{]}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{is\PYZus{}official\PYZus{}shop}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{p}{)} \PY{o}{\PYZlt{}} \PY{l+m+mi}{2}\PY{p}{:}
        \PY{k}{if} \PY{n}{official}\PY{p}{[}\PY{n}{official}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{brand}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{o}{==}\PY{n}{i}\PY{p}{]}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{is\PYZus{}official\PYZus{}shop}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{o}{.}\PY{n}{values} \PY{o}{==} \PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{t}\PY{l+s+s1}{\PYZsq{}}\PY{p}{:}
            \PY{n}{official} \PY{o}{=} \PY{n}{official}\PY{o}{.}\PY{n}{append}\PY{p}{(}\PY{n}{pd}\PY{o}{.}\PY{n}{Series}\PY{p}{(}\PY{p}{\PYZob{}}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{brand}\PY{l+s+s1}{\PYZsq{}}\PY{p}{:} \PY{n}{i}\PY{p}{,} \PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{is\PYZus{}official\PYZus{}shop}\PY{l+s+s1}{\PYZsq{}}\PY{p}{:}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{f}\PY{l+s+s1}{\PYZsq{}}\PY{p}{,}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{count\PYZus{}ofiicial}\PY{l+s+s1}{\PYZsq{}}\PY{p}{:}\PY{l+m+mi}{0}\PY{p}{\PYZcb{}}\PY{p}{)}\PY{p}{,}\PY{n}{ignore\PYZus{}index}\PY{o}{=}\PY{k+kc}{True}\PY{p}{)}
        \PY{k}{else}\PY{p}{:}
            \PY{n}{official} \PY{o}{=} \PY{n}{official}\PY{o}{.}\PY{n}{append}\PY{p}{(}\PY{n}{pd}\PY{o}{.}\PY{n}{Series}\PY{p}{(}\PY{p}{\PYZob{}}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{brand}\PY{l+s+s1}{\PYZsq{}}\PY{p}{:} \PY{n}{i}\PY{p}{,} \PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{is\PYZus{}official\PYZus{}shop}\PY{l+s+s1}{\PYZsq{}}\PY{p}{:}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{t}\PY{l+s+s1}{\PYZsq{}}\PY{p}{,}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{count\PYZus{}ofiicial}\PY{l+s+s1}{\PYZsq{}}\PY{p}{:}\PY{l+m+mi}{0}\PY{p}{\PYZcb{}}\PY{p}{)}\PY{p}{,}\PY{n}{ignore\PYZus{}index}\PY{o}{=}\PY{k+kc}{True}\PY{p}{)}
\end{Verbatim}
\end{tcolorbox}

    \begin{tcolorbox}[breakable, size=fbox, boxrule=1pt, pad at break*=1mm,colback=cellbackground, colframe=cellborder]
\prompt{In}{incolor}{47}{\boxspacing}
\begin{Verbatim}[commandchars=\\\{\}]
\PY{n}{official} \PY{o}{=} \PY{n}{official}\PY{o}{.}\PY{n}{sort\PYZus{}values}\PY{p}{(}\PY{n}{by}\PY{o}{=}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{brand}\PY{l+s+s1}{\PYZsq{}}\PY{p}{,}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{is\PYZus{}official\PYZus{}shop}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{p}{,}\PY{n}{ascending}\PY{o}{=}\PY{k+kc}{True}\PY{p}{)}
\PY{n}{official}
\end{Verbatim}
\end{tcolorbox}

            \begin{tcolorbox}[breakable, size=fbox, boxrule=.5pt, pad at break*=1mm, opacityfill=0]
\prompt{Out}{outcolor}{47}{\boxspacing}
\begin{Verbatim}[commandchars=\\\{\}]
                          brand is\_official\_shop  count\_ofiicial
0             Amazfit (อเมซฟิต)                f               1
1             Amazfit (อเมซฟิต)                t               3
12           Ecovacs(อีโคแวคส์)                f               0
2            Ecovacs(อีโคแวคส์)                t               2
3                Haier(ไฮเออร์)                f               1
4                Haier(ไฮเออร์)                t               2
13  Mister Robot(มิสเตอร์โรบอต)                f               0
5   Mister Robot(มิสเตอร์โรบอต)                t               1
14                Pando(แพนโด้)                f               0
6                 Pando(แพนโด้)                t               1
7               Petkit(เพ็ทคิท)                f               5
8               Petkit(เพ็ทคิท)                t               4
9             Xiaomi(เสี่ยวมี่)                f               1
10            Xiaomi(เสี่ยวมี่)                t               2
15              iRobot(ไอโรบอท)                f               0
11              iRobot(ไอโรบอท)                t               1
\end{Verbatim}
\end{tcolorbox}
        
    \begin{tcolorbox}[breakable, size=fbox, boxrule=1pt, pad at break*=1mm,colback=cellbackground, colframe=cellborder]
\prompt{In}{incolor}{48}{\boxspacing}
\begin{Verbatim}[commandchars=\\\{\}]
\PY{k+kn}{from} \PY{n+nn}{matplotlib}\PY{n+nn}{.}\PY{n+nn}{pyplot} \PY{k+kn}{import} \PY{n}{figure}

\PY{n}{figure}\PY{p}{(}\PY{n}{figsize}\PY{o}{=}\PY{p}{(}\PY{l+m+mi}{15}\PY{p}{,} \PY{l+m+mi}{6}\PY{p}{)}\PY{p}{,} \PY{n}{dpi}\PY{o}{=}\PY{l+m+mi}{200}\PY{p}{)}

\PY{n}{x\PYZus{}labels} \PY{o}{=} \PY{p}{[}\PY{n}{i}\PY{o}{.}\PY{n}{split}\PY{p}{(}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{(}\PY{l+s+s1}{\PYZsq{}}\PY{p}{)}\PY{p}{[}\PY{l+m+mi}{0}\PY{p}{]} \PY{k}{for} \PY{n}{i} \PY{o+ow}{in} \PY{n}{official}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{brand}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{o}{.}\PY{n}{unique}\PY{p}{(}\PY{p}{)}\PY{o}{.}\PY{n}{tolist}\PY{p}{(}\PY{p}{)}\PY{p}{]}

\PY{n}{X\PYZus{}axis} \PY{o}{=} \PY{n}{np}\PY{o}{.}\PY{n}{arange}\PY{p}{(}\PY{n+nb}{len}\PY{p}{(}\PY{n}{x\PYZus{}labels}\PY{p}{)}\PY{p}{)}

\PY{n}{freq1} \PY{o}{=} \PY{n}{plt}\PY{o}{.}\PY{n}{bar}\PY{p}{(}\PY{n}{X\PYZus{}axis} \PY{o}{\PYZhy{}} \PY{l+m+mf}{0.2}\PY{p}{,} \PY{n}{official}\PY{p}{[}\PY{n}{official}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{is\PYZus{}official\PYZus{}shop}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{o}{==}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{t}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{count\PYZus{}ofiicial}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{p}{,} \PY{l+m+mf}{0.4}\PY{p}{,} \PY{n}{label} \PY{o}{=} \PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{Mall}\PY{l+s+s1}{\PYZsq{}}\PY{p}{)}
\PY{n}{freq2} \PY{o}{=} \PY{n}{plt}\PY{o}{.}\PY{n}{bar}\PY{p}{(}\PY{n}{X\PYZus{}axis} \PY{o}{+} \PY{l+m+mf}{0.2}\PY{p}{,} \PY{n}{official}\PY{p}{[}\PY{n}{official}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{is\PYZus{}official\PYZus{}shop}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{o}{==}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{f}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{count\PYZus{}ofiicial}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{p}{,} \PY{l+m+mf}{0.4}\PY{p}{,} \PY{n}{label} \PY{o}{=} \PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{Not Mall}\PY{l+s+s1}{\PYZsq{}}\PY{p}{,}\PY{n}{color} \PY{o}{=} \PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{orange}\PY{l+s+s1}{\PYZsq{}}\PY{p}{)}

\PY{k}{for} \PY{n}{f} \PY{o+ow}{in} \PY{n}{freq1}\PY{p}{:}
    \PY{n}{height} \PY{o}{=} \PY{n}{f}\PY{o}{.}\PY{n}{get\PYZus{}height}\PY{p}{(}\PY{p}{)}
    \PY{n}{plt}\PY{o}{.}\PY{n}{annotate}\PY{p}{(}\PY{l+s+sa}{f}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+si}{\PYZob{}}\PY{n}{height}\PY{l+s+si}{:}\PY{l+s+s1}{.0f}\PY{l+s+si}{\PYZcb{}}\PY{l+s+s1}{\PYZsq{}}\PY{p}{,}
                \PY{n}{xy}\PY{o}{=}\PY{p}{(}\PY{n}{f}\PY{o}{.}\PY{n}{get\PYZus{}x}\PY{p}{(}\PY{p}{)} \PY{o}{+} \PY{n}{f}\PY{o}{.}\PY{n}{get\PYZus{}width}\PY{p}{(}\PY{p}{)} \PY{o}{/} \PY{l+m+mi}{2}\PY{p}{,} \PY{n}{height}\PY{p}{)}\PY{p}{,}
                \PY{n}{xytext}\PY{o}{=}\PY{p}{(}\PY{l+m+mi}{0}\PY{p}{,} \PY{l+m+mi}{3}\PY{p}{)}\PY{p}{,}
                \PY{n}{textcoords}\PY{o}{=}\PY{l+s+s2}{\PYZdq{}}\PY{l+s+s2}{offset points}\PY{l+s+s2}{\PYZdq{}}\PY{p}{,}
                \PY{n}{ha}\PY{o}{=}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{center}\PY{l+s+s1}{\PYZsq{}}\PY{p}{,} \PY{n}{va}\PY{o}{=}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{bottom}\PY{l+s+s1}{\PYZsq{}}\PY{p}{)}

\PY{k}{for} \PY{n}{f} \PY{o+ow}{in} \PY{n}{freq2}\PY{p}{:}
    \PY{n}{height} \PY{o}{=} \PY{n}{f}\PY{o}{.}\PY{n}{get\PYZus{}height}\PY{p}{(}\PY{p}{)}
    \PY{n}{plt}\PY{o}{.}\PY{n}{annotate}\PY{p}{(}\PY{l+s+sa}{f}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+si}{\PYZob{}}\PY{n}{height}\PY{l+s+si}{:}\PY{l+s+s1}{.0f}\PY{l+s+si}{\PYZcb{}}\PY{l+s+s1}{\PYZsq{}}\PY{p}{,}
                \PY{n}{xy}\PY{o}{=}\PY{p}{(}\PY{n}{f}\PY{o}{.}\PY{n}{get\PYZus{}x}\PY{p}{(}\PY{p}{)} \PY{o}{+} \PY{n}{f}\PY{o}{.}\PY{n}{get\PYZus{}width}\PY{p}{(}\PY{p}{)} \PY{o}{/} \PY{l+m+mi}{2}\PY{p}{,} \PY{n}{height}\PY{p}{)}\PY{p}{,}
                \PY{n}{xytext}\PY{o}{=}\PY{p}{(}\PY{l+m+mi}{0}\PY{p}{,} \PY{l+m+mi}{3}\PY{p}{)}\PY{p}{,}
                \PY{n}{textcoords}\PY{o}{=}\PY{l+s+s2}{\PYZdq{}}\PY{l+s+s2}{offset points}\PY{l+s+s2}{\PYZdq{}}\PY{p}{,}
                \PY{n}{ha}\PY{o}{=}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{center}\PY{l+s+s1}{\PYZsq{}}\PY{p}{,} \PY{n}{va}\PY{o}{=}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{bottom}\PY{l+s+s1}{\PYZsq{}}\PY{p}{)}
    
\PY{n}{plt}\PY{o}{.}\PY{n}{title}\PY{p}{(}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{Propotion of mall shop and not mall shop by brand}\PY{l+s+s1}{\PYZsq{}}\PY{p}{,} \PY{n}{fontsize}\PY{o}{=}\PY{l+m+mi}{17}\PY{p}{)}
\PY{n}{plt}\PY{o}{.}\PY{n}{xlabel}\PY{p}{(}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{Brand}\PY{l+s+s1}{\PYZsq{}}\PY{p}{,} \PY{n}{fontsize}\PY{o}{=}\PY{l+m+mi}{15}\PY{p}{)}
\PY{n}{plt}\PY{o}{.}\PY{n}{ylabel}\PY{p}{(}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{Number of shops}\PY{l+s+s1}{\PYZsq{}}\PY{p}{,} \PY{n}{fontsize}\PY{o}{=}\PY{l+m+mi}{15}\PY{p}{)}

\PY{n}{plt}\PY{o}{.}\PY{n}{xticks}\PY{p}{(}\PY{n}{X\PYZus{}axis}\PY{p}{,}\PY{n}{x\PYZus{}labels}\PY{p}{)}
\PY{n}{plt}\PY{o}{.}\PY{n}{legend}\PY{p}{(}\PY{p}{)}
\PY{n}{plt}\PY{o}{.}\PY{n}{show}\PY{p}{(}\PY{p}{)}
\end{Verbatim}
\end{tcolorbox}

    \begin{center}
    \adjustimage{max size={0.9\linewidth}{0.9\paperheight}}{output_71_0.png}
    \end{center}
    { \hspace*{\fill} \\}
    
    ในข้อมูลที่เรามีจะมีแบรนด์ Petkit ที่มีจำนวน official Mall และ Unofficial
Mallที่พอๆกัน นอกจากนั้นจำนวนร้านส่วนใหญ่ในแต่ละแบรนด์จะเป็น official mall ส่วนใหญ่

    \hypertarget{campaign-styles-for-each-brand}{%
\subsection{Campaign styles for each
brand}\label{campaign-styles-for-each-brand}}

\hypertarget{official-brand}{%
\paragraph{Official Brand}\label{official-brand}}

    \begin{tcolorbox}[breakable, size=fbox, boxrule=1pt, pad at break*=1mm,colback=cellbackground, colframe=cellborder]
\prompt{In}{incolor}{49}{\boxspacing}
\begin{Verbatim}[commandchars=\\\{\}]
\PY{n}{count\PYZus{}overall\PYZus{}sale\PYZus{}mall} \PY{o}{=} \PY{n}{mega\PYZus{}sale\PYZus{}df}\PY{p}{[}\PY{n}{mega\PYZus{}sale\PYZus{}df}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{is\PYZus{}official\PYZus{}shop}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{o}{==}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{t}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{o}{.}\PY{n}{groupby}\PY{p}{(}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{brand}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{p}{)}\PY{p}{[}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{brand}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{p}{]}\PY{o}{.}\PY{n}{count}\PY{p}{(}\PY{p}{)}\PY{o}{.}\PY{n}{rename}\PY{p}{(}\PY{n}{columns}\PY{o}{=}\PY{p}{\PYZob{}}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{brand}\PY{l+s+s1}{\PYZsq{}}\PY{p}{:}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{count\PYZus{}mega\PYZus{}sale}\PY{l+s+s1}{\PYZsq{}}\PY{p}{\PYZcb{}}\PY{p}{)}\PY{o}{.}\PY{n}{reset\PYZus{}index}\PY{p}{(}\PY{p}{)}
\PY{n}{temp} \PY{o}{=} \PY{n}{mid\PYZus{}month\PYZus{}sale\PYZus{}df}\PY{p}{[}\PY{n}{mid\PYZus{}month\PYZus{}sale\PYZus{}df}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{is\PYZus{}official\PYZus{}shop}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{o}{==}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{t}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{o}{.}\PY{n}{groupby}\PY{p}{(}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{brand}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{p}{)}\PY{p}{[}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{brand}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{p}{]}\PY{o}{.}\PY{n}{count}\PY{p}{(}\PY{p}{)}\PY{o}{.}\PY{n}{rename}\PY{p}{(}\PY{n}{columns}\PY{o}{=}\PY{p}{\PYZob{}}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{brand}\PY{l+s+s1}{\PYZsq{}}\PY{p}{:}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{count\PYZus{}mid\PYZus{}month}\PY{l+s+s1}{\PYZsq{}}\PY{p}{\PYZcb{}}\PY{p}{)}\PY{o}{.}\PY{n}{reset\PYZus{}index}\PY{p}{(}\PY{p}{)}
\PY{n}{temp1} \PY{o}{=} \PY{n}{pay\PYZus{}day\PYZus{}sale\PYZus{}df}\PY{p}{[}\PY{n}{pay\PYZus{}day\PYZus{}sale\PYZus{}df}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{is\PYZus{}official\PYZus{}shop}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{o}{==}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{t}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{o}{.}\PY{n}{groupby}\PY{p}{(}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{brand}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{p}{)}\PY{p}{[}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{brand}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{p}{]}\PY{o}{.}\PY{n}{count}\PY{p}{(}\PY{p}{)}\PY{o}{.}\PY{n}{rename}\PY{p}{(}\PY{n}{columns}\PY{o}{=}\PY{p}{\PYZob{}}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{brand}\PY{l+s+s1}{\PYZsq{}}\PY{p}{:}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{count\PYZus{}pay\PYZus{}day}\PY{l+s+s1}{\PYZsq{}}\PY{p}{\PYZcb{}}\PY{p}{)}\PY{o}{.}\PY{n}{reset\PYZus{}index}\PY{p}{(}\PY{p}{)} 
\PY{n}{count\PYZus{}overall\PYZus{}sale\PYZus{}mall} \PY{o}{=} \PY{n}{pd}\PY{o}{.}\PY{n}{concat}\PY{p}{(}\PY{p}{[}\PY{n}{count\PYZus{}overall\PYZus{}sale\PYZus{}mall}\PY{p}{,}\PY{n}{temp}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{count\PYZus{}mid\PYZus{}month}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{p}{,}\PY{n}{temp1}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{count\PYZus{}pay\PYZus{}day}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{p}{]}\PY{p}{,}\PY{n}{axis}\PY{o}{=}\PY{l+m+mi}{1}\PY{p}{)}
\PY{n}{count\PYZus{}overall\PYZus{}sale\PYZus{}mall} \PY{o}{=} \PY{n}{pd}\PY{o}{.}\PY{n}{merge}\PY{p}{(}\PY{n}{count\PYZus{}overall\PYZus{}sale\PYZus{}mall}\PY{p}{,}\PY{n}{temp}\PY{p}{,}\PY{n}{how}\PY{o}{=}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{left}\PY{l+s+s1}{\PYZsq{}}\PY{p}{,}\PY{n}{on}\PY{o}{=}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{brand}\PY{l+s+s1}{\PYZsq{}}\PY{p}{)}\PY{o}{.}\PY{n}{drop}\PY{p}{(}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{count\PYZus{}mid\PYZus{}month\PYZus{}y}\PY{l+s+s1}{\PYZsq{}}\PY{p}{,}\PY{n}{axis}\PY{o}{=}\PY{l+m+mi}{1}\PY{p}{)}\PY{o}{.}\PY{n}{rename}\PY{p}{(}\PY{n}{columns}\PY{o}{=}\PY{p}{\PYZob{}}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{count\PYZus{}mid\PYZus{}month\PYZus{}x}\PY{l+s+s1}{\PYZsq{}}\PY{p}{:}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{count\PYZus{}mid\PYZus{}month}\PY{l+s+s1}{\PYZsq{}}\PY{p}{\PYZcb{}}\PY{p}{)}
\PY{n}{count\PYZus{}overall\PYZus{}sale\PYZus{}mall} \PY{o}{=} \PY{n}{pd}\PY{o}{.}\PY{n}{merge}\PY{p}{(}\PY{n}{count\PYZus{}overall\PYZus{}sale\PYZus{}mall}\PY{p}{,}\PY{n}{temp1}\PY{p}{,}\PY{n}{how}\PY{o}{=}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{left}\PY{l+s+s1}{\PYZsq{}}\PY{p}{,}\PY{n}{on}\PY{o}{=}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{brand}\PY{l+s+s1}{\PYZsq{}}\PY{p}{)}\PY{o}{.}\PY{n}{drop}\PY{p}{(}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{count\PYZus{}pay\PYZus{}day\PYZus{}x}\PY{l+s+s1}{\PYZsq{}}\PY{p}{,}\PY{n}{axis}\PY{o}{=}\PY{l+m+mi}{1}\PY{p}{)}\PY{o}{.}\PY{n}{rename}\PY{p}{(}\PY{n}{columns}\PY{o}{=}\PY{p}{\PYZob{}}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{count\PYZus{}pay\PYZus{}day\PYZus{}y}\PY{l+s+s1}{\PYZsq{}}\PY{p}{:}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{count\PYZus{}pay\PYZus{}day}\PY{l+s+s1}{\PYZsq{}}\PY{p}{\PYZcb{}}\PY{p}{)}
\PY{n}{count\PYZus{}overall\PYZus{}sale\PYZus{}mall} \PY{o}{=} \PY{n}{count\PYZus{}overall\PYZus{}sale\PYZus{}mall}\PY{o}{.}\PY{n}{fillna}\PY{p}{(}\PY{l+m+mi}{0}\PY{p}{)}
\PY{n}{count\PYZus{}overall\PYZus{}sale\PYZus{}mall}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{count\PYZus{}pay\PYZus{}day}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]} \PY{o}{=} \PY{n}{count\PYZus{}overall\PYZus{}sale\PYZus{}mall}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{count\PYZus{}pay\PYZus{}day}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{o}{.}\PY{n}{astype}\PY{p}{(}\PY{n+nb}{int}\PY{p}{)}
\end{Verbatim}
\end{tcolorbox}

    \begin{tcolorbox}[breakable, size=fbox, boxrule=1pt, pad at break*=1mm,colback=cellbackground, colframe=cellborder]
\prompt{In}{incolor}{50}{\boxspacing}
\begin{Verbatim}[commandchars=\\\{\}]
\PY{n}{count\PYZus{}overall\PYZus{}sale\PYZus{}mall}
\end{Verbatim}
\end{tcolorbox}

            \begin{tcolorbox}[breakable, size=fbox, boxrule=.5pt, pad at break*=1mm, opacityfill=0]
\prompt{Out}{outcolor}{50}{\boxspacing}
\begin{Verbatim}[commandchars=\\\{\}]
                         brand  count\_mega\_sale  count\_mid\_month  \textbackslash{}
0            Amazfit (อเมซฟิต)               18               13
1           Ecovacs(อีโคแวคส์)                6                2
2               Haier(ไฮเออร์)                4                5
3  Mister Robot(มิสเตอร์โรบอต)                6                3
4                Pando(แพนโด้)               14                5
5              Petkit(เพ็ทคิท)               24               17
6            Xiaomi(เสี่ยวมี่)               23               12

   count\_pay\_day
0             27
1              5
2             15
3              0
4             21
5             50
6             18
\end{Verbatim}
\end{tcolorbox}
        
    \hypertarget{unofficial-brand}{%
\paragraph{Unofficial brand}\label{unofficial-brand}}

    \begin{tcolorbox}[breakable, size=fbox, boxrule=1pt, pad at break*=1mm,colback=cellbackground, colframe=cellborder]
\prompt{In}{incolor}{51}{\boxspacing}
\begin{Verbatim}[commandchars=\\\{\}]
\PY{n}{count\PYZus{}overall\PYZus{}sale\PYZus{}not\PYZus{}mall} \PY{o}{=} \PY{n}{mega\PYZus{}sale\PYZus{}df}\PY{p}{[}\PY{n}{mega\PYZus{}sale\PYZus{}df}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{is\PYZus{}official\PYZus{}shop}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{o}{==}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{f}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{o}{.}\PY{n}{groupby}\PY{p}{(}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{brand}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{p}{)}\PY{p}{[}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{brand}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{p}{]}\PY{o}{.}\PY{n}{count}\PY{p}{(}\PY{p}{)}\PY{o}{.}\PY{n}{rename}\PY{p}{(}\PY{n}{columns}\PY{o}{=}\PY{p}{\PYZob{}}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{brand}\PY{l+s+s1}{\PYZsq{}}\PY{p}{:}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{count\PYZus{}mega\PYZus{}sale}\PY{l+s+s1}{\PYZsq{}}\PY{p}{\PYZcb{}}\PY{p}{)}\PY{o}{.}\PY{n}{reset\PYZus{}index}\PY{p}{(}\PY{p}{)}
\PY{n}{temp} \PY{o}{=} \PY{n}{mid\PYZus{}month\PYZus{}sale\PYZus{}df}\PY{p}{[}\PY{n}{mid\PYZus{}month\PYZus{}sale\PYZus{}df}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{is\PYZus{}official\PYZus{}shop}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{o}{==}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{f}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{o}{.}\PY{n}{groupby}\PY{p}{(}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{brand}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{p}{)}\PY{p}{[}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{brand}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{p}{]}\PY{o}{.}\PY{n}{count}\PY{p}{(}\PY{p}{)}\PY{o}{.}\PY{n}{rename}\PY{p}{(}\PY{n}{columns}\PY{o}{=}\PY{p}{\PYZob{}}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{brand}\PY{l+s+s1}{\PYZsq{}}\PY{p}{:}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{count\PYZus{}mid\PYZus{}month}\PY{l+s+s1}{\PYZsq{}}\PY{p}{\PYZcb{}}\PY{p}{)}\PY{o}{.}\PY{n}{reset\PYZus{}index}\PY{p}{(}\PY{p}{)}
\PY{n}{temp1} \PY{o}{=} \PY{n}{pay\PYZus{}day\PYZus{}sale\PYZus{}df}\PY{p}{[}\PY{n}{pay\PYZus{}day\PYZus{}sale\PYZus{}df}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{is\PYZus{}official\PYZus{}shop}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{o}{==}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{f}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{o}{.}\PY{n}{groupby}\PY{p}{(}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{brand}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{p}{)}\PY{p}{[}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{brand}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{p}{]}\PY{o}{.}\PY{n}{count}\PY{p}{(}\PY{p}{)}\PY{o}{.}\PY{n}{rename}\PY{p}{(}\PY{n}{columns}\PY{o}{=}\PY{p}{\PYZob{}}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{brand}\PY{l+s+s1}{\PYZsq{}}\PY{p}{:}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{count\PYZus{}pay\PYZus{}day}\PY{l+s+s1}{\PYZsq{}}\PY{p}{\PYZcb{}}\PY{p}{)}\PY{o}{.}\PY{n}{reset\PYZus{}index}\PY{p}{(}\PY{p}{)} 
\PY{n}{count\PYZus{}overall\PYZus{}sale\PYZus{}not\PYZus{}mall} \PY{o}{=} \PY{n}{pd}\PY{o}{.}\PY{n}{concat}\PY{p}{(}\PY{p}{[}\PY{n}{count\PYZus{}overall\PYZus{}sale\PYZus{}not\PYZus{}mall}\PY{p}{,}\PY{n}{temp}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{count\PYZus{}mid\PYZus{}month}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{p}{,}\PY{n}{temp1}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{count\PYZus{}pay\PYZus{}day}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{p}{]}\PY{p}{,}\PY{n}{axis}\PY{o}{=}\PY{l+m+mi}{1}\PY{p}{)}
\PY{n}{count\PYZus{}overall\PYZus{}sale\PYZus{}not\PYZus{}mall} \PY{o}{=} \PY{n}{pd}\PY{o}{.}\PY{n}{merge}\PY{p}{(}\PY{n}{count\PYZus{}overall\PYZus{}sale\PYZus{}not\PYZus{}mall}\PY{p}{,}\PY{n}{temp}\PY{p}{,}\PY{n}{how}\PY{o}{=}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{left}\PY{l+s+s1}{\PYZsq{}}\PY{p}{,}\PY{n}{on}\PY{o}{=}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{brand}\PY{l+s+s1}{\PYZsq{}}\PY{p}{)}\PY{o}{.}\PY{n}{drop}\PY{p}{(}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{count\PYZus{}mid\PYZus{}month\PYZus{}y}\PY{l+s+s1}{\PYZsq{}}\PY{p}{,}\PY{n}{axis}\PY{o}{=}\PY{l+m+mi}{1}\PY{p}{)}\PY{o}{.}\PY{n}{rename}\PY{p}{(}\PY{n}{columns}\PY{o}{=}\PY{p}{\PYZob{}}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{count\PYZus{}mid\PYZus{}month\PYZus{}x}\PY{l+s+s1}{\PYZsq{}}\PY{p}{:}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{count\PYZus{}mid\PYZus{}month}\PY{l+s+s1}{\PYZsq{}}\PY{p}{\PYZcb{}}\PY{p}{)}
\PY{n}{count\PYZus{}overall\PYZus{}sale\PYZus{}not\PYZus{}mall} \PY{o}{=} \PY{n}{pd}\PY{o}{.}\PY{n}{merge}\PY{p}{(}\PY{n}{count\PYZus{}overall\PYZus{}sale\PYZus{}not\PYZus{}mall}\PY{p}{,}\PY{n}{temp1}\PY{p}{,}\PY{n}{how}\PY{o}{=}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{left}\PY{l+s+s1}{\PYZsq{}}\PY{p}{,}\PY{n}{on}\PY{o}{=}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{brand}\PY{l+s+s1}{\PYZsq{}}\PY{p}{)}\PY{o}{.}\PY{n}{drop}\PY{p}{(}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{count\PYZus{}pay\PYZus{}day\PYZus{}x}\PY{l+s+s1}{\PYZsq{}}\PY{p}{,}\PY{n}{axis}\PY{o}{=}\PY{l+m+mi}{1}\PY{p}{)}\PY{o}{.}\PY{n}{rename}\PY{p}{(}\PY{n}{columns}\PY{o}{=}\PY{p}{\PYZob{}}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{count\PYZus{}pay\PYZus{}day\PYZus{}y}\PY{l+s+s1}{\PYZsq{}}\PY{p}{:}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{count\PYZus{}pay\PYZus{}day}\PY{l+s+s1}{\PYZsq{}}\PY{p}{\PYZcb{}}\PY{p}{)}
\PY{n}{count\PYZus{}overall\PYZus{}sale\PYZus{}not\PYZus{}mall} \PY{o}{=} \PY{n}{count\PYZus{}overall\PYZus{}sale\PYZus{}not\PYZus{}mall}\PY{o}{.}\PY{n}{fillna}\PY{p}{(}\PY{l+m+mi}{0}\PY{p}{)}
\PY{n}{count\PYZus{}overall\PYZus{}sale\PYZus{}not\PYZus{}mall}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{count\PYZus{}pay\PYZus{}day}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]} \PY{o}{=} \PY{n}{count\PYZus{}overall\PYZus{}sale\PYZus{}not\PYZus{}mall}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{count\PYZus{}pay\PYZus{}day}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{o}{.}\PY{n}{astype}\PY{p}{(}\PY{n+nb}{int}\PY{p}{)}
\end{Verbatim}
\end{tcolorbox}

    \begin{tcolorbox}[breakable, size=fbox, boxrule=1pt, pad at break*=1mm,colback=cellbackground, colframe=cellborder]
\prompt{In}{incolor}{52}{\boxspacing}
\begin{Verbatim}[commandchars=\\\{\}]
\PY{n}{count\PYZus{}overall\PYZus{}sale\PYZus{}not\PYZus{}mall}
\end{Verbatim}
\end{tcolorbox}

            \begin{tcolorbox}[breakable, size=fbox, boxrule=.5pt, pad at break*=1mm, opacityfill=0]
\prompt{Out}{outcolor}{52}{\boxspacing}
\begin{Verbatim}[commandchars=\\\{\}]
             brand  count\_mega\_sale  count\_mid\_month  count\_pay\_day
0  Petkit(เพ็ทคิท)                3                3             15
\end{Verbatim}
\end{tcolorbox}
        
    \begin{tcolorbox}[breakable, size=fbox, boxrule=1pt, pad at break*=1mm,colback=cellbackground, colframe=cellborder]
\prompt{In}{incolor}{53}{\boxspacing}
\begin{Verbatim}[commandchars=\\\{\}]
\PY{c+c1}{\PYZsh{} figure(figsize=(20, 10), dpi=200)}

\PY{n}{fig}\PY{p}{,} \PY{p}{(}\PY{n}{a1}\PY{p}{,} \PY{n}{a2}\PY{p}{)} \PY{o}{=} \PY{n}{plt}\PY{o}{.}\PY{n}{subplots}\PY{p}{(}\PY{l+m+mi}{1}\PY{p}{,} \PY{l+m+mi}{2}\PY{p}{,}\PY{n}{sharey}\PY{o}{=}\PY{k+kc}{True}\PY{p}{,}\PY{n}{figsize}\PY{o}{=}\PY{p}{(}\PY{l+m+mi}{20}\PY{p}{,} \PY{l+m+mi}{15}\PY{p}{)}\PY{p}{,} \PY{n}{dpi}\PY{o}{=}\PY{l+m+mi}{200}\PY{p}{,}\PY{n}{gridspec\PYZus{}kw}\PY{o}{=}\PY{p}{\PYZob{}}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{width\PYZus{}ratios}\PY{l+s+s1}{\PYZsq{}}\PY{p}{:} \PY{p}{[}\PY{l+m+mi}{3}\PY{p}{,} \PY{l+m+mf}{0.5}\PY{p}{]}\PY{p}{\PYZcb{}}\PY{p}{)}
\PY{n}{a2}\PY{o}{.}\PY{n}{yaxis}\PY{o}{.}\PY{n}{set\PYZus{}tick\PYZus{}params}\PY{p}{(}\PY{n}{which}\PY{o}{=}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{both}\PY{l+s+s1}{\PYZsq{}}\PY{p}{,} \PY{n}{labelbottom}\PY{o}{=}\PY{k+kc}{True}\PY{p}{)}

\PY{n}{label} \PY{o}{=} \PY{p}{[}\PY{n}{i}\PY{o}{.}\PY{n}{split}\PY{p}{(}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{(}\PY{l+s+s1}{\PYZsq{}}\PY{p}{)}\PY{p}{[}\PY{l+m+mi}{0}\PY{p}{]} \PY{k}{for} \PY{n}{i} \PY{o+ow}{in} \PY{n}{count\PYZus{}overall\PYZus{}sale\PYZus{}mall}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{brand}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{p}{]}
\PY{n}{ax1} \PY{o}{=} \PY{n}{a1}\PY{o}{.}\PY{n}{bar}\PY{p}{(}\PY{n}{label}\PY{p}{,} \PY{n}{count\PYZus{}overall\PYZus{}sale\PYZus{}mall}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{count\PYZus{}mega\PYZus{}sale}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{p}{,} \PY{n}{color}\PY{o}{=}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{lightsalmon}\PY{l+s+s1}{\PYZsq{}}\PY{p}{,} \PY{n}{label}\PY{o}{=}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{Mega sale campaign}\PY{l+s+s1}{\PYZsq{}}\PY{p}{)}
\PY{n}{ax2} \PY{o}{=} \PY{n}{a1}\PY{o}{.}\PY{n}{bar}\PY{p}{(}\PY{n}{label}\PY{p}{,} \PY{n}{count\PYZus{}overall\PYZus{}sale\PYZus{}mall}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{count\PYZus{}mid\PYZus{}month}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{p}{,} \PY{n}{bottom}\PY{o}{=}\PY{n}{count\PYZus{}overall\PYZus{}sale\PYZus{}mall}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{count\PYZus{}mega\PYZus{}sale}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{p}{,} \PY{n}{color}\PY{o}{=}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{lightblue}\PY{l+s+s1}{\PYZsq{}}\PY{p}{,} \PY{n}{label}\PY{o}{=}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{Mid Month sale campaign}\PY{l+s+s1}{\PYZsq{}}\PY{p}{)}
\PY{n}{ax3} \PY{o}{=} \PY{n}{a1}\PY{o}{.}\PY{n}{bar}\PY{p}{(}\PY{n}{label}\PY{p}{,} \PY{n}{count\PYZus{}overall\PYZus{}sale\PYZus{}mall}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{count\PYZus{}pay\PYZus{}day}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{p}{,} \PY{n}{bottom}\PY{o}{=}\PY{n}{count\PYZus{}overall\PYZus{}sale\PYZus{}mall}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{count\PYZus{}mega\PYZus{}sale}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{o}{+}\PY{n}{count\PYZus{}overall\PYZus{}sale\PYZus{}mall}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{count\PYZus{}mid\PYZus{}month}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{p}{,} \PY{n}{color}\PY{o}{=}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{pink}\PY{l+s+s1}{\PYZsq{}}\PY{p}{,}\PY{n}{label}\PY{o}{=}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{PayDay sale campaign}\PY{l+s+s1}{\PYZsq{}}\PY{p}{)}
\PY{n}{a1}\PY{o}{.}\PY{n}{set\PYZus{}title}\PY{p}{(}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{Number of Items in Official Mall Brand}\PY{l+s+s1}{\PYZsq{}}\PY{p}{,} \PY{n}{size}\PY{o}{=}\PY{l+m+mi}{20}\PY{p}{)}
\PY{n}{a1}\PY{o}{.}\PY{n}{set\PYZus{}xlabel}\PY{p}{(}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{Brand}\PY{l+s+s1}{\PYZsq{}}\PY{p}{,} \PY{n}{size}\PY{o}{=}\PY{l+m+mi}{20}\PY{p}{)}
\PY{n}{a1}\PY{o}{.}\PY{n}{set\PYZus{}ylabel}\PY{p}{(}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{Number of items}\PY{l+s+s1}{\PYZsq{}}\PY{p}{,} \PY{n}{size}\PY{o}{=}\PY{l+m+mi}{20}\PY{p}{)}

\PY{k}{for} \PY{n}{r1}\PY{p}{,} \PY{n}{r2}\PY{p}{,} \PY{n}{r3} \PY{o+ow}{in} \PY{n+nb}{zip}\PY{p}{(}\PY{n}{ax1}\PY{p}{,} \PY{n}{ax2}\PY{p}{,} \PY{n}{ax3}\PY{p}{)}\PY{p}{:}
    \PY{n}{h1} \PY{o}{=} \PY{n}{r1}\PY{o}{.}\PY{n}{get\PYZus{}height}\PY{p}{(}\PY{p}{)}
    \PY{n}{h2} \PY{o}{=} \PY{n}{r2}\PY{o}{.}\PY{n}{get\PYZus{}height}\PY{p}{(}\PY{p}{)}
    \PY{n}{h3} \PY{o}{=} \PY{n}{r3}\PY{o}{.}\PY{n}{get\PYZus{}height}\PY{p}{(}\PY{p}{)}

    \PY{n}{a1}\PY{o}{.}\PY{n}{text}\PY{p}{(}\PY{n}{r1}\PY{o}{.}\PY{n}{get\PYZus{}x}\PY{p}{(}\PY{p}{)} \PY{o}{+} \PY{n}{r1}\PY{o}{.}\PY{n}{get\PYZus{}width}\PY{p}{(}\PY{p}{)} \PY{o}{/} \PY{l+m+mf}{2.}\PY{p}{,} \PY{n}{h1} \PY{o}{/} \PY{l+m+mf}{2.}\PY{p}{,} \PY{l+s+s2}{\PYZdq{}}\PY{l+s+si}{\PYZob{}0:.2f\PYZcb{}}\PY{l+s+s2}{\PYZpc{}}\PY{l+s+s2}{\PYZdq{}}\PY{o}{.}\PY{n}{format}\PY{p}{(}\PY{p}{(}\PY{n}{h1}\PY{o}{/}\PY{p}{(}\PY{n}{h1}\PY{o}{+}\PY{n}{h2}\PY{o}{+}\PY{n}{h3}\PY{p}{)}\PY{p}{)}\PY{o}{*}\PY{l+m+mi}{100}\PY{p}{)}\PY{p}{,} \PY{n}{ha}\PY{o}{=}\PY{l+s+s2}{\PYZdq{}}\PY{l+s+s2}{center}\PY{l+s+s2}{\PYZdq{}}\PY{p}{,} \PY{n}{va}\PY{o}{=}\PY{l+s+s2}{\PYZdq{}}\PY{l+s+s2}{center}\PY{l+s+s2}{\PYZdq{}}\PY{p}{,} \PY{n}{color}\PY{o}{=}\PY{l+s+s2}{\PYZdq{}}\PY{l+s+s2}{black}\PY{l+s+s2}{\PYZdq{}}\PY{p}{,} \PY{n}{fontsize}\PY{o}{=}\PY{l+m+mi}{14}\PY{p}{)}
    \PY{n}{a1}\PY{o}{.}\PY{n}{text}\PY{p}{(}\PY{n}{r2}\PY{o}{.}\PY{n}{get\PYZus{}x}\PY{p}{(}\PY{p}{)} \PY{o}{+} \PY{n}{r2}\PY{o}{.}\PY{n}{get\PYZus{}width}\PY{p}{(}\PY{p}{)} \PY{o}{/} \PY{l+m+mf}{2.}\PY{p}{,} \PY{n}{h1} \PY{o}{+} \PY{n}{h2} \PY{o}{/} \PY{l+m+mf}{2.}\PY{p}{,} \PY{l+s+s2}{\PYZdq{}}\PY{l+s+si}{\PYZob{}0:.2f\PYZcb{}}\PY{l+s+s2}{\PYZpc{}}\PY{l+s+s2}{\PYZdq{}}\PY{o}{.}\PY{n}{format}\PY{p}{(}\PY{p}{(}\PY{n}{h2}\PY{o}{/}\PY{p}{(}\PY{n}{h1}\PY{o}{+}\PY{n}{h2}\PY{o}{+}\PY{n}{h3}\PY{p}{)}\PY{p}{)}\PY{o}{*}\PY{l+m+mi}{100}\PY{p}{)}\PY{p}{,} \PY{n}{ha}\PY{o}{=}\PY{l+s+s2}{\PYZdq{}}\PY{l+s+s2}{center}\PY{l+s+s2}{\PYZdq{}}\PY{p}{,} \PY{n}{va}\PY{o}{=}\PY{l+s+s2}{\PYZdq{}}\PY{l+s+s2}{center}\PY{l+s+s2}{\PYZdq{}}\PY{p}{,} \PY{n}{color}\PY{o}{=}\PY{l+s+s2}{\PYZdq{}}\PY{l+s+s2}{black}\PY{l+s+s2}{\PYZdq{}}\PY{p}{,} \PY{n}{fontsize}\PY{o}{=}\PY{l+m+mi}{14}\PY{p}{)}
    \PY{n}{a1}\PY{o}{.}\PY{n}{text}\PY{p}{(}\PY{n}{r3}\PY{o}{.}\PY{n}{get\PYZus{}x}\PY{p}{(}\PY{p}{)} \PY{o}{+} \PY{n}{r2}\PY{o}{.}\PY{n}{get\PYZus{}width}\PY{p}{(}\PY{p}{)} \PY{o}{/} \PY{l+m+mf}{2.}\PY{p}{,} \PY{n}{h1} \PY{o}{+} \PY{n}{h2} \PY{o}{+} \PY{n}{h3} \PY{o}{/} \PY{l+m+mf}{2.}\PY{p}{,} \PY{l+s+s2}{\PYZdq{}}\PY{l+s+si}{\PYZob{}0:.2f\PYZcb{}}\PY{l+s+s2}{\PYZpc{}}\PY{l+s+s2}{\PYZdq{}}\PY{o}{.}\PY{n}{format}\PY{p}{(}\PY{p}{(}\PY{n}{h3}\PY{o}{/}\PY{p}{(}\PY{n}{h1}\PY{o}{+}\PY{n}{h2}\PY{o}{+}\PY{n}{h3}\PY{p}{)}\PY{p}{)}\PY{o}{*}\PY{l+m+mi}{100}\PY{p}{)}\PY{p}{,} \PY{n}{ha}\PY{o}{=}\PY{l+s+s2}{\PYZdq{}}\PY{l+s+s2}{center}\PY{l+s+s2}{\PYZdq{}}\PY{p}{,} \PY{n}{va}\PY{o}{=}\PY{l+s+s2}{\PYZdq{}}\PY{l+s+s2}{center}\PY{l+s+s2}{\PYZdq{}}\PY{p}{,} \PY{n}{color}\PY{o}{=}\PY{l+s+s2}{\PYZdq{}}\PY{l+s+s2}{black}\PY{l+s+s2}{\PYZdq{}}\PY{p}{,} \PY{n}{fontsize}\PY{o}{=}\PY{l+m+mi}{14}\PY{p}{)}

\PY{n}{a1}\PY{o}{.}\PY{n}{legend}\PY{p}{(}\PY{n}{prop}\PY{o}{=}\PY{p}{\PYZob{}}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{size}\PY{l+s+s1}{\PYZsq{}}\PY{p}{:} \PY{l+m+mi}{15}\PY{p}{\PYZcb{}}\PY{p}{)}

\PY{c+c1}{\PYZsh{} a = plt.show()}


\PY{n}{label} \PY{o}{=} \PY{p}{[}\PY{n}{i}\PY{o}{.}\PY{n}{split}\PY{p}{(}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{(}\PY{l+s+s1}{\PYZsq{}}\PY{p}{)}\PY{p}{[}\PY{l+m+mi}{0}\PY{p}{]} \PY{k}{for} \PY{n}{i} \PY{o+ow}{in} \PY{n}{count\PYZus{}overall\PYZus{}sale\PYZus{}not\PYZus{}mall}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{brand}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{p}{]}
\PY{n}{ax1} \PY{o}{=} \PY{n}{a2}\PY{o}{.}\PY{n}{bar}\PY{p}{(}\PY{n}{label}\PY{p}{,} \PY{n}{count\PYZus{}overall\PYZus{}sale\PYZus{}not\PYZus{}mall}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{count\PYZus{}mega\PYZus{}sale}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{p}{,} \PY{n}{color}\PY{o}{=}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{lightsalmon}\PY{l+s+s1}{\PYZsq{}}\PY{p}{,} \PY{n}{label} \PY{o}{=} \PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{Mega sale campaign}\PY{l+s+s1}{\PYZsq{}}\PY{p}{)}
\PY{n}{ax2} \PY{o}{=} \PY{n}{a2}\PY{o}{.}\PY{n}{bar}\PY{p}{(}\PY{n}{label}\PY{p}{,} \PY{n}{count\PYZus{}overall\PYZus{}sale\PYZus{}not\PYZus{}mall}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{count\PYZus{}mid\PYZus{}month}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{p}{,} \PY{n}{bottom}\PY{o}{=}\PY{n}{count\PYZus{}overall\PYZus{}sale\PYZus{}not\PYZus{}mall}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{count\PYZus{}mega\PYZus{}sale}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{p}{,} \PY{n}{color}\PY{o}{=}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{lightblue}\PY{l+s+s1}{\PYZsq{}}\PY{p}{,} \PY{n}{label} \PY{o}{=} \PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{Mid month sale campaign}\PY{l+s+s1}{\PYZsq{}}\PY{p}{)}
\PY{n}{ax3} \PY{o}{=} \PY{n}{a2}\PY{o}{.}\PY{n}{bar}\PY{p}{(}\PY{n}{label}\PY{p}{,} \PY{n}{count\PYZus{}overall\PYZus{}sale\PYZus{}not\PYZus{}mall}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{count\PYZus{}pay\PYZus{}day}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{p}{,} \PY{n}{bottom}\PY{o}{=}\PY{n}{count\PYZus{}overall\PYZus{}sale\PYZus{}not\PYZus{}mall}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{count\PYZus{}mega\PYZus{}sale}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{o}{+}\PY{n}{count\PYZus{}overall\PYZus{}sale\PYZus{}not\PYZus{}mall}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{count\PYZus{}mid\PYZus{}month}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{p}{,} \PY{n}{color}\PY{o}{=}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{pink}\PY{l+s+s1}{\PYZsq{}}\PY{p}{,} \PY{n}{label} \PY{o}{=} \PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{PayDay sale campaign}\PY{l+s+s1}{\PYZsq{}}\PY{p}{)}
\PY{n}{a2}\PY{o}{.}\PY{n}{set\PYZus{}title}\PY{p}{(}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{Number of Items in Unofficial/Not mall Brand}\PY{l+s+s1}{\PYZsq{}}\PY{p}{,} \PY{n}{size}\PY{o}{=}\PY{l+m+mi}{20}\PY{p}{)}
\PY{n}{a2}\PY{o}{.}\PY{n}{set\PYZus{}xlabel}\PY{p}{(}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{Brand}\PY{l+s+s1}{\PYZsq{}}\PY{p}{,} \PY{n}{size}\PY{o}{=}\PY{l+m+mi}{20}\PY{p}{)}
\PY{n}{a2}\PY{o}{.}\PY{n}{set\PYZus{}ylabel}\PY{p}{(}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{Number of items}\PY{l+s+s1}{\PYZsq{}}\PY{p}{,} \PY{n}{size}\PY{o}{=}\PY{l+m+mi}{20}\PY{p}{)}

\PY{k}{for} \PY{n}{r1}\PY{p}{,} \PY{n}{r2}\PY{p}{,} \PY{n}{r3} \PY{o+ow}{in} \PY{n+nb}{zip}\PY{p}{(}\PY{n}{ax1}\PY{p}{,} \PY{n}{ax2}\PY{p}{,} \PY{n}{ax3}\PY{p}{)}\PY{p}{:}
    \PY{n}{h1} \PY{o}{=} \PY{n}{r1}\PY{o}{.}\PY{n}{get\PYZus{}height}\PY{p}{(}\PY{p}{)}
    \PY{n}{h2} \PY{o}{=} \PY{n}{r2}\PY{o}{.}\PY{n}{get\PYZus{}height}\PY{p}{(}\PY{p}{)}
    \PY{n}{h3} \PY{o}{=} \PY{n}{r3}\PY{o}{.}\PY{n}{get\PYZus{}height}\PY{p}{(}\PY{p}{)}

    \PY{n}{a2}\PY{o}{.}\PY{n}{text}\PY{p}{(}\PY{n}{r1}\PY{o}{.}\PY{n}{get\PYZus{}x}\PY{p}{(}\PY{p}{)} \PY{o}{+} \PY{n}{r1}\PY{o}{.}\PY{n}{get\PYZus{}width}\PY{p}{(}\PY{p}{)} \PY{o}{/} \PY{l+m+mf}{2.}\PY{p}{,} \PY{n}{h1} \PY{o}{/} \PY{l+m+mf}{2.}\PY{p}{,} \PY{l+s+s2}{\PYZdq{}}\PY{l+s+si}{\PYZob{}0:.2f\PYZcb{}}\PY{l+s+s2}{\PYZpc{}}\PY{l+s+s2}{\PYZdq{}}\PY{o}{.}\PY{n}{format}\PY{p}{(}\PY{p}{(}\PY{n}{h1}\PY{o}{/}\PY{p}{(}\PY{n}{h1}\PY{o}{+}\PY{n}{h2}\PY{o}{+}\PY{n}{h3}\PY{p}{)}\PY{p}{)}\PY{o}{*}\PY{l+m+mi}{100}\PY{p}{)}\PY{p}{,} \PY{n}{ha}\PY{o}{=}\PY{l+s+s2}{\PYZdq{}}\PY{l+s+s2}{center}\PY{l+s+s2}{\PYZdq{}}\PY{p}{,} \PY{n}{va}\PY{o}{=}\PY{l+s+s2}{\PYZdq{}}\PY{l+s+s2}{center}\PY{l+s+s2}{\PYZdq{}}\PY{p}{,} \PY{n}{color}\PY{o}{=}\PY{l+s+s2}{\PYZdq{}}\PY{l+s+s2}{black}\PY{l+s+s2}{\PYZdq{}}\PY{p}{,} \PY{n}{fontsize}\PY{o}{=}\PY{l+m+mi}{14}\PY{p}{)}
    \PY{n}{a2}\PY{o}{.}\PY{n}{text}\PY{p}{(}\PY{n}{r2}\PY{o}{.}\PY{n}{get\PYZus{}x}\PY{p}{(}\PY{p}{)} \PY{o}{+} \PY{n}{r2}\PY{o}{.}\PY{n}{get\PYZus{}width}\PY{p}{(}\PY{p}{)} \PY{o}{/} \PY{l+m+mf}{2.}\PY{p}{,} \PY{n}{h1} \PY{o}{+} \PY{n}{h2} \PY{o}{/} \PY{l+m+mf}{2.}\PY{p}{,} \PY{l+s+s2}{\PYZdq{}}\PY{l+s+si}{\PYZob{}0:.2f\PYZcb{}}\PY{l+s+s2}{\PYZpc{}}\PY{l+s+s2}{\PYZdq{}}\PY{o}{.}\PY{n}{format}\PY{p}{(}\PY{p}{(}\PY{n}{h2}\PY{o}{/}\PY{p}{(}\PY{n}{h1}\PY{o}{+}\PY{n}{h2}\PY{o}{+}\PY{n}{h3}\PY{p}{)}\PY{p}{)}\PY{o}{*}\PY{l+m+mi}{100}\PY{p}{)}\PY{p}{,} \PY{n}{ha}\PY{o}{=}\PY{l+s+s2}{\PYZdq{}}\PY{l+s+s2}{center}\PY{l+s+s2}{\PYZdq{}}\PY{p}{,} \PY{n}{va}\PY{o}{=}\PY{l+s+s2}{\PYZdq{}}\PY{l+s+s2}{center}\PY{l+s+s2}{\PYZdq{}}\PY{p}{,} \PY{n}{color}\PY{o}{=}\PY{l+s+s2}{\PYZdq{}}\PY{l+s+s2}{black}\PY{l+s+s2}{\PYZdq{}}\PY{p}{,} \PY{n}{fontsize}\PY{o}{=}\PY{l+m+mi}{14}\PY{p}{)}
    \PY{n}{a2}\PY{o}{.}\PY{n}{text}\PY{p}{(}\PY{n}{r3}\PY{o}{.}\PY{n}{get\PYZus{}x}\PY{p}{(}\PY{p}{)} \PY{o}{+} \PY{n}{r2}\PY{o}{.}\PY{n}{get\PYZus{}width}\PY{p}{(}\PY{p}{)} \PY{o}{/} \PY{l+m+mf}{2.}\PY{p}{,} \PY{n}{h1} \PY{o}{+} \PY{n}{h2} \PY{o}{+} \PY{n}{h3} \PY{o}{/} \PY{l+m+mf}{2.}\PY{p}{,} \PY{l+s+s2}{\PYZdq{}}\PY{l+s+si}{\PYZob{}0:.2f\PYZcb{}}\PY{l+s+s2}{\PYZpc{}}\PY{l+s+s2}{\PYZdq{}}\PY{o}{.}\PY{n}{format}\PY{p}{(}\PY{p}{(}\PY{n}{h3}\PY{o}{/}\PY{p}{(}\PY{n}{h1}\PY{o}{+}\PY{n}{h2}\PY{o}{+}\PY{n}{h3}\PY{p}{)}\PY{p}{)}\PY{o}{*}\PY{l+m+mi}{100}\PY{p}{)}\PY{p}{,} \PY{n}{ha}\PY{o}{=}\PY{l+s+s2}{\PYZdq{}}\PY{l+s+s2}{center}\PY{l+s+s2}{\PYZdq{}}\PY{p}{,} \PY{n}{va}\PY{o}{=}\PY{l+s+s2}{\PYZdq{}}\PY{l+s+s2}{center}\PY{l+s+s2}{\PYZdq{}}\PY{p}{,} \PY{n}{color}\PY{o}{=}\PY{l+s+s2}{\PYZdq{}}\PY{l+s+s2}{black}\PY{l+s+s2}{\PYZdq{}}\PY{p}{,} \PY{n}{fontsize}\PY{o}{=}\PY{l+m+mi}{14}\PY{p}{)}

\PY{n}{a2}\PY{o}{.}\PY{n}{legend}\PY{p}{(}\PY{n}{prop}\PY{o}{=}\PY{p}{\PYZob{}}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{size}\PY{l+s+s1}{\PYZsq{}}\PY{p}{:} \PY{l+m+mi}{15}\PY{p}{\PYZcb{}}\PY{p}{)}

\PY{n}{a1}\PY{o}{.}\PY{n}{tick\PYZus{}params}\PY{p}{(}\PY{n}{axis}\PY{o}{=}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{both}\PY{l+s+s1}{\PYZsq{}}\PY{p}{,} \PY{n}{labelsize}\PY{o}{=}\PY{l+m+mi}{15}\PY{p}{)}
\PY{n}{a2}\PY{o}{.}\PY{n}{tick\PYZus{}params}\PY{p}{(}\PY{n}{axis}\PY{o}{=}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{both}\PY{l+s+s1}{\PYZsq{}}\PY{p}{,} \PY{n}{labelsize}\PY{o}{=}\PY{l+m+mi}{15}\PY{p}{)}
\PY{c+c1}{\PYZsh{} plt.setp(a2.get\PYZus{}yticklabels(), visible=True)}

\PY{c+c1}{\PYZsh{} a = plt.show()}
\end{Verbatim}
\end{tcolorbox}

    \begin{center}
    \adjustimage{max size={0.9\linewidth}{0.9\paperheight}}{output_79_0.png}
    \end{center}
    { \hspace*{\fill} \\}
    
    การเข้าร่วม campaign ทั้ง 3 สามารถบอกได้ดังนี้ - Payday ที่การทำ Flash sale
สูงที่สุดเนื่องจากมีจำนวนวันในการทำและมีระยะเวลาในการทำสูงที่สุด (ข้อ 4) -
แบรนด์ที่การเข้าร่วม campaign คือ Petkit รองลงมาคือ Amazfit และ Xiaomi -
ร้านค้าที่ไม่เป็น official mall จะมีการเข้าร่วมเพียงหนึ่งแบรนด์ คือ Petkit และ ทำ
flash sale ใน pay day เยอะที่สุด

ร้านค้าส่วนใหญ่ที่เข้าร่วมทั้ง 3 campaign จะเป็น official mall และ pay day จะมีการทำ
flash sale สูงที่สุด

    \hypertarget{relationship-between-discount-and-sales}{%
\section{7. Relationship between discount and
sales}\label{relationship-between-discount-and-sales}}

ความสัมพันธ์ของการลดราคากับจำนวนสินค้าที่ขายได้

    \begin{tcolorbox}[breakable, size=fbox, boxrule=1pt, pad at break*=1mm,colback=cellbackground, colframe=cellborder]
\prompt{In}{incolor}{54}{\boxspacing}
\begin{Verbatim}[commandchars=\\\{\}]
\PY{n}{df} \PY{o}{=} \PY{n}{pd}\PY{o}{.}\PY{n}{read\PYZus{}csv}\PY{p}{(}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{shopee\PYZus{}project.csv}\PY{l+s+s1}{\PYZsq{}}\PY{p}{)}
\PY{n}{unique\PYZus{}id} \PY{o}{=} \PY{p}{[}\PY{p}{]}
\PY{k}{for} \PY{n}{i} \PY{o+ow}{in} \PY{n}{df}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{itemid}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{o}{.}\PY{n}{unique}\PY{p}{(}\PY{p}{)}\PY{o}{.}\PY{n}{tolist}\PY{p}{(}\PY{p}{)}\PY{p}{:}
    \PY{k}{if} \PY{n+nb}{len}\PY{p}{(}\PY{n}{df}\PY{p}{[}\PY{n}{df}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{itemid}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{o}{==}\PY{n}{i}\PY{p}{]}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{modelid}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{o}{.}\PY{n}{unique}\PY{p}{(}\PY{p}{)}\PY{p}{)} \PY{o}{==} \PY{l+m+mi}{1}\PY{p}{:}
\PY{c+c1}{\PYZsh{}         print(i)}
        \PY{n}{unique\PYZus{}id}\PY{o}{.}\PY{n}{append}\PY{p}{(}\PY{n}{i}\PY{p}{)}
\PY{n}{df}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{brand}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]} \PY{o}{=} \PY{n}{df}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{brand}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{o}{.}\PY{n}{replace}\PY{p}{(}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{Petkit(เพ็ทคิต)}\PY{l+s+s1}{\PYZsq{}}\PY{p}{,}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{Petkit(เพ็ทคิท)}\PY{l+s+s1}{\PYZsq{}}\PY{p}{)}
\PY{n}{df} \PY{o}{=} \PY{n}{df}\PY{p}{[}\PY{n}{df}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{itemid}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{o}{.}\PY{n}{isin}\PY{p}{(}\PY{n}{unique\PYZus{}id}\PY{p}{)}\PY{p}{]}\PY{o}{.}\PY{n}{reset\PYZus{}index}\PY{p}{(}\PY{n}{drop}\PY{o}{=}\PY{k+kc}{True}\PY{p}{)}
\end{Verbatim}
\end{tcolorbox}

    \begin{tcolorbox}[breakable, size=fbox, boxrule=1pt, pad at break*=1mm,colback=cellbackground, colframe=cellborder]
\prompt{In}{incolor}{55}{\boxspacing}
\begin{Verbatim}[commandchars=\\\{\}]
\PY{k}{def} \PY{n+nf}{extract\PYZus{}year}\PY{p}{(}\PY{n}{row}\PY{p}{)}\PY{p}{:}
    \PY{n}{date} \PY{o}{=} \PY{n}{datetime}\PY{o}{.}\PY{n}{strptime}\PY{p}{(}\PY{n}{row}\PY{p}{,} \PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{\PYZpc{}}\PY{l+s+s1}{Y\PYZhy{}}\PY{l+s+s1}{\PYZpc{}}\PY{l+s+s1}{m\PYZhy{}}\PY{l+s+si}{\PYZpc{}d}\PY{l+s+s1}{ }\PY{l+s+s1}{\PYZpc{}}\PY{l+s+s1}{H:}\PY{l+s+s1}{\PYZpc{}}\PY{l+s+s1}{M:}\PY{l+s+s1}{\PYZpc{}}\PY{l+s+s1}{S}\PY{l+s+s1}{\PYZsq{}}\PY{p}{)}
    \PY{k}{return} \PY{n}{date}\PY{o}{.}\PY{n}{strftime}\PY{p}{(}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{\PYZpc{}}\PY{l+s+s1}{Y}\PY{l+s+s1}{\PYZsq{}}\PY{p}{)}
\end{Verbatim}
\end{tcolorbox}

    \begin{tcolorbox}[breakable, size=fbox, boxrule=1pt, pad at break*=1mm,colback=cellbackground, colframe=cellborder]
\prompt{In}{incolor}{56}{\boxspacing}
\begin{Verbatim}[commandchars=\\\{\}]
\PY{n}{df}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{year}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]} \PY{o}{=} \PY{n}{df}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{ingest\PYZus{}date}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{o}{.}\PY{n}{apply}\PY{p}{(}\PY{n}{extract\PYZus{}year}\PY{p}{)}
\PY{n}{df} \PY{o}{=} \PY{n}{df}\PY{p}{[}\PY{n}{df}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{year}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{o}{==}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{2022}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}
\end{Verbatim}
\end{tcolorbox}

    \begin{tcolorbox}[breakable, size=fbox, boxrule=1pt, pad at break*=1mm,colback=cellbackground, colframe=cellborder]
\prompt{In}{incolor}{57}{\boxspacing}
\begin{Verbatim}[commandchars=\\\{\}]
\PY{c+c1}{\PYZsh{} Preview dataframe before calculate sales, stock ,discount, duration of flashsale}
\PY{n}{df}\PY{p}{[}\PY{n}{df}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{flash\PYZus{}sale}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{o}{.}\PY{n}{notnull}\PY{p}{(}\PY{p}{)}\PY{p}{]}\PY{p}{[}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{modelid}\PY{l+s+s1}{\PYZsq{}}\PY{p}{,}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{ingest\PYZus{}date}\PY{l+s+s1}{\PYZsq{}}\PY{p}{,}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{stock}\PY{l+s+s1}{\PYZsq{}}\PY{p}{,}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{flash\PYZus{}sale}\PY{l+s+s1}{\PYZsq{}}\PY{p}{,}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{price}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{p}{]}\PY{p}{[}\PY{p}{:}\PY{l+m+mi}{10}\PY{p}{]}
\end{Verbatim}
\end{tcolorbox}

            \begin{tcolorbox}[breakable, size=fbox, boxrule=.5pt, pad at break*=1mm, opacityfill=0]
\prompt{Out}{outcolor}{57}{\boxspacing}
\begin{Verbatim}[commandchars=\\\{\}]
          modelid          ingest\_date  stock  \textbackslash{}
56   115174576667  2022-09-09 01:00:00      6
57    91345241895  2022-09-09 01:00:00      9
58   172837567688  2022-09-09 01:00:00     30
179   91345241895  2022-10-17 12:00:01     10
180   91345241895  2022-10-17 12:00:01     10
215  171396661950  2022-09-09 00:00:00     50
217   90444301281  2022-09-09 00:00:00     40
239   61970382186  2022-10-04 15:00:01     20
242   44602375718  2022-10-04 15:00:01      5
267  124955024348  2022-09-09 13:00:01     37

                                            flash\_sale  price
56   \{'price\_before\_discount': 1499000000, 'hidden\_{\ldots}  11490
57   \{'price\_before\_discount': 2141900000, 'hidden\_{\ldots}  11900
58   \{'price\_before\_discount': 2141900000, 'hidden\_{\ldots}  11900
179  \{'price\_before\_discount': 2141900000, 'hidden\_{\ldots}  10900
180  \{'price\_before\_discount': 2141900000, 'hidden\_{\ldots}  10900
215  \{'price\_before\_discount': 1700000000, 'hidden\_{\ldots}  11500
217  \{'price\_before\_discount': 1890000000, 'hidden\_{\ldots}  14000
239  \{'price\_before\_discount': 1999900000, 'hidden\_{\ldots}  10590
242  \{'price\_before\_discount': 2141400000, 'hidden\_{\ldots}  11900
267  \{'price\_before\_discount': 2141900000, 'hidden\_{\ldots}  11900
\end{Verbatim}
\end{tcolorbox}
        
    \begin{tcolorbox}[breakable, size=fbox, boxrule=1pt, pad at break*=1mm,colback=cellbackground, colframe=cellborder]
\prompt{In}{incolor}{62}{\boxspacing}
\begin{Verbatim}[commandchars=\\\{\}]
\PY{n}{sale\PYZus{}diff} \PY{o}{=} \PY{n}{pd}\PY{o}{.}\PY{n}{DataFrame}\PY{p}{(}\PY{n}{columns}\PY{o}{=}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{sale\PYZus{}stock}\PY{l+s+s1}{\PYZsq{}}\PY{p}{,}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{price\PYZus{}diff}\PY{l+s+s1}{\PYZsq{}}\PY{p}{,}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{hour\PYZus{}duration}\PY{l+s+s1}{\PYZsq{}}\PY{p}{,}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{modelid}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{p}{)}
\PY{k}{for} \PY{n}{m\PYZus{}id} \PY{o+ow}{in} \PY{n}{df}\PY{p}{[}\PY{n}{df}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{flash\PYZus{}sale}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{o}{.}\PY{n}{notnull}\PY{p}{(}\PY{p}{)}\PY{p}{]}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{modelid}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{o}{.}\PY{n}{unique}\PY{p}{(}\PY{p}{)}\PY{o}{.}\PY{n}{tolist}\PY{p}{(}\PY{p}{)}\PY{p}{:}
\PY{c+c1}{\PYZsh{}     print(\PYZsq{}modelid:\PYZsq{},modelid)}
    \PY{n}{modelid} \PY{o}{=} \PY{n}{m\PYZus{}id}
    \PY{n}{temp} \PY{o}{=} \PY{n}{df}\PY{p}{[}\PY{n}{df}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{modelid}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{o}{==}\PY{n}{modelid}\PY{p}{]}\PY{o}{.}\PY{n}{sort\PYZus{}values}\PY{p}{(}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{ingest\PYZus{}date}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{p}{)}\PY{p}{[}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{modelid}\PY{l+s+s1}{\PYZsq{}}\PY{p}{,}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{ingest\PYZus{}date}\PY{l+s+s1}{\PYZsq{}}\PY{p}{,}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{stock}\PY{l+s+s1}{\PYZsq{}}\PY{p}{,}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{flash\PYZus{}sale}\PY{l+s+s1}{\PYZsq{}}\PY{p}{,}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{price}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{p}{]}\PY{o}{.}\PY{n}{reset\PYZus{}index}\PY{p}{(}\PY{n}{drop}\PY{o}{=}\PY{k+kc}{True}\PY{p}{)}
    \PY{n}{n} \PY{o}{=} \PY{l+m+mi}{0}

    \PY{n}{sale\PYZus{}stock} \PY{o}{=} \PY{p}{[}\PY{p}{]}
    \PY{n}{price\PYZus{}diff} \PY{o}{=} \PY{p}{[}\PY{p}{]}
    \PY{n}{hour\PYZus{}duration} \PY{o}{=} \PY{p}{[}\PY{p}{]}
    \PY{k}{for} \PY{n}{i} \PY{o+ow}{in} \PY{n}{temp}\PY{p}{[}\PY{n}{temp}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{flash\PYZus{}sale}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{o}{.}\PY{n}{notnull}\PY{p}{(}\PY{p}{)}\PY{p}{]}\PY{o}{.}\PY{n}{index}\PY{o}{.}\PY{n}{tolist}\PY{p}{(}\PY{p}{)}\PY{p}{:}
\PY{c+c1}{\PYZsh{}         print(\PYZsq{}current index\PYZsq{},i)}
        \PY{k}{if} \PY{n}{n} \PY{o}{==} \PY{l+m+mi}{0}\PY{p}{:}
            \PY{n}{n}\PY{o}{+}\PY{o}{=}\PY{l+m+mi}{1}
            \PY{n}{start\PYZus{}index} \PY{o}{=} \PY{n}{i}
            \PY{n}{start\PYZus{}stock} \PY{o}{=} \PY{n}{temp}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{stock}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{o}{.}\PY{n}{loc}\PY{p}{[}\PY{n}{i}\PY{p}{]}
            \PY{n}{start\PYZus{}price} \PY{o}{=} \PY{n}{temp}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{price}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{o}{.}\PY{n}{loc}\PY{p}{[}\PY{n}{i}\PY{p}{]}
\PY{c+c1}{\PYZsh{}             last\PYZus{}index = i}
            \PY{n}{hour} \PY{o}{=} \PY{l+m+mi}{1}
        \PY{k}{elif} \PY{n}{i} \PY{o}{\PYZhy{}} \PY{n}{last\PYZus{}index} \PY{o}{\PYZgt{}} \PY{l+m+mi}{1} \PY{o+ow}{or} \PY{n}{i} \PY{o}{==} \PY{n}{temp}\PY{p}{[}\PY{n}{temp}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{flash\PYZus{}sale}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{o}{.}\PY{n}{notnull}\PY{p}{(}\PY{p}{)}\PY{p}{]}\PY{o}{.}\PY{n}{index}\PY{o}{.}\PY{n}{tolist}\PY{p}{(}\PY{p}{)}\PY{p}{[}\PY{o}{\PYZhy{}}\PY{l+m+mi}{1}\PY{p}{]}\PY{p}{:}
            \PY{k}{if} \PY{n}{repeat} \PY{o}{==} \PY{k+kc}{True}\PY{p}{:}
                \PY{n}{start\PYZus{}index} \PY{o}{=} \PY{n}{i}
                \PY{n}{start\PYZus{}stock} \PY{o}{=} \PY{n}{temp}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{stock}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{o}{.}\PY{n}{loc}\PY{p}{[}\PY{n}{i}\PY{p}{]}
                \PY{n}{start\PYZus{}price} \PY{o}{=} \PY{n}{temp}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{price}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{o}{.}\PY{n}{loc}\PY{p}{[}\PY{n}{i}\PY{p}{]}
                \PY{n}{last\PYZus{}index} \PY{o}{=} \PY{n}{i}
                \PY{n}{hour} \PY{o}{=} \PY{l+m+mi}{1}
            \PY{k}{else}\PY{p}{:}
\PY{c+c1}{\PYZsh{}                 print(\PYZsq{}\PYZhy{}\PYZhy{}\PYZhy{}\PYZhy{}\PYZhy{}\PYZhy{}\PYZhy{}\PYZhy{}\PYZhy{}\PYZhy{}\PYZhy{}\PYZhy{}\PYZhy{}\PYZhy{}\PYZhy{}\PYZsq{})}
\PY{c+c1}{\PYZsh{}                 print(\PYZsq{}start\PYZus{}index\PYZsq{},start\PYZus{}index)}
\PY{c+c1}{\PYZsh{}                 print(\PYZsq{}last\PYZus{}index\PYZsq{},last\PYZus{}index)}
\PY{c+c1}{\PYZsh{}                 print(\PYZsq{}start\PYZus{}stock \PYZsq{},start\PYZus{}stock,\PYZsq{}last\PYZus{}stock \PYZsq{},last\PYZus{}stock)}
\PY{c+c1}{\PYZsh{}                 print(start\PYZus{}stock \PYZhy{} last\PYZus{}stock)}
                \PY{k}{if} \PY{n}{start\PYZus{}index} \PY{o}{==} \PY{l+m+mi}{0}\PY{p}{:}
                    \PY{k}{pass}
                \PY{k}{else}\PY{p}{:}
\PY{c+c1}{\PYZsh{}                     print(temp[\PYZsq{}price\PYZsq{}].loc[start\PYZus{}index \PYZhy{} 1])}
\PY{c+c1}{\PYZsh{}                     print(start\PYZus{}price)}
\PY{c+c1}{\PYZsh{}                     print(\PYZsq{}hour\PYZus{}duration\PYZsq{},hour)}
\PY{c+c1}{\PYZsh{}                     print(\PYZsq{}\PYZhy{}\PYZhy{}\PYZhy{}\PYZhy{}\PYZhy{}\PYZhy{}\PYZhy{}\PYZhy{}\PYZhy{}\PYZhy{}\PYZhy{}\PYZhy{}\PYZhy{}\PYZhy{}\PYZhy{}\PYZsq{})}
                    \PY{n}{sale\PYZus{}stock}\PY{o}{.}\PY{n}{append}\PY{p}{(}\PY{n}{start\PYZus{}stock} \PY{o}{\PYZhy{}} \PY{n}{last\PYZus{}stock}\PY{p}{)}
                    \PY{n}{price\PYZus{}diff}\PY{o}{.}\PY{n}{append}\PY{p}{(}\PY{p}{(}\PY{n}{temp}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{price}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{o}{.}\PY{n}{loc}\PY{p}{[}\PY{n}{start\PYZus{}index} \PY{o}{\PYZhy{}} \PY{l+m+mi}{1}\PY{p}{]}\PY{o}{\PYZhy{}}\PY{n}{start\PYZus{}price}\PY{p}{)}\PY{o}{/}\PY{n}{temp}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{price}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{o}{.}\PY{n}{loc}\PY{p}{[}\PY{n}{start\PYZus{}index} \PY{o}{\PYZhy{}} \PY{l+m+mi}{1}\PY{p}{]}\PY{o}{*}\PY{l+m+mi}{100}\PY{p}{)}
                    \PY{n}{hour\PYZus{}duration}\PY{o}{.}\PY{n}{append}\PY{p}{(}\PY{n}{hour}\PY{p}{)}

                    \PY{n}{start\PYZus{}index} \PY{o}{=} \PY{n}{i}
                    \PY{n}{start\PYZus{}stock} \PY{o}{=} \PY{n}{temp}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{stock}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{o}{.}\PY{n}{loc}\PY{p}{[}\PY{n}{i}\PY{p}{]}
                    \PY{n}{start\PYZus{}price} \PY{o}{=} \PY{n}{temp}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{price}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{o}{.}\PY{n}{loc}\PY{p}{[}\PY{n}{i}\PY{p}{]}
                    \PY{n}{last\PYZus{}index} \PY{o}{=} \PY{n}{i}
                    \PY{n}{hour} \PY{o}{=} \PY{l+m+mi}{1}

            \PY{n}{repeat} \PY{o}{=} \PY{k+kc}{True}

        \PY{k}{else}\PY{p}{:}
            \PY{n}{repeat} \PY{o}{=} \PY{k+kc}{False}
            \PY{n}{last\PYZus{}index} \PY{o}{=} \PY{n}{i}
            \PY{n}{last\PYZus{}stock} \PY{o}{=} \PY{n}{temp}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{stock}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{o}{.}\PY{n}{loc}\PY{p}{[}\PY{n}{i}\PY{p}{]}
            \PY{n}{hour} \PY{o}{+}\PY{o}{=}\PY{l+m+mi}{1}

    \PY{n}{temp\PYZus{}df} \PY{o}{=} \PY{n}{pd}\PY{o}{.}\PY{n}{DataFrame}\PY{p}{(}\PY{p}{)}
    \PY{n}{temp\PYZus{}df}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{sale\PYZus{}stock}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]} \PY{o}{=} \PY{n}{sale\PYZus{}stock}
    \PY{n}{temp\PYZus{}df}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{price\PYZus{}diff}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]} \PY{o}{=} \PY{n}{price\PYZus{}diff}
    \PY{n}{temp\PYZus{}df}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{hour\PYZus{}duration}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]} \PY{o}{=} \PY{n}{hour\PYZus{}duration}
    \PY{n}{temp\PYZus{}df}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{modelid}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]} \PY{o}{=} \PY{n}{modelid}
    
    \PY{n}{sale\PYZus{}diff} \PY{o}{=} \PY{n}{sale\PYZus{}diff}\PY{o}{.}\PY{n}{append}\PY{p}{(}\PY{n}{temp\PYZus{}df}\PY{p}{)}
\end{Verbatim}
\end{tcolorbox}

    \begin{tcolorbox}[breakable, size=fbox, boxrule=1pt, pad at break*=1mm,colback=cellbackground, colframe=cellborder]
\prompt{In}{incolor}{63}{\boxspacing}
\begin{Verbatim}[commandchars=\\\{\}]
\PY{n}{sale\PYZus{}diff}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{sale\PYZus{}stock}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]} \PY{o}{=}  \PY{n}{sale\PYZus{}diff}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{sale\PYZus{}stock}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{o}{/}\PY{o}{/}\PY{n}{sale\PYZus{}diff}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{hour\PYZus{}duration}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}
\end{Verbatim}
\end{tcolorbox}

    \begin{tcolorbox}[breakable, size=fbox, boxrule=1pt, pad at break*=1mm,colback=cellbackground, colframe=cellborder]
\prompt{In}{incolor}{64}{\boxspacing}
\begin{Verbatim}[commandchars=\\\{\}]
\PY{n}{sale\PYZus{}diff} \PY{o}{=} \PY{n}{sale\PYZus{}diff}\PY{p}{[}\PY{p}{(}\PY{n}{sale\PYZus{}diff}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{price\PYZus{}diff}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{o}{\PYZgt{}}\PY{o}{=}\PY{l+m+mi}{0}\PY{p}{)} \PY{o}{\PYZam{}} \PY{p}{(}\PY{n}{sale\PYZus{}diff}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{sale\PYZus{}stock}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{o}{\PYZgt{}}\PY{o}{=}\PY{l+m+mi}{0}\PY{p}{)}\PY{p}{]}
\end{Verbatim}
\end{tcolorbox}

    \begin{tcolorbox}[breakable, size=fbox, boxrule=1pt, pad at break*=1mm,colback=cellbackground, colframe=cellborder]
\prompt{In}{incolor}{65}{\boxspacing}
\begin{Verbatim}[commandchars=\\\{\}]
\PY{n}{figure}\PY{p}{(}\PY{n}{figsize}\PY{o}{=}\PY{p}{(}\PY{l+m+mi}{15}\PY{p}{,} \PY{l+m+mi}{10}\PY{p}{)}\PY{p}{,} \PY{n}{dpi}\PY{o}{=}\PY{l+m+mi}{200}\PY{p}{)}
\PY{n}{plt}\PY{o}{.}\PY{n}{scatter}\PY{p}{(}\PY{n}{sale\PYZus{}diff}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{price\PYZus{}diff}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{p}{,} \PY{n}{sale\PYZus{}diff}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{sale\PYZus{}stock}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{p}{)}
\PY{n}{plt}\PY{o}{.}\PY{n}{title}\PY{p}{(}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{Scatter plot between }\PY{l+s+si}{\PYZpc{}d}\PY{l+s+s1}{iscount and product sales}\PY{l+s+s1}{\PYZsq{}}\PY{p}{,} \PY{n}{fontsize}\PY{o}{=}\PY{l+m+mi}{17}\PY{p}{)}
\PY{n}{plt}\PY{o}{.}\PY{n}{xlabel}\PY{p}{(}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{\PYZpc{}}\PY{l+s+s1}{ Discount}\PY{l+s+s1}{\PYZsq{}}\PY{p}{,} \PY{n}{fontsize}\PY{o}{=}\PY{l+m+mi}{15}\PY{p}{)}
\PY{n}{plt}\PY{o}{.}\PY{n}{ylabel}\PY{p}{(}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{Number of product sales}\PY{l+s+s1}{\PYZsq{}}\PY{p}{,} \PY{n}{fontsize}\PY{o}{=}\PY{l+m+mi}{15}\PY{p}{)}
\PY{c+c1}{\PYZsh{} \PYZus{} = plt.xticks(range(0,70,1))}
\end{Verbatim}
\end{tcolorbox}

            \begin{tcolorbox}[breakable, size=fbox, boxrule=.5pt, pad at break*=1mm, opacityfill=0]
\prompt{Out}{outcolor}{65}{\boxspacing}
\begin{Verbatim}[commandchars=\\\{\}]
Text(0, 0.5, 'Number of product sales')
\end{Verbatim}
\end{tcolorbox}
        
    \begin{center}
    \adjustimage{max size={0.9\linewidth}{0.9\paperheight}}{output_89_1.png}
    \end{center}
    { \hspace*{\fill} \\}
    
    ตัด outliner ที่เป็นข้อมูลที่ไม่มีความสำคัญออก เพื่อให้สามารถขยายกราฟให้ใหญ่มากขึ้นได้

    \begin{tcolorbox}[breakable, size=fbox, boxrule=1pt, pad at break*=1mm,colback=cellbackground, colframe=cellborder]
\prompt{In}{incolor}{66}{\boxspacing}
\begin{Verbatim}[commandchars=\\\{\}]
\PY{n}{sale\PYZus{}diff} \PY{o}{=} \PY{n}{sale\PYZus{}diff}\PY{p}{[}\PY{p}{(}\PY{n}{sale\PYZus{}diff}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{price\PYZus{}diff}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{o}{\PYZgt{}}\PY{o}{=}\PY{l+m+mi}{0}\PY{p}{)} \PY{o}{\PYZam{}} \PY{p}{(}\PY{n}{sale\PYZus{}diff}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{sale\PYZus{}stock}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{o}{\PYZgt{}}\PY{o}{=}\PY{l+m+mi}{0}\PY{p}{)} \PY{o}{\PYZam{}} \PY{p}{(}\PY{n}{sale\PYZus{}diff}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{price\PYZus{}diff}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{o}{\PYZlt{}}\PY{l+m+mi}{50}\PY{p}{)}\PY{p}{]}
\end{Verbatim}
\end{tcolorbox}

    \begin{tcolorbox}[breakable, size=fbox, boxrule=1pt, pad at break*=1mm,colback=cellbackground, colframe=cellborder]
\prompt{In}{incolor}{67}{\boxspacing}
\begin{Verbatim}[commandchars=\\\{\}]
\PY{n}{figure}\PY{p}{(}\PY{n}{figsize}\PY{o}{=}\PY{p}{(}\PY{l+m+mi}{15}\PY{p}{,} \PY{l+m+mi}{10}\PY{p}{)}\PY{p}{,} \PY{n}{dpi}\PY{o}{=}\PY{l+m+mi}{200}\PY{p}{)}
\PY{n}{plt}\PY{o}{.}\PY{n}{scatter}\PY{p}{(}\PY{n}{sale\PYZus{}diff}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{price\PYZus{}diff}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{p}{,} \PY{n}{sale\PYZus{}diff}\PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{sale\PYZus{}stock}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{p}{)}
\PY{n}{plt}\PY{o}{.}\PY{n}{title}\PY{p}{(}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{Scatter plot between }\PY{l+s+si}{\PYZpc{}d}\PY{l+s+s1}{iscount and product sales}\PY{l+s+s1}{\PYZsq{}}\PY{p}{,} \PY{n}{fontsize}\PY{o}{=}\PY{l+m+mi}{17}\PY{p}{)}
\PY{n}{plt}\PY{o}{.}\PY{n}{xlabel}\PY{p}{(}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{\PYZpc{}}\PY{l+s+s1}{ Discount}\PY{l+s+s1}{\PYZsq{}}\PY{p}{,} \PY{n}{fontsize}\PY{o}{=}\PY{l+m+mi}{15}\PY{p}{)}
\PY{n}{plt}\PY{o}{.}\PY{n}{ylabel}\PY{p}{(}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{Number of product sales}\PY{l+s+s1}{\PYZsq{}}\PY{p}{,} \PY{n}{fontsize}\PY{o}{=}\PY{l+m+mi}{15}\PY{p}{)}
\PY{n}{\PYZus{}} \PY{o}{=} \PY{n}{plt}\PY{o}{.}\PY{n}{xticks}\PY{p}{(}\PY{n+nb}{range}\PY{p}{(}\PY{l+m+mi}{0}\PY{p}{,}\PY{l+m+mi}{25}\PY{p}{,}\PY{l+m+mi}{1}\PY{p}{)}\PY{p}{)}
\end{Verbatim}
\end{tcolorbox}

    \begin{center}
    \adjustimage{max size={0.9\linewidth}{0.9\paperheight}}{output_92_0.png}
    \end{center}
    { \hspace*{\fill} \\}
    
    ส่วนลดในช่วง 8-10\% มีผลต่อยอดขายสินค้า ทำให้สินค้าขายได้มากกว่าปกติ 2-3 เท่า
ส่วนลดเป็นเปอร์เซ็นต์ในช่วงอื่นไม่ได้มีผลกับจำนวนสินค้าที่ขายมากนัก

    \hypertarget{summary}{%
\section{Summary}\label{summary}}

\begin{enumerate}
\def\labelenumi{\arabic{enumi}.}
\tightlist
\item
  วันที่ทำ flash sale บ่อยที่สุด 25 เที่ยงคืน 15 เที่ยงคืน
\item
  แคมเปญที่ทำแฟลชเซลบ่อยที่สุดคือ PayDay
\item
  วันและเวลาที่ทำแฟลชเซลบ่อยของ PayDay - 25-00, 30-12, 25-12, 27-12
\item
  mega sale จะทำแฟลชเซลบ่อยกว่า mid month sale
  แต่จำนวนชั่วโมงในการแฟลชเซลน้อยกว่า mid month
\item
  PayDay นิยมทำแฟลชเซลในช่วงเวลากลางวัน 12, 18 ส่วน mega, mid month
  ทำแฟลชเซลคล้ายๆกัน นิยมทำในช่วงเวลากลางคืน 00:00-02:00
\item
  official brand ส่วนมากจะนิยมทำแฟลชเซลในแคมเปญ Mega sale และ PayDay
  มากกว่า Midmonth
\item
  ส่วนลด 8-10\% มีผลกับยอดขายมากที่สุด
\end{enumerate}

    \begin{tcolorbox}[breakable, size=fbox, boxrule=1pt, pad at break*=1mm,colback=cellbackground, colframe=cellborder]
\prompt{In}{incolor}{ }{\boxspacing}
\begin{Verbatim}[commandchars=\\\{\}]

\end{Verbatim}
\end{tcolorbox}


    % Add a bibliography block to the postdoc
    
    
    
\end{document}
