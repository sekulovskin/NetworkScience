Before arriving at Utrecht please install the following software:
- [R and RStudio](https://posit.co/download/rstudio-desktop/)
- [Pixi](https://pixi.sh/) for Python

Please update R if you have it installed but you haven’t updated it in the last 6-12 months.

## Python setup with Pixi

Pixi is a package and environment manager. It reads `pixi.toml`, creates the Python environment automatically, and runs commands inside that environment. You do not need Anaconda for the Python practicals.

Install Pixi:

### macOS and Linux

```bash
curl -fsSL https://pixi.sh/install.sh | sh
```

Or, if you use Homebrew:

```bash
brew install pixi
```

### Windows PowerShell

```powershell
powershell -ExecutionPolicy Bypass -c "irm -useb https://pixi.sh/install.ps1 | iex"
```

Restart your terminal/PowerShell afterwards, then check that Pixi works:

```bash
pixi --version
```

## Test your installation

Please test that your installation works by downloading the files in this folder.
- For R, open `test_R.Rmd` with RStudio and try to run it.
- For Python, download `test_Python.ipynb` and `pixi.toml` into the same folder (not on a cloud drive such as OneDrive or pCloud, but in a normal folder on your computer). Then open the terminal/PowerShell in that folder and run `pixi run jupyter lab`. JupyterLab will open in your browser and show `test_Python.ipynb` in the left menu; open it and try to run it.

The first run takes a few minutes because Pixi downloads the Python environment.

## Troubleshooting

If the folder is inside a synced drive such as pCloud, OneDrive, Dropbox, or iCloud Drive, Pixi may fail with an error about symlinks. You can solve it by moving the folder out of the synced drive, or by running this once from the folder before starting JupyterLab:

```bash
pixi config set --local detached-environments true
```

This keeps the generated Python environment outside the synced folder, which avoids file-linking problems on some systems.

If Pixi still reports that it cannot create a symlink for `.pixi/envs`, create that folder manually and rerun:

```bash
mkdir -p .pixi/envs
pixi run jupyter lab
```

In case you encounter problems, please contact [Javier Garcia-Bernardo](mailto:javier.uu@proton.me).
