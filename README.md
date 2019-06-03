# galaxy-tool-lca
A tool to determine the lowest common ancestor from BLAST results with taxonomy. This approach is partly based on MEGAN's (Huson et al., 2007) LCA method. This tool is more flexible and easier to use then MEGAN, it does not specificly use taxonids or sepperated mapping files. Instead the script handles files with the taxonomy present in de last column of the input file. Those input files can be generated with our BLAST pipeline (not been published yet) or you can create them manually.   

## Getting Started
### Prerequisites
python 2.7
### Download
```
git clone https://github.com/naturalis/galaxy-tool-lca
```

## Usage
There is an example input file included in the example folder, this file will be used to execute the example commands. The file consist of 11 columns, has a specific header and is tab seperated.<br />
<br />
**Column explanation:**

| Column name | Description |
| --- | --- |
| Query ID | Id of the input sequence (qseqid) |
| Subject | means Subject Title (stitle) |
| Subject accession | Subject accession (sacc) |
| Subject Taxonomy ID | unique Subject Taxonomy ID (staxid), this value can be any value and is not used the find the lca |
| Identity percentage | Identity percentage of hit () |
| Coverage | means Query Coverage Per Subject (qcovs) |
| Evalue | expect value of the hit (evalue) |
| Bitscore | Bit score of hit (bitscore) |
| Source | The source of were the taxonomy comes from, this value can be any value and is not used the find the lca |
| Taxonomy | This column contains the taxonomy of the hit in the order Kingdom / phylum / class / order / family / genus /species |

The script itself has multiple parameter options.<br />
**Parameters:**

| Parameter | Description |
| --- | --- |
| -i [input] | Input file |
| -o [output] | Output file |
| -b | bitscore top percentage treshold |
| -id | Minimum identity treshold |
| -cov | Minimum coverage treshold |
| -t | Check the top hit first or perform an lca analysis on all hits. Options:['only_lca', 'best_hit', "best_hits_range"] |
| -tid | Identity treshold for the tophit, only used when -t best_hit or best_hits_range |
| -tcov | Coverage treshold for the tophit, only used when -t best_hit or best_hits_range |
| -fh | Filter hits, filter out lines that contain a certain string |
| -flh | Filter lca hits, during the determination of the lca ignore this string  |
| -minbit | Minimum bitscore treshold |

### Quick start

## Source
Huson, D. H., Auch, A. F., Qi, J., & Schuster, S. C. (2007). MEGAN analysis of metagenomic data. Genome Research, 17(3), 377–386. http://doi.org/10.1101/gr.5969107

## Getting Started
### Prerequisites
This tool uses specifically the BLAST output as input
### Installing
Installing the tool for use in Galaxy
```
cd /home/galaxy/Tools
```
```
git clone https://github.com/naturalis/galaxy-tool-lca
```
Add the following line to /home/galaxy/galaxy/config/tool_conf.xml
```
<tool file="/home/galaxy/Tools/galaxy-tool-lca/lca.xml" />
```
