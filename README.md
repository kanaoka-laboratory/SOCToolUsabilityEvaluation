# Supplemental Materials for SOC Tool Usability Evaluation Research

This repository provides supplemental materials for an academic study on the usability evaluation of Security Operations Center (SOC) tools.  
The repository includes the evaluation criteria, simulated operational environment, and Syslog datasets that were used to perform a structured usability evaluation of a SIEM system.

The associated research paper is currently under submission, so the full paper cannot be publicly linked at this time.  
Once the review process is complete, citation information will be added.

---

## Repository Structure

### `docs/`
This folder contains documentation related to the proposed usability evaluation method, including:

- Detailed descriptions of the eleven evaluation criteria  
- Supplemental explanations of the heuristic walkthrough procedure  
- Additional methodological notes that support reproducibility  

These documents correspond to the evaluation framework described in the submitted paper.

### `environment/`
This directory provides detailed information about the simulated SOC operational environment used in the study.

It includes:

- Network topology and its rationale  
- Host configuration data  
- Attack scenario definitions  
- Supporting metadata used during log synthesis  

These materials allow other researchers to understand or replicate the evaluation environment.

### `logs/`
This folder contains all Syslog-format log files that were ingested into the SIEM during the usability evaluation.

The dataset includes:

- Benign operational logs  
- False positive alerts  
- Logs generated from two attack scenarios (malware infection and insider threat)  

All logs were synthetically generated based on predefined templates and scenario timelines to ensure reproducibility.

---

## Purpose of This Repository

The primary goal of this repository is to make the evaluation method reproducible and transparent.  
It provides:

- A complete set of artifacts used during the study  
- Data required for independent verification  
- A foundation for researchers to extend the usability evaluation of SOC tools

Although the main research paper is still under review, this repository is intended to accompany that work once published.

---

## License

All materials in this repository are distributed under the following license:

