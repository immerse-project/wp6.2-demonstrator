# wp6.2-demonstator

## Quick start on Archer2 (UK National Supercomputing Service)
```shell
git clone git@github.com:immerse-project/wp6.2-demonstrator.git
cd wp6.2-demonstrator
./setup
```
The setup script downloads nemo, compiles tools and configurations, and submits the scripts to generate domains and weights.
Wait until all domains and weights are generated, then run NEMO.

To run NEMO:
```shell
cd nemo/cfgs/AGRIF_QCO/GSRIDGE36Zx2-GIBSTRA36Zx2/
../../../scripts/python/mkslurm_immerse -S 24 -s 16 -m 1 -C 3712 -g 0 -a n01-CLASS -q short -t 0-00:20:00 --gnu > run_nemo-short.slurm
```
There are a few variables to set in `run_nemo-short.slurm`. For example, the following variables will generate a 2-hour simulation split in 1-hour jobs.
```bash
# ========================================================
# PARAMETERS TO SET
# Restart frequency (<0 days, >0 hours)
FREQRST=1
# Simulation length (<0 days, >0 hours)
LENGTH=2
# Parent initial time step (0: infer from time.step)
# PARENT_IT000 != 0 -> auto-resubmission is switched OFF
PARENT_IT000=0
# Name of this script (to resubmit)
SCRIPTNAME=run_nemo-short.slurm
# =======================================================
```
Finally:
```shell
sbatch run_nemo-short.slurm
```

Example `mkslurm_immerse` settings for production runs:
```shell
../../../scripts/python/mkslurm_immerse -S 24 -s 16 -m 1 -C 5504 -g 0 -a n01-CLASS -j WP6.2 -t 1-00:00:00 --gnu > run_nemo.slurm
```

## Setup
### Parent: Global
Resolution:
- Horizontal: 1/12°
- Vertical: 75 levels

<img alt="eORCA12" src="figures/parent.png" width="50%">

### Child 1: Greenland-Scotland Ridge
Resolution:
- Horizontal: 1/36°
- Vertical: 150 levels

![GSRIDGE36](figures/frame-bare.png)

### Child 2: Gibraltar Strait
Resolution:
- Horizontal: 1/36°
- Vertical: 150 levels
