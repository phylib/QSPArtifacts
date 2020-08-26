# Capturing Minecraft Change Traces

For capturing the changes in the Minecraft world, the following steps are
required.

1. A SpigotMC Minecraft Server enriched with the _change-logger_ and the _AutoOppPlugin_ needs to be started
1. The mineflayer-based emulated clients need to be started and stopped after a predefined time
1. The Spigot Server needs to be shutdown
1. The change traces can be found in the plugins data folder.
1. To use the change traces for the QSP evaluation clients, a post-processing step is required.

In the following, the individual steps to reproduce the traces are explained.

## Installation of SpigotMC

For the installation of SpigotMC, please follow the part `Installation of modified Spigot` from: https://github.com/phylib/ACM-ICN-19-Reproducibility/blob/master/SourceCode/README.md

### Change-Logger Plugin

The source code of the `change-logger` plugin can be found on [GitHub](https://github.com/phylib/MinecraftNDN-RAFNET19/tree/master/gamestate-changes/change_logger). Please follow the instruction given in the repository's `README` and put the compiled plugin to the plugin folder of spigot.

###  AutoOppPlugin

The `AutoOppPlugin` is accessible on [GitHub](https://github.com/phylib/AutoOppPlugin) and can be compiled with `maven`. Put the compiled Plugin in the plugin folder of Spigot.

## Installation and Execution of emulated players.

With submodules initialized, the folder `mc_wanderer` contains the mineflayer-based script that controls the emulated clients. To install the dependencies, install `nodejs` and `npm`, then execute:

    npm install .

The script `squareWanderer.js` is the implementation of a  single client. To start multiple clients, the script `executeSquareWanderer.py` can be executed. Execute `python3 ./executeSquareWanderer.py -h` to display possible parameters. To generate the traces used in the papers, traces of the following three settings were generated:

| Scenario         | --numBots | --delta | --length | --evalTime |
|------------------|-----------|---------|----------|------------|
| **concentrated** |        40 |      20 |       50 |        600 |
| **widespread**   |        40 |   5.000 |       50 |        600 |
| **maxdistance**  |        40 |  50.000 |       50 |        600 |

The Python script requires the `pip3` dependency `argparse` to work correctly. Install with: `pip3 install argparse`

## Post-Processing of change logs

The execution of the emulated Minecraft clients results in changes in Minecrafts game world, which are logged by the change-logger plugin. The created log-file however, contains all changes to Minecraft's game world, and for our evaluation, we are only interested in which world chunks changed. To extract changed chunks, the following `jupyter notebook` can be used:

https://github.com/phylib/MinecraftNDN-RAFNET19/blob/master/gamestate-changes/change_statistics/AnalyzeChunkChanges.ipynb

With the `jupyter notebook` file, chunk-change-traces for each of the above described scenarios can be generated.

## Ready to use trace-files

Instead of creating new traces, the original trace files used for the paper
evaluation are ready to use and available in the MiniNDN-Fork. Please see
the following folder: https://gitlab.itec.aau.at/minecraft/QuadTreeSyncEvaluation/tree/master/traceFiles
