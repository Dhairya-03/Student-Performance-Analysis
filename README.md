# student_percentage_chart.py
import pandas as pd
import matplotlib.pyplot as plt

# Step 1: Create student data (10 students, marks vary a lot)
data = {
    "Name": ["Amit", "Riya", "Dhimahi", "Neha", "Raj", "Kiran", "Meena", "Suresh", "Pooja", "Vivek"],
    "Enrollment": [101, 102, 103, 104, 105, 106, 107, 108, 109, 110],
    "Sub1": [95, 40, 28, 95, 32, 30, 99, 45, 83, 60],
    "Sub2": [25, 92, 35, 98, 50, 95, 42, 38, 55, 70],
    "Sub3": [81, 93, 27, 40, 56, 25, 90, 28, 73, 82],
    "Sub4": [40, 89, 35, 91, 38, 80, 60, 35, 45, 47],
    "Sub5": [50, 95, 40, 99, 32, 45, 30, 92, 60, 88]
}

# Step 2: Convert to DataFrame
df = pd.DataFrame(data)

# Step 3: Calculate total and percentage
df["Total"] = df[["Sub1", "Sub2", "Sub3", "Sub4", "Sub5"]].sum(axis=1)
df["Percentage"] = df["Total"] / 5   # 5 subjects

# Step 4: Sort by percentage (low to high)
df = df.sort_values(by="Percentage")

# Step 5: Print results
print(df[["Name", "Enrollment", "Percentage"]])

# Step 6: Plot chart
plt.bar(df["Name"], df["Percentage"], color="skyblue")
plt.title("Student Percentage (Low to High)")
plt.xlabel("Students")
plt.ylabel("Percentage")
plt.xticks(rotation=45)
plt.show()



