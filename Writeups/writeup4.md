```
Writeup 4 
Alex Stanford 


How could one add a differential expression analysis (DESeq2) step to the rnaseq_pipeline_array_depend.sh script such that DESeq2 runs
only after all salmon jobs for all samples have completed? (No code required - describe conceptually)

You could add a differential expression analysis step to the rnaseq_pipeline_array_depend.sh script that runs only after all the
salmon jobs have completed by implementing slurm job dependencies. This way your code for the differential expression analysis is 
dependent on all salmon jobs completing, only starting when this is complete. 

```
