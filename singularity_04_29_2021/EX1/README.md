# Example 1

Running Singularity on Hoffman2

This example uses Singularity to run TensorFlow on Hoffman2

Files:
- tf-example.py: sample Tensorflow example
- tf-example.job: Batch Job script

Examples of using an Interactive job `singularity shell` and Batch Job `singularity exec`

Hoffman2 has a location of pre-built containers `$H2_CONTAINER_LOC`

```
cat $H2_CONTAINER_LOC/README
```

## Interactive job

Using Singularity, run an interactive shell of Tensorflow

Setting up interactive session

```
qrsh -l rh7,h_data=15G,h_rt=0:30:00
```

set up singularity

```
module load singularity
singularity shell --userns $H2_CONTAINER_LOC/tensorflow-2.4.1-gpu-jupyter.sif
```

Run python

```
python3 tf-example.py > tf-example.out
exit
exit
```

The output file is in tf-example.out

## Batch Job

Using Singularity, ran an Batch job using Tensorflow

```
qsub tf-example.job
```

The output file is in tf-example-batch.out


