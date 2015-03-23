# Šablona pro psaní disertační prace na ČVUT FEL 

Tento repositář obsahuje předváděcí verzi šablony pro psaní doktorský prací na FEL ČVUT v anglickém jazyce. Šablona vznikla protože jsem nebyl spokojen s komplikovaným provozem šablony felthesis, nelogičností fit šablony a zastaralostí všech ostatních šablon. Rozhodl jsem se tedy připravit šablonu, která bude maximálně kopírovat způsob práce s LaTeXem a jeho šablonou book jak jen to je možné. 

Základní zavedení šablony je velmi jednoduché, a to:
```
\documentclass{phdthesis}
```

Následně je nutné nastavit jméno disertační práce:
```
\title{Very Long Name of Disertation Thesis Dealing With Some Science}
```

Poskytnout informaci o autorovi práce a jeho školiteli
```
\author{Ing. Name Surname}
\authorAffiliation{
Department of Telecommunication Engineering\\
Faculty of Electrical Engineering\\
Czech Technical University in Prague\\
Technická 2\\
160 00 Prague 6\\
Czech Republic \\
\url{email_author@fel.cvut.cz}}

\supervisor{Doc. Ing. Name Surname, Ph.D.}
\supervisorAffiliation{
Department of Telecommunication Engineering\\
Faculty of Electrical Engineering\\
Czech Technical University in Prague\\
Technická 2\\
160 00 Prague 6\\
Czech Republic \\
\url{email_supervisor@fel.cvut.cz}}
```

Doplňující informace
```
\placeyear{Prague, March 2015}
\date{March 2015}
```

A pak jen začít psát

```
\begin{document}

\maketitle
\listoftables
\listoffigures
\printglossary[title=List of Acronyms,toctitle=List of Acronyms]
\tableofcontents


\mainmatter
%% Vlastni text disertacni prace

\appendix
%% Prilohy

\end{document}
```


V této složce je možné najít 3 ukázkové dokumenty sestavené právě diky šabloně phdthesis.cls, jedná se o Teze (statement), Seznam vlastní literatury (literature) a vlastní disertační práce (thesis-final). Dále je zde soubor, který se jmenuje thesis.tex a osobně se mi osvědčil pro vlastní psaní. 

Při psaní disertační práce člověk naráží na spousty balastu okolo a v první chvíli se chce soustředit hlavně na samotné psaní. Přesně pro tyto účely slouží právě thesis.tex, který v sobě obsahuje minimální sadu balíčků a nastavení, aby bylo možné začít psát disertační práci. Tento soubor je postavený na základě šablony book, takže je možné použít vše na co jste zvyklí ze psaní článků. Tento dokument je navíc vhodný pro korekce, protože je kompaktnější.

Ve chvíli, kdy je text připraven je nutné text zasadit do šablony. K tomuto zde složí soubor thesis-final.tex, který ve své horní části obsahuje soubor metadat, která popisují autora, jméno práce a pár dalších základních parametrů. Prakticky stačí jen překopírovat \input direktivy a zavolat příkaz pdflatex, či jinou oblíbenou variantu pro sestavení. Šablona je připravena na práci s automaticky generovanými zkratkami. Zkratky se definují v souboru zkratky.tex. Literatura je generována opět automaticky s využitím bibtex. Kvůli lepší podpoře znaků je však vhodné reference udržovat v UTF-8 formátu biblatex (Jabref tuto volbu má v nastavení). Odstraní se tím řada problémů se speciálními znaky v názvech. Šablona na pozadí využívá právě biblatex a šablonu IEEE pro formátování literatury. 

V případě, že je využito automaticky generovaných zkratek postup pro sestavení je následující:
pdflatex thesis-final
makeglossaries thesis-final
bibtex thesis-final
pdflatex thesis-final


Dalším důležitým dokumentem jsou samotné Teze. Pro teze je zde připravena šablona statement.tex. Opět se využívá šablony phdthesis.cls, jen byly změněny volby šablony. Pro tezi je možné přidat ještě parameter print, který vloží prázdné stránky takovým způsobem, že tisk na booklet vypadá o kousíček víc profesionálně. Zde stojí za zmínku podstránka, která obsahuje autorovu literaturu. Zde je dobré se všimnout, že je možné se odkazovat na vlastní publikace pomocí příkazu \bibentry, která je nabízena speciálně šablonou phdthesis, jelikož běžne dostupná implementace má problémy se speciálními znaky a tedy nefunguje s biblatex.

Sestavení:
pdflatex thesis-final
makeglossaries thesis-final
bibtex thesis-final
pdflatex thesis-final


Posledním důležitým dokumentem je literature.tex, což je prakticky je výcuc z Teze a jedná se o samostatný dokument, který se odevzdává při podání disertační práce. Využívá již připraveného seznamu literatury, jen definuje úvodní stranu tak, aby všechny dokumenty byly graficky jednotné.

Sestavení:
pdflatex thesis-final
bibtex thesis-final
pdflatex thesis-final






Vhodná rozšíření:
 * Podpora více jazyků než jen EN
 * Podpora pro více kateder. - Doporučil bych implementací formou parametru třídy, typicky k13132, k13101, taková to notace by umožnila nasazení pro celé ČVUT.
 * 



FAQ:
 * Není využito biberu, jelikož na Debian stable správně nefungoval a na Windows 7 64bit pouze padal hned od samého stažení. Navíc pro zdroje stažené z Internetu (IEEE, Elsevir,..) a ručně připravené zdroje nedošlo k ani jedné chybě.
 * Sablona neni v současné době odladěna pro oboustanný tisk, ani 1.0 řádkování, a to protože se v této podobě na K13132 tak neodevzdávají, nicméně není problém přepnout.
