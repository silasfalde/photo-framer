# Photo Framer

Photo Framer processes images from any input directory and produces:
- processed outputs (split landscape images or copied portraits)
- framed outputs sized for Instagram-style posting

The core logic lives in the Python package and is reused by both:
- a command line script
- the notebook

## Requirements

- Python 3.10+
- pip

Install dependencies:

python -m pip install -r requirements.txt

## Quick Start

Run against any directory of images:

python photo_framer_cli.py /path/to/source-images

You can also run the executable form:

./photo_framer_cli.py /path/to/source-images

Default outputs are created next to the source directory:
- SOURCE_NAME-processed
- SOURCE_NAME-framed

## CLI Usage

Basic form:

python photo_framer_cli.py SOURCE_DIR [options]

Common options:
- --processed-dir PATH
- --framed-dir PATH
- --target-width INT (default 1080)
- --target-height INT (default 1440)
- --baseline-frame-width INT (default 60)
- --frame-color R,G,B (default 255,255,255)
- --extensions .jpg,.jpeg
- --no-upscale
- --reencode-portraits
- --validate
- --run-tests
- --quiet

Example with explicit output folders:

python photo_framer_cli.py ./instagram --processed-dir ./instagram-processed --framed-dir ./instagram-framed --validate

## Notebook Usage

Open and run [photo_framer.ipynb](photo_framer.ipynb).

Suggested order:
1. Run Cell 3 (imports)
2. Run Cell 5 (configuration)
3. Run Cell 11 (source summary)
4. Run Cell 13 (basic tests, optional)
5. Run Cells 15 and 16 (processing, validation, diagnostics, preview)

The notebook imports shared logic from [photo_framer/core.py](photo_framer/core.py), so notebook and CLI behavior stay aligned.

## Supported Files

By default, the tool processes:
- .jpg
- .jpeg

Use --extensions to customize accepted suffixes.

## Typical Workflow

1. Place source images in any folder.
2. Run the CLI with that folder path.
3. Check processed outputs in the processed folder.
4. Check framed outputs in the framed folder.
5. Use --validate when you want structural checks after processing.

## Project Structure

- [photo_framer/core.py](photo_framer/core.py): shared processing logic
- [photo_framer_cli.py](photo_framer_cli.py): command line entrypoint
- [photo_framer.ipynb](photo_framer.ipynb): interactive workflow and preview
- [requirements.txt](requirements.txt): dependencies
