# Page-View-Time-Series-Visualizer
certification python project from <a href="https://www.freecodecamp.org/learn/data-analysis-with-python/data-analysis-with-python-projects/page-view-time-series-visualizer" target="_blank" rel="noopener noreferrer">freecodecamp</a>


1. using Python to visualize time series data using a line chart, bar chart, and box plots. 

2. the data visualizations will help us understand the patterns in visits and identify yearly and monthly growth of page views each day on the freeCodeCamp.org forum from 2016-05-09 to 2019-12-03. 

3. import libaries

    <details>
    <summary>library</summary>
    <pre>
    import matplotlib.pyplot as plt
    import pandas as pd
    import seaborn as sns
    from pandas.plotting import register_matplotlib_converters
    register_matplotlib_converters()
    </pre>
    </details>

4. Import data (Make sure to parse dates. Consider setting index column to 'date')
    
    <details>
    <summary>import data</summary>
    <pre>
    df = pd.read_csv("fcc-forum-pageviews.csv", index_col="date", parse_dates=["date"])
    </pre>
    </details>

5. clean the data by filtering out days when the page views were in the top 2.5% of the dataset or bottom 2.5% of the dataset
    
    <details>
    <summary>clean data</summary>
    <pre>
    df = df[(df["value"] >= df["value"].quantile(0.025)) & (df["value"] <= df["value"].quantile(0.975))]
    </pre>
    </details>

6. create a draw_line_plot function that uses Matplotlib to draw a line chart. The title should be Daily freeCodeCamp Forum Page Views 5/2016-12/2019. The label on the x axis should be Date and the label on the y axis should be Page Views.
    
    <details>
    <summary>draw_line_plot</summary>
    <pre>
    def draw_line_plot():
    # Draw line plot
    fig, ax = plt.subplots(figsize=(12,6))
    ax.plot(df.index, df["value"], color="red", linewidth=1)
    ax.set_xlabel("Date")
    ax.set_ylabel("Page Views")
    ax.set_title("Daily freeCodeCamp Forum Page Views 5/2016-12/2019")</br>
    # Save image and return fig
    fig.savefig('line_plot.png')
    return fig
    </pre>
    </details>
    
    
    <details>
    <summary>line plot</summary>
    <img src="https://github.com/mas-tono/Page-View-Time-Series-Visualizer/blob/main/image/line_plot.png">
    </details>

7.Create a draw_bar_plot function that draws a bar chart. It should show average daily page views for each month grouped by year. The legend should show month labels and have a title of Months. On the chart, the label on the x axis should be Years and the label on the y axis should be Average Page Views.




put them together in time_series_visualizer.py file

call via main.py
