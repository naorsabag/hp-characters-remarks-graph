# Harry Potter Characters Remarks Graph

A complete toolkit for extracting, analyzing, and visualizing character relationships in Harry Potter through dialogue analysis and sentiment visualization.

![demo](demo-graph.gif)

## What This Project Does

This project provides two powerful tools that work together to create interactive network graphs from Harry Potter text:

### 🔍 **Remarks Extractor** (`remarks_extractor.html`)
A sophisticated web application that:
- **Extracts character dialogue** from raw Harry Potter book text files using OpenAI GPT-4
- **Identifies speaker-target relationships** including thoughts, behind-the-back remarks, and indirect comments
- **Performs sentiment analysis** on existing CSV data with AI-powered classification
- **Maps character names** to a standardized vocabulary (188+ recognized characters)
- **Handles large text processing** with intelligent chunking and retry mechanisms
- **Outputs structured CSV data** ready for visualization

### 📊 **Graph Builder** (`graph_builder.ipynb`)
A Jupyter notebook that:
- **Creates interactive network visualizations** from dialogue CSV data
- **Provides dual viewing modes:**
  - **Speaker Mode**: Shows who speaks the most and their outgoing sentiment patterns
  - **Target Mode**: Shows who receives the most remarks and their incoming sentiment patterns
- **Visualizes relationships** through color-coded sentiment analysis
- **Offers advanced filtering** with searchable character lists
- **Generates self-contained HTML** with rich interactivity

## Complete Workflow

### Option 1: Extract Your Own Data (Full Pipeline)
1. **Get Harry Potter text files** (Book1.txt, Book2.txt, etc.)
2. **Use Remarks Extractor** to extract dialogue data
3. **Use Graph Builder** to create interactive visualizations

### Option 2: Use Existing Data (Visualization Only)
1. **Start with CSV data** (`hp-dialogues.csv` is included)
2. **Use Graph Builder** to create interactive visualizations

## Requirements

### For Remarks Extractor
- **Modern web browser** with JavaScript enabled
- **OpenAI API key** (requires paid OpenAI account)
- **Harry Potter book text files** (`.txt` format)
- **Optional**: Existing CSV file for sentiment re-analysis

### For Graph Builder
- **Python 3.7+** with Jupyter Notebook support
- **Required Python packages:**
  - `pandas` - data manipulation
  - `networkx` - graph processing  
  - `pyvis` - interactive network visualization
  - `pathlib`, `json` - built-in Python modules

## Getting Started

### Step 1: Extract Character Remarks (Optional)

If you want to extract data from your own Harry Potter text files:

1. **Open `remarks_extractor.html`** in your web browser
2. **Enter your OpenAI API key** (stored locally, never transmitted)
3. **Upload Harry Potter book files** (Book1.txt through Book7.txt)
4. **Click "Start Extraction"** and wait for processing
5. **Save the output JSON** and convert to CSV format

**For existing CSV sentiment analysis:**
1. Upload your CSV file with columns: `book`, `speaker`, `target`, `sentiment`, `description`
2. Click "Analyze Sentiment from CSV"
3. Save the enhanced results

### Step 2: Create Interactive Visualization

1. **Set up Python environment:**
   ```bash
   # Install Jupyter
   pip install jupyter pandas networkx pyvis
   
   # Start Jupyter
   jupyter notebook  # or jupyter lab
   ```

2. **Prepare your data:**
   - Ensure you have `hp-dialogues.csv` in the project directory
   - CSV should have columns: `speaker`, `target`, `sentiment`

3. **Run the notebook:**
   - Open `graph_builder.ipynb`
   - Run all cells (or `Cell > Run All`)
   - Wait for processing (creates speaker and target graph data)

4. **View the results:**
   - Open generated `index.html` in your browser
   - Explore the interactive visualization!

## Understanding the Visualization

### Graph Elements

**Nodes (Characters):**
- **Size**: Number of remarks (spoken in Speaker mode, received in Target mode)
- **Color**: Sentiment mix using weighted color blending:
  - **Green** tones: More positive remarks
  - **Red** tones: More negative remarks
  - **Gray** tones: Neutral/balanced remarks

**Edges (Relationships):**
- **Thickness**: Total number of remarks between characters
- **Color**: Sentiment mix of the relationship using same color scheme
- **Direction**: Arrow shows speaker → target relationship

### Interactive Features

**Viewing Modes:**
- **Speaker Graph**: Focus on who makes remarks (outgoing relationships)
- **Target Graph**: Focus on who receives remarks (incoming relationships)

