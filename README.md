# Closing the Gap: Achieving Better Accuracy-Robustness Tradeoffs against Query-Based Attacks

This repository contains the Python source code for the experiments of the paper "Closing the Gap: Achieving Better Accuracy-Robustness Tradeoffs against Query-Based Attacks", published in the Proceedings of the AAAI Conference on Artificial Intelligence 2024. 

## Experiments 

### Conda environment setup

To set up the environment ```query_based_framework``` with all required packages just run:

```
conda env create -f environment.yml
```

### Structure

```
.
├── attacks // attack implementations
├── configs
│   ├── main.json
│   ├── runall.json
│   └── surfree.json
├── dataset_helper.py
├── datasets
├── defenses // defense implementations
├── environment.yml
├── main.py // main script for executing a specified experiment
├── evaluation.py // script for generting Pareto plots out of experimental results
├── model_factory.py
├── model_interface.py
├── models // contains models and special architectures 
│   ├── calibration
│   │   └── temperature_scaling.py
│   ├── cifar10
│   │   ├── densenet121.pt
│   │   ├── resnet20_pni
│   │   ├── resnet34_oat
│   │   ├── robust_training
│   │   └── vgg16_rse
│   ├── cifar100
│   │   └── resnet50.pt
│   ├── densenet.py
│   └── resnet.py
└── runall.py // wrapper that calls main.py with various parameters
```

### Launch experiments
The experiments are launched with the wrapper script ```runall.py```, which essentially constructs a list of tasks from the main.json file and then dispatches them.

It is parameterized as follows:

```
usage: runall.py [-h] [--gpus GPUS] [--attack {popskipjump,surfree}]
                 [--attacks_per_gpu ATTACKS_PER_GPU] [--seed SEED]
                 [--config_path CONFIG_PATH] [--output_folder OUTPUT_FOLDER]
                 [--output | --no-output] [--evaluate | --no-evaluate]
                 [--override | --no-override]
                 [--calibration | --no-calibration]

optional arguments:
  -h, --help            show this help message and exit
  --gpus GPUS, -g GPUS  Comma separated list of GPUs to use. Sorted by
                        PCI_BUS_ID.
  --attack {popskipjump,surfree}, -a {popskipjump,surfree}
                        Attack to evaluate.
  --attacks_per_gpu ATTACKS_PER_GPU, -p ATTACKS_PER_GPU
                        Number of attacks to be run on a single GPU.
  --seed SEED           Seed to randomize each attack.
  --config_path CONFIG_PATH
  --output_folder OUTPUT_FOLDER
                        Specifies the output path.
  --output, --no-output
                        Just outputs all command lines to be executed without
                        actually starting them. (default: False)
  --evaluate, --no-evaluate
                        Only performs an evaluation of experimental results.
                        (default: False)
  --override, --no-override
                        Overrides existing experiments/results. (default:
                        False)
  --calibration, --no-calibration
                        Applies calibration to the output of the model.
                        (default: True)
```

### Results

The generated adversarial images and parsed json files can be downloaded [here](https://ruhr-uni-bochum.sciebo.de/s/pYrsmzVPOq040g6) and need to be unpacked into the root of the project.
Then the main results in form of Pareto plots can be generated with the script ```evaluation.py```.

## Citation

```
@article{Zimmer_Andreina_Marson_Karame_2024, 
    title={Closing the Gap: Achieving Better Accuracy-Robustness Tradeoffs against Query-Based Attacks}, 
    volume={38}, url={https://ojs.aaai.org/index.php/AAAI/article/view/30187}, 
    DOI={10.1609/aaai.v38i19.30187}, 
    number={19}, 
    journal={Proceedings of the AAAI Conference on Artificial Intelligence}, 
    author={Zimmer, Pascal and Andreina, Sébastien and Marson, Giorgia Azzurra and Karame, Ghassan}, 
    year={2024}, 
    month={Mar.}, 
    pages={21859-21868} 
}
```

## Contact

Feel free to contact the first author via the e-mail provided on the publication.