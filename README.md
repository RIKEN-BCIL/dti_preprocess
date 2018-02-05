# DTI_PREPROCESS
Unwarping of B0 inhomogeneity distortion, correction of eddy current distortion and motion, tensor calculation and QC using FSL

## Installation

Before installation of dti_preprocess, you need to install FSL (>5.0). You also require [gdcmdump] (http://gdcm.sourceforge.net/html/gdcmdump.html) and [HCP pipleine] (https://github.com/Washington-University/Pipelines) for some scripts (getdwelltime and regdtiprep2hcp).

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


