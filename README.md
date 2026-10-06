# Grammar Scoring Engine

A Jupyter Notebook-based machine-learning project for predicting grammar scores from spoken-audio samples. The notebook develops an end-to-end scoring workflow and produces a CSV submission containing one predicted score for each audio file.

**Repository:** [prathamkumar125/grammar-scoring-engine](https://github.com/prathamkumar125/grammar-scoring-engine)

## Implementation summary

The implementation is contained in [`grammar-scoring-engine.ipynb`](./grammar-scoring-engine.ipynb). At a high level, the notebook:

1. Extracts the SHL Hiring Assessment 2026 dataset.
2. Loads the training and test metadata along with the corresponding `.wav` audio files.
3. Uses OpenAI Whisper to transcribe the spoken audio into text.
4. Cleans the transcripts by lowercasing text, removing punctuation and special characters, and normalizing whitespace.
5. Converts the cleaned transcripts into numerical features using a TF-IDF vectorizer with the top 1,000 features.
6. Trains a `RandomForestRegressor` with 100 estimators to predict continuous grammar scores.
7. Splits the training data into 80% training and 20% validation sets.
8. Evaluates the model using Mean Squared Error and Pearson correlation.
9. Applies the same transcription, cleaning, and TF-IDF pipeline to the test audio files.
10. Generates predictions and saves them to `submission.csv`.
11. Visualizes actual versus predicted grammar scores with a scatter plot.

The notebook reports a validation MSE of approximately `1.2522` and a training-set Pearson correlation of approximately `0.8925` for the saved run. Results can vary depending on the execution environment and model configuration.

### Pipeline

```text
Audio files
    ↓
Whisper speech-to-text transcription
    ↓
Text cleaning and normalization
    ↓
TF-IDF feature extraction
    ↓
Random Forest regression
    ↓
Predicted grammar scores
    ↓
submission.csv
```

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

### 2. Install the notebook dependencies

The notebook installs or uses packages including:

- `openai-whisper`
- `librosa`
- `language-tool-python`
- `scikit-learn`
- `pandas`
- `numpy`
- `matplotlib`

You can install the main dependencies with:

```bash
pip install openai-whisper librosa language-tool-python scikit-learn pandas numpy matplotlib
```

### 3. Open the notebook

Launch Jupyter Notebook or JupyterLab:

```bash
jupyter notebook
```

Then open `grammar-scoring-engine.ipynb` and run the cells from top to bottom.

> The notebook was developed in a Kaggle environment and expects the competition dataset under the configured input paths. Update the dataset and audio paths if you run it locally.

## Reproducing predictions

1. Download and make the required audio dataset available to the notebook.
2. Open `grammar-scoring-engine.ipynb`.
3. Run the data-loading and transcription cells.
4. Clean the generated transcripts.
5. Fit the TF-IDF vectorizer and Random Forest regression model.
6. Run inference on the test transcripts.
7. Export the predictions in the same two-column format as `submission.csv`.

## Notes

- This project is currently organized as a single Jupyter Notebook.
- The checked-in CSV is a generated prediction submission; the source audio dataset is not included in this repository.
- Despite the repository name, the main scoring workflow does not directly parse grammar rules. It learns a regression relationship between transcript TF-IDF features and grammar-score labels.
- Model performance depends on the audio data, Whisper model, preprocessing, feature extraction, and training configuration used in the notebook.

## License

No license has been specified for this repository yet.
