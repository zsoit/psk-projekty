
include auth.mk

zipname = projektsieci-latex-$$(date +"%Y-%m-%-d").zip

version:
	echo PK textemplate 1.2.0 - Tex Live Version for Linux or WSL
run:
	pdflatex index.tex; pdflatex index.tex; make clear; make pdf-mv;

clear:
	rm -rf *.toc *.aux *.out *.log src/*.aux src/*/*.aux src/*/*.log src/*/*.f* sections/*.aux tex/*.aux

build:
	make run; make clear;

pdf-mv:
	mv index.pdf pdf/index.pdf;

new:
	touch sections/$(s).tex; echo "$(s) was added!"; echo  \include{./sections/$(s).tex}\newpage

# backup

zip:
	zip -r $(zipname) *

clean-zip:
	rm -rf $(zipname)

sftp:
	scp -P 10189 -r $(zipname) keepass@maluch.mikr.us:/home/keepass/backup/latex

backup:
	make zip; make sftp; make clean-zip
