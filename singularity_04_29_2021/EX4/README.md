# Using Singularity on GPU

Example: Using PyTorch


Singularity can be ran on GPU nodes on Hoffman2

No need to install divers or libraries, just load the container

Files:

- pytorch-gpu.job: Job script to run your job
- pytorch-gpu.py: Example pytorch example

To run this job:

```
qsub pytorch-gpu.job
```

