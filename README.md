# 🌐 GCP Infrastructure Visualizer

[![Python](https://img.shields.io/badge/python-3.10+-blue.svg)](https://www.python.org/)
[![License](https://img.shields.io/github/license/damian-sztankowski/GCP-Visualizer)](LICENSE)
![Made with](https://img.shields.io/badge/made%20with-%E2%9D%A4%20and%20AI%20magic-ff69b4)

Visualize your Google Cloud infrastructure in seconds — with detailed IAM relationships, project resources, and pretty interactive graphs (or static diagrams for reports). 

Whether you need to debug permissions, understand complexity, or simply explain your setup — this tool gives you superpowers.

---

## ✨ Features

- 🔍 Discover GCP projects, folders, and organizations
- 📦 Visualize all resources via Asset Inventory API
- 👥 Include IAM roles and their bindings
- 🎨 Export as:
  - Interactive HTML (zoom, filter, dark mode!)
  - Static SVG or PNG (for reports and documentation)
- 🧙‍♂️ Emoji-based labels, colored node types, and clean layouts
- 🛠 CLI-based: scriptable, automatable, DevOps-friendly

---

## 🚀 Installation

### 🛡 Permissions

1. Before using this tool, make sure your Google Cloud account or service account has the following roles:

- `roles/cloudasset.viewer` – to list assets in your organization or project
- `roles/browser` – to read metadata about folders, orgs, and projects
- `roles/resourcemanager.projectViewer` – to fetch IAM policies and project info

You can grant them using:

```bash
gcloud projects add-iam-policy-binding YOUR_PROJECT_ID \
  --member="user:you@example.com" \
  --role="roles/cloudasset.viewer"
```
2. Repeat for the other roles

| 💡 Don’t forget to enable the Cloud Asset Inventory API and Resource Manager API on your GCP project.


### 📦 Repo Cloning
Clone the repo and install dependencies:
```bash
git clone https://github.com/damian-sztankowski/GCP-Visualizer.git
cd GCP-Visualizer
python3 -m venv gcpviz
source gcpviz/bin/activate
pip3 install -r requirements.txt
```
---

## 🔧 Usage

This generates an interactive graph for a GCP project.

```bash

python gcpviz.py -p your-project-id -o output.html --use-pyvis
```

🔹 HTML (Interactive)
```bash
python gcpviz.py -p my-project -o graph.html --use-pyvis
```
🔸 SVG (Static)
```bash
python gcpviz.py -p my-project -o graph.svg
```

## 📁 Output Samples
| Output Type	    | Description |
| -------- | ------- |
| `graph.html` | Interactive Pyvis-based visualization with zoom, hover, dark theme |
| `graph.svg` or `graph.png` | Clean static export using Graphviz (great for documentation) |

## 🧠 Architecture
* `gcpviz.py` – CLI entrypoint using Click
* `graph_builder.py` – Static SVG/PNG generator via Graphviz
* `pyvis_drawer.py` – Interactive HTML generator via Pyvis
* `discovery.py` – Google Cloud resource discovery using Cloud Asset Inventory & IAM APIs

🙌 Acknowledgements
* `Google Cloud Python SDK`
* `Pyvis`
* `Graphviz`
