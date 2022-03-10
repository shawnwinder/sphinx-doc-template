
# Install Dependence with conda
1. run 'conda create -n pydoc python=3.7'  need python 3.6 or newer
2. conda activate pydoc
3. run 'pip install -r requirements.txt -i https://pypi.antfin-inc.com/simple' to install environments.

# How to write document
1. write 'your_doc.md' in ./manual/Abc.
2. add your_doc.md in sphinx/source/abc.rst 's toctree.

# How to view the web
1. cd sphinx, run `make compile` to generate html.
2. open build/zh_CN/html/index.html in your browser.

# How to deploy it
1. git pull
2. cd sphinx, run `make deploy` to generate html and publish them to nas.
