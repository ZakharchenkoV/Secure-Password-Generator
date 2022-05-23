import random

DIGITS = '0123456789'
LOWERCASE_LETTERS = 'abcdefghijklmnopqrstuvwxyz'
UPPERCASE_LETTERS = 'ABCDEFGHIJKLMNOPQRSTUVWXYZ'
PUNCTUATION = '!#$%&*+-=?@^_'
AMBIGUOUS = 'il1Lo0O'
chars = ''
numb = 0
lenght = 0


def is_valid(a):  # Проверка: пользователь ввел числовое значение?
    if a.isdigit():
        return True


def letter_answer(b):  # Проверка словарного ответа (да/нет)
    if b.isalpha() and "да" in b.lower() or "нет" in b.lower():
        return True


def numb_psswrd():  # Количество паролей
    global numb
    while True:
        print('Сколько случайных паролей вы хотите сгенерировать?')
        numb_of_psswrds = input()
        if is_valid(numb_of_psswrds):
            numb = numb_of_psswrds
            break
        else:
            print("Введите число или цифру.")
        continue


def lenght_psswrd():  # Длина паролей
    global lenght
    while True:
        print('Введите необходимую длину пароля.')
        lenght_of_psswrd = input()
        if is_valid(lenght_of_psswrd):
            lenght = lenght_of_psswrd
            break
        else:
            print("Для указания длины паролей необходимо ввести число или цифру.")
            continue


def digits_in_psswrd():  # Включаем цифры?
    global chars
    while True:
        print('Включать ли цифры ', DIGITS, '?', sep='')
        answer = input()
        if letter_answer(answer):
            if answer.lower() == 'да':
                chars += DIGITS
                break
            elif answer.lower() == 'нет':
                break
        else:
            print("Принимаются только ответы да/нет")
            continue


def upp_let():  # Включаем заглавные буквы?
    global chars
    while True:
        print('Включать ли прописные буквы ', UPPERCASE_LETTERS, '?', sep='')
        answer2 = input()
        if letter_answer(answer2):
            if answer2.lower() == 'да':
                chars += UPPERCASE_LETTERS
                break
            elif answer2.lower() == 'нет':
                break
        else:
            print("Принимаются только ответы да/нет")
            continue


def low_let():  # Включаем строчные буквы?
    global chars
    while True:
        print('Включать ли строчные буквы ', LOWERCASE_LETTERS, '?', sep='')
        answer3 = input()
        if letter_answer(answer3):
            if answer3.lower() == 'да':
                chars += LOWERCASE_LETTERS
                break
            elif answer3.lower() == 'нет':
                break
        else:
            print("Принимаются только ответы да/нет")
            continue


def punctuation():  # Включаем знаки препинания?
    global chars
    while True:
        print('Включать ли символы ', PUNCTUATION, '?', sep='')
        answer4 = input()
        if letter_answer(answer4):
            if answer4.lower() == 'да':
                chars += PUNCTUATION
                break
            elif answer4.lower() == 'нет':
                break
        else:
            print("Принимаются только ответы да/нет")
            continue


def ambiguous():  # Исключаем неоднозначные символы?
    global chars
    while True:
        print('Исключать ли неоднозначные символы ', AMBIGUOUS, '?', sep='')
        answer5 = input()
        if letter_answer(answer5):
            if answer5.lower() == "да":
                for i in AMBIGUOUS:
                    chars = chars.replace(i, '')
                break
            elif answer5.lower() == "нет":
                break
        else:
            print("Принимаются только ответы да/нет")
            continue


def generate_password():
    global numb
    global lenght
    for j in range(int(numb)):
        for y in range(int(lenght)):
            print(random.choice(chars), end='')
        print()


def poll():
    numb_psswrd()
    lenght_psswrd()
    digits_in_psswrd()
    upp_let()
    low_let()
    punctuation()
    ambiguous()
    generate_password()


poll()
input()