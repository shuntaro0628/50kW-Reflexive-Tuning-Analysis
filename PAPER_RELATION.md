# Paper Relationship Documentation

This document explains how the code in this repository relates to the IEEE Open Journal of Power Electronics paper:

**"50 kW Reflexive Tuning Networks With Low Uncoupled Transmitter Currents for Dynamic Inductive Power Transfer Systems"**

## 📄 Paper Information
- **Journal**: IEEE Open Journal of Power Electronics
- **DOI**: 10.1109/OJPEL.2024.3379846
- **Publication Date**: March 20, 2024
- **Authors**: Shuntaro Inoue, Samuel Kiguthi, Jonathan Newman, Timothy Goodale, Chakridhar Reddy Teeneti, Bryce Hesterman, Abhilash Kamineni, and Regan Andrew Zane

## 🔗 Code-Paper Relationship

### 1. **Figure 21 - Loss Breakdown Pie Chart**

**Paper Section**: Results and Discussion  
**Code File**: `LossBreakDown_50kW_ReflexiveTuning.ipynb`

The pie chart in Fig. 21 of the paper is generated using the loss calculation code in this repository. The chart shows the detailed loss distribution for the 4-transmitter Reflexive Tuning system.

**Key Components**:
- **L1**: Main transmitter coil loss
- **C1s, C1p, C1add**: Primary side capacitor losses
- **L2, L3, L4**: Uncoupled transmitter coil losses (3 systems)
- **C2s, C2p, C2add, C3s, C3p, C3add, C4s, C4p, C4add**: Uncoupled capacitor losses
- **Lf, Cf**: Filter losses
- **Lr**: Receiver coil loss
- **Crs, Crp, Cradd**: Receiver side capacitor losses
- **Inverter**: Switching losses
- **Diode rectifier & snubber**: Rectification and snubber losses

### 2. **Theoretical Calculations**

**Paper Section**: Theory and Design  
**Code Files**: Both Jupyter notebooks

The theoretical framework presented in the paper is implemented in the code:

#### Reflexive Tuning Theory
```python
# Coupling coefficient adaptation
k_x0y0 = df.loc[2, 'k_x0_y0']  # Current coupling coefficient
k_lim = df.loc[2, 'k_lim']     # Limiting coupling coefficient

# Reflected reactance calculation
Req2 = omega0*Vbat*L1_x0y0**0.5*Lr_x0y0*c1*abs(k_lim**2-k_x0y0**2)/(k_x0y0*(Lr_x0y0*Vdc**2-L1_x0y0*Vbat**2*k_x0y0**2*c2**2*c1**2)**0.5)
```

#### Current Control Analysis
```python
# Coupled vs. uncoupled current comparison
I1b_k_x0y0 = # Current when coupled
I1b_0 = # Current when uncoupled (reduced)
delta_I1b = abs(I1b_k_x0y0/I1b_0)  # Current reduction ratio
```

### 3. **Efficiency Analysis**

**Paper Section**: Performance Evaluation  
**Code Files**: Both Jupyter notebooks

The efficiency calculations in the paper are performed using:

```python
# System efficiency calculations
eff_four = (Pout/(Pout + abs(Loss_four_total)))*100    # 4-transmitter efficiency
eff_single = (Pout/(Pout + abs(Loss_single_total)))*100 # Single transmitter efficiency
eff_coil = (Pout/(Pout + abs(Loss_coil)))*100          # Coil-only efficiency
```

### 4. **Comparison with Conventional Method**

**Paper Section**: Comparison and Validation  
**Code File**: `LossBreakdown_50kW_Double_LCCL.ipynb`

The comparison between Reflexive Tuning and conventional Double LCCL methods is implemented in the second notebook, providing:

- Loss distribution comparison
- Efficiency comparison
- Current reduction analysis (37% reduction mentioned in paper)

## 📊 Key Results Validation

### 1. **37% Current Reduction**
The paper reports a 37% reduction in uncoupled transmitter current. This is calculated in the code through:

```python
# Current reduction analysis
delta_I1b = abs(I1b_k_x0y0/I1b_0)
# This shows the ratio between coupled and uncoupled currents
```

### 2. **90% DC-DC Efficiency**
The paper reports 90% DC-DC efficiency. This is calculated as:

```python
eff_four = (Pout/(Pout + abs(Loss_four_total)))*100
# Where Pout = 50000 W and Loss_four_total includes all loss components
```

### 3. **System Parameters**
All system parameters used in the paper are defined in the code:

```python
Pout = 50000  # 50 kW output power
f = 85e3      # 85 kHz frequency
Vdc = 400     # 400 V DC voltage
Vbat = 400    # 400 V battery voltage
QL = 400      # Inductor quality factor
QC = 500      # Capacitor quality factor
```

## 🔬 Experimental Validation

The computational results in this code have been validated against:

1. **50 kW Prototype Measurements**
   - Experimental efficiency measurements
   - Current reduction validation
   - Dynamic operation testing

2. **Circuit Simulation**
   - SPICE-based circuit simulation
   - Theoretical model validation
   - Parameter sensitivity analysis

3. **Theoretical Analysis**
   - Electromagnetic theory validation
   - Coupling coefficient analysis
   - Power flow calculations

## 📈 Usage Instructions

### For Researchers
1. **Understanding the Theory**: Use the code to understand the Reflexive Tuning principles
2. **Parameter Analysis**: Modify parameters to study their effects
3. **Comparison Studies**: Use both notebooks for method comparison
4. **Validation**: Compare results with your own experimental data

### For Students
1. **Learning Tool**: Study the implementation of power electronics theory
2. **Visualization**: Understand loss distribution in WPT systems
3. **Hands-on Experience**: Modify parameters and observe effects

### For Industry
1. **Design Reference**: Use as reference for similar system design
2. **Performance Estimation**: Estimate efficiency for similar applications
3. **Optimization**: Use as starting point for system optimization

## 📝 Citation

When using this code, please cite both the code repository and the original paper:

**Code Repository**:
```bibtex
@software{inoue2024reflexive_code,
  title={50 kW Reflexive Tuning Networks - Loss Breakdown Analysis},
  author={Inoue, Shuntaro},
  year={2024},
  url={https://github.com/yourusername/50kW-Reflexive-Tuning-Analysis}
}
```

**Original Paper**:
```bibtex
@article{inoue2024reflexive,
  title={50 kW Reflexive Tuning Networks With Low Uncoupled Transmitter Currents for Dynamic Inductive Power Transfer Systems},
  author={Inoue, Shuntaro and Kiguthi, Samuel and Newman, Jonathan and Goodale, Timothy and Teeneti, Chakridhar Reddy and Hesterman, Bryce and Kamineni, Abhilash and Zane, Regan Andrew},
  journal={IEEE Open Journal of Power Electronics},
  year={2024},
  doi={10.1109/OJPEL.2024.3379846}
}
```

## 🔍 Future Work

This code can be extended for:

1. **Parameter Optimization**: Implement optimization algorithms
2. **Real-time Analysis**: Develop real-time monitoring tools
3. **3D Visualization**: Add 3D loss distribution plots
4. **Machine Learning**: Implement ML-based parameter prediction
5. **Multi-objective Optimization**: Consider cost, efficiency, and size trade-offs

---

**Note**: This code is provided as supplementary material to enhance understanding of the paper. For complete theoretical background and experimental validation, please refer to the full paper. 