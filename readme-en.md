**This is the readme file in English**

This tutorial aims to use **DIAMOND** aligner and **MEGAN** to perform whole-genome metagenomic and will cover all steps starting from getting needed data to data interpretation.

Please, keep in mind that there will be a need server or high computing power with at least 8 GB RAM for MEGAN and 16 GB RAM for  DIAMOND and more than 24 processing cores for DIAMOND. I would suggest getting google cloud VM instance or AWS instance so CPU performance can be adjusted.

# Tools installation:

## 1- DIAMOND

There are different ways to install DIMOND the easiest way to use conda, through using the following code.

``` 
conda install -c bioconda diamond
```
please use this [link](https://docs.conda.io/projects/conda/en/latest/user-guide/install/index.html#installing-conda-on-a-system-that-has-other-python-installations-or-packages) to install conda in case conda was missing

**Another way**

Install DIAMOND by downloading it in a binary format for immediate use (The current diamond version is 0.9.31)
```
wget http://github.com/bbuchfink/diamond/releases/download/v0.9.31/diamond-linux64.tar.gz
tar xzf diamond-linux64.tar.gz
```
Do not forget to add the extracted files to the executable search PATH. 

To get the latest DIAMOND version, check this [link](http://www.diamondsearch.org/index.php)

**Another way**

Finally, compile DIAMOND from source:

```
wget http://github.com/bbuchfink/diamond/archive/v0.9.31.tar.gz
tar xzf v0.9.31.tar.gz
cd diamond-0.9.31
mkdir bin
cd bin
cmake ..
make install
```

For more information regarding DIAMOND installation, please refer to the following [link](http://www.diamondsearch.org/index.php?pages/installation/)


# 2- MEGAN
There are two versions of MEGAN, MEGAN6 Community Edition, and MEGAN6 Ultimate Edition (require license key). In this tutorial, we will install MEGAN6 Community Edition only.

Different MEGAN6 installers are available based on OS. Please follow this [link](https://software-ab.informatik.uni-tuebingen.de/download/megan6/welcome.html) to download the appropriate version.

To install current version 6.18.11 on Linux, use the following instructions:

```
wget https://software-ab.informatik.uni-tuebingen.de/download/megan6/MEGAN_Community_unix_6_18_11.sh
chmod +x MEGAN_unix_6_18_11.sh 
./MEGAN_unix_6_18_11.sh
``` 

Please note, to MEGANize DIAMOND result, a mapping file should be downloaded:

The following file maps NCBI-nr accessions to taxonomic and functional classes (eggNOG, InterPro2GO, and SEED), unzip before use:
[megan-map-Oct2019.db.zip](https://software-ab.informatik.uni-tuebingen.de/download/megan6/megan-map-Oct2019.db.zip)
```
wget https://software-ab.informatik.uni-tuebingen.de/download/megan6/megan-map-Oct2019.db.zip
unzip megan-map-Oct2019.db.zip
```

The following file maps genomic DNA accessions to taxonomic classes, unzip before use:
[megan-nucl-Oct2019.db.zip](https://software-ab.informatik.uni-tuebingen.de/download/megan6/megan-nucl-Oct2019.db.zip)
```
wget https://software-ab.informatik.uni-tuebingen.de/download/megan6/megan-nucl-Oct2019.db.zip
unzip megan-nucl-Oct2019.db.zip
```
