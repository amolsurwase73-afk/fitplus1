import json
import os
from datetime import datetime, timedelta

# File to store user data
DATA_FILE = "fitpulse_data.json"

# Load existing data
if os.path.exists(DATA_FILE):
    with open(DATA_FILE, "r") as f:
        data = json.load(f)
else:
    data = {}

# Function to save data
def save_data():
    with open(DATA_FILE, "w") as f:
        json.dump(data, f, indent=4)

# Function to get today's entry
def get_today():
    today = datetime.now().strftime("%Y-%m-%d")
    if today not in data:
        data[today] = {"steps":0, "water":0, "mood":0, "workouts":[]}
    return today, data[today]

# Log steps
def log_steps():
    today, entry = get_today()
    steps = input("Enter number of steps: ")
    if steps.isdigit() and int(steps) >= 0:
        entry["steps"] = int(steps)
        print(f"Steps logged: {entry['steps']}")
    else:
        print("Invalid entry! Please enter a positive number.")
    save_data()

# Log water intake
def log_water():
    today, entry = get_today()
    water = input("Enter water intake in ml: ")
    if water.isdigit() and int(water) >= 0:
        entry["water"] = int(water)
        print(f"Water intake logged: {entry['water']} ml")
    else:
        print("Invalid entry! Please enter a positive number.")
    save_data()

# Log mood
def log_mood():
    today, entry = get_today()
    mood = input("Rate your mood 1-5: ")
    if mood.isdigit() and 1 <= int(mood) <= 5:
        entry["mood"] = int(mood)
        print(f"Mood logged: {entry['mood']}")
    else:
        print("Invalid mood rating! Enter 1-5.")
    save_data()

# Simulated AI workout suggestion
def ai_workout():
    today, entry = get_today()
    print("\nAI Suggestion: Quick 10-minute workout")
    print("- 2 min warm-up jogging in place")
    print("- 3 min bodyweight squats")
    print("- 2 min push-ups (knees optional)")
    print("- 2 min planks / core exercise")
    print("- 1 min cooldown stretch\n")
    entry["workouts"].append("10-min AI workout")
    save_data()

# Display weekly summary
def weekly_summary():
    print("\nWeekly Summary:")
    today_date = datetime.now()
    for i in range(6,-1,-1):
        day = (today_date - timedelta(days=i)).strftime("%Y-%m-%d")
        entry = data.get(day, {"steps":0,"water":0,"mood":0,"workouts":[]})
        print(f"{day}: Steps={entry['steps']}, Water={entry['water']}ml, Mood={entry['mood']}, Workouts={len(entry['workouts'])}")

# Main menu
def main_menu():
    while True:
        print("\n--- FitPulse Smart Fitness Assistant ---")
        print("1. Log Steps")
        print("2. Log Water Intake")
        print("3. Log Mood")
        print("4. AI Workout Suggestion")
        print("5. Weekly Summary")
        print("6. Exit")

        choice = input("Choose an option: ")
        if choice == "1":
            log_steps()
        elif choice == "2":
            log_water()
        elif choice == "3":
            log_mood()
        elif choice == "4":
            ai_workout()
        elif choice == "5":
            weekly_summary()
        elif choice == "6":
            print("Exiting FitPulse. Keep up the healthy habits!")
            break
        else:
            print("Invalid option. Try again.")

if __name__ == "__main__":
    main_menu()


  
