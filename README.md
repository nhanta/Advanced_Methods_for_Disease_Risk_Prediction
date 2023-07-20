# Advanced Methods for Disease Risk Prediction
 The study outlines a workflow integrating the Genome Analysis Toolkit (GATK) and PRS to process and analyze data from next-generation sequencing (NGS) platforms. The article also discusses implementing machine learning models and neural networks for predicting disease risk and selecting significant genetic variants.
## Tool Installations
### Installing GATK 4.2.0.0
```
wget https://github.com/broadinstitute/gatk/releases/download/4.2.0.0/gatk-4.2.0.0.zip
unzip gatk-4.2.0.0.zip -d /path to your directory/
export PATH=$PATH:/path to your directory/
```
### Installing Samtools
```
wget https://sourceforge.net/projects/samtools/files/samtools/
tar xvjf samtools-1.1.tar.bz2
cd samtools-1.1
make
export PATH=$PATH:/path to your directory/
```
### Installing Other Tools
- `conda install -c bioconda bcftools`
- `conda install -c bioconda plink`
- `conda install -c bioconda sra-tools`
- `conda install -c bioconda fastqc`
- `conda install -c bioconda trimmomatic`
- `conda install -c bioconda bwa`
- `conda install -c bioconda tabix`
- `conda install vcftools`
- `pip install bed-reader`
- `pip install captum`
## Data Preparation 
Single-end read data includes [139 obesity samples](https://www.ncbi.nlm.nih.gov/Traces/study/?acc=SRP139885&o=acc_s%3Aa) from Ion Torrent. We run [bash script files](https://github.com/nhanta/Advanced_Methods_for_Disease_Risk_Prediction/tree/main/gatk) to download data, and extract the data to fastq.
- Download pileup data by sratools: `prefetch --option-file SRR_Acc_List.txt`
- Decompress sra to fastq: `sh sra_to_fastq.sh`
- Fix fastq files: `sh fix_fastq.sh`
## Implementing GATK 
In the study, this part belongs to the **initial data preprocessing** and **variant calling**:

`sh gatk_obesity.sh [gatk directory] [input directory] [output directory] [number of threads]`

Folders can be arranged as follows:
```
GATK
|-- Work            
|   |-- GATK directory                   Include GRCh38 and related data.
|   `-- GATK 4.2.0.0                     GATK version 4.2.0.0.                 
|   `-- snpEff/Funcotator                To annotate variants.
|-- Input directory                      Include 139 samples, type of fastq.
|-- Output directory                     To generate result files.
```



