# Bayesian IMC Core

*A Hardware-Efficient Bayesian In-Memory Computing Engine implemented in Verilog RTL*

![License](https://img.shields.io/badge/license-MIT-blue.svg)
![Status](https://img.shields.io/badge/status-active-success.svg)
![Verilog](https://img.shields.io/badge/HDL-Verilog-orange.svg)

---

## 📘 Description

The **Bayesian IMC Core** is a hardware-optimized computational block that performs *Bayesian inference directly inside memory*, reducing data movement and enabling low-power probabilistic processing.

This implementation includes:

- SRAM-based weight lookup
- Confidence-driven stochastic bit perturbation
- LFSR-based randomness
- Kogge–Stone inspired popcount
- FSM-controlled sampling + Bayesian analysis

It is designed for:

- Edge AI accelerators
- Probabilistic processing
- In-memory compute research
- Low-power inference systems

---

## ✨ Features

- 🔹 **SRAM-based weight memory** (`sram_bayesian`)
- 🔹 **Random generator** using an 8-bit LFSR (`lfsr_random`)
- 🔹 **Bayesian weight perturbation** with confidence masks
- 🔹 **Popcount via hierarchical adder tree** (`kogge_stone_popcount`)
- 🔹 **Full Bayesian sampling engine (8 samples)**
- 🔹 **Posterior mean computation**
- 🔹 **Variance-based confidence scoring**
- 🔹 **Multi-stage FSM for structured execution**

---

## 📁 Repository Structure

```
bayesian-imc-core/
├── src/
│   ├── bayesian_imc_core.v
│   ├── sram_bayesian.v
│   ├── lfsr_random.v
│   ├── weight_perturb.v
│   └── kogge_stone_popcount.v
├── simulation/
│   ├── testbench.v
│   ├── waveform.vcd
│   └── results.md
├── docs/
│   ├── block-diagram.png
│   └── architecture.md
├── README.md
└── .gitignore
```

---

## 🖼️ Visuals

You can include any of the following:

- Architectural block diagram
- FSM diagram
- Waveform screenshot from GTKWave
- Simulation output summary

---

## 🔧 Installation

### Requirements

- `iverilog`
- `vvp`
- `gtkwave` (optional for waveform visualization)
- Any Linux/Windows environment with basic shell

### Clone the repository

```sh
git clone https://github.com/AneeshVRao/BayesianIMC-Core.git
cd BayesianIMC-Core
```

---

## ▶️ Usage

### Run simulation

```sh
iverilog -o sim.out src/*.v simulation/testbench.v
vvp sim.out
```

### View waveform

```sh
gtkwave waveform.vcd
```

### Example testbench snippet

```verilog
initial begin
    clk = 0;
    rst_n = 0;
    #10 rst_n = 1;
    start = 1;
    input_data = 8'b10101010;
    weight_select = 2'b01;
    confidence_pattern = 8'b11110000;
end
```

---

## 🛠️ Support

For questions or improvements, open a GitHub issue:

👉 https://github.com/AneeshVRao/BayesianIMC-Core/issues

Or contact the author directly.

---

## 🗺️ Roadmap

### Planned Enhancements

- [ ] FPGA synthesis (Artix-7 recommended)
- [ ] Timing and power estimation
- [ ] Parameterized sample count (e.g., 16/32 samples)
- [ ] Wider datapaths (16-bit, 32-bit)
- [ ] Parallel IMC tiles
- [ ] Support for custom SRAM initialization files

---

## 🤝 Contributing

Contributions are welcome!

### Steps:

1. Fork the repository
2. Create a new branch (`feature/xyz`)
3. Commit your changes
4. Open a Pull Request

For developers, recommended environment setup is in `docs/architecture.md`.

---

## 👤 Author & Acknowledgments

**Aneesh V. Rao**

Verilog Design | Bayesian IMC Architecture | Digital Computing Systems

Special thanks to reference IMC architectures studied during coursework and research.

---

## 📜 License

This project is licensed under the MIT License.

See [LICENSE](LICENSE) for details.

---

## 📌 Project Status

🟢 **Active** — currently maintained and open to improvements.
