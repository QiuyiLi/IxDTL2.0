# MLMSC Simulator

MLMSC Simulator is a program for the simulation of gene family evolution within a species tree based on the Multilocus Multipecies Coalescent (MLMSC) model. MLMSC model generalises the multispecies coalescent to gene families, and is designed to capture all possible scenarios that can arise through incomplete lineage sorting, gene duplication, transfer and loss, and any interaction between these processes. The MLMSC combines forward- and backward-in-time modelling in order to properly account for copy number hemiplasy and linkage between loci. 
The input for MLMSC Simulator are the simulation parameter values and a pre-specified species tree in Newick format as an input file. The output is a simulated gene tree in Newick format.

## Citation
If you use the MLMSC simulator, please cite:

--To be listed--

## Obtaining the program

### Download

The source code of MLMSC Simulator is available in the GitHub repository: 
```
https://github.com/QiuyiLi/MLMSC
```
You can clone the sources in your computer by executing 
```
git clone https://github.com/QiuyiLi/MLMSC.git
```

### Requirements
MLMSC Simulator is built under Python 3.7.2 and requirs the installation of the following packages: 
```
scikit-bio
numpy
statistics
```
You can install these packages by executing 
```
pip install -r requirements.txt
```
### Testing

The MLMSC Simulator should be ready to use now. You can test the the simulator by executing
```
python3 MLMSC.py -i species_trees/species_tree_0.newick -s 2020210
```
The simulator will run with the default setting and you should be able to see the following outputs:
```
gene tree:
                                        /-A_locus0_event3
                              /--------|
                             |         |          /-A
                    /--------|          \--------|
                   |         |                    \-A_locus0_event1
          /--------|         |
         |         |          \-A_locus0_event2
---------|         |
         |          \-D_locus0_event0
         |
          \-D
```

##  Usage

### Input file
* Species tree: -i or --inputFile; the prespecified species tree written in [Newick](https://en.wikipedia.org/wiki/Newick_format) format
```
e.g., python3 MLMSC.py -i species_trees/species_tree_0.newick
```

### Input parameters

* Coalescent rate: -c or --coalescentRate; the coalescent rate in multispecies coalescent, default: -c 1.0
```
e.g., python3 MLMSC.py -i species_trees/species_tree_0.newick -c 0.5
```
  
* Recombination rate: -r or --recombinationRate; the recombiantion rate in linked coalescent, default: -r 0.5
```
e.g., python3 MLMSC.py -i species_trees/species_tree_0.newick -r 0.5
```
  
* Duplication rate: -d or --duplicationRate; occurrence rate of gene duplication, default: -d 0.2
```
e.g., python3 MLMSC.py -i species_trees/species_tree_0.newick -d 0.5
```
  
* Transfer rate; -t or --transferRate; occurrence rate of horizontal gene transfer, default: -t 0.1
```
e.g., python3 MLMSC.py -i species_trees/species_tree_0.newick -t 0.5
```
  
* Loss rate; -l or --lossRate; occurrence rate of gene loss, default: -l 0.2
```
e.g., python3 MLMSC.py -i species_trees/species_tree_0.newick -l 0.5
```
  
* Unlink probability; -u or --unlinkProb; the probability that a duplication is unlinked, default: -u 0.5
```
e.g., python3 MLMSC.py -i species_trees/species_tree_0.newick -u 0.5 
```
  
* Hemiplasy option: -h or --hemiplasy; whether or not the copy number hemiplasy is allowed, default: -h True
```
e.g., python3 MLMSC.py -i species_trees/species_tree_0.newick -h False
```
  
* Verbose option: -v or --verbose; detailed outputs for debugging purposes, default: -v False
```
e.g., python3 MLMSC.py -i species_trees/species_tree_0.newick -v True
```

* Number of repeats: -n or --numRepeats; number of gene trees simulated, defult: -n 1
```
e.g., python3 MLMSC.py -i species_trees/species_tree_0.newick -n 10
```

* Seed number: -s or --seed; set seed for reproduciblility, default -s None (random seed)
```
e.g., python3 MLMSC.py -i species_trees/species_tree_0.newick -s 0
```


### Command line outputs
* gene tree: an ascii drawing of the gene tree as a first-stage visualization, which does not cover the information of branch lengths. A much better visualization can be obtained by importing gene_tree.newick to many third party programs.
* Exception: ALL LOST: all gene lineages are lost, hence there is not gene tree.
  
### Output files
* gene_tree_untruncated.newick: intermediate output for debugging purposes, the fully labelled gene (with internal node names) tree before cutted from the loss points.
* gene_tree_truncated.newick: intermediate output for debugging purposes, the fully labelled gene (with internal node names) tree after cutted from the loss points.
* gene_tree.newick: final output for the end users, the final gene with internal node names removed and leaf names converted according to the names of species.

## Authors

* **Qiuyi Li** - *Initial work*
* **Geoffrey Law** - *Data structure*

## License

This project is licensed under the MIT License - see the [LICENSE.md](LICENSE.md) file for details.

## Acknowledgments

QL would like to thank Yao-ban Chan, Yupei You, Yichi Zhang, and Yiling Cao for helpful comments and assistance in  programming.
