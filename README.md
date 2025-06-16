# mysql-classes-work
A collection of MySQL exercises, queries, and schema designs completed during classwork or coursework. This repository includes practice SQL scripts for creating databases, managing tables, writing queries (SELECT, JOIN, GROUP BY, etc.), and performing CRUD operations. Useful for students, educators, and anyone learning or reviewing My
![image](https://github.com/user-attachments/assets/49ef42ef-5d5c-4b02-a074-5e43f6da8d62)
import time
from datetime import datetime, timedelta

class ExpiringIntro:
    def __init__(self, name, role, skills, expires_in_seconds):
        self.name = name
        self.role = role
        self.skills = skills
        self.created_at = datetime.now()
        self.expires_at = self.created_at + timedelta(seconds=expires_in_seconds)

    def is_expired(self):
        return datetime.now() > self.expires_at

    def show_intro(self):
        if self.is_expired():
            return "This data analyst introduction has expired."
        else:
            intro = (
                f"👋 Hi, I'm {self.name}!\n"
                f"🔍 Role: {self.role}\n"
                f"📊 Key Skills: {', '.join(self.skills)}\n"
                f"⏳ Expires at: {self.expires_at.strftime('%Y-%m-%d %H:%M:%S')}"
            )
            return intro

# Example usage
intro = ExpiringIntro(
    name="Jordan Smith",
    role="Data Analyst",
    skills=["SQL", "Python", "Tableau", "Data Visualization"],
    expires_in_seconds=10  # 10 seconds until expiration
)

# Simulate checking the intro multiple times
for i in range(15):
    print(intro.show_intro())
    time.sleep(1)
