```
Writeup 1 
Alex stanford 

  
 How many slurm job will be submitted?
I believe 3 slurm jobs will be submitted based on the code #SBATCH --array= 0-2
   

 What is the purpose of the if statement?
The if statement makes sure each task isn't done more than once by a different slurm job. Essentially allowing each line of the text file to have an assigned job and ensuring this.
   

 What is the expected output in each *.out file?
The expected output in each out .out file would be the index and the value of the assigned line.
```
