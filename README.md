def print_board(b):
    for row in b:
       print(" | ".join(row))
       print("-" * 5)

def check_win(b, m):
	    return any(all(s == m for s in r) for r in b) or \
	           any(all(b[i][j] == m for i in range(3)) for j in range(3)) or \
           all(b[i][i] == m for i in range(3)) or \
	           all(b[i][2 - i] == m for i in range(3))
	
	def get_move(b):
	    while True:
	        try:
	            p = int(input("Enter position (1-9): ")) - 1
	            if 0 <= p < 9 and b[p // 3][p % 3] == " ":
	                return divmod(p, 3)
	            print("Invalid move.")
	        except ValueError:
	            print("Please enter a number.")
	
	def tic_tac_toe():
	    b, p = [[" "]*3 for _ in range(3)], "X"
	    for _ in range(9):
	        print_board(b)
	        r, c = get_move(b)
	        b[r][c], p = p, "O" if p == "X" else "X"
	        if check_win(b, "X") or check_win(b, "O"):
	            print_board(b)
	            print(f"{p} wins!")
	            return
	    print("It's a tie!")
	
	tic_tac_toe()
