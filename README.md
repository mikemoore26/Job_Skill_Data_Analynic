# The Analysis

## 1. What are the most demanded skills for the top 3 most popular data roles?

To identify the most in-demand skills for the top three most popular data roles, I first filtered these positions by their popularity. Then, I determined the top five skills for each of the top three roles. This analysis reveals the most sought-after job titles and their essential skills, helping you focus on the skills relevant to your target roles.

View my notebook with detailed steps here:
[Notebook](skill_demand.ipynb)

### Visualize Data

```python

fig, ax = plt.subplots(len(job_titles),1, sharex=True)
sns.set_theme(style="ticks")
for ind, job_title in enumerate(job_titles):
    temp = df_skill_perc[df_skill_perc['job_title_short'] == job_title].head()
   # temp.plot(kind="barh", x="job_skills", y='perc', ax=ax[ind], title=job_title)
    sns.barplot(data=temp, x="perc", y="job_skills", hue="skill_count", palette="dark:b_r", ax=ax[ind])
    ax[ind].set_ylabel("")
    ax[ind].set_title(job_title)
    ax[ind].set_ylabel("")
    ax[ind].set_xlabel("")
    ax[ind].set_xlim(0,90)
    ax[ind].legend().set_visible(False)

    for i, v in enumerate(temp['perc']):
        ax[ind].text(v + 1,i, f"{round(v,2)}%", va='center')
    

fig.suptitle("Counts of Top Skills in Job Posting", fontsize=15)
plt.tight_layout(h_pad=0.5)
plt.show()

```

### Results

![Visualization of the Top Skills fir data Nerds](images/skill_demand.png)

### Insights

### Data Analyst

**Role Overview:**
Data Analysts gather, process, and analyze data to help organizations make informed decisions. They often work with large datasets to identify trends, patterns, and insights.

**Top Skills (from the chart):**
- **SQL (50.8%):** Essential for querying and managing data from databases.
- **Excel (40.58%):** Widely used for organizing, analyzing, and visualizing data.
- **Tableau (28.48%):** A popular tool for creating interactive data visualizations.
- **Python (27.11%):** Useful for data manipulation and analysis.
- **SAS (19.46%):** Employed for advanced statistical analysis.

### Data Engineer

**Role Overview:**
Data Engineers develop, construct, test, and maintain architectures such as databases and large-scale processing systems. They ensure data is accessible, reliable, and secure for other roles in the organization.

**Top Skills (from the chart):**
- **SQL (68.3%):** Crucial for designing, implementing, and maintaining databases.
- **Python (64.89%):** Used for scripting, data manipulation, and automation.
- **AWS (42.81%):** Provides cloud-based services and infrastructure.
- **Azure (32.27%):** Another cloud platform for deploying and managing data solutions.
- **Spark (32.05%):** Used for processing large datasets quickly.

### Data Scientist

**Role Overview:**
Data Scientists analyze and interpret complex data to help companies make strategic decisions. They use advanced analytics, machine learning, and statistical methods to build predictive models.

**Top Skills (from the chart):**
- **Python (72.04%):** Preferred for its powerful libraries for data science and machine learning.
- **SQL (51.05%):** Essential for querying databases to extract data.
- **R (44.23%):** Popular for statistical analysis and data visualization.
- **SAS (24.38%):** Used for advanced analytics and predictive modeling.
- **Tableau (23.56%):** Important for creating and sharing data visualizations.

### Summary Based on the Chart
- **Data Analysts** are highly skilled in **SQL** and **Excel**, with notable use of **Tableau** and **Python** for data visualization and analysis.
- **Data Engineers** primarily utilize **SQL** and **Python**, with significant use of cloud platforms like **AWS** and **Azure**, and big data processing tools like **Spark**.
- **Data Scientists** rely heavily on **Python** and **SQL**, with **R** also being a key skill for statistical analysis, along with tools like **SAS** and **Tableau** for specific tasks.
