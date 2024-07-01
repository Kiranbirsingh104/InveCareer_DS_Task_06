# project-Employee-Turnover-Analysis-
# load the data set
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
hr_df = pd.read_csv('/kaggle/input/hr-analytics-data-set/HR_capstone_dataset.csv')
df = hr_df.copy()
df.head()
# Bar graph: Turnover by department
plt.figure(figsize=(10, 6))
sns.countplot(data=data, x='Department', hue='Turnover')
plt.title('Turnover by Department')
plt.xlabel('Department')
plt.ylabel('Count')
plt.xticks(rotation=45)
plt.legend(title='Turnover')
plt.show()
# Pie chart: Reasons for leaving
reasons = df[df['Reason_for_Leaving'] != '']['Reason_for_Leaving']
plt.figure(figsize=(8, 8))
plt.pie(reasons.value_counts(), labels=reasons.value_counts().index, autopct='%1.1f%%', startangle=140)
plt.title('Reasons for Leaving')
plt.show()
# Convert to DataFrame
df = pd.DataFrame(data)
# Create a pivot table or cross-tabulation
pivot_table = pd.crosstab(df['Department'], df['JobSatisfaction'])
# Plot heatmap
plt.figure(figsize=(10, 6))
sns.heatmap(pivot_table, annot=True, cmap='YlGnBu', fmt='d')
plt.title('Job Satisfaction Counts by Department')
plt.xlabel('Job Satisfaction')
plt.ylabel('Department')
plt.show()
