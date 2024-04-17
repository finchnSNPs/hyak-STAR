# UW HYAK STAR container

See [STAR repo by Alex Dobin](https://github.com/alexdobin/STAR.git) for more details and the manual for using STAR. 

To provide a version of STAR for HYAK users, I converted the [Dockerfile](https://github.com/alexdobin/STAR/blob/master/extras/docker/Dockerfile) provided by Dobin into an `apptainer` .def file. The changes were minor. The only addition that was required was to install vim-common and all of its dependencies to have `xxd` which is required for building STAR. 

### Building the STAR container

Download the `STAR_aligner.def` file from this repo. 

```shell terminal=true
$ wget https://github.com/finchnSNPs/hyak-STAR/blob/main/STAR_aligner.def
```

Build the `apptainer` container. On HYAK, load the `apptainer` module with `module load apptainer` from an [interactive job](https://hyak.uw.edu/docs/compute/scheduling-jobs#interactive-node-partitions).

```shell terminal=true
$ apptainer build STAR_aligner.sif STAR_aligner.def
```

Test the container.

```shell terminal=true
$ apptainer run STAR_aligner.sif STAR -h
$ apptainer run STAR_aligner.sif STAR --version
```
