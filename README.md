# *E.coli* Metabolic Gene–Gene Network

Visualize and explore the gene–gene connectivity of the *Escherichia coli* metabolic network using Cytoscape.

---

## What’s in this repo?

* **`GG_network.sif`**
  Simple Interaction Format (SIF) file describing how nodes (genes) are connected. Each row is an edge:
  `source <interaction> target`

* **`GG_network_nodeattr.txt`**
  Node-attribute table (tab-delimited). Contains per-gene metadata, e.g., **Essential** vs **Non-Essential**, etc..

* **`Cytoscape_session.cys`**
  A ready-to-use Cytoscape session. Open this to load the network, attributes, and visual styles in one go.

---

## Requirements

* [Cytoscape](https://cytoscape.org/) (v3.9+ recommended)

---

## Quick start

### Option A — Open the ready-made session (fastest)

1. Launch Cytoscape.
2. **File → Open Session** and select **`Cytoscape_session.cys`**.
   That’s it—network, attributes, and styling should load automatically.

### Option B — Import the raw files (from scratch)

1. **Import the network**

   * **File → Import → Network from File…**
   * Select **`GG_network.sif`**, then **Import**.
     Cytoscape will create nodes for the genes and edges for their connections.

2. **Add node attributes**

   * **File → Import → Table from File…** 
   * Select **`GG_network_nodeattr.txt`**.
   * In the dialog:
     * **Where to Import Table:** *To a network collection*
     * **Import Data As:** *Node Table Columns*
   * Click **OK** to attach attributes (e.g., Essentiality) to each node.

---

## Viewing gene essentiality

Once attributes are attached:

* Open the **Style** panel (right side).
* Under **Fill Color**, set a **Column** to your essentiality field (e.g., `LABEL{E/NE`).
* Choose a **Mapping**:
  * **Discrete Mapping** (e.g., `E` → one color, `NE` → another).
* (Optional) Use **Size** or **Border Width** to emphasize specific categories or scores.


---

## Network analysis (to probe mechanisms of action)

Use Cytoscape’s **Network Analyzer** tools to identify critical genes and paths that may be perturbed:

---

## File format notes

* **SIF (`GG_network.sif`)**
  Minimal format: `source  interaction  target`
  The interaction label is a free text token (e.g.,`mp`, `pp`, `interacts_with`, `regulates`). If absent, Cytoscape will still import edges, but adding an interaction type can help with styling.

* **Attributes (`GG_network_nodeattr.txt`)**

  * **Tab-delimited** text with a header row.
  * First column should match node IDs used in the SIF (commonly the node `name`).
  * Include a column like `LABEL(E/NE)` with values such as `E` / `NE`.

