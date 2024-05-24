# ATDM Toradex oe-core Setup

Starting with V2.1 images, OpenEmbedded requires multiple git repositories to build our images. To manage this complexity, we use a utility called 'repo'. The repo manifest handles the various git repositories and their respective branches.

Install the repo bootstrap binary: <br/>

```
$  mkdir ~/bin
$  export PATH=~/bin:$PATH
$  curl https://commondatastorage.googleapis.com/git-repo-downloads/repo > ~/bin/repo
$  chmod a+x ~/bin/repo
```

This manifest facilitates the setup of TorizonCore or Toradex Images for the ATDM platform. The final build will generate a TEZI image that can be installed on the ATDM board.

## Pre-requisite for yocto compilation

- [Guide for one time installation for specific platform](https://docs.yoctoproject.org/ref-manual/system-requirements.html#required-packages-for-the-build-host)

## Repo init link

We currently support the Kirkstone branch and have also added support for the master branch, but its compilation success is not guaranteed.

```
$ repo init -u https://github.com/AndroInt/atdm-manifest.git -b kirkstone-6.x.y -m torizoncore/atdm.xml
$ repo sync
```

## Prepare compilation environment

**command**: [MACHINE=<MACHINE>] source setup-environment [BUILDDIR]

for **ATDM** board based on imx8mp command example:<br/>
```
$ export LC_ALL="en_US.UTF-8"
$ export LC_CTYPE="en_US.UTF-8"
$ MACHINE=verdin-imx8mp source setup-environment build-verdin-imx8mp
```

## start compilation

```
$ bitbake torizon-core-docker
```

## Tezi image directory

[BUILDDIR]/deploy/images/verdin-imx8mp/ <br/>

