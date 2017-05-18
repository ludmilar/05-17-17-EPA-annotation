
1. Make searchable database from Araport11

    `makeblastdb -in Araport11_genes.201606.pep.fasta -parse_seqids -dbtype prot`

2. Created list from Matrix table with epa only:  **/Users/ncbi-blast-2.6.0+/bin/Files/epa_from_matrix.csv** 

3. **Get corresponded** sequences from Ep prot database   `blastdbcmd -entry_batch /Users/ncbi-blast-2.6.0+/bin/Files/epa_from_matrix.csv -db epa_vf_proteins.txt -out epa_from_matrix_prot_seq.csv`

4. This file had 40,799 entries. After collecting sequences, 31,767. Error file had 9032. However some sequences that does not have protein seq, are present  in Ep DNA database. So going to repeat collecting **sequences from DNA**. `makeblastdb -in epa_vf_genes.txt -parse_seqids -dbtype nucl`

5. Run **blastdbcmd** with DNA database. `blastdbcmd -entry_batch epa_from_matrix.csv -db epa_vf_genes.txt -out epa_from_matrix_dna_seq.csv`

6. After running DNA database - all sequences were retrieved into file:  **epa_from_matrix_dna_seq.csv**

7. Now run the batch BLAST (**blastx** - translated nucleotides vs protein db) of those epa seq vs Araport11_genes.201606: `blastx -db Araport11_genes.201606.pep.fasta -query epa_from_matrix_dna_seq.csv -out epa_from_matrix_dna_seqANNOTATED.csv -evalue 10e-10 -max_target_seqs 1 -outfmt 10` (Started on 05-18-17, 3:00pm, finished - )


> Written with [StackEdit](https://stackedit.io/).
