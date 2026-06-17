# Installation Instructions

Before arriving at Utrecht, please install:

1. R from <https://cran.r-project.org/>
2. RStudio Desktop from <https://www.rstudio.com/products/rstudio/download/>
3. Pixi from <https://pixi.sh/> 

You do not need to install Python separately; Pixi will install the right Python version for this course.

If you already have R installed but have not updated it in the last 6-12 months, please install the latest version from CRAN.

## 1. Install R and RStudio

Install both, in this order:

1. Install **R** from <https://cran.r-project.org/>
2. Install **RStudio Desktop** from <https://www.rstudio.com/products/rstudio/download/>

R is the programming language. RStudio is the app we will use to work with R files.

To test R:

1. Download `test_R.Rmd` from this folder (https://github.com/jgarciab/NetworkScience/tree/main/Installation).
2. Open RStudio.
3. In RStudio, open `test_R.Rmd`.
4. Try to run the file. In RStudio, you can run code chunks by clicking the green play buttons.

## 2. Install Pixi for Python

Pixi is the program we use to install Python and the Python packages for the course. Pixi reads the `pixi.toml` file and creates the correct Python environment automatically.

You will install Pixi by opening a text-based app called Terminal or PowerShell, pasting one command, and pressing `Enter`.

### macOS

1. Open the **Terminal** app.
   - You can find it with Spotlight: press `Command` + `Space`, type `Terminal`, and press `Enter`.
2. Copy and paste this command into Terminal, then press `Enter`:

```bash
curl -fsSL https://pixi.sh/install.sh | sh
```

3. Close Terminal and open it again.
4. Check that Pixi installed correctly:

```bash
pixi --version
```

If you use Homebrew, you can install Pixi with this instead:

```bash
brew install pixi
```

### Windows

1. Open **PowerShell**.
   - Click the Start menu, type `PowerShell`, and open **Windows PowerShell**.
2. Copy and paste this command into PowerShell, then press `Enter`:

```powershell
powershell -ExecutionPolicy Bypass -c "irm -useb https://pixi.sh/install.ps1 | iex"
```

3. Close PowerShell and open it again.
4. Check that Pixi installed correctly:

```powershell
pixi --version
```

### Linux

1. Open your **Terminal** app.
2. Copy and paste this command into Terminal, then press `Enter`:

```bash
curl -fsSL https://pixi.sh/install.sh | sh
```

3. Close Terminal and open it again.
4. Check that Pixi installed correctly:

```bash
pixi --version
```

## 3. Test Python and JupyterLab

Please test Python before the course.

1. Create a normal folder on your computer, for example on your Desktop or in Documents.
2. Download `test_Python.ipynb` and `pixi.toml` from here (https://github.com/jgarciab/NetworkScience/tree/main/Installation) into that same folder.

The folder must contain both files:

- `test_Python.ipynb`
- `pixi.toml`



On macOS:

1. Open the **Terminal** app.
2. Type `cd `, including the space after `cd`.
3. Drag the folder containing `test_Python.ipynb` and `pixi.toml` into the Terminal window. This fills in the folder path.
4. Press `Enter`.

On some Macs, you can also right-click the folder in Finder and choose **New Terminal at Folder**. If you do not see that option, use the drag-the-folder method above.

On Windows:

1. Open the folder in File Explorer.
2. Right-click inside the folder and choose **Open in Terminal** (or **Open a PowerShell Window**).
3. If you do not see **Open in Terminal**, click the address bar at the top, type `powershell`, and press `Enter`. PowerShell will open in that folder.

On Linux:

1. Open Terminal.
2. Type `cd `, including the space after `cd`.
3. Drag the folder into the Terminal window if your file manager supports it, or type the folder path.
4. Press `Enter`.

Then run:

```bash
pixi run jupyter lab
```

The first run can take a few minutes because Pixi downloads Python and the course packages. When JupyterLab opens in your browser, click `test_Python.ipynb` in the left menu and try to run the notebook.

## Troubleshooting

### Pixi command not found

If `pixi --version` gives an error, close Terminal or PowerShell and open it again. If it still does not work, restart your computer and try again.

### Synced folders such as pCloud, OneDrive, Dropbox, or iCloud Drive

Pixi may fail inside synced folders because these folders sometimes do not support the file links used by Python environments.

The simplest solution is to move the course folder to a normal folder on your computer.

If you need to keep the folder inside a synced drive, open Terminal or PowerShell in that folder and run this once before starting JupyterLab:

```bash
pixi config set --local detached-environments true
```

Then run:

```bash
pixi run jupyter lab
```

If Pixi still reports that it cannot create a symlink for `.pixi/envs`, create that folder manually and rerun:

```bash
mkdir -p .pixi/envs
pixi run jupyter lab
```

In case you encounter problems, please contact [Javier Garcia-Bernardo](mailto:j.garciabernardo@uu.nl).
