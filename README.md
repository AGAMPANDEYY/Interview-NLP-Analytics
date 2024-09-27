# IBY_Round2
Round2 assestment for Data Science Role Intern 

# Data Science Analysis (EDA) on Video Interview Dataset.

Welcome to the **Interview Dataset Analysis** repository! This project takes you on an in-depth journey through a dataset containing emotional, visual, and transcript data for 10 interview candidates. Using cutting-edge data analysis techniques, we explore each candidate's performance, helping you make data-driven hiring decisions!

## 📝 Dataset Breakdown

The dataset comprises three main components:

- **Emotion Data**: Tracks emotional states like anger, happiness, and fear throughout the interview. 
- **Gaze Data**: Eye metrics like blink rate and gaze direction, measuring engagement and focus.
- **Transcript Data**: Contains the transcription of each interview, including detailed metrics like speech speed and confidence levels.

### Example Snippet of `emotion_data.csv`

```csv
movie_id,image_seq,participant_id,elapsed_time,distance,gaze,blink,eye_offset,angry,happy,sad
1,001,10,0.001,0.45,12,1,0.2,0,1,0
``` 

## 📊 Key Analysis Insights
Our analysis explores the following dimensions:

### 1. Gaze Analysis
Tracking candidates' eye contact provides valuable insights into their level of engagement and focus.

```python
import plotly.express as px

# Plot gaze distribution for all candidates
fig = px.histogram(df, x="gaze", color="candidate_id", title="Gaze Distribution Across Candidates")
fig.show()
```

### 2. Emotion Analysis
We measured emotional responses like happiness and fear to gauge emotional intelligence (EQ).

```python
# Generate emotion summary statistics
emotion_summary = df_emotion.groupby('candidate_id').agg(['mean', 'std'])
```

### 3. Speech & Confidence Metrics
Analyzing speech speed and confidence during the interview reveals how effectively candidates communicate.

``` python

# Calculate confidence score
df['confidence_score'] = (df['avg_confidence'] * 0.7) - (df['std_confidence'] * 0.3)
```

### 📈 Visualizing the Data
We created interactive plots using Plotly to visualize each candidate's performance across key metrics:

- **Gaze Sum Per Candidate**: Total eye contact during the interview.
- **Emotion Variability**: Tracking fluctuations in happiness, fear, and sadness.
- **Speech & Confidence Distribution**: Insights into speaking style and clarity.

```python
import plotly.graph_objects as go

# Plot confidence scores
fig = go.Figure(data=[go.Bar(x=candidates, y=confidence_scores)])
fig.update_layout(title="Confidence Score per Candidate", xaxis_title="Candidate", yaxis_title="Confidence Score")
fig.show()
```

### 🚀 Final Candidate Scores
After analyzing all the metrics, we scored each candidate across four categories:

- **Communication**: Eye contact, speech speed, confidence, conciseness.
- **Emotional Intelligence**: Stability and regulation of emotions.
- **Transcript Analysis**: NLP techniques applied to transcriptions.
- **Final Hiring Decision**: Based on the cumulative scores from all categories.

#### Candidate Score Example

```python
# Final hiring decision example
final_scores = {
    'Candidate 1': 3.05,
    'Candidate 2': 4.23,  # Recommended for hire
    'Candidate 3': 3.23,
    ...
}
```

### 🔧 Tools & Techniques
This project leverages various powerful tools for data analysis and visualization:

- **Python (Pandas, Plotly, NLP Libraries)**: For data processing, statistical analysis, and visualizations.
- **VADER & NLP**: Applied for sentiment analysis and keyword extraction.
- **Plotly**: Interactive charts and data visualizations.
- **Google Colab**: Interactive notebooks for running the analysis.

### 📚 Getting Started
Want to dive into the code? Here's how to get started:

1. Clone this repo:

    ```bash
    git clone https://github.com/your-repo/EDA-interview-analysis.git
    cd EDA-interview-analysis
    ```

2. Install the required Python packages:

    ```bash
    pip install -r requirements.txt
    ```

3. Run the analysis:

    ```bash
    jupyter notebook
    ```

4. Open the notebook `EDA_interview_analysis.ipynb` and start exploring!

### 🎓 Contributing
We welcome contributions to improve this analysis! Feel free to open an issue or submit a pull request if you'd like to enhance the functionality or add new insights.
