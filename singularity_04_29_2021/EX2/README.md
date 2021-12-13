# Example with using tensorflow v1

Example of using tensorflow v1 on Hoffman2

This example will download a tensorflow v1 container from DockerHub

Set up interactive job

```
qrsh -l rh7,h_data=20G,h_rt=0:20:00
```

Set up singularity

```
module load singularity
```

Pull tensorflow from DockerHub. Changed deafult cache dir so $HOME does not fill up

```
export SINGULARITY_CACHEDIR=$SCRATCH/singularity_cache
singularity pull tensorflow-1.15.5-gpu-jupyter.sif docker://tensorflow/tensorflow:1.15.5-gpu-jupyter
```

Run container

```
singularity exec --userns tensorflow-1.15.5-gpu-jupyter.sif python3 tensorflow1-example.py > tensorflow1-example.out
exit
```

