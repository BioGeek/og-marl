<p align="center">
    <a href="docs/assets/og_marl_logo_short.png">
        <img src="docs/assets/og_marl_logo_short.png" alt="OG-MARL logo" width="50%"/>
    </a>
</p>

[![Python Versions](https://upload.wikimedia.org/wikipedia/commons/a/a5/Blue_Python_3.8_Shield_Badge.svg)](https://www.python.org/doc/versions/)
[![License](https://img.shields.io/badge/License-Apache%202.0-orange.svg)](https://opensource.org/licenses/Apache-2.0)

<!-- [**Environments**](#environments)
| [**Datasets**](#environments)
| [**Installation**](#install)
| [**Downloading Datasets**](#install)
| [**Tutorials**](#tutorials)
| [**Citation**](#citing)
| [**Docs**](https://instadeepai.github.io/og-marl) -->

---

<p align="center"> 
    <a href="docs/assets/offline_marl_diagram.jpg">
        <img src="docs/assets/offline_marl_diagram.jpg" alt="Offline MARL diagram" width="80%"/>
    </a>
</p>

## Going Off-the-Grid! 🤖 ⚡ 🔌 🔋

Multi-Agent Reinforcement Learning is a reach field of research with a lot of potential for real-world impact by promising robust, decentralised controlers for challenging multi-agent systems. However, MARL is typically very sample inefficient, requireing a lot of environment interactions. In practice this can be a significant obstacle to applying MARL in the real-world where environment interactions can be slow or dangerous to collect. As a  consequence MARL research has largely been focused on quick to simulate grid-world tasks and video-games. 

But recently the field of Offline RL has offered a promising way to overcome the challenges with collecting large amounts of experience in the real-world. Namely, in offline RL policies are trained on static, pre-collected data. Similarly, in offline MARL the goal is to apply MARL algorithms to large static datasets of experience inorder to learn decentralised policies without any environment interactions. Offline MARL has the potential to help the field go beyond the current MARL research settings (e.g. gridworlds and video games) and towards real-world settings.

However, offline MARL is currently an under-researched area that lacks standardised benchmark datasets. In order to help drive this nacent field forward, Off-the-Grid MARL (OG-MARL) fills this gap by providing a diverse suite of dataset with baselines on popular MARL benchmark environments. In addition we include a comprehensive set of baseline implementations from the literature and benchmark their performance on all of our datasets.


Originating in the Research Team at
[InstaDeep](https://www.instadeep.com/), OG-MARL is now developed jointly with the open-source
community. To join us in these efforts, reach out, raise issues and read our
[contribution guidelines](https://github.com/instadeepai/og-marl/blob/main/CONTRIBUTING.md) or just
🌟 to stay up to date with the latest developments!

# Environments 🌍
We have generated datasets on a diverse set of popular MARL environments. A list of currently supported environments are included in the table below. For more information on why we chose to include each environment and their properties, please read our accompanying [paper](https://arxiv.org/abs/2302.00521). 

<p align="center"> 
    <a href="docs/assets/og_marl_environments.jpg">
        <img src="docs/assets/og_marl_environments.jpg" alt="OG-MARL environments" width="80%"/>
    </a>
</p>

## Sources 🔗
| Environment | Source |
| --- | ---|
| SMAC v1 | https://github.com/oxwhirl/smac |
| SMAC v2 | https://github.com/oxwhirl/smacv2 |
| PettingZoo | https://pettingzoo.farama.org/ |
| Flatland | https://flatland.aicrowd.com/intro.html |
| MAMuJoCo | https://github.com/schroederdewitt/multiagent_mujoco |
| CityLearn | https://github.com/intelligent-environments-lab/CityLearn |
| Voltage Control | https://github.com/Future-Power-Networks/MAPDN |

# Datasets 📚
It is well known from the single-agent offline RL literature that the quality of experience in offline datasets can play a large role in the final performance of offline RL algorithms. In OG-MARL, we include a range of dataset distributions including `Good`, `Medium`, `Poor` and `Replay` datasets in order to benchmark offline MARL algorithms on a range of different dataset qualities. The dataset types are characterised by the quality of the joint policy that generated the trajectories in the dataset. For each dataset we provided a violin plot of the distribution of episode returns in the dataset. For all of the violin plots, please refer to our accompanying [paper](https://arxiv.org/abs/2302.00521).

<p align="center"> 
    <a href="docs/assets/og_marl_datasets.jpg">
        <img src="docs/assets/og_marl_datasets.jpg" alt="OG-MARL environments" width="80%"/>
    </a>
</p>

# Installation 🛠️

## Using Conda 🐍
Because we support many different environments, each with their own set of dependencies which are often conflicting, you will need to follow slightly different instalation instruction for each environment. 

To manage the different dependencies, we reccomend using `miniconda` as a python virtual environment manager. Follow these instructions to install `conda`. 

* https://docs.conda.io/projects/conda/en/latest/user-guide/install/linux.html

🚨 In the near future we will also be releasing Dockerfiles! 🚨

## Installing Datasets and/or Baselines 🀄
There are two options for installing OG-MARL. The first is to install the datasets only. The second is to optionally also install the baseline algorithm implementations.

Installing the datasets only is a lot easier and will likely work on most computer setups. Installing the baselines is a bit more complicated because of some additional dependencies. Unfortunatly baselines are unlikely to work on Windows and Mac because of our dependency on DeepMind's `reverb` and `launchpad` packages. In future we hope to relax these requirements.

### Installing OG-MARL Datasets (minimal requirements) 🧮
Install og-marl with the `datasets` option.

`pip install -e .["datasets"]`

### Installing OG-MARL Baselines 🔱
Install og-marl with the `baselines` option.

`pip install -e .["datasets","baselines"]`

### Installing Environments ⛰️
Depending on the environment you want to use, you should install that environments dependencies. We provide convenient shell scripts for this.

`bash install_environments/<environment_name>.sh`

You should replace `<environment_name>` with the name of the environment you want to install.

Installing several different environments dependencies in the same python virtual environment (or conda environment) may work in some cases but in others, they may have conflicting requirements. So we reccomend maintaining a different virtual environment for each environment.

# Downloading Datasets ⏬

Next you need to download the dataset you want to use and add it to the correct file path. Go to the OG-MARL website (https://sites.google.com/view/og-marl) and download the dataset. Once the zip file is downloaded add it to a directory called `datasets` on the same level as the `og-marl/` directory. The folder structure should look like this:

```
examples/
    |_> ...
og_marl/
    |_> ...
datasets/
    |_> smacv1/
        |_> 3m/
        |   |_> Good/
        |   |_> Medium/
        |   |_> Poor/
        |_> ...
    |_> smacv2/
        |_> terran_5_vs_5/
        |   |_> Good/
        |   |_> Medium/
        |   |_> Poor/
        |_> ...
```

# Tutorials 💯
We provide various examples of how to use OG-MARL. 

## Overview 🗼
In the `examples/` directory we include scripts to load and profile each of our datasets.
* `examples/profile_datasets/profile_smacv1.py`
* `examples/profile_datasets/profile_smacv2.py`
* `examples/profile_datasets/profile_flatland.py`
* `examples/profile_datasets/profile_pettingzoo.py`
* `examples/profile_datasets/profile_mamujoco.py`
* `examples/profile_datasets/profile_city_learn.py`
* `examples/profile_datasets/profile_voltage_control.py`

We also include a quickstart tutorial on how to make your own dataset on a new environment:
* `examples/quickstart/part1_double_cartpole.py`
* `examples/quickstart/part2_generate_dataset.py`
* `examples/quickstart/part3_train_offline_algo.py`

We also include scripts for replicating our benchmarking results:
* `examples/benchmark_mamujoco.py`
* `examples/benchmark_smac.py`

## Profiling Datasets 📊
In order to profile a dataset you will need to install og-marl with the `datasets` option, as well as the corresponding environment. You should then be able to run the dataset profiling script for the environement/scenario you just installed and downloaded the datases. 

`python examples/profile_datasets/profile_<environment_name>.py`

Once again, replace `<environment_name>` with the name of the environment you just installed (e.g. "smacv1", "smacv2" or "mamujoco").

Be patient while it runs. It can take a minute or two to loop through the whole dataset. At the end statistics about the dataset will be printed out and a sample of the dataset will also be printed. A violin plot of the data will also be generated and saved alongside the `og_marl/` directory.

## Dataset Generation Quickstart 🎥
Inorder to run the datasets generation quickstart tutorial you will need to also install the og-marl with the `datasets` and `baselines` options. You are now ready to run through the quickstart tutorial. Open the file `examples/quickstart/generate_dataset.py` and read the comments throughout to do the tutorial.

## Running Baselines 🏃
We provide scripts to reproduce the MAMuJoCo and SMAC baseline results. Inorder to run them you will need to install OG-MARL with the `datasets` and `baselines` options. Then install the corresponding environment. 

After that you can run the SMAC script as follows:

`python examples/baselines/benchmark_smac.py --algo_name=qmix --dataset_quality=Good --env_name=3m`

    --algo_name can be used to change the algorithm you want to run
    --dataset_quality is used to change wich dataset type to run
    --env_name is used to change the scenario

You will need to make sure you download the datasets from the OG-MARL website.

https://sites.google.com/view/og-marl

Make sure the unzip the dataset and add it to the path 
`datasets/smac/<env_name>/<dataset_quality>/`

## Code Snippet ✂️
Inorder to run the code snippet you will need to also install the OG-MARL with `baselines`. You will then also need to install SMAC.

Finally, download the "3m" dataset from the website and put it in the apropriate directory as above.

You should then be able to run the code snippet:

`python examples/code_snippet.py`

# Roadmap 🗺️

Offline MARL also lends itself well to the new wave of hardware-accelerated research and development in the
field of RL. In the near future we hope to add JAX support to our baselines.


# Troubleshoot ⚙️

In MAMuJoCo you may need to export the following environment variables.

`export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/lib/x86_64-linux-gnu/:$MUJOCOPATH/mujoco210/bin:/usr/lib/nvidia`

`export LD_PRELOAD=$LD_PRELOAD:/usr/lib/x86_64-linux-gnu/libGLEW.so`

Error:

`ImportError: libpython3.8.so.1.0: cannot open shared object file: No such file or directory`

Solution:

`export LD_LIBRARY_PATH=$CONDA_PREFIX/lib:\$LD_LIBRARY_PATH`