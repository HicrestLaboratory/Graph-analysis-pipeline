This is a pipeline for analyzing big graphs on a slurm managed cluster.
To run the pipeline, you will first need to create a rapids-ai conda environment
To do so, load anaconda and follow the instructions at https://rapids.ai/start.html

After this, you have to 
-Create a dask scheduler
-Start the dask-cuda workers
-Run the centrality_tests python script

To do so, we have provided three example scripts (dask_schedule_*.sh) that you can easily adapt to your specific machine.
Just substitute the LOCAL_DIRECTORY variable for your local directory, and modify the dask_schedule_third script so that it points to your copy of the centrality_tests.py file and to your graph files. You may also want to modify the SBATCH parameters depending on your machine and the dimension of your graph.
Then run:

sbatch dask_schedule_first
sbatch dask_schedule_second
sbatch dask_schedule_third

This pipeline only supports graphs in edgelist format, labeled with consecutive integer. If you have an edgelist with arbitrarily named nodes, you can convert it in using the "relable_graph.py" python script.  
