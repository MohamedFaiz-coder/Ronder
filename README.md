# csv_analysis.py
import csv

file_name = input("أدخل اسم ملف CSV (مثال: data.csv): ")

try:
    with open(file_name, newline='', encoding='utf-8') as csvfile:
        reader = csv.DictReader(csvfile)
        data = list(reader)

        print("الأعمدة المتاحة:", reader.fieldnames)
        column = input("اختر العمود لحساب المتوسط: ")

        values = [float(row[column]) for row in data if row[column]]
        average = sum(values) / len(values)

        print(f"متوسط العمود {column} هو: {average:.2f}")

except FileNotFoundError:
    print("الملف غير موجود.")
except ValueError:
    print("تأكد أن العمود يحتوي على أرقام فقط.")
except KeyError:
    print("العمود غير موجود في الملف.")
