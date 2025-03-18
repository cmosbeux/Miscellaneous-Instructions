# Tools for working with ISMIP6 data

<div style="background-color: #f8d7da; color: #721c24; border: 1px solid #f5c6cb; padding: 10px; border-radius: 5px; margin-bottom: 20px;">
  <strong style="font-size: 1.2em;">⚠️ Warning:</strong> This page is based on 
  <a href="https://git.smce.nasa.gov/eis-sealevel/eis-sea-level-change-general/-/blob/master/ismip6/README.md" target="_blank">ISMIP6 README</a>.
</div>
<br>
        
This directory contains instructions and code to work with datasets from the Ice Sheet Model Intercomparison Project for CMIP6 (ISMIP6). The ISMIP6 ice sheet projection datasets were used in the IPCC Assessment Report 6 (AR6) as the ice sheet component in 21st century sea-level change projections.

## Obtaining ISMIP6 datasets
ISMIP6 datasets are hosted by the University at Buffalo and available for download using Globus APIs. More information can be found here: https://theghub.org/2022-07-29-23-00-23/2022-07-29-23-01-39/dataset-listing.

To obtain datasets, a Globus account is needed. Once a Globus account is created, the datasets can be accessed using the Globus command line interface (CLI). More info here: https://docs.globus.org/cli/. 


### Install Globus CLI
Here are some quick-start steps to install the Globus CLI on the SMCE JupyterHub. From a terminal:
1. Install pipx

        python3 -m pip install --user pipx
        python3 -m pipx ensurepath

1. Restart the Terminal
        
        pipx install globus-cli

1. Login to Globus

        globus login --no-local-server

1. More quick start info here: https://docs.globus.org/cli/quickstart/

1. Search for available ISMIP6 endpoints

        globus endpoint search 'ISMIP6'

1. List the contents of the GHub-ISMIP6-Forcing endpoint:

        globus ls 'ad1a6ed8-4de0-4490-93a9-8258931766c7:/'

### Install Globus Personal Connect
This is needed to establish the SMCE JupyterHub as a Globus endpoint. From a terminal:

1. Download tar gzip file, untar/unzip, and install:

        wget https://downloads.globus.org/globus-connect-personal/linux/stable/globusconnectpersonal-latest.tgz
        tar xzf globusconnectpersonal-latest.tgz
   
1. Enter into the new directory and run`globusconnectpersonal`
        cd globusconnectpersonal-latest
        ./globusconnectpersonal 

1. Add ```globusconnectpersonal-3.1.6/``` to the ```$PATH```. For example:

        export PATH=/home/user/globusconnectpersonal-3.2.6:$PATH
  
1. Start the Globus Personal Connect client

        globusconnectpersonal -start &

1. Test a transfer of one of the ISMIP6 README files to the current directory:

        globus transfer 'ad1a6ed8-4de0-4490-93a9-8258931766c7:/GrIS/Ocean_Forcing/README_GrIS_Ocean_Forcing.txt' `globus endpoint local-id`:./README_GrIS_Ocean_Forcing.txt

1. To download the entire colllection `ISMIP6-2300`, it seems that the following command works:

        globus transfer '3881e705-3290-4e81-8990-0ef8cfb54d74:/*' `globus endpoint local-id`:./bettik/test-globus/

1. To check the list of all tasks, use: ```globus task list```
1. To check the status of that transfer task, use: ```globus task show <task ID that is output by the transfer command>```

More info anout the Globus Personal Connect client here: https://docs.globus.org/how-to/globus-connect-personal-linux/

### Download ISMIP6 datasets
Now, you are ready to download any ISMIP6 datasets that are available on the GHub endpoint!
