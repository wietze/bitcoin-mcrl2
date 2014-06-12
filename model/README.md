##Contents
* model.mcrl2 (the actual model)
* cases/1_incorrect_messages/
    * a_invalid_amount.mcrl2
    * b_invalid_outputs.mcrl2
    * c_invalid_inputs.mcrl2
* cases/2_contradictin_messages/
    * a_same_input_different_output.mcrl2
* cases/3_partial_messages/
* cases/4_ignoring_incomming_messages/
    * a_peer.mcrl2
    * b_tx_receiver.mcrl2
    * c_tx_sender.mcrl2
    * d_block.mcrl2

To see what the models in subdirectories of cases/ exactly specify, please open the mcrl2 files and read the comments at the beginning.

##Analysis
A few important notes on the created models.

###Number of transactions
The number of allowed transactions is 0 by default; by changing the constant `MAX_NUMBER_OF_NEW_TRANSACTIONS` into value greater than 0, there will be allowed as many transactions as you set. Note that linearising models with a high number of allowed transactions will take significantly longer, as the state space increases rapidly. 

###Majority
All models can be tried in various configurations; for instance, most models have exactly one malicous peer. By changing the number of malicious peers, the behaviour of the model also changes. If more than 50% of the nodes is malicious, the network is unreliable, as the malicous nodes might introduce fake information or ignore real information. 
You can turn normal peers into malicious peers by changing Peer() processes in the `init` clause too MaliciousPeer processes. 

##Running a simulation
Make sure you have installed the [mCRL2](http://www.mcrl2.org/) toolkit. 

To run a simulation of a model, first generate a linear program specification (LPS) using `mcrl22lps`:

    $ ./bin/mcrl22lps model.mcrl2 model.lps

Secondly, run `lpssim` for command line simulation or `lpsxsim` for a GUI:

    $ ./bin/lpssim model.lps
    $ ./bin/lpsxsim model.lps
    
The command line interface or GUI will guide you through the simulation.

##Generating an LTS (Labeled Transition System)
To generate an LTS, first generate an LPS using `mcrl22lps`:

    $ ./bin/mcrl22lps model.mcrl2 model.lps

Secondly, run `lps2lts` with the following parameters:

    $ ./bin/lps2lts -aerror -D -t1 -v model.lps model.lts
    
Running this command, an lts will be generated. When the linearisation has completed, the number of states, depth and number of traces will be printed.
###On error actions
If an `error` action occurs, the file 'model.lps_act_0_error.trc' will be generated, containing information about the trace that leads to the `error` action. To get the trace in plaintext, run `tracepp`:

    $ ./bin/tracepp model.lps_act_0_error.trc trace.txt
    
The file 'trace.txt' now contains the trace in plain text.


