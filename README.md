import random

num_players = int(input("Enter number of players: "))

players = {}
called_numbers = []
4

for i in range(1, num_players + 1):
    ticket = random.sample(range(1, 91), 15)  
    players[f"Player {i}"] = ticket

for player, ticket in players.items():
    print(player, "Ticket:", ticket)

available_numbers = list(range(1, 91))
random.shuffle(available_numbers)

for number in available_numbers:
    print("\nNumber Called:", number)

    for player, ticket in players.items():
        if number in ticket:
            index = ticket.index(number)
            ticket[index] = "X"
            print(player, "matched!")

        print(player, "Ticket:", ticket)

        if all(num == "X" for num in ticket):
            print("\n", player, "wins Tambola!")
            exit()

    input("Press Enter for next number...")

print("All numbers called. No winner!")
