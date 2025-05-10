# StringRebuilder-from-Paired-k-mers

# Description

This script reconstructs a DNA string from a set of paired 
𝑘 k-mers with a known distance  𝑑 d between the pairs. It is typically used in genome assembly processes where reads are given as pairs of short sequences (left and right parts), and the original string must be reconstructed from these overlaps.

The function assumes that the pairs are given in an appropriate order, such as one obtained from a de Bruijn graph path traversal.

# Usage
```
Example:
k = 3
d = 1
pairs = [("ACC", "ATA"),
         ("ACT", "ATT"),
         ("ATA", "TGA"),
         ("ATT", "TGA"),
         ("CAC", "GAT"),
         ("CCG", "TAC"),
         ("CGA", "ACT"),
         ("CTG", "AGC"),
         ("CTG", "TTC"),
         ("GAA", "CTT"),
         ("GAT", "CTG"),
         ("GAT", "CTG"),
         ("TAC", "GAT"),
         ("TCT", "AAG"),
         ("TGA", "GCT"),
         ("TGA", "TCT"),
         ("TTC", "GAA")]

result = ReconstructString(k, d, pairs)
print(result)
```
# Output:
ACCTATCGAGGATTCTAACAATTGTAATCCCGAGTG

# Function
```
def ReconstructString(k, d, pairs):
    first_kmer = pairs[0][0]
    reconstructed_string = first_kmer

    for pair in pairs[1:]:
        reconstructed_string += pair[0][-1]

    for pair in pairs:
        reconstructed_string += pair[1][:d]

    return reconstructed_string
```
# Applications
* Genome Assembly from paired reads.
* Bioinformatics education and algorithms involving reconstruction from graph paths.
* k-d-mer based analysis in DNA sequence alignment and comparative genomics.

#  License
This project is licensed under the MIT License.


