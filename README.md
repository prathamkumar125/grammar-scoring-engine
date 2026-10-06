# Grammar Scoring Engine

A Jupyter Notebook-based machine-learning project for predicting grammar scores from spoken-audio samples. The notebook develops an end-to-end scoring workflow and produces a CSV submission containing one predicted score for each audio file.

## Implementation summary

The implementation is contained in [`grammar-scoring-engine.ipynb`](./grammar-scoring-engine.ipynb). At a high level, the notebook:

1. Loads the audio-based grammar-scoring data and organizes the available samples for modeling.
2. Preprocesses the audio inputs so they can be used as numerical model features.
3. Builds a supervised regression workflow to learn the relationship between speech/audio characteristics and grammar-score labels.
4. Generates predictions for the evaluation audio files.
5. Writes the predictions to `submission.csv` using the required `filename,label` format.

The resulting labels are continuous scores. The checked-in submission includes predictions ranging from approximately `1.20` to `4.37` for the provided audio files.

> The notebook is the authoritative source for the exact preprocessing, feature extraction, model configuration, and evaluation steps. Those details should be kept in sync with this README if the notebook changes.

## Repository contents

- [`grammar-scoring-engine.ipynb`](./grammar-scoring-engine.ipynb) — Complete experimentation and prediction workflow.
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
3. Run the data-loading and preprocessing cells.
4. Run the model-training and prediction cells.
5. Export the predictions in the same two-column format as `submission.csv`.

## Notes

- This project is currently organized as a single Jupyter Notebook.
- The checked-in CSV is a generated prediction submission; the source audio dataset is not included in this repository.
- Model performance depends on the audio data, preprocessing, feature extraction, and training configuration used in the notebook.

## License

No license has been specified for this repository yet.
