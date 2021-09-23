# Kaggle OpenVaccine Models

Codebase of deep learning models for inferring stability of mRNA molecules, corresponding to the [Kaggle Open Vaccine Challenge](https://www.kaggle.com/c/stanford-covid-vaccine) and accompanying manuscript "Predictive models of RNA degradation through dual crowdsourcing", Wayment-Steele et al (2021) (full citation when available).

Models contained here are:

"Nullrecurrent": winning solution by Jiayang Gao

"BT": A model based the [original DegScore model](https://github.com/eternagame/DegScore) and XGBoost.

## Organization of the Repository

scripts: Python scripts to perform inference.

notebooks: Python notebooks to perform inference.

model_files: Store .h5 model files used at inference time.

data: Data corresponding to Kaggle challenge and to subsequent tests on mRNAs.

## Dependencies

Install via `pip install requirements.txt` or `conda install --file requirements.txt`.

*Not pip-installable:* See below.

## Setup

1. [Install git-lfs](https://git-lfs.github.com/) (best to do before git-cloning this KaggleOpenVaccine repo).

2. Install EternaFold, available for free noncommercial use [here](https://www.eternagame.org/about/software).

3. Git clone [Arnie](https://github.com/DasLab/arnie), which wraps EternaFold in python and allows RNA thermodynamic calculations across many packages. Follow instructions [here](https://github.com/DasLab/arnie/blob/master/docs/setup_doc.md) to link EternaFold to it.

4. Add path to this repository as `KOV_PATH` (so that script can find path to stored model files):

```
export KOV_PATH='/path/to/KaggleOpenVaccine'
```

## Usage for one construct at a time

To run the nullrecurrent winning solution on one construct, given in `example.txt`:

```
CGC
```

Run

```
python scripts/nullrecurrent_inference.py -i example.txt -o predict.txt
```

or for the BT model:

```
python scripts/BT_inference.py -i example.txt -o predict.txt
```

This write a text file of output predictions to `predict.txt`:

(nullrecurrent output)
```
2.1289976365, 2.650808962, 2.1869660805000004
```

(BT output)
```
0.2697107, 0.37091506, 0.48528114
```

### A note on Energy model versions

The predictions in the Kaggle competition and for the manuscript were performed with EternaFold parameters and CONTRAfold-SE code. The currently available EternaFold code will result in slightly different values. For more on the difference, see the EternaFold README.

## Individual Kaggle Solutions

This code is based on the winning solution for the Open Vaccine Kaggle Competition Challenge. The competition can be found here:

https://www.kaggle.com/c/stanford-covid-vaccine/overview

This code is also the supplementary material for the Kaggle Competition Solution Paper. The individual Kaggle writeups for the top solutions that have been featured in that paper can be found in the following table:


| Team Name                       |  Team Members  | Rank  | Link to the solution                                            |
|---------------------------------|-----------------|-------|-----------------------------------------------------------------|
|Jiayang Gao                      | Jiayang Gao     |   1   |https://www.kaggle.com/c/stanford-covid-vaccine/discussion/189620|
|                                 |                 |       |                                                                 |
|Kazuki ** 2                      |Kazuki Onodera   |   2   |https://www.kaggle.com/c/stanford-covid-vaccine/discussion/189709| 
|                                 |Kazuki Fujikawa  |       |                                                                 |
|                                 |                 |       |                                                                 |
|Striderl                         |Hanfei Mao       |   3   |https://www.kaggle.com/c/stanford-covid-vaccine/discussion/189574|
|                                 |                 |       |                                                                 |
|FromTheWheel & Dyed & StoneShop  |Gilles Vandewiele|   4   |https://www.kaggle.com/group16/covid-19-mrna-4th-place-solution  |
|                                 |Michele Tinti    |       |                                                                 |
|                                 |Bram Steenwinckel|       |                                                                 |
|                                 |                 |       |                                                                 |
|tito                             |Takuya Ito       |   5   |https://www.kaggle.com/c/stanford-covid-vaccine/discussion/189691|
|                                 |                 |       |                                                                 |
|nyanp                            |Taiga Noumi      |   6   |https://www.kaggle.com/c/stanford-covid-vaccine/discussion/189241|
|                                 |                 |       |                                                                 |
|One architecture                 |Shujun He        |   7   |https://www.kaggle.com/c/stanford-covid-vaccine/discussion/189564|
|                                 |                 |       |                                                                 |
|ishikei                          |Keiichiro Ishi   |   8   |https://www.kaggle.com/c/stanford-covid-vaccine/discussion/190314|
|                                 |                 |       |                                                                 |
|Keep going to be GM              |Youhan Lee       |   9   |https://www.kaggle.com/c/stanford-covid-vaccine/discussion/189845|
|                                 |                 |       |                                                                 |
|Social Distancing Please         |Fatih Öztürk     |   11  |https://www.kaggle.com/c/stanford-covid-vaccine/discussion/189571|
|                                 |Anthony Chiu     |       |                                                                 |
|                                 |Emin Ozturk      |       |                                                                 |
|                                 |                 |       |                                                                 |
|The Machine                      |Karim Amer       |   13  |https://www.kaggle.com/c/stanford-covid-vaccine/discussion/189585|
|                                 |Mohamed Fares    |       |                                                                 |





