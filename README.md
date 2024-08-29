
# T20 Cricket Match Score Prediction

This project aims to predict the final score of a cricket match using ball-by-ball data from T20 matches. The data is processed and features are engineered to create a machine learning model that predicts the total runs scored in a match based on various factors such as the teams involved, venue, current run rate, and more.

## Project Structure

- **data/**: Contains the raw YAML files of T20 cricket matches.
- **notebooks/**: Jupyter notebooks used for data exploration, feature engineering, and model building.
- **README.md**: Project documentation.

## Data Description

The data consists of ball-by-ball information from various T20 cricket matches. The key features include:

- `batting_team`: The team currently batting.
- `bowling_team`: The team currently bowling.
- `city`: The city where the match is being played.
- `current_score`: The score at the current ball.
- `balls_left`: The number of balls remaining in the innings.
- `wickets_left`: The number of wickets remaining.
- `crr`: Current run rate (runs per over).
- `last_five`: Runs scored in the last five overs.

## Data Preprocessing

1. **Loading and Merging Data**: YAML files are loaded and converted into a tabular format using Pandas. Each match is assigned a unique `match_id`.
2. **Feature Engineering**:
   - Extracted features like `current_score`, `balls_left`, `wickets_left`, `crr`, and `last_five`.
   - Encoded categorical variables like `batting_team`, `city`, and `bowling_team`.
   - Filtered data to include only relevant matches and teams.
3. **Data Cleaning**:
   - Filled missing values in `city` by extracting from `venue`.
   - Dropped irrelevant columns and rows with missing data in the `last_five` column.

## Model Training

A pipeline was created to preprocess the data and train an XGBoost regressor:

- **Preprocessing**:
  - Categorical variables were one-hot encoded.
  - Data was scaled using `StandardScaler`.
- **Model**:
  - Used `XGBRegressor` with `n_estimators=1000`, `learning_rate=0.2`, and `max_depth=12`.
  - Evaluated using `r2_score`, `mean_absolute_error`, and `adjusted_r2_score`.

## Results

- **R² Score**: 0.98
- **Mean Absolute Error (MAE)**: 1.92
- **Adjusted R² Score**: 0.988

The model demonstrates a strong ability to predict the final score based on the ball-by-ball data.

## Usage

- The model pipeline is saved as `pipe.pkl`. You can load the model and make predictions on new data by loading the pipeline using `pickle`:

## Contributing

Contributions are welcome! Please fork the repository and submit a pull request for any enhancements or bug fixes.

## Acknowledgments

- Special thanks to the developers of `pandas`, `tqdm`, `XGBoost`, and other libraries that made this project possible.

