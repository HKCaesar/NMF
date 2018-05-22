# Scripts for running NMF and doing preliminary analysis

### These scripts are written to run NMF for a number of Ks, each with multiple repeats, and to output the stability scores of the results from each K.

**Python3 environment is required**

To try these scripts, clone/download the whole repository to your local computer and type the following command in terminal:
```
bash run_nmf.sh > example_run_log.txt
```
This will run NMF on the `example_data.csv` dataset, and create the `example_results` folder and its content, as well as the `example_run_log.txt` file. 

You can modify run_nmf.sh to run your own dataset (tab or comma delimited files with genes as row names and cells as column names) with the parameters of your own choice.

The Results_obj.pkl file generated by these scripts can be loaded into python by:
```
import nmf_fxn
Results_obj=nmf_fxn.load_obj("Results_obj.pkl”)
```
It contains the data used, parameters used, and the decomposed matrices in the form of pandas dataframe. 


Because the algorithm can run for a long time with large dataset, `run_nmf.sh` can be called multiple times in parallel to run different Ks and/or repeats at the same time (for example, as individual jobs on a cluster). Once all the jobs are done, the results from them can then be integrated into a single object and be analyzed together by the following command:
```
bash integrate_and_output.sh
```
This script will also generate an R object that contains the factor matrices and the top ranking genes resulting from the NMF runs for people who likes to to subsequent analysis in R. Example of running multiple NMFs and integrating the results are not included in this repository.