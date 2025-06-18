# 50 kW Reflexive Tuning Networks - Loss Breakdown Analysis

## 📄 Overview

This repository contains the loss analysis code for the IEEE Open Journal of Power Electronics paper:

**"50 kW Reflexive Tuning Networks With Low Uncoupled Transmitter Currents for Dynamic Inductive Power Transfer Systems"**

- **Journal**: IEEE Open Journal of Power Electronics
- **DOI**: 10.1109/OJPEL.2024.3379846
- **Authors**: Shuntaro Inoue, Samuel Kiguthi, Jonathan Newman, Timothy Goodale, Chakridhar Reddy Teeneti, Bryce Hesterman, Abhilash Kamineni, and Regan Andrew Zane

## 🔬 Research Background

### Problem Statement
In Dynamic Wireless Power Transfer (DWPT) systems, the coupling coefficient varies significantly as vehicles move. Conventional Double LCCL topology suffers from high currents flowing through uncoupled transmitter coils, leading to efficiency degradation.

### Proposed Solution: Reflexive Tuning
- **Adaptive Coupling Control**: Adjusts reflected reactance based on coupling conditions
- **Uncoupled Current Reduction**: Achieves 37% current reduction
- **System Efficiency Improvement**: Reaches 90% DC-DC efficiency (50 kW, 85 kHz)

## 📁 Repository Structure

### Jupyter Notebooks
- **`LossBreakDown_50kW_ReflexiveTuning.ipynb`**: Reflexive Tuning analysis (Paper Fig. 21(a))
- **`LossBreakdown_50kW_Double_LCCL.ipynb`**: Conventional Double LCCL analysis (Paper Fig. 21(b))

### Data Files
- **`LossBreakdown_Reflexive.xlsx`**: Reflexive Tuning analysis results
- **`LossBreakdown_LCCL.xlsx`**: Double LCCL analysis results
- **`MagneticParameters.xlsx`**: System parameters

## 🚀 Quick Start

### Prerequisites
```bash
pip install pandas numpy matplotlib seaborn openpyxl
```

### Usage
1. **Clone the repository**
2. **Launch Jupyter Notebook**
3. **Run the notebooks**
   - `LossBreakDown_50kW_ReflexiveTuning.ipynb`: Novel method analysis
   - `LossBreakdown_50kW_Double_LCCL.ipynb`: Conventional method comparison

## 📊 Analysis Results

### Loss Breakdown (Paper Fig. 21)

#### Fig. 21(a) - Reflexive Tuning
- **L1**: Main transmitter coil loss
- **C1s, C1p, C1add**: Primary side capacitor losses
- **L2, L3, L4**: Uncoupled transmitter coil losses (3 systems)
- **C2s-C4s, C2p-C4p, C2add-C4add**: Uncoupled capacitor losses
- **Lf, Cf**: Filter losses
- **Lr**: Receiver coil loss
- **Crs, Crp, Cradd**: Secondary side capacitor losses
- **Inverter**: Switching losses
- **Diode rectifier & snubber**: Rectification and snubber losses

#### Fig. 21(b) - Double LCCL
- Similar loss structure but with higher uncoupled currents

### Performance Comparison
| Parameter | Reflexive Tuning | Double LCCL |
|-----------|------------------|-------------|
| DC-DC Efficiency | 90% | Lower |
| Uncoupled Current Reduction | 37% | 0% |
| Output Power | 50 kW | 50 kW |
| Operating Frequency | 85 kHz | 85 kHz |

## 🔧 Technical Details

### System Specifications
```python
Pout = 50000  # 50 kW
f = 85e3      # 85 kHz
Vdc = 400     # 400 V
Vbat = 400    # 400 V
QL = 400      # Inductor quality factor
QC = 500      # Capacitor quality factor
```

