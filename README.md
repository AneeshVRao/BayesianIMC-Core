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
BayesianIMC-Core/
├── BayesianIMC_Core.cache/
├── BayesianIMC_Core.hw/
├── BayesianIMC_Core.ip_user_files/
├── BayesianIMC_Core.sim/
│   └── sim_1/
│       └── behav/
│           └── xsim/
│               └── tb_bayesian_imc.tcl
├── BayesianIMC_Core.srcs/
│   └── sources_1/
│       └── new/
│           ├── bayesian_imc_core.v
│           ├── sram_bayesian.v
│           ├── lfsr_random.v
│           ├── weight_perturb.v
│           └── kogge_stone_popcount.v
├── BayesianIMC_Core.xpr
└── README.md
```

---

## 🔧 Installation

### Requirements

- **Xilinx Vivado** (2020.1 or later recommended)

### Clone the repository
```sh
git clone https://github.com/AneeshVRao/BayesianIMC-Core.git
cd BayesianIMC-Core
```

---

## ▶️ Usage

### Open in Vivado

1. Launch Xilinx Vivado
2. Select **File → Open Project**
3. Navigate to the cloned repository and open `BayesianIMC_Core.xpr`

### Run Simulation

1. In Vivado, go to **Flow Navigator → Simulation → Run Simulation**
2. Select **Run Behavioral Simulation**

### Example testbench snippet
```verilog
module tb_bayesian_imc;
    reg clk;
    reg rst_n;
    reg start;
    reg [7:0] input_data;
    reg [1:0] weight_select;
    reg [7:0] confidence_pattern;
    wire [3:0] mean_result;
    wire [3:0] confidence_level;
    wire done;
    wire [2:0] current_state;

    bayesian_imc_core dut (
        .clk(clk),
        .rst_n(rst_n),
        .start(start),
        .input_data(input_data),
        .weight_select(weight_select),
        .confidence_pattern(confidence_pattern),
        .mean_result(mean_result),
        .confidence_level(confidence_level),
        .done(done),
        .current_state_out(current_state)
    );

    always #5 clk = ~clk;

    initial begin
        clk = 0;
        rst_n = 0;
        start = 0;
        input_data = 8'b0;
        weight_select = 2'b0;
        confidence_pattern = 8'b0;
        #20 rst_n = 1;
        #20;
        input_data = 8'b10101010;
        weight_select = 2'b00;
        confidence_pattern = 8'b11111111;
        start = 1;
        #10 start = 0;
        wait(done == 1);
        $finish;
    end
endmodule
```

---

## 🛠️ Support

For questions or improvements, open a GitHub issue:

👉 https://github.com/AneeshVRao/BayesianIMC-Core/issues

Or contact the author directly.

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

**Aneesh Venkatesha Rao**, **Akula Sahasra**, **Adhvay Shrujal**

Verilog Design | Bayesian IMC Architecture | Digital Computing Systems

Special thanks to reference IMC architectures studied during coursework and research.

---

## 📜 License

This project is licensed under the MIT License.

See [LICENSE](LICENSE) for details.

---

## 📌 Project Status

🟢 **Active** — currently maintained and open to improvements.
