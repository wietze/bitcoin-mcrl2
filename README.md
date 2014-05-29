Bitcoin Protocol
===============
In order to verify whether the Bitcoin Protocol is as safe as it claims to be, a formal verification of the Bitcoin Protocol is necessary. By creating a model of the Bitcoin Protocol, as specified in [Bitcoin Core](https://github.com/bitcoin/bitcoin), it is possible to draw conclusions on the design of the protocol. This project intends to investigate this issue.

The mCRL2 toolset is used to verify the Bitcoin Protocol. For more information and to download the toolkit, please visit [mcrl2.org](http://www.mcrl2.org/).  

## Model
In the *model* subdirectory, you can find a simplified model of the Bitcoin Protocol expressed in mCRL2. To verify the model, we make use of scenario-based analysis. Therefore, multiple versions of the model are included in this directory, all representing a certain scenario. 

## Requirements
In the *requirements* subdirectory, you can find requirements - expressed in mu-Calculus - that will be verified against the created models. 

## Running
Instructions on how to run the files in this repository with the tools from mCRL2 will be added here soon. 



__NOTE: this repository is still under development__