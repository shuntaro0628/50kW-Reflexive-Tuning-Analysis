# 50 kW Reflexive Tuning Networks - Loss Breakdown Analysis

This repository contains the computational analysis and visualization code for the paper:

**"50 kW Reflexive Tuning Networks With Low Uncoupled Transmitter Currents for Dynamic Inductive Power Transfer Systems"**

Published in: IEEE Open Journal of Power Electronics  
DOI: 10.1109/OJPEL.2024.3379846  
Authors: Shuntaro Inoue, Samuel Kiguthi, Jonathan Newman, Timothy Goodale, Chakridhar Reddy Teeneti, Bryce Hesterman, Abhilash Kamineni, and Regan Andrew Zane

## 📋 Overview

This repository provides the computational tools and analysis scripts used to generate the loss breakdown analysis and efficiency calculations presented in the paper. The code includes:

- **Reflexive Tuning loss analysis** (Fig. 21 in the paper)
- **Double LCCL loss analysis** (comparison with conventional method)
- **Theoretical calculations** for 50 kW dynamic inductive power transfer systems
- **Visualization tools** for loss distribution pie charts

## 🎯 Key Features

### Reflexive Tuning Analysis
- Loss breakdown calculation for 4-transmitter coil system
- Uncoupled transmitter current reduction analysis
- Efficiency comparison with conventional double-sided LCC tuning
- Theoretical validation of reflexive tuning principles

### Loss Components Analyzed
- **Coil losses**: L1, L2, L3, L4, Lr
- **Capacitor losses**: C1s, C1p, C2s, C2p, C3s, C3p, C4s, C4p, Crs, Crp
- **Filter losses**: Lf, Cf
- **Power electronics losses**: Inverter switching, Diode rectifier, Snubber
- **System efficiency**: Single vs. four-transmitter configurations

## 📁 Repository Structure

```
├── LossBreakDown_50kW_ReflexiveTuning.ipynb    # Reflexive Tuning analysis
├── LossBreakdown_50kW_Double_LCCL.ipynb        # Double LCCL analysis
├── MagneticParameters.xlsx                      # System parameters
├── LossBreakdown_Reflexive.xlsx                 # Output data (Reflexive)
├── LossBreakdown_LCCL.xlsx                      # Output data (LCCL)
├── requirements.txt                             # Python dependencies
└── README.md                                    # This file
```

## 🚀 Quick Start

### Prerequisites
- Python 3.7 or higher
- Jupyter Notebook or JupyterLab

### Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/yourusername/50kW-Reflexive-Tuning-Analysis.git
   cd 50kW-Reflexive-Tuning-Analysis
   ```

2. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```

3. **Run the analysis**
   ```bash
   jupyter notebook
   ```

### Usage

1. **Open `LossBreakDown_50kW_ReflexiveTuning.ipynb`**
   - This notebook contains the Reflexive Tuning analysis
   - Generates the loss breakdown pie chart (Fig. 21 in the paper)
   - Calculates system efficiency and loss distribution

2. **Open `LossBreakdown_50kW_Double_LCCL.ipynb`**
   - This notebook contains the conventional Double LCCL analysis
   - Provides comparison with Reflexive Tuning method
   - Shows loss distribution for conventional approach

## 📊 Key Results

### Reflexive Tuning Performance
- **37% reduction** in uncoupled transmitter current compared to conventional method
- **90% DC-DC efficiency** achieved with 223 mm air gap
- **Dynamic operation** capability up to 60 km/h vehicle speed

### Loss Distribution (Fig. 21)
The pie chart shows the detailed loss breakdown for the 4-transmitter Reflexive Tuning system:
- Coil losses (L1, L2, L3, L4, Lr)
- Capacitor losses (C1s, C1p, C2s, C2p, C3s, C3p, C4s, C4p, Crs, Crp)
- Filter losses (Lf, Cf)
- Power electronics losses (Inverter, Diode, Snubber)

## 🔬 Technical Details

### System Parameters
- **Power**: 50 kW
- **Frequency**: 85 kHz
- **Voltage**: 400 V DC
- **Air gap**: 223 mm
- **Quality factors**: QL = 400, QC = 500

### Theoretical Framework
The analysis is based on the Reflexive Tuning theory presented in the paper:
- Coupling coefficient adaptation
- Reflected reactance utilization
- Dynamic current control

## 📈 Validation

The computational results have been validated against:
- **Experimental measurements** from 50 kW prototype
- **Simulation results** using circuit simulation tools
- **Theoretical analysis** based on electromagnetic theory

## 🤝 Contributing

We welcome contributions to improve the analysis and visualization tools. Please feel free to:
- Report issues or bugs
- Suggest improvements
- Submit pull requests

## 📄 Citation

If you use this code in your research, please cite the original paper:

```bibtex
@article{inoue2024reflexive,
  title={50 kW Reflexive Tuning Networks With Low Uncoupled Transmitter Currents for Dynamic Inductive Power Transfer Systems},
  author={Inoue, Shuntaro and Kiguthi, Samuel and Newman, Jonathan and Goodale, Timothy and Teeneti, Chakridhar Reddy and Hesterman, Bryce and Kamineni, Abhilash and Zane, Regan Andrew},
  journal={IEEE Open Journal of Power Electronics},
  year={2024},
  doi={10.1109/OJPEL.2024.3379846}
}
```

## 📞 Contact

For questions about the code or analysis:
- **Author**: Shuntaro Inoue
- **Email**: shuntaro0628@gmail.com
- **Institution**: Utah State University

## 📜 License

This project is licensed under the MIT License - see the LICENSE file for details.

---

**Note**: This code is provided as supplementary material to the IEEE Open Journal of Power Electronics paper. For complete understanding, please refer to the full paper for theoretical background and experimental validation. 