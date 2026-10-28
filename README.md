DGTPC-Net Anonymous Reproducibility Repository
Overview
This repository contains the source code and supporting files for the Distillation-Guided Temporal Prototype Calibration Network (DGTPC-Net), developed for early student dropout risk prediction in online higher education.

The package covers data acquisition, cohort construction, feature engineering, model definition, model training, probability calibration, threshold selection, evaluation, robustness analysis, statistical analysis, and manuscript-aligned report generation. It is organized as an anonymous reproducibility package and does not include author-identifying information.

This README describes the contents of the code package only. It does not report experimental findings, performance values, cohort counts, or study conclusions.
Repository Structure
.
├── artifacts/
│   └── reference_runs/          # Reference command transcripts and output-field layouts
├── configs/                     # Experiment and analysis configurations
├── manuscript_targets/          # Machine-readable reference tables used by comparison utilities
├── provenance/                  # Anonymity and artifact-status statements
├── scripts/                     # Pipeline, validation, and comparison utilities
├── src/
│   └── dgtpc/                   # Main Python package
├── tests/                       # Deterministic tests for core pipeline components
├── CITATION.cff                 # Software citation metadata
├── DATA.md                      # Dataset source and local data-boundary documentation
├── LICENSE                      # MIT License
├── MANIFEST.sha256              # Repository file-integrity manifest
├── README.md                    # Repository overview
├── REPRODUCIBILITY.md           # Manuscript-to-command and artifact mapping
├── environment.yml              # Conda environment specification
├── pyproject.toml               # Package metadata and build configuration
├── reproduce.py                 # Top-level reproduction entry point
├── requirements.lock            # Pinned Python dependencies
└── requirements.txt             # Compatible Python dependency ranges
Main Python Package
The implementation is located in src/dgtpc/.
Module	Contents
__init__.py	Package initialization and version metadata.
cli.py	Command-line interface for data download, preparation, experiment execution, and report generation.
config.py	YAML configuration loading and validation.
download.py	OULAD archive retrieval, checksum recording, and extraction.
io.py	Shared file and serialization helpers.
dataset.py	Data containers and prepared-dataset loading utilities.
cohort.py	Midpoint cohort construction, eligibility rules, outcome construction, and cohort auditing.
features.py	Static, registration, course, VLE, assessment, temporal, and reliability feature construction.
preprocess.py	Tabular preprocessing and temporal-sequence standardization.
splits.py	Student-grouped data partitioning and fold management.
model.py	DGTPC-Net architecture, including tabular, temporal, and reliability encoders; gated feature fusion; prototype representations; and prediction head.
teacher.py	CatBoost teacher fitting and teacher-probability generation for knowledge distillation.
losses.py	Training objectives for classification, distillation, and probability quality.
training.py	Model optimization, epoch selection, refitting, prediction, and checkpoint-related training logic.
baselines.py	Classical and neural baseline model implementations.
calibration.py	Identity, temperature, Platt, and isotonic probability-calibration methods.
thresholds.py	Decision-threshold selection utilities.
metrics.py	Discrimination, calibration, classification, and decision-oriented metric functions.
statistics.py	Paired student-cluster bootstrap and multiple-comparison utilities.
runner.py	Experiment orchestration for cross-validation, transfer analyses, ablations, robustness checks, and related pipeline stages.
reporting.py	Generation of manuscript-aligned tables, figures, logs, and comparison-ready files.
utils.py	Random-seed control and shared utility functions.


Configuration Files
The configs/ directory contains YAML files that define the fixed settings used by the pipeline.
File	Purpose
paper.yaml	Central project, dataset, architecture, optimization, splitting, calibration, threshold, robustness, bootstrap, and baseline settings.
main_cv.yaml	Main student-grouped cross-validation experiment.
ccc_transfer.yaml	Module-transfer experiment configuration.
temporal_transfer.yaml	Temporal-transfer experiment configuration.
ablations.yaml	Model-component ablation configuration.
robustness.yaml	Fixed-model sensitivity and robustness configuration.


Pipeline and Utility Scripts
The scripts/ directory contains repository-level launchers and validation tools.
File	Purpose
run_all.sh	Runs the top-level reproduction workflow and output-comparison utility.
download_data.sh	Shell launcher for dataset acquisition.
run_tests.py	Executes the repository test suite.
validate_repository.sh	Runs syntax checks, tests, and repository validation.
validate_repository.py	Checks package structure, anonymous metadata, required files, and excluded generated artifacts.
compare_results.py	Compares locally generated tables with the machine-readable reference tables.
build_manifest.py	Builds the SHA-256 file-integrity manifest.


The root-level reproduce.py file coordinates the configured experiment stages and report generation.
Tests
The tests/test_core.py file contains deterministic checks for core repository behavior, including cohort rules, grouped data boundaries, metric calculations, threshold selection, probability calibration, and model-source expectations.
Supporting Files
- DATA.md documents the public OULAD sources, required source tables, download behavior, and the boundary between distributed and locally generated data.
- REPRODUCIBILITY.md maps manuscript items to pipeline stages and generated files.
- provenance/ANONYMITY.md records the anonymous-review boundary applied to the repository.
- provenance/ARTIFACT_STATUS.md identifies which reproducibility materials are included and which are generated locally.
- manuscript_targets/ contains machine-readable CSV files used by the repository's comparison utility.
- artifacts/reference_runs/ contains specification-oriented command transcripts that document stage order and output-field structure.
- CITATION.cff contains software citation metadata intended for completion after anonymous review.
- LICENSE provides the MIT software license.
- MANIFEST.sha256 provides hashes for checking repository-file integrity.
Environment Specifications
The package includes several dependency specifications:
- requirements.lock records pinned Python package versions.
- requirements.txt records compatible dependency ranges.
- environment.yml provides a Conda environment definition.
- pyproject.toml defines the installable dgtpc-net Python package and the dgtpc command-line entry point.
The implementation uses Python and includes dependencies for numerical computing, tabular data processing, machine learning, deep learning, plotting, configuration parsing, network requests, and model serialization.
Data and Generated-File Boundary
The repository is designed to work with the publicly available Open University Learning Analytics Dataset (OULAD). Dataset identifiers and acquisition utilities are included, while the raw dataset itself is not distributed in the package.

Trained model weights, per-record predictions, processed datasets, and run-generated tables, figures, and logs are also excluded. These files are created locally by the pipeline and are covered by the repository's .gitignore rules.
License
The source code is distributed under the MIT License. See LICENSE for the complete license text.
