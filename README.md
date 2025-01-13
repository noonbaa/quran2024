import json
import os
import re
pip install texttable
import  texttable
from texttable import Texttable
surahs = {}
import os
folder_name = 'C:\\Users\\basne\\Desktop\\quranjson-master\\source\\surah'
file_names = os.listdir(folder_name)
for file_name in file_names:
    if file_name.endswith('.json'):
        with open(os.path.join(folder_name, file_name), encoding='utf-8') as f:
         data = json.load(f)
         with open('C:/Users/basne/Desktop/quranjson-master/source\surah.json', 'r', encoding='utf-8' ) as f:
   data = json.load(f)
table = Texttable()
table.set_cols_align(["l","c","r"])
table.set_cols_valign(["t","m","b"])
for surah in data:
    name_surah = surah['titleAr']
    juz = surah['index']
    ayeh = surah['count']
    table.header(["سوره","جزء","آیه"])

    table = texttable.Texttable()
    table.add_row([name_surah, juz,ayeh])
   
    print(table.draw())
    word_count = {
    'ايهاالذين امنوا': 0,
    'قل': 0,
    'نجم': 0,
    'صيام': 0
}
import os
import json
from texttable import Texttable

# مسیر فولدر حاوی فایل‌های JSON
folder_name = 'C:\\Users\\basne\\Desktop\\quranjson-master\\source\\surah'
file_names = os.listdir(folder_name)

# ایجاد جدول برای نمایش داده‌ها
table = Texttable()
table.set_cols_align(["l", "c", "r"])
table.set_cols_valign(["t", "m", "b"])
table.header(["سوره", "جزء", "آیه"])

# تعریف دیکشنری برای شمارش کلمات
word_count = {
    'ايهاالذين امنوا': 0,
    'قل': 0,
    'نجم': 0,
    'صيام': 0
}

# حلقه برای پردازش هر فایل JSON در فولدر
for file_name in file_names:
    if file_name.endswith('.json'):
        file_path = os.path.join(folder_name, file_name)
        
        # بارگذاری داده‌های JSON از هر فایل
        with open(file_path, encoding='utf-8') as f:
            data = json.load(f)
        
        # بررسی نوع داده‌ها در هر سوره
        if isinstance(data, dict):  # بررسی اینکه داده‌ها دیکشنری هستند
            name_surah = data.get('titleAr', 'نام سوره موجود نیست')  # نام سوره
            juz = data.get('index', 'جزء موجود نیست')  # جزء
            ayeh = data.get('count', 'آیه موجود نیست')  # تعداد آیه‌ها
            
            # افزودن داده‌ها به جدول
            table.add_row([name_surah, juz, ayeh])
            
            # شمارش کلمات در آیات
            verses = data.get('verses', [])  # فرض بر این است که آیات در کلید 'verses' قرار دارند
            for verse in verses:
                text = verse  # آیه به صورت رشته است
                for word in word_count.keys():
                    word_count[word] += text.count(word)
        else:
            print(f"داده اشتباه است: {data}")

# چاپ جدول نهایی
print(table.draw())

# چاپ آمار کلمات
for word, count in word_count.items():
    print(f"تعداد کلمه '{word}': {count}")
    print(type(word_count))
    for i in range(1, 115):
      with open(os.path.join(folder_name, file_name), encoding='utf-8') as f:
         data = json.load(f)
         print(type(data))
         print(data)
         print(type(ayah))
         print(ayah)
         # فرض بر این است که 'data' یک دیکشنری است که در آن هر کلید یک آیه است
# word_count یک دیکشنری است که کلمات مورد نظر را به عنوان کلید و مقدار اولیه صفر دارد
word_count = {
    'ايهاالذين امنوا': 0,
    'قل': 0,
    'نجم': 0,
    'صيام': 0
}

# شمارش کلمات در آیه‌ها
for key, ayah in data.items():
    if isinstance(ayah, str):  # اگر ayah یک رشته است
        text = ayah.strip()  # حذف فاصله‌های اضافی در ابتدا و انتهای متن
        # شمارش کلمات
        for word in word_count.keys():
            word_count[word] += text.count(word)
    else:
        print(f"آیه '{key}' به‌طور صحیح به‌عنوان رشته شناسایی نشد. نوع داده: {type(ayah)}")

# چاپ آمار کلمات مورد نظر
print(f"تعداد کلمه 'ايهاالذين امنوا': {word_count['ايهاالذين امنوا']}")
print(f"تعداد کلمه 'قل': {word_count['قل']}")
print(f"تعداد کلمه 'نجم': {word_count['نجم']}")
print(f"تعداد کلمه 'صيام': {word_count['صيام']}")
    'ايهاالذين امنوا': 0,
    'قل'







