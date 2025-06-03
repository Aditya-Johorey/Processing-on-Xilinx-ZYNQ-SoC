# 📷 Gaussian Blur Image Filter on Xilinx ZYNQ SoC

This project demonstrates the design and implementation of a **3x3 Gaussian blur filter peripheral** on a **Xilinx ZYNQ SoC**, enabling **real-time image processing** using custom FPGA hardware with AXI4-Lite interfacing to an ARM processor.

The filter smooths images by applying a 3x3 convolutional Gaussian kernel, making it ideal for noise reduction and preprocessing in computer vision applications such as robotics, medical imaging, and autonomous systems.

---

## 🧠 Core Features

- 🟨 **Custom 3x3 Gaussian Blur Kernel**
- ⚙️ **AXI4-Lite Interface** for register-level communication between ARM and FPGA
- 💾 **On-Chip BRAM Buffers** for efficient tile-wise image processing
- 🖼️ **Supports PGM images (512x512+)**
- ⚡ **Real-Time Performance**: 1 tile per 9 clock cycles
- 🔬 **Software+Hardware Co-design**: Embedded C + Verilog/VHDL

---

## 🖼️ System Architecture

- **ARM Processor (ZYNQ)**  
  Manages image tiling, filter invocation, and result reassembly.

- **FPGA-based Convolution Core**  
  Hardware-accelerated image convolution using:
  - Register/BRAM pixel buffering
  - Dedicated DSP blocks for multipliers
  - Carry-save adders
  - 32-bit output registers

- **AXI4-Lite Interface**  
  Enables pixel transfer and control from software to hardware.

- **PC Output Viewer**  
  Displays original and filtered images for visual comparison.

![image](https://github.com/user-attachments/assets/6851023b-9d6c-4ff6-a4d3-560b37dadfb1)

---

## 📐 Gaussian Kernel

Applied 3x3 Guasian blur matrix as Gaussian kernel.

---

## 🛠️ Development Flow

### 🔩 Hardware Components
- Input Buffers (BRAM or registers)
- DSP-based Multipliers
- Carry-save Adders
- Output Register (32-bit)
- Clock Synchronization
- AXI4-Lite Interface

### 💻 Software (Embedded C on ARM)
- `init_platform()` and `cleanup_platform()` for setup/teardown
- Image stored as 2D array
- Loops extract 3x3 pixel tiles
- Filter invoked using `send()` + `FILTER_mReadReg()`
- Result clipped and stored in output array

---

## ⚡ Performance Metrics

| Metric           | Value                       |
|------------------|-----------------------------|
| Latency          | 9 clock cycles per tile     |
| Throughput       | Real-time 512×512 filtering |
| BRAM Usage       | 2 blocks                    |
| LUTs Used        | 1,200 (~15%)                |
| Flip-Flops Used  | 800 (~10%)                  |

---

## 🧪 Testing & Validation

- ✅ **Functional Simulation** via Testbench

![image](https://github.com/user-attachments/assets/7b043c94-e631-46c7-9a2b-34bde4a6cc13)


- 🖼️ **PGM Format Test Images**

![image](https://github.com/user-attachments/assets/b1f9e737-b748-46d0-84d1-2cf3485905db)


- 📊 Visual comparison of filtered vs. original image
- 🧾 Filter output verified with known Gaussian convolution software

---

## 🧰 Use Cases

- 🧬 **Medical Imaging**: Preprocessing CT/MRI scans
- 🛰️ **Satellite Imaging**: Noise reduction from atmospheric distortion
- 🤖 **Robotics**: Preprocessing before edge detection/object recognition
- 🎨 **Photography/Film**: Blurring and depth effects

---

## 👨‍💻 Author

**Aditya Johorey**  
MSc in Intelligent Robotics  
[LinkedIn](https://linkedin.com/in/adityajohorey)  
[GitHub](https://github.com/yourusername)

---