**Advanced Controls:**
- **Character Filtering**: Searchable dropdown menus for speakers and targets
- **Smart Filtering Logic**:
  - Select speakers only → shows all their outgoing edges
  - Select targets only → shows all their incoming edges  
  - Select both → shows only edges FROM selected speakers TO selected targets
- **Node Interaction**: Click nodes to highlight their connections
- **Edge Toggle**: Hide/show all edges for better node visibility
- **Reset**: Double-click background to reset all filters

## File Structure

```
hp-characters-remarks-graph/
├── remarks_extractor.html       # Web-based text extraction tool
├── graph_builder.ipynb          # Jupyter notebook for visualization
├── character_names.json         # Standardized character names database
├── hp-dialogues.csv            # Sample dialogue data (24K+ entries)
├── index.html                  # Generated interactive graph
├── books/                      # Directory for book text files
│   ├── Book1.txt              # (you provide these)
│   ├── Book2.txt
│   └── ...
└── README.md                   # This file
```

## Advanced Features

### Remarks Extractor Capabilities
- **Intelligent text chunking** (1000 words per chunk with paragraph boundaries)
- **Context continuity** (provides previous chunk context for better analysis)
- **Character name standardization** (maps variants to 188 standardized names)
- **Batch processing** with concurrent API calls
- **Automatic retry logic** for failed chunks
- **Progress tracking** with detailed status updates

### Graph Builder Features
- **Weighted color mixing** for nuanced sentiment representation
- **Fixed graph layout** using NetworkX spring layout (reproducible)
- **Responsive filtering** with real-time search
- **Tooltip information** showing detailed statistics
- **Cross-browser compatibility** (self-contained HTML/CSS/JS)

## Data Format

### Input CSV Format
```csv
book,speaker,target,sentiment,description
1,Harry Potter,Ron Weasley,positive,"Harry complimented Ron's chess skills"
1,Hermione Granger,Harry Potter,neutral,"Hermione explained the homework assignment"
2,Draco Malfoy,Hermione Granger,negative,"Draco called Hermione a mudblood"
```

### Expected Character Names
The system recognizes 260+ standardized character names loaded from `character_names.json`, including:
- **Main characters**: `Harry Potter`, `Hermione Granger`, `Ron Weasley`
- **Professors**: `Albus Dumbledore`, `Severus Snape`, `Minerva McGonagall`
- **Families**: `Vernon Dursley`, `Molly Weasley`, `Lucius Malfoy`
- **Groups**: `Death Eaters`, `Order of the Phoenix`, `Students`
- **Creatures**: `Dobby`, `Buckbeak`, `Hedwig`, `Crookshanks`
- **Places/Objects**: `Hogwarts`, `Ministry of Magic`, `Sorting Hat`
- **And many more** - see `character_names.json` for the complete list

## Troubleshooting

### Remarks Extractor Issues
1. **API Key Problems**: Ensure key starts with `sk-` and has sufficient credits
2. **File Upload Issues**: Use `.txt` files only, ensure proper encoding
3. **Processing Failures**: Check console for detailed error messages
4. **Character Names File Missing**: Ensure `character_names.json` is in the same directory as the extractor
5. **Character Name Issues**: Check the browser console for character loading errors

### Graph Builder Issues
1. **Missing CSV**: Ensure `hp-dialogues.csv` is in the same directory
2. **Module Errors**: Install required packages: `pip install pandas networkx pyvis`
3. **Empty Graph**: Check CSV format and column names
4. **Browser Issues**: Try different browsers, ensure JavaScript is enabled

### Performance Tips
- **Large datasets**: Consider filtering data before visualization
- **API costs**: Monitor OpenAI usage when extracting from books
- **Memory usage**: Close other applications when processing large text files

## Customization

### Graph Appearance
```python
# In graph_builder.ipynb, modify these settings:
min_size, max_size = 10, 50        # Node size range
k=5.0, iterations=150              # Layout parameters
colors = {'positive': {...}, ...}  # Color scheme
```

### Character Recognition
The system uses a standardized database of character names stored in `character_names.json`. This file contains:
- **260+ character names** organized in a structured format
- **Automatic loading** by the remarks extractor on page load
- **Fallback handling** if the file cannot be loaded
- **Easy maintenance** - simply edit the JSON file to add/modify character names

To customize character names:
1. Edit `character_names.json`
2. Add new names to the `character_names` array
3. The extractor will automatically use the updated list on next page load