### Reflexive Tuning Theory
```python
# Coupling coefficient adaptation
k_x0y0 = df.loc[2, 'k_x0_y0']  # Current coupling coefficient
k_lim = df.loc[2, 'k_lim']     # Limiting coupling coefficient

# Reflected reactance calculation
Req2 = omega0*Vbat*L1_x0y0**0.5*Lr_x0y0*c1*abs(k_lim**2-k_x0y0**2)/(k_x0y0*(Lr_x0y0*Vdc**2-L1_x0y0*Vbat**2*k_x0y0**2*c2**2*c1**2)**0.5)
```

### LCCL Theoretical Foundation
Double LCCL analysis uses theoretical equations from:

**"Fast Design Optimization Method Utilizing a Combination of Artificial Neural Networks and Genetic Algorithms for Dynamic Inductive Power Transfer Systems"**
- **Journal**: IEEE Open Journal of Power Electronics
- **DOI**: 10.1109/OJPEL.2022.3224422

#### Key Theoretical Equations
```python
# Design constants
c1 = math.pi * w * L1 * I1 * math.sqrt(2) / (4 * Vdc)  # Primary side
c2 = (math.pi**2 * w * math.sqrt(L1 * Lr) * Pout) / (8 * k_x0y0 * c1 * Vdc * Vbat)  # Secondary side

# Current calculations
I1a = (4 * c1 * c2 * Vbat * k_x0y0) / (math.pi * w * math.sqrt(L1) * math.sqrt(Lr)) / math.sqrt(2)
I1b = (4 * c1 * Vdc) / (math.pi * w * L1) / math.sqrt(2)

# Loss calculations
Ploss = omega * L1 * I1**2 / Qcoil + omega * Lr * Ir**2 / Qcoil
```

## 🎯 Applications

### Research Applications
- **Academic Research**: Understanding Reflexive Tuning principles
- **System Design**: Reference for similar WPT system design
- **Performance Analysis**: Loss analysis methodology learning
- **Optimization Studies**: Parameter optimization framework

### Industry Applications
- **EV Charging**: Dynamic wireless charging system design
- **Industrial WPT**: High-power wireless power transfer
- **System Integration**: Component selection and sizing
- **Performance Validation**: Experimental result comparison

## 📚 Educational Value

This repository is suitable for learning:
- **Power Electronics**: Resonant converter design
- **Wireless Power Transfer**: Dynamic WPT system analysis
- **Loss Analysis**: Comprehensive loss modeling
- **System Optimization**: Multi-parameter optimization
- **Research Methodology**: Academic paper implementation

## 📝 Citation

Please cite the following papers when using this code:

```bibtex
@article{inoue2024reflexive,
  title={50 kW Reflexive Tuning Networks With Low Uncoupled Transmitter Currents for Dynamic Inductive Power Transfer Systems},
  author={Inoue, Shuntaro and Kiguthi, Samuel and Newman, Jonathan and Goodale, Timothy and Teeneti, Chakridhar Reddy and Hesterman, Bryce and Kamineni, Abhilash and Zane, Regan Andrew},
  journal={IEEE Open Journal of Power Electronics},
  year={2024},
  doi={10.1109/OJPEL.2024.3379846}
}

@article{inoue2022fast,
  title={Fast Design Optimization Method Utilizing a Combination of Artificial Neural Networks and Genetic Algorithms for Dynamic Inductive Power Transfer Systems},
  author={Inoue, Shuntaro and Goodrich, Dakota and Saha, Shaju and Nimri, Reebal and Kamineni, Abhilash and Flann, Nicholas S.},
  journal={IEEE Open Journal of Power Electronics},
  volume={3},
  pages={915--929},
  year={2022},
  doi={10.1109/OJPEL.2022.3224422}
}
```

## 🤝 Contributing

- Bug reports and improvement suggestions are welcome
- Adding new analysis features
- Documentation improvements

## 📄 License

MIT License - see [LICENSE](LICENSE) file for details

## 📞 Contact

- **Author**: Shuntaro Inoue
- **Email**: [Your Email]
- **Institution**: [Your Institution]

---

**Note**: This code is provided as supplementary material to enhance understanding of the paper. For complete theoretical background and experimental validation, please refer to the original papers. 