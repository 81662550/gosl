# Installing Gosl on Ubuntu Linux (Debian)

<div id="container">
<p>
<a href="https://github.com/cpmech/gosl/blob/master/doc/InstallationOnUbuntu.md"><img src="icon-linux.png"></a>
<a href="https://github.com/cpmech/gosl/blob/master/doc/InstallationOnUbuntu.md"><img src="icon-debian.png"></a>
<a href="https://github.com/cpmech/gosl/blob/master/doc/InstallationOnUbuntu.md"><img src="icon-ubuntu.png"></a>
</p>
</div>



## 0 [Required] Install Go language

1. [See instructions here](https://github.com/cpmech/gosl/blob/master/doc/InstallAndTestGo.md)



## 1 [Required] Install some dependencies:

1. Run the following commands

```bash
sudo apt-get install libopenmpi-dev libhwloc-dev libsuitesparse-dev libmumps-dev 
sudo apt-get install gfortran libvtk6-dev python-scipy python-matplotlib dvipng
sudo apt-get install libfftw3-dev libfftw3-mpi-dev libmetis-dev
sudo apt-get install liblapacke-dev libopenblas-dev libhdf5-dev git
```



## 2 [Optional] Install Intel MKL

1. Download MKL (~900Mb) from [the intel MKL website](https://software.intel.com/en-us/intel-mkl). Notes:
   1. Click on Free Download
   2. Need to sign-in
   3. [See figure of download options here](https://github.com/cpmech/gosl/blob/master/doc/intel-mkl-page.png)
2. Run the following commands (must install using `sudo`)

```bash
mkdir -p $HOME/xpkg && cd $HOME/xpkg
tar xzf tar xzf l_mkl_2019.0.117.tgz
cd cd l_mkl_2019.0.117/
sudo bash install_GUI.sh
```

3. Click next then make sure that the installation directory is **/opt/intel**. Then click Install.



## 3 [Required] Clone and install Gosl

1. Run the following commands

```bash
mkdir -p ${GOPATH%:*}/src/github.com/cpmech
cd ${GOPATH%:*}/src/github.com/cpmech
git clone https://github.com/cpmech/gosl.git
cd gosl
./all.bash
```



## 4 [Optional] Test la/mkl subpackage

1. Run the following commands

```bash
cd ${GOPATH%:*}/src/github.com/cpmech/la/mkl
go install
go test
```



## 5 [Optional] Install VTK

```bash
sudo apt-get install libvtk7-dev
cd ${GOPATH%:*}/src/github.com/cpmech/vtk
./xgenflagsfile.bash
go install
go test
cd ../examples
go run vtk_isosurf01.go
```
