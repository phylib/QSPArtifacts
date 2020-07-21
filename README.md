# QSPArtifacts

This repository contains software artifacts for the the paper:
_Philipp Moll, Selina Isak, Hermann Hellwagner, Jeff Burke. A Quadtree-based Synchronization Protocol for Inter-Server Game State Synchronization. Submitted to Computer Networks, Elsevier._

For more information about this work, or the paper, please contact the corresponding
author ([Philipp Moll](mailto:philipp.moll@itec.aau.at)).

The repository is structured as follows:

- **Minecraft_Traces**: Contains material for generating the Minecraft traces used for the evaluation
- **ZMQ_Client**: Contains the Python ZMQ Client
- **NDN_Clients**: Contains the NDN-based Clients implementing the QSP and SVS protocol
- **MiniNDN**: Contains the MineNDN code used for experimentation

To install all dependencies, checkout the MiniNDN repository checkout the
`install.sh` script of the linked MiniNDN (forked) repository and execute
`./install.sh -a`. Alternatively, follow the instructions given in the
individual subrepositories.
