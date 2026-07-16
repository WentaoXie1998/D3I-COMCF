# D3I-COMCF

Official implementation of **D3I-COMCF: Dissimilarity-driven dual-interaction via co-occurrence motifs and complementary fragments for drug--drug interaction prediction**.

D3I-COMCF is a multi-scale graph learning framework for drug--drug interaction (DDI) prediction. It integrates molecule--motif co-occurrence information and backbone-directed complementary fragment interactions to improve generalization and interpretability, especially under cold-start settings.

## Repository Download

This repository uses **Git LFS** to store large files. Please do **not** download the repository using the GitHub web page "Download ZIP" button, because some large files may be downloaded as Git LFS pointer files instead of the real files.

Please download the complete repository using:

```bash
git clone https://github.com/WentaoXie1998/D3I-COMCF.git
cd D3I-COMCF
git lfs install
git lfs pull
```

After running `git lfs pull`, the complete data and large files tracked by Git LFS will be downloaded correctly.

## Environment

The required environment is provided in `environment.yml`. You can create the environment using:

```bash
conda env create -f environment.yml
conda activate <env_name>
```

Please replace `<env_name>` with the environment name specified in `environment.yml`.

## Data Sources

The data of **DrugBank** and **TWOSIDES** are from the original manuscript of DSN-DDI:

```text
https://github.com/microsoft/Drug-Interaction-Research/tree/DSN-DDI-for-DDI-Prediction
```

The data of **DeepDDI** and **ZhangDDI** are available from HTCL-DDI:

```text
https://github.com/ranzhran/HTCL-DDI
```

The processed files used in this repository are organized according to the experimental protocols described in the manuscript.

## Usage

### 1. DrugBank inductive setting

#### Training under the Train-only CMMIG protocol

For example, to train fold 0 under the DrugBank inductive setting, run:

```bash
python train_only_cmmig.py --fold 0 --exp_tag train_only_main --cost_csv cost_profile_train_main.csv
```

#### Testing on S1 setting

To evaluate the trained model on the S1 cold-start setting:

```bash
python test_inductive.py --fold 0 --test_file s1.csv --exp_tag train_only_main --cost_csv cost_profile_test_main.csv
```

#### Testing on S2 setting

To evaluate the trained model on the S2 cold-start setting:

```bash
python test_inductive.py --fold 0 --test_file s2.csv --exp_tag train_only_main --cost_csv cost_profile_test_main.csv
```

### 2. DrugBank transductive setting

#### Training

```bash
python transductive_train.py --fold 0
```

#### Testing

```bash
python transductive_test.py --fold 0
```

### 3. DeepDDI dataset

For training and testing on the DeepDDI dataset, run:

```bash
python deep_train.py
```

## Notes

* The fold index can be changed by modifying the `--fold` argument.
* Please make sure that the corresponding dataset files are placed in the correct directories before running the scripts.
* For large files managed by Git LFS, please always use `git lfs pull` after cloning the repository.

## Contact

If you have any questions about the code, please contact:

```text
Wentao Xie
Email: taobiubiu1998@163.com
```
## License

This repository is released for academic research and non-commercial use only.

The code, processed data, scripts, and supplementary materials in this repository may be used for reproducing the results reported in the paper and for academic research purposes. Commercial use, including but not limited to use in commercial software, commercial services, industrial drug discovery pipelines, paid consulting, or proprietary product development, is not permitted without prior written permission from the authors.

If you would like to use this repository for commercial purposes, please contact Wentao Xie (taobiubiu1998@163.com) to obtain explicit written authorization.

## Citation

If you use this repository or build further research based on the paper **D3I-COMCF: Dissimilarity-driven dual-interaction via co-occurrence motifs and complementary fragments for drug--drug interaction prediction**, please cite our work.

```bibtex
@article{xie2026d3i,
  title={D3I-COMCF: Dissimilarity-driven dual-interaction via co-occurrence motifs and complementary fragments for drug-drug interaction prediction},
  author={Xie, Wentao and Jin, Min and Yang, Mingjian and Zhou, Yulu and Liu, Xinhua and Li, Meng and Rajapakse, Jagath C},
  journal={Neural Networks},
  pages={109328},
  year={2026},
  publisher={Elsevier}
}
```

The BibTeX entry will be updated once the final publication information is available.
