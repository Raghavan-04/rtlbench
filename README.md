
# RTL Bench — Web EDA Architecture & Netlist Visualizer

![License](https://img.shields.io/badge/License-MIT-blue.svg)
![Status](https://img.shields.io/badge/Status-Active-success.svg)
![Web](https://img.shields.io/badge/Platform-Web-cyan.svg)

**RTL Bench** is a next-generation, in-browser EDA tool that compiles multi-file SystemVerilog RTL projects into interactive, gate-level schematics. It features hierarchy-preserving synthesis, real vector bus collapsing, and on-demand gate-level static timing analysis (STA) with per-process-node estimation. 

No installs. No licenses. Just your browser.

🔗 **[Launch RTL Bench](https://rtlbench.com)**

---

## ✨ Features

- **Multi-file Projects:** Drop a folder of `.sv`/`.v` sources and data files. Relative paths are preserved so `$readmemh("dv/hex/fw.hex")` finds its files.
- **Hierarchy-preserving Synthesis:** Submodule instances render as encapsulated blocks. Toggle between **Hierarchy** view (collapsed blocks) and **Flat** view (unrolled gates) from the same compile.
- **Gate-level Static Timing Analysis:** Yosys `techmap` decomposes the design to real gates. Per-process-node conversion (180nm, 90nm, 45nm, 7nm) provides nanosecond estimates with top-K critical paths.
- **Semantic LOD Zooming:** No dropdowns to switch views. The tool watches your zoom level and cross-fades between macro block diagrams and detailed gate schematics.
- **Vector Bus Collapsing:** Bit-blasted nets are regrouped into single vector wires with IEEE `/W` slash notation and width labels.
- **Fused Constant Comparators:** Operations like `== 8'hA5` are rendered as a single comparator cell with the value fused into an adjacent chip.
- **Click-to-Trace Nets:** Every wire is interactive. Click any net to highlight the full routed path across the canvas.
- **Orthogonal Manhattan Routing:** Powered by the Eclipse Layout Kernel (ELK) for clean, commercial-grade 90° wire routing.
- **Vector SVG Export:** Export the current view as a clean, resolution-independent SVG.

---

## 🏗️ The Pipeline

Every compile runs through a four-stage pipeline:

1. **Upload:** Drop a folder, paste a single file, or pick a preset. Top module and data files are auto-detected.
2. **Elaborate:** Source is sandboxed and elaborated using Yosys (`read_verilog` → `proc` → `opt` → `clean`).
3. **Place & Route:** Eclipse Layout Kernel (ELK) positions cells in a LEFT→RIGHT layered graph with orthogonal Manhattan edges.
4. **Analyze:** Zoom through the hierarchy, click nets to trace, run gate-level STA, and export as SVG.

---

## 🚀 Getting Started (Frontend Only)

This repository contains the **frontend UI and landing page** for RTL Bench. 

### Prerequisites
- Node.js (v18 or higher)
- npm or yarn

### Local Development
1. Clone the repository:
   ```bash
   git clone https://github.com/your-username/rtl-bench-public.git
   cd rtl-bench-public
   ```

2. Install dependencies:
   ```bash
   npm install
   ```

3. Start the Vite development server:
   ```bash
   npm run dev
   ```

4. Open `http://localhost:5173` in your browser.

> **⚠️ Note:** The backend synthesis engine is not included in this repository. The UI will load, but API calls for compilation and timing analysis will fail locally. To use the full tool, please visit [rtlbench.com](https://rtlbench.com).

---

## 🧩 Open-Core Model (Partial Open Source)

RTL Bench operates on an **Open-Core** model:
- **Open Source (This Repo):** The frontend UI, landing page, HTML/CSS/JS components, and client-side routing are open-source under the MIT License.
- **Proprietary (Closed Source):** The backend synthesis engine, Yosys orchestration, WASM compilation pipeline, and proprietary static timing analysis algorithms are closed-source and not included in this repository.

We welcome contributions to the UI and user experience! For backend inquiries, please contact us.

---

## 🤝 Contributing

Contributions are welcome! Whether it's a bug report, feature request, or a pull request for the UI, we'd love your help.

1. Fork the repo.
2. Create your feature branch (`git checkout -b feature/AmazingFeature`).
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`).
4. Push to the branch (`git push origin feature/AmazingFeature`).
5. Open a Pull Request.

Please read `CONTRIBUTING.md` for more details on our code of conduct and the process for submitting pull requests.

---

## 📄 License

This project is licensed under the **MIT License** — see the [LICENSE](LICENSE) file for details. 

*Note: The MIT License applies only to the files included in this repository. The proprietary backend engine remains the intellectual property of the author.*

---

## 👨‍💻 Author

**Raghavan**
- LinkedIn: [Raghavan SU](https://www.linkedin.com/in/raghavan-su-04r/)
- GitHub: [@Raghavan-04](https://github.com/Raghavan-04/)
- Email: [contact@rtlbench.com](mailto:contact@rtlbench.com)

---

## 🙏 Acknowledgments

- [Yosys Open SYnthesis Suite](https://yosyshq.net/yosys/)
- [Eclipse Layout Kernel (ELK)](https://www.eclipse.org/elk/)
- Built with ❤️ for the open-source hardware community.
```

### 💡 Pro-tips for your README:
1. **Add a GIF or Screenshot:** At the very top of the README, right under the badges, insert the animated schematic GIF or a screenshot of the studio. It's the first thing people look at. You can use the one from your landing page.
2. **Badges:** The badges at the top (`![License]`, etc.) make it look very professional. You can customize them if you want.
3. **Keep it updated:** As you add features, update the "Features" list and the "Pipeline" section.