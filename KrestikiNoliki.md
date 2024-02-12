def board(field):
    print("_____")
    for i in field:
        print(*field[0:3], sep="|")
        print("_____")
        print(*field[3:6], sep="|")
        print("_____")
        print(*field[6:9], sep="|")
        print("_____")
        field = list(range(0, 10))
        break
def put_mark():
    while True:
        a = int(input("Куда поставим отметку?"))
        if a <= 0 or a >= 10:
            print("Введите число в диапазоне от 1 до 9:")
        else:
            break
    return a

def check_win(field):
    win_notes=((0, 1, 2), (3, 4, 5), (6, 7, 8),
        (0, 3, 6), (1, 4, 7), (2, 5, 8),
        (0, 4, 8), (2, 4, 6))
    for i in win_notes:
        if field[i[0]] == field[i[1]] == field[i[2]]:
            return field[i[0]]
def main_board():
    counter = 0
    field = list(range(0, 10))
    while True:
        board(field)
        if counter % 2 == 1:
            mark = 'X'
        else:
            mark = '0'
        turn = put_mark()
        if isinstance(field[turn], int):
            field[turn] = mark
        counter += 1
        if check_win(field):
            print("победа")
            break
        if counter == 9:
            print("Ничья!")
            break
    board(field)

main_board()
print("Конец игры")
