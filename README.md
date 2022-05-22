# python
DZ BozhkoElena
Задание 1

def input_num(my_string):
    try:
        num = int(input(my_string))
    except ValueError:
        print('Вы ввели не натуральное число')
        num = input_num(my_string)
    return num


def calculate():
    """Вводим знак операции над числами"""
    try:
        sign = input('Введите знак операции: ')
        sign = sign.replace(' ', '')
        if sign == '0':
            print('Работа завершена')
            raise ValueError()
        elif sign not in '+-*/':
            print('Такой операции не существует, или вы указали не знак операции')
            calculate()
    except ValueError:
        pass
    else:

        a = input_num('Введите первое число: ')
        b = input_num('Введите второе число: ')

        if sign == '+':
            print(f'{a}+{b}={a + b}')
            calculate()
        elif sign == '-':
            print(f'{a}-{b}={a - b}')
            calculate()
        elif sign == '*':
            print(f'{a}*{b}={a * b}')
            calculate()
        else:
            try:
                print(f'{a}/{b}={a / b}')
                calculate()
            except ZeroDivisionError:
                print('На ноль делить нельзя')
                calculate()


if __name__ == "__main__":
    calculate()
    
    
    Задание 2
    
    def recur_method(num, even=0, odd=0):

    if num == 0:
        return even, odd
    else:
        cur_n = num % 10
        num = num // 10
        if cur_n % 2 == 0:
            even += 1
        else:
            odd += 1
        return recur_method(num, even, odd)


if __name__ == "__main__":
    try:
        NUM = int(input("Введите натуральное число: "))
        print(f"Количество четных и нечетных цифр в числе: {recur_method(NUM)}")
    except ValueError:
        print("Вы вместо числа ввели строку. Исправьтесь")
        
        
        Задание 3
        def reversed_number(user_number, reverse_num=''):
    if user_number == 0:
        return reverse_num
    else:
        reverse_num += str(user_number % 10)
        user_number = user_number // 10
        return reversed_number(user_number, reverse_num)


if __name__ == "__main__":
    try:
        user_num = int(input("Введите натуральное число: "))
        print(f"Обратное по порядку: {reversed_number(user_num)}")
    except ValueError:
        print("Вы вместо числа ввели строку. Исправьтесь")
        
        
        
        Задание 4
        
        def my_function(user_number, num=1, result_sum=0):
    if user_number == 0:
        return result_sum
    else:
        user_number -= 1
        result_sum += num
        num /= -2
        return my_function(user_number, num, result_sum)


if __name__ == "__main__":
    try:
        user_num = int(input("Введите натуральное число: "))
        print(f"Сумма n элементов следующего ряда чисел:\n1-0.5 0.25 -0.125 ... n равна:"
              f" {my_function(user_num)}")
    except ValueError:
        print("Вы вместо числа ввели строку. Исправьтесь")
        
        
        Задание 5
        
def ascii_simbols(num=32, counter=0, rezult=''):
    if num == 128:
        return rezult
    else:
        rezult += f'{num} - {chr(num)} '
        num += 1
        counter += 1
        if counter == 10:
            rezult += '\n'
            counter = 0
        return ascii_simbols(num, counter, rezult)


if __name__ == "__main__":
    print(ascii_simbols())
    
    
    
  Задание 6
  
 from random import randint


def game(num_x, attempts=10):
    if attempts == 0:
        return print(f'Попытки закончились, загаданное число: {num_x}')
    else:
        try:
            num_user = int(input('Введите натуральное число: '))
        except ValueError:
            return print('Было введено неправильное число, игра окончена!')
        attempts -= 1
        if num_user == num_x:
            return print(f'Действительно, загаданное число: {num_x}')
        elif num_x > num_user:
            return print('Загаданное число больше!'), game(num_x, attempts)
        else:
            return print('Загаданное число меньше!'), game(num_x, attempts)


if __name__ == "__main__":
    game(randint(1, 100))
