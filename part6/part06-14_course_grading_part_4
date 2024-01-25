# tee ratkaisu tänne
if True:
    student_file = input('Student information: ')
    exercises_file = input('Exercises completed: ')
    exams_file = input("Exam points:")
    courses_file = input("Course information:")
else:
    student_file = 'students2.csv'
    exercises_file = 'exercises2.csv'
    exams_file = 'exam_points2.csv'
    courses_file = 'course2.txt'
# student_file = 'students2.csv'
# exercises_file = 'exercises2.csv'
# exams_file = 'exam_points2.csv'
# courses_file = 'course2.txt'
print("Results written to files results.txt and results.csv")


def to_points(number):
    return number // 4


def to_grade(points):
    if 0 <= total_points <= 14:
        grade = 0
    elif 15 <= total_points <= 17:
        grade = 1
    elif 18 <= total_points <= 20:
        grade = 2
    elif 21 <= total_points <= 23:
        grade = 3
    elif 24 <= total_points <= 27:
        grade = 4
    elif total_points >= 28:
        grade = 5
    return grade


students = {}
with open(f"src/{student_file}") as file:
    for line in file:
        line = line.strip()
        parts = line.split(";")
        if parts[0] == "id":
            continue
        students[parts[0]] = f"{parts[1]} {parts[2]}"
    # print(students)

exercises = {}
with open(f"src/{exercises_file}") as file:
    for line in file:
        line = line.strip()
        parts = line.split(";")
        if parts[0] == "id":
            continue
        total = 0
        for i in range(1, 8):
            total += int(parts[i])
            # exec_pts = int(((total/40)*100)//10)

        exercises[parts[0]] = total
    # print(exercises)


exams = {}
with open(f"src/{exams_file}") as file:
    for line in file:
        line = line.strip()
        parts = line.split(";")
        if parts[0] == "id":
            continue
        total = 0
        for i in range(1, 4):
            total += int(parts[i])
        exams[parts[0]] = total
    # print(exams)


courses = []
with open(f"src/{courses_file}") as file:
    for line in file:
        line = line.strip()
        parts = line.split(":")
        courses.append(parts[1].strip())

    # print(courses)

results = ""
total_points = 0
grade = 0

w1 = "name"
r1 = "exec_nbr"
r2 = "exec_pts."
r3 = "exm_pts."
r4 = "tot_pts."
r5 = "grade"
results += (f"{courses[0]}, {courses[1]} credits\n")
results += ("======================================\n")
results += (f"{w1:30}{r1:10}{r2:10}{r3:10}{r4:10}{r5}\n")

for sid, name in students.items():
    exec_nbr = exercises[sid]
    exec_score = to_points(exec_nbr)
    exams_points = exams[sid]
    total_points = exec_score + exams_points
    grades = to_grade(total_points)
    results += (f"{name:30}{exec_nbr:<10}{exec_score:<10}{exams_points:<10}{total_points:<10}{grades:<10}\n")


with open("results.txt", "w") as file:
    file.write(results)

with open("results.csv", "w") as file:
    for sid, name in students.items():
        exec_nbr = exercises[sid]
        exec_score = to_points(exec_nbr)
        exams_points = exams[sid]
        total_points = exec_score + exams_points
        grades = to_grade(total_points)
        row = ";".join([sid, name, str(grades)])
        file.write(f"{row}\n")
