# Grammar Scoring Engine

A Jupyter Notebook-based project for estimating grammar scores from spoken-audio samples. The repository contains the full experimentation workflow and a generated submission file with one predicted score per audio recording.

## Repository contents

- [`grammar-scoring-engine.ipynb`](./grammar-scoring-engine.ipynb) — Notebook containing the data-processing, modeling, evaluation, and prediction workflow.
- [`submission.csv`](./submission.csv) — Generated predictions with the columns `filename` and `label`.

## Output format

`submission.csv` follows this format:

```csv
filename,label
audio_128.wav,3.075
audio_156.wav,3.365
```

- `filename`: Name of the audio sample.
- `label`: Predicted grammar score for that sample.

## Getting started

### 1. Clone the repository

```bash
git clone https://github.com/prathamkumar125/grammar-scoring-engine.git
cd grammar-scoring-engine
```

### 2. Open the notebook

Launch Jupyter Notebook or JupyterLab:

```bash
jupyter notebook
```

Then open `grammar-scoring-engine.ipynb` and run the cells from top to bottom.

> The notebook may require additional Python packages and access to the input audio dataset. Install the dependencies referenced by the notebook and update the dataset paths if your files are stored in a different location.

## Reproducing predictions

1. Make the required audio data available to the notebook.
2. Open `grammar-scoring-engine.ipynb`.
3. Run the preprocessing and inference cells.
4. Export the predictions in the same two-column format as `submission.csv`.

## Notes

- This project is currently organized as a single Jupyter Notebook.
- The checked-in CSV is an example/generated prediction submission, not the source audio dataset.
- Model performance depends on the audio data, preprocessing steps, feature extraction, and training configuration used in the notebook.

## License

No license has been specified for this repository yet.
