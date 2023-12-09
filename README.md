# XO
matrix =[[' ', '0', '1', '2'],
         ['0', '-', '-', '-'],
         ['1', '-', '-', '-'],
         ['2', '-', '-', '-']]
def draw():
    for i in matrix:
        print(*i)



def check_condition_win():
    if matrix[1][1] == matrix[1][2] == matrix[1][3] == 'x' or matrix[1][1] == matrix[1][2] == matrix[1][3] == 'o':
        return matrix[1][1]
    elif matrix[2][1] == matrix[2][2] == matrix[2][3] == 'x' or matrix[2][1] == matrix[2][2] == matrix[2][3] == 'o':
        return matrix[2][1]
    elif matrix[3][1] == matrix[3][2] == matrix[3][3] == 'x' or matrix[3][1] == matrix[3][2] == matrix[3][3] == 'o':
        return matrix[3][1]
    elif matrix[1][1] == matrix[2][1] == matrix[3][1] == 'x' or matrix[1][1] == matrix[2][1] == matrix[3][1] == 'o':
        return matrix[1][1]
    elif matrix[1][2] == matrix[2][2] == matrix[3][2] == 'x' or matrix[1][2] == matrix[2][2] == matrix[3][2] == 'o':
        return matrix[1][2]
    elif matrix[1][3] == matrix[2][3] == matrix[3][3] == 'x' or matrix[1][3] == matrix[2][3] == matrix[3][3] == 'o':
        return matrix[1][3]
    elif matrix[1][1] == matrix[2][2] == matrix[3][3] == 'x' or matrix[1][1] == matrix[2][2] == matrix[3][3] == 'o':
        return matrix[1][1]
    elif matrix[1][3] == matrix[2][2] == matrix[3][1] == 'x' or matrix[1][3] == matrix[2][2] == matrix[3][1] == 'o':
        return matrix[1][3]
    else:
        return False

def do_step(player_token):
    valid = False
    while not valid:
        player_answer = input("Куда поставим " + player_token + "? ")

        if player_answer in ('00', '01', '10', '11', '02', '20', '22', '12', '21'):
            if matrix[int(player_answer[0])+1][int(player_answer[1])+1] not in 'xo00':
                matrix[int(player_answer[0])+1][int(player_answer[1])+1] = player_token
                valid = True
            else:
                print ("Эта место занято")
        else:
            print ("Некорректный ввод. Введите координаты заново.")



def start():
    counter = 0
    win = False
    while not win:
        draw()
        if counter % 2 == 0:
            do_step("x")
        else:
            do_step("o")
        counter += 1

        cond = check_condition_win()
        if cond:
            print(cond, "выиграл!")
            win = True
            break
        if counter == 9:
            print("Ничья!")
            break
    draw()

start()
