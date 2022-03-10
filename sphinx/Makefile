# Makefile for Sphinx documentation
#
 
# You can set these variables from the command line.
SPHINXOPTS    =
SPHINXBUILD   = sphinx-build
ZH_DIR        = zh_CN
ZH_BUILDDIR   = build/zh_CN
EN_DIR        = en
EN_BUILDDIR   = build/en
BUILDDIR      = build

# User-friendly check for sphinx-build
ifeq ($(shell which $(SPHINXBUILD) >/dev/null 2>&1; echo $$?), 1)
$(error The '$(SPHINXBUILD)' command was not found. Make sure you have Sphinx installed, then set the SPHINXBUILD environment variable to point to the full path of the '$(SPHINXBUILD)' executable. Alternatively you can add the directory with the executable to your PATH. If you don't have Sphinx installed, grab it from http://sphinx-doc.org/)
endif
 
.PHONY: help clean html zh_compile zh_deploy #en_compile en_deploy
 
help:
	@echo "Please use make <target> where <target> is one of"
	@echo "  clean      to clean the build_dir"
	@echo "  compile    to make zh_CN & en website"
	@echo "  deploy     to move zh_CN & en website to nas"

clean:
	@rm -rf $(BUILDDIR)/*

html:
	$(SPHINXBUILD) -b html $(BUILDDIR)/html
	@echo
	@echo "Build finished. The HTML pages are in $(BUILDDIR)/html."

compile: zh_compile 
# compile: en_compile

deploy: zh_deploy 
# deploy: en_deploy

zh_compile:
	$(SPHINXBUILD)  -D language='zh_CN' -D html_search_language='zh' -b html -d $(ZH_BUILDDIR)/doctrees $(ZH_DIR) $(ZH_BUILDDIR)/html
	@echo
	@echo "zh_CN Build finished. The HTML pages are in $(ZH_BUILDDIR)/html."

zh_deploy: zh_compile
	sudo mv build/zh_CN/ /home/admin/proxima/data/documents/proxima_de_doc_data/zh_CN/latest_tmp
	sudo mv /home/admin/proxima/data/documents/proxima_de_doc_data/zh_CN/latest /home/admin/proxima/data/documents/proxima_de_doc_data/zh_CN/latest_delete
	sudo mv /home/admin/proxima/data/documents/proxima_de_doc_data/zh_CN/latest_tmp /home/admin/proxima/data/documents/proxima_de_doc_data/zh_CN/latest
	sudo rm -rf /home/admin/proxima/data/documents/proxima_de_doc_data/zh_CN/latest_delete
