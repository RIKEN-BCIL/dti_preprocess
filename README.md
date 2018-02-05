# DTI_PREPROCESS
Unwarping of B0 inhomogeneity distortion, correction of eddy current distortion and motion, tensor calculation and QC

## Installation

Before installation of dti_preprocess, you need to install [FSL](https://www.fmrib.ox.ac.uk/fsl) (>5.0). You also require [gdcmdump](http://gdcm.sourceforge.net/html/gdcmdump.html) and [HCP pipleine](https://github.com/Washington-University/Pipelines) for scripts, getdwelltime and regdtiprep2hcp, respectively.

1. After uncompressing the downloaded dti_preprocess.zip, move dti_preprocess into /usr/local 

  ```
  sudo mv dti_preprocess /usr/local/
  ```

2. Add the following lines in .bashrc in your home directory

  ```
  export DTI_PREPROCESS=/usr/local/dti_preprocess;
  export PATH=${DTI_PREPROCESS}/bin:${PATH};
  ```

3. Modify the section of "Default environments" in `/usr/local/dti_preprocess/etc/conf/dti_preprocess.conf`, depending on your environments. 

4. Open new terminal and run dti_preprocess so that you should be able to see the help page

  ```
  dti_preprocess
  ```

## Usage
```
  Usage 1: Minimal data-based correction (using eddy_correct)

    dti_preprocess -k <dwi> -b <bvals> -r <bvecs> [option]

    -k <dwi>        : dwi 4D data
    -b <bvals>      : a text file containing a list of b-values
    -r <bvecs>      : a text file containing a list of b-vectors
          
  Usage 2: Data-based correction (using fieldmap, fugue and eddy_correct)

   2.1  Run fieldmap correction only :

    dti_preprocess -k <dwi> -t <num> -f <img> -m <img> [option]

   2.2  Run both fieldmap and eddy-current correction :

    dti_preprocess -k <dwi> -b <bvals> -r <bvecs> -t <num> -f <img> -m <img> [option]

    -t <num>        : dwell time (ms) of dwi in phase-encoding direction (divided by accerelation factor)
    -f <img>        : B0 fieldmap image (radian/sec)
    -m <img>        : B0 fieldmap magnitude image

    Options: 
    -u <x, x-, y, y-, z, or z->  : unwarp direction (default: y-)
    -D <img>        : mask file for dti image (by default, this is calculated by bet)
    -M <img>        : mask file for fieldmap magnitude image (by default, this is calculated by bet)
    -E <num>        : reference volume (default : 0th volume)
    -n              : do not register between fieldmap and dti data (requires to register beforehand)
    -U              : do not mask DTI images

  Usage 3: Model-based correction (using blip-up and down data, topup and eddy)
   
   3.1  Run fieldmap correction only :

    dti_preprocess -k <dwi> -K <dwi-PER> -t <num> [options]

   3.2  Run both fieldmap and eddy-current correction :

    dti_preprocess -k <dwi> -b <bvals> -r <bvecs> -K <dwi-PER> -B <bvals-PER> -R <bvecs-PER> -t <num> [options]

    -K <dwi-PER>    : dwi 4D data with phase-encode reversed (PER)
    -B <bvals-PER>  : bvals for dwi-PER
    -R <bvecs-PER>  : bvecs for dwi-PER
    -t <num>        : dwll time (ms) of dwi in phase-encoding direction
   
    Options:
    -u <x or y>     : phase-reversed direction (default: y)
    -p              : optimized for single-shell data
    -w              : potentially better converge if there is substantial subject movement

  General options applied for all usages:
    -o <dir>        : output directory (default is <dwi 4D data>.prep)
    -F              : use the actual directory name given (i.e. do not add + to make a new directory)
    -c              : use mcflirt instead of flirt (faster but may not be accurate)
    -H <HCP subject dir> : registeter to HCP pipelined directory and run QA
    -v              : verbose
    -h              : output help page
```
