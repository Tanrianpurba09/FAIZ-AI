FAIZ-AIA master-level universal file search bot and retrieval engine.FAIZ-AI is a powerful, asynchronous CLI tool designed to search for files across multiple protocols (HTTP, FTP, IPFS, Torrent) simultaneously. It leverages semantic search with vector embeddings to rank results by relevance, ensuring high-quality retrieval. It also features built-in safety mechanisms, including virus scanning and intent verification.🚀 Key FeaturesMulti-Protocol Search: Aggregates results from:HTTP: Advanced Google Dorking for specific file types.FTP: Asynchronous scanning of public FTP servers (e.g., FreeBSD, kernel.org).IPFS: Decentralized file search via IPFS gateways.Torrent: DHT (Distributed Hash Table) simulation for magnet links.Semantic Intelligence: Uses SentenceTransformer (all-MiniLM-L6-v2) to generate vector embeddings for queries and results, ranking files by semantic similarity rather than just keyword matching.Smart Query Processing:Spell Correction: Automatically corrects typos in search queries using pyspellchecker.Intent Verification: Blocks unsafe or malicious queries (e.g., searching for passwords or executable scripts).Safety First:VirusTotal Integration: Capable of verifying file hashes against the VirusTotal API.Extension Filtering: automatically blocks dangerous file extensions (.exe, .bat, .sh).High Performance: Built on asyncio and aiohttp for non-blocking, concurrent execution across all search protocols.🛠️ InstallationPrerequisitesPython 3.8+pipLinux/Unix environment (recommended for the automated setup script)Automated SetupThe project includes a setup script to automate environment creation and dependency installation.Bash# Make the script executable
chmod +x setup.sh

# Run the setup script
./setup.sh
Note: The setup script will update system packages, create a virtual environment, and install all necessary Python libraries.Manual InstallationClone the repository:Bashgit clone https://github.com/yourusername/faiz-ai.git
cd faiz-ai
Create and activate a virtual environment:Bashpython3 -m venv venv
source venv/bin/activate  # On Windows use: venv\Scripts\activate
Install dependencies:Bashpip install sentence-transformers==2.2.2 aiohttp==3.9.1 aioftp==0.21.3 pyspellchecker==0.7.2 pyyaml==6.0.1 numpy==1.24.3
⚙️ ConfigurationFAIZ-AI is highly configurable via config/config.yaml.CategoryOptionDescriptionCoremodelThe SentenceTransformer model used (default: all-MiniLM-L6-v2).SearchtimeoutGlobal search timeout in seconds.protocolsActive protocols (e.g., ["http", "ftp", "ipfs", "torrent"]).filetypesSupported extensions for HTTP search (pdf, docx, mp4, etc.).Safetyblocked_extensionsList of extensions to ignore for safety.FTPpublic_serversList of public FTP servers to scan.🖥️ UsageActivate the virtual environment (if not already active):Bashsource venv/bin/activate
Run the main CLI:Bashpython main.py
Enter your search query when prompted.Example: linux documentation pdfExample: ubuntu iso torrentThe tool will display real-time logs of the scanning process. Once complete, it ranks the results using the Semantic Brain and saves the top findings to faiz_results.json.📂 Project Structurefaiz-ai/
├── config/
│   └── config.yaml          # Configuration settings
├── src/
│   ├── agents/              # Headless browsing agents
│   ├── core/
│   │   └── semantic_brain.py # Vector embedding logic
│   ├── protocols/           # Protocol handlers (HTTP, FTP, IPFS, Torrent)
│   ├── safety/              # Safety verifiers (VirusTotal, Hash checks)
│   ├── search/              # Main retriever and ranker logic
│   └── utils/               # Helpers (Logger, Spell Check)
├── main.py                  # CLI Entry point
├── setup.sh                 # Installation script
└── README.md
⚠️ DisclaimerThis tool is a personal project intended for educational purposes. Please use responsibly and adhere to all applicable laws regarding file downloading and copyright. The developers are not responsible for the content retrieved or how the tool is used.
