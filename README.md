# Naloga 5.2
import json
import random
import datetime

while True:
    with open("naloga_5.2.txt", "r") as score_file:
        score_list = json.loads(score_file.read())


    def game():

        secret = random.randint(1, 30)
        poiskus = 0
        ime = str(input("Vpiši svoje ime?:___"))
        while True:
            guess = int(input("Guess the secret number (between 1 and 30): "))
            poiskus = poiskus + 1

            if guess == secret:
                print("Čestitam. Številka je:  " + str(secret))
                score_list.append({"\n""attempts": poiskus, "ime": ime, "datum": str(datetime.datetime.now())})

                with open("naloga_5.2.txt", "w") as score_file:
                    score_file.write(json.dumps(score_list))

                break

            if guess > secret:
                print("Poskusi z manjšo številko!")

            elif guess < secret:
                print("Poiskusi z večjo številko!")


    selection = input("Would you like to:"
                      "A play a new game, "
                      "B see the best scores, or "
                      "C quit?")

    if selection.upper() == "A":
        game()
    elif selection.upper() == "B":
        with open("naloga_5.2.txt") as score_fail:
            score_fail.read

            for player in score_list:
                print(player)
            # sorted(score_list.items(), key=lambda players :attemtps[0]) /poskusla sem razvrstit po vrstnem redu, glede na poiskuse pa
            # mi ne rata?!!

    elif selection.upper() == "C":
        exit()

