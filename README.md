### OboToTerm

Convert ontology files in _.obo_ format to tables `term.txt`, `term2term.txt` and `graph_path.txt`  
from the GO MySQL Database Schema.

#### Background
[Gene Ontology](http://geneontology.org/) (GO) will at some point no longer provide their ontology in the GO MySQL Database Schema.  
The GO enrichment R-package [_GOfuncR_](https://bioconductor.org/packages/release/bioc/html/GOfuncR.html),
however, needs the old table format as input.  

Since _GOfuncR_, although primarly used with the Gene Ontology, works with any ontology, this conversion can be useful for other ontologies in _.obo_ format too, e.g. the [Human Phenotype Ontology](https://hpo.jax.org/app/).

#### Usage

`obo_to_term_tables.py` has 2 positional arguments: the _.obo_ file and the target directory for the term tables.  
Optional `--root_nodes` need to be defined for other ontologies than Gene Ontology.

Optional if you mark a date instead of the _.obo_ file, it will download the file of onthology inside the [release database](http://release.geneontology.org) and put it inside your outdir with the date you indicate.


#### Examples
Assuming you saved `obo_to_term_tables.py` and `obo_to_term_functions.py` in directory `/path/to/script/`  

*  Download and convert Gene Ontology

```sh
wget http://current.geneontology.org/ontology/go-basic.obo
/path/to/script/obo_to_term_tables.py go-basic.obo .
```

*  Download automatically and convert Gene Ontology
```sh
/path/to/script/obo_to_term_tables.py 2021-02-01 .
```



*  Download and convert Human Phenotype Ontology

```sh
wget http://purl.obolibrary.org/obo/hp.obo
/path/to/script/obo_to_term_tables.py hp.obo . --root_nodes "All"
```
