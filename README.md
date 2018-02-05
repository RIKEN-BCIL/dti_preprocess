# dti_preprocess
Unwarping of B0 inhomogeneity distortion, correction of eddy current distortion and motion, tensor calculation and QC using FSL

##Installation

0. Before installation of dti_preprocess, you need to install FSL (>5.0). You also require gdcmdump and HCP pipleine for some scripts (getdwelltime and regdtiprep2hcp).

1. After uncompressing the downloaded dti_preprocess.tar.gz, move dti_preprocess into /usr/local 

`sudo mv dti_preprocess /usr/local/`

2. Add the following lines in .bashrc in your home directory

`DTI_PREPROCESS=/usr/local/dti_preprocess`
`PATH=${DTI_PREPROCESS}/bin:${PATH}`
`export DTI_PREPROCESS PATH`

3. Modify the section of "Default environments" in /usr/local/dti_preprocess/etc/conf/dti_preprocess.conf, depending on your environments. 

4. Open new terminal and run dti_preprocess so that you should be able to see the help page

dti_preprocess

