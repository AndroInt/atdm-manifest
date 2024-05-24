# ATDM Toradex oe-core Setup

Since OpenEmbedded requires several git repositories to build our images, starting with V2.1 images, <br/>
we use a utility called 'repo'. The repo manifest manages the various git repositories and their branches.<br/>

Install the repo bootstrap binary: <br/>

```
$  mkdir ~/bin
$  export PATH=~/bin:$PATH
$  curl https://commondatastorage.googleapis.com/git-repo-downloads/repo > ~/bin/repo
$  chmod a+x ~/bin/repo
```

This manifest allows setting up TorizonCore or Toradex Images for ATDM platform.
The final build will prepare Tezi image that can be installed on ATDM board.

## Pre-requisite for yocto compilation

- [Guide for one time installation for specific platform](https://docs.yoctoproject.org/ref-manual/system-requirements.html#required-packages-for-the-build-host)

## Repo init link

Currently we are supporting **kirkstone** branch. We have also added support for master branch but not sure for compilation success. <br/>

```
$ repo init -u https://github.com/DeviceSolutions/toradex-manifest.git -b kirkstone-6.x.y -m torizoncore/atdm.xml
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

