# Repo Health Visualization Tool

Our visualization tool calculates metrics essential for repository health analysis, including:
- Turnaround times for issues and PRs.
- Open-to-closed ratios for issues and PRs.
- Monthly and cumulative trends for open/closed issues and PRs.
- Age distributions of open issues and PRs.
- Commit frequency and average commit size.
Additionally, we provide a method to define custom groups of labels and visualize their counts over time. This method enables users to aggregate and track the trends of related labels such as 'bug,' 'enhancement,' and 'feature request,' or severity and impact-related labels. These visualizations can offer deeper insights into the evolution of project priorities and focus areas.

## How to use it

Make sure to install all requirements using `pip install requirements.txt`. (`requirementsV2.txt` is created using conda)!
Generate a GitHub Access token with at least read permissions and add it to the .env file: GITHUB_PAT=`[YOUR_GITHUB_PAT]`. Open the Jupyter notebook and adjust the variables in the first cell: `user_name`, `repository_name` and also `input_json_file` if you got a .json file containing all issue and pull request data. Otherwise all of this data has to be fetched from GitHub which can be very time consuming due to rate limits.
Afterwards execute the Jupyter Notebook and it will generate `.png`s for all visualizations created using Matplotlib, as well as `.json`s and `.csv`s containing the data required for those plots, making them ready for integration into custom dashboards. The integration can be done using e.g. Plotly similarly as shown in the Notebook. It is planned to integrate all of that into a dashboard of our own, but currently that isn't implemented yet.

### What to do with the results

The visualizations can provide valuable insights on how the project is going and support the decision between working on fixing bugs vs. implementing new features/ adding documentation. Things like increases in turnaround times for or the amounts of issues and PRs can be due to a variety of factors. These visualizations can help identifying what a probable cause for those is and therefore help mitigating that.

While testing the utility of our visualizations and investigating the causes of bug spikes in vaadin/flow, we found that a graph combining commit frequency, average commit size, and bug issue counts over time provided valuable insights as can be seen below:

![Commit frequency, average commit size, and bug issue counts over time](https://raw.githubusercontent.com/SmartDeltaFraunhoferFOKUS/Repo_Health_Visualization_Tool/master/commit_freq__avg_commit_size__bug_issues.png)

The figure above depicts a visualization showing commit frequency, average commit size, and bug issue counts over time for vaadin/flow. This graph highlights patterns and provides insights into bug spike causes.
