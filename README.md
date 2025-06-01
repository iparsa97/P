# task_planner_ai.py
import datetime
from sklearn.ensemble import RandomForestClassifier  # مدل پیشرفته‌تر

class PersianTaskPlanner:
    def __init__(self):
        self.tasks = []
        self.model = RandomForestClassifier()  # مدل برای پیش‌بینی اولویت‌ها
    
    def add_task(self, name, duration, priority="medium"):
        """افزودن کار با زمان و اولویت"""
        self.tasks.append({
            "name": name,
            "duration": duration,
            "priority": priority,
            "added_at": datetime.datetime.now()
        })
    
    def suggest_schedule(self):
        """پیشنهاد زمانبندی بهینه"""
        return sorted(self.tasks, key=lambda x: 0 if x["priority"] == "high" else 1)def learn_from_habits(self, historical_data):
    # تحلیل داده‌های تاریخی برای پیش‌بینی زمان‌های بهینه
    self.model.fit(historical_data["features"], historical_data["labels"])
    pip install streamlit
    # app.py
import streamlit as st
from task_planner_ai import PersianTaskPlanner

st.title("🗓 برنامه‌ریز هوشمند فارسی")
task_name = st.text_input("کار جدید:")
duration = st.slider("مدت زمان (دقیقه):", 1, 120)
if st.button("اضافه کن"):
    planner = PersianTaskPlanner()
    planner.add_task(task_name, duration)
    st.success(f"کار '{task_name}' اضافه شد!")
