# Fitness Tracker CLI

A comprehensive command-line fitness tracking tool built in Python. Log workouts, track diet, monitor progress, and uncover correlations between your nutrition and performance. All from the terminal.

## Why a CLI?

No apps and websites full of ads and subscriptions. Open a terminal, run the tool, and log a workout in seconds. The entire experience is keyboard-driven, instant, and lives on your machine. Data is stored locally in SQLite; fast to query, easy to back up, and entirely yours.

## Features

### Logging
- **Workouts**: Interactive exercise logging with automatic set parsing (`135lb x 10`, `135x10`, etc.)
- **Diet**: Daily nutrition tracking (calories, protein, carbs, creatine)
- **Bodyweight**: Daily bodyweight for relative strength metrics

### Reports
- **Daily**: Full day view: all exercises, sets, diet stats, bodyweight
- **Weekly**: Aggregated volume, macros, and training frequency
- **Monthly**: Long-term trends and summaries

### Analytics
- **Personal Records**: Auto-detected max weight, max volume, max reps per exercise
- **Progress Tracking**: Volume, volume/set, best set, e1RM over time
- **Exercise Comparison**: Overlay progress curves of multiple exercises
- **Correlation Analysis**: Diet vs performance with statistical significance

### Visualization
- Progress line charts
- Correlation scatter plots with regression
- Muscle group radar charts
- Heatmaps, stacked bars, and more

## Project Structure

```
fitness_tracker/
├── cli.py            # Main entry point, menu routing
├── database.py       # SQLite initialization, schema, migrations
├── models.py         # Dataclasses for all entities
├── workout.py        # Interactive workout logging, set parsing
├── diet.py           # Daily diet logging
├── bodyweight.py     # Bodyweight logging
├── reports.py        # Daily/weekly/monthly report generation
├── analytics.py      # PRs, progress, correlations, comparisons
├── plots.py          # Matplotlib/seaborn chart generation
├── muscle_groups.py  # Exercise -> muscle group auto-detection
└── utils.py          # Set parsing, formatting, date helpers
```

## Data Manipulation & Analysis

The system is designed to support rich analysis from simple log-style entries:

| Analysis                  | Input | Output |
|---------------------------|---|---|
| **Progressive Overload**  | Sets × reps × weight over time | Line chart of e1RM per exercise |
| **Diet -> Strength**      | Daily macros + workout volume | Scatter + regression, Pearson r |
| **Recovery Optimization** | Session dates + performance delta | Optimal rest day recommendation |
| **Muscle Balance**        | Exercise names → muscle groups | Radar chart of volume distribution |
| **Phase Comparison**      | Date ranges + PRs | Bar chart: PRs in surplus vs deficit |
| **Volume Trend**          | Weekly total volume | Rolling average with plateau detection |
| **Creatine Impact**       | Creatine log start date + strength | Pre/post strength comparison |
| **Relative Strength**     | Bodyweight + exercise max | Strength-to-BW ratio over time |
| **Frequency Analysis**    | Sessions per week per exercise | Frequency vs progress rate scatter |
| **Best Set Tracking**     | Individual set volumes | Single best set per session over time |
| **Carb Timing**           | Same-day carbs + workout | Performance on high vs low carb days |
| **Consistency Score**     | Logged days / total days | Monthly consistency percentage |

## Tools Used

- **Python 3.12+**
- **SQLite** — Zero-config, file-based database
- **Rich** — Terminal tables and prompts
- **Matplotlib / Seaborn** — Plot generation
- **SciPy** — Statistical analysis (correlations, p-values)
- **uv** — Fast Python package management
