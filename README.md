# buiquocvuongBIT253655-20-3
# ==============================
# PROG2005 - LUYỆN TẬP 10
# ==============================

import matplotlib.pyplot as plt
import numpy as np

# ==============================
# BÀI 1
# ==============================
def bai1():
    path = input("Nhập đường dẫn: ")
    filename = path.split("\\")[-1]
    name = filename.split(".")[0]

    print("Tên file:", filename)
    print("Tên bài hát:", name)


# ==============================
# BÀI 2
# ==============================
def bai2():
    s = input("Nhập chuỗi: ")
    char = input("Nhập ký tự: ")
    print(f"Ký tự '{char}' xuất hiện {s.count(char)} lần")


# ==============================
# BÀI 3
# ==============================
def factorial(n):
    if n <= 1:
        return 1
    return n * factorial(n - 1)

def bai3():
    n = int(input("Nhập số: "))
    if n < 0:
        print("Không hợp lệ")
    else:
        print("Giai thừa:", factorial(n))


# ==============================
# BÀI 4
# ==============================
def bai4():
    s = input("Nhập chuỗi: ")

    if s == "":
        print("Lỗi: Chuỗi rỗng!")
    else:
        print("Độ dài:", len(s))


# ==============================
# BÀI 5
# ==============================
def bai5():
    x = np.linspace(0, 10, 100)

    plt.figure(figsize=(10, 4))

    plt.subplot(1, 2, 1)
    plt.plot(x, x**2)
    plt.title("y = x^2")
    plt.xlabel("x")
    plt.ylabel("y")

    plt.subplot(1, 2, 2)
    plt.plot(x, np.sqrt(x))
    plt.title("y = sqrt(x)")
    plt.xlabel("x")
    plt.ylabel("y")

    plt.tight_layout()
    plt.show()


# ==============================
# BÀI 6
# ==============================
def bai6():
    s = input("Nhập chuỗi: ")
    result = ""

    for i in range(len(s)-1, -1, -1):
        result += s[i]

    print("Chuỗi đảo:", result)


# ==============================
# BÀI 7
# ==============================
def bai7():
    while True:
        password = input("Nhập mật khẩu: ")
        if password == "python123":
            print("Đúng mật khẩu!")
            break
        else:
            print("Sai, thử lại!")


# ==============================
# BÀI 8
# ==============================
def bai8():
    arr = []
    for i in range(5):
        arr.append(input(f"Chuỗi {i+1}: "))

    n = len(arr)

    for i in range(n):
        for j in range(0, n-i-1):
            if len(arr[j]) < len(arr[j+1]):
                arr[j], arr[j+1] = arr[j+1], arr[j]
                print("Bước:", arr)

    print("Kết quả:", arr)


# ==============================
# BÀI 9
# ==============================
class Person:
    def __init__(self, name, age):
        if age < 0:
            raise ValueError("Tuổi không hợp lệ")
        self._name = name
        self._age = age

    def get_name(self):
        return self._name

    def set_age(self, age):
        if age < 0:
            raise ValueError("Tuổi phải >= 0")
        self._age = age

    def __str__(self):
        return f"Name: {self._name}, Age: {self._age}"

    def greet(self):
        return f"Hello, I am {self._name}"

    @classmethod
    def species(cls):
        return "Human"

    @staticmethod
    def is_adult(age):
        return age >= 18

    def __eq__(self, other):
        return self._name == other._name and self._age == other._age


class Student(Person):
    def __init__(self, name, age, grade):
        super().__init__(name, age)
        if grade < 0 or grade > 10:
            raise ValueError("Điểm không hợp lệ")
        self._grade = grade

    def __str__(self):
        return super().__str__() + f", Grade: {self._grade}"

    def study(self):
        return "Studying..."


def bai9():
    p = Person("An", 20)
    s = Student("Binh", 18, 8)

    print(p)
    print(p.greet())
    print(Person.species())
    print(Person.is_adult(20))

    print(s)
    print(s.study())

    print("So sánh:", p == Person("An", 20))


# ==============================
# BÀI 10
# ==============================
def bai10():
    arr = []

    for i in range(5):
        s = input(f"Nhập chuỗi thứ {i+1}: ")
        arr.append(s)

    print("\nDanh sách ban đầu:", arr)

    n = len(arr)

    for i in range(n):
        print(f"\n--- Lượt {i+1} ---")
        for j in range(0, n - i - 1):
            if len(arr[j]) < len(arr[j + 1]):
                arr[j], arr[j + 1] = arr[j + 1], arr[j]
                print("Hoán đổi:", arr)
            else:
                print("Giữ nguyên:", arr)

    print("\nKết quả cuối cùng:", arr)


# ==============================
# BÀI 11 - MENU
# ==============================
def main():
    while True:
        print("\n===== MENU =====")
        print("1. Bài 1")
        print("2. Bài 2")
        print("3. Bài 3")
        print("4. Bài 4")
        print("5. Bài 5")
        print("6. Bài 6")
        print("7. Bài 7")
        print("8. Bài 8")
        print("9. Bài 9")
        print("10. Bài 10")
        print("0. Thoát")

        choice = input("Chọn bài: ")

        if choice == "1":
            bai1()
        elif choice == "2":
            bai2()
        elif choice == "3":
            bai3()
        elif choice == "4":
            bai4()
        elif choice == "5":
            bai5()
        elif choice == "6":
            bai6()
        elif choice == "7":
            bai7()
        elif choice == "8":
            bai8()
        elif choice == "9":
            bai9()
        elif choice == "10":
            bai10()
        elif choice == "0":
            print("Thoát chương trình!")
            break
        else:
            print("Lựa chọn không hợp lệ!")


# Chạy chương trình
main()
