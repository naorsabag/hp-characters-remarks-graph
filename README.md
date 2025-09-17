# Harry Potter Characters Remarks Graph

An interactive network visualization tool that analyzes dialogues and remarks between Harry Potter characters, showing their relationships through sentiment analysis and conversation patterns.

## What This Project Does

This project creates an interactive network graph from Harry Potter dialogue data that:

- **Visualizes character relationships** based on who talks to/about whom
- **Analyzes sentiment** of conversations (positive, negative, neutral)  
- **Shows conversation patterns** through node sizes and edge weights
- **Provides dual viewing modes:**
  - **Speaker Mode**: Shows who speaks the most and their sentiment patterns
  - **Target Mode**: Shows who receives the most remarks and their sentiment patterns
- **Generates an interactive HTML visualization** with filtering capabilities

## Requirements

### Software Requirements
- **Python 3.7+** with Jupyter Notebook support
- **Required Python packages:**
  - `pandas` - for data manipulation
  - `networkx` - for graph processing  
  - `pyvis` - for interactive network visualization
  - `pathlib` - for file handling (built-in)
  - `json` - for data serialization (built-in)

### Data Requirements
- A CSV file named `hp-dialogues - Sheet1.csv` with the following columns:
  - `speaker` - Character who speaks
  - `target` - Character being spoken to/about
  - `sentiment` - Sentiment of the remark ("positive", "negative", or "neutral")

## How to Run

### Step 1: Set Up Your Environment

**Option A: Using Jupyter Notebook**
```bash
# Install Jupyter if you don't have it
pip install jupyter notebook

# Install required packages (or let the notebook install them)
pip install pandas networkx pyvis
```

**Option B: Using JupyterLab**
```bash
# Install JupyterLab
pip install jupyterlab

# Install required packages
pip install pandas networkx pyvis
```

**Option C: Using Google Colab**
- Upload the notebook to Google Colab
- Upload your CSV data file
- Run the cells (dependencies will be installed automatically)

### Step 2: Prepare Your Data

Ensure you have a CSV file named `hp-dialogues - Sheet1.csv` in the same directory as the notebook. The CSV should have this structure:

```csv
speaker,target,sentiment
Harry Potter,Hermione Granger,positive
Hermione Granger,Harry Potter,neutral
Draco Malfoy,Harry Potter,negative
...
```

### Step 3: Run the Notebook

1. **Start Jupyter:**
   ```bash
   # For Jupyter Notebook
   jupyter notebook
   
   # For JupyterLab  
   jupyter lab
   ```

2. **Open the notebook:**
   - Navigate to `graph_builder.ipynb`
   - Click to open it

3. **Run all cells:**
   - **Cell 1**: Installs the `pyvis` package
   - **Cell 2**: Imports required libraries
   - **Cell 3**: Processes the data and generates the visualization
   
   You can run cells individually with `Shift + Enter` or run all cells with `Cell > Run All`

### Step 4: View the Results

After running the notebook, you'll get:
- **An HTML file**: `hp_conversation_graph_toggle.html`
- **Console output**: "✔ Done! Open 'hp_conversation_graph_toggle.html' in your browser."

Open the HTML file in any web browser to interact with your graph!

## Understanding the Visualization

### Graph Elements

**Nodes (Characters):**
- **Size**: Represents the number of remarks (spoken in Speaker mode, received in Target mode)
- **Color**: Represents overall sentiment ratio
  - More **green** = more positive remarks
  - More **red** = more negative remarks
  - **Gray/purple** = neutral/mixed remarks

**Edges (Relationships):**
- **Thickness**: Number of remarks between characters
- **Color**: Overall sentiment of the relationship
  - **Green** (#2ED573): Positive
  - **Red** (#FF4757): Negative  
  - **Gray** (#747D8C): Neutral

### Interactive Features

**Viewing Modes:**
- **Speaker Graph**: Focus on who speaks and their outgoing relationships
- **Target Graph**: Focus on who receives remarks and their incoming relationships

**Controls:**
- **Click a node**: Highlight only that character's connections
- **Double-click background**: Reset to show all connections
- **Hide/Show Edges**: Toggle edge visibility
- **Hover over elements**: See detailed information

## File Structure

```
hp-characters-remarks-graph/
├── graph_builder.ipynb          # Main Jupyter notebook
├── hp-dialogues - Sheet1.csv    # Your dialogue data (you provide this)
├── hp_conversation_graph_toggle.html  # Generated interactive graph
└── README.md                    # This file
```

## Troubleshooting

**Common Issues:**

1. **"FileNotFoundError: hp-dialogues - Sheet1.csv"**
   - Make sure your CSV file is in the same directory as the notebook
   - Check the filename exactly matches (including spaces and capitalization)

2. **"ModuleNotFoundError: No module named 'pyvis'"**  
   - Run the first cell to install pyvis, or install manually: `pip install pyvis`

3. **Empty or broken graph**
   - Check your CSV data format and column names
   - Ensure you have data with the required columns: `speaker`, `target`, `sentiment`

4. **Graph doesn't display properly**
   - Try opening the HTML file in a different browser
   - Ensure JavaScript is enabled in your browser

## Customization

You can modify the notebook to:
- **Change input filename**: Edit the `INPUT_CSV` variable
- **Adjust graph layout**: Modify the `nx.spring_layout` parameters
- **Change colors**: Update the `EDGE_COLORS` dictionary
- **Adjust node/edge sizing**: Modify the size calculation formulas
- **Add more sentiment categories**: Extend the sentiment processing logic

## Example Data Format

Your CSV should look like this:

```csv
speaker,target,sentiment
Harry Potter,Ron Weasley,positive
Harry Potter,Hermione Granger,positive
Draco Malfoy,Harry Potter,negative
Severus Snape,Harry Potter,negative
Hermione Granger,Ron Weasley,neutral
Hagrid,Harry Potter,positive
Voldemort,Harry Potter,negative
```

## Output

The generated HTML file is completely self-contained and can be:
- Opened in any modern web browser
- Shared with others (no dependencies needed)
- Embedded in websites or presentations
- Used for interactive exploration of character relationships

Enjoy exploring the magical world of Harry Potter character interactions! ⚡
