## Automatic File Sorter in Explorer (Python)

This Python script helps you automatically organize files in a folder by sorting them into subfolders based on their file type (e.g., `.csv`, `.png`, `.txt`, `.pdf`, `.pptx`).


### Features

* Automatically creates folders:
  `csv files/`, `image files/`, `txt files/`, `pdf files/`, `ppt files/`
* Moves each file into the correct folder based on its extension
* Prevents overwriting by checking if the file already exists in the target folder


### Example Output Structure

If you run the script in a folder with these files:

```
data.csv
image.png
notes.txt
document.pdf
slides.pptx
```

After running the script, the folder structure becomes:

```
your-folder/
├── csv files/
│   └── data.csv
├── image files/
│   └── image.png
├── txt files/
│   └── notes.txt
├── pdf files/
│   └── document.pdf
├── ppt files/
│   └── slides.pptx
└── your_script.py
```


### How It Works

1. Checks for five target folders (one for each file type).
2. Creates any that don't already exist.
3. Loops through all files in the main folder.
4. If a file matches `.csv`, `.png`, `.txt`, `.pdf`, or `.pptx`, and doesn't already exist in the target folder, it moves it.


### Setup and Usage

#### Requirements

* Python 3.x
* Uses only built-in libraries: `os`, `shutil`

#### Usage

1. Place the script in the folder containing the files you want to sort.
2. Set the `path` variable in the script to the full path of that folder.
3. Run the script:

```bash
python your_script_name.py
```

---

### Example Python Code

```python
import os
import shutil

path = "C:/path/to/your/folder/"  # Update this to your folder path

folder_names = ['csv files', 'image files', 'txt files', 'pdf files', 'ppt files']

# Create folders if they don't exist
for loop in range(0, 5):
    if not os.path.exists(path + folder_names[loop]):
        os.makedirs(path + folder_names[loop])

files_names = os.listdir(path)

# Sort files based on extension
for file in files_names:
    if ".csv" in file and not os.path.exists(path + "csv files/" + file):
        shutil.move(path + file, path + "csv files/" + file)
    elif ".png" in file and not os.path.exists(path + "image files/" + file):
        shutil.move(path + file, path + "image files/" + file)
    elif ".txt" in file and not os.path.exists(path + "txt files/" + file):
        shutil.move(path + file, path + "txt files/" + file)
    elif ".pdf" in file and not os.path.exists(path + "pdf files/" + file):
        shutil.move(path + file, path + "pdf files/" + file)
    elif ".pptx" in file and not os.path.exists(path + "ppt files/" + file):
        shutil.move(path + file, path + "ppt files/" + file)
```


### Notes

* You can add more file types by expanding the `elif` block.
* Make sure the `path` ends with `/` (or `\\` for Windows).
* It is recommended to test the script on a sample folder first.


### Author

Created by LIATA ORNELLA
A simple project to practice Python and automate daily tasks.

