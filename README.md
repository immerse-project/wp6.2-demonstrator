# wp6.2-demonstator

Quick start on Archer2:
```shell
git clone git@github.com:immerse-project/wp6.2-demonstrator.git
cd wp6.2-demonstrator
./setup
```

Slurm examples:
```shell
mkslurm_immerse -S 24 -s 16 -m 1 -C 9006 -g 0 -a n01-CLASS -j WP6.2 --gnu > run_nemo.slurm
mkslurm_immerse -S 24 -s 16 -m 1 -C 3668 -g 0 -a n01-CLASS -j WP6.2-test -q short --gnu > run_nemo-short.slurm
```
