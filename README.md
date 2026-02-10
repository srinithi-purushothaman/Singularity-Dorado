## Singularity-Dorado
Definition file to build singularity image for ONT basecaller Dorado in HPC.

## Definition file 
- [Dorado-definition file](https://github.com/srinithi-purushothaman/Singularity-Dorado/blob/main/dorado_build_v1.1.def)

## Build image with Singularity (with root permissions, e.g. cloud VM)
```
sudo singularity build dorado.sif dorado_build_v1.1.def
```
## Convert SIF to sandbox (optional)

If you already have a `.sif` image and want to reduce the overhead of decompressing it during SLURM jobs, you can convert it to a sandbox container
```
singularity build --sandbox dorado_sandbox/ dorado.sif
```
## Run the image
```
singularity exec --nv dorado_sandbox/ dorado --help # --nv indicatees the use of GPUs
```
## Tested environment
HPC scheduler: SLURM
GPU: NVIDIA A100 and V100
Singularity version: 3.12

## Notes

- GPU basecalling requires NVIDIA drivers on the host system.
- Make sure the NVIDIA driver version in your HPC environment is compatible with the container and CUDA requirements.
- Commands may use `apptainer` instead of `singularity` depending on the cluster.

