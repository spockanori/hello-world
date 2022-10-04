import time, random, sys

#Program 0 -- Main Menu
def mainMenu():
    time.sleep(1)
    
    print("""
    --------------------------------
    Here are the programs available. Indicate the program you'd you like to run using the listed number.
    Admins may request notes.
    -------------------------------- """,
    end="")
    
    time.sleep(1)
    
    print("""   
    1 - helloWorld()
    2 - firstPassword()
    3 - yourNamePlease()
    4 - rangeLooper()
    5 - rockPaperScissors()
    6 - magic8Ball()
    -------------------------------- """)

    while True:
        userPath = input()
        if userPath.lower() == "notes":
            noteKeeper()
            break
        elif userPath.lower() == "1":
            helloWorld()
            break
        elif userPath.lower() =="2":
            firstPassword()
            break
        elif userPath.lower() =="3":
            yourNamePlease()
            break
        elif userPath.lower() =="4":
            rangeLooper()
            break
        elif userPath.lower() == "5":
            rockPaperScissors()
            break
        elif userPath.lower() == "6":
            magic8Ball()
            break
        else:
            print("Just the number, please!")


#Program 6 magic8Ball()
def getAnswer(answerNumber):
    if answerNumber == 1:
        return 'It is certain'
    elif answerNumber == 2:
        return 'It is decidedly so'
    elif answerNumber == 3:
        return 'Yes'
    elif answerNumber == 4:
        return 'Reply hazy try again'
    elif answerNumber == 5:
        return 'Ask again later'
    elif answerNumber == 6:
        return 'Concentrate and ask again'
    elif answerNumber == 7:
        return 'My reply is no'
    elif answerNumber == 8:
        return 'Outlook not so good'
    elif answerNumber == 9:
        return 'Very doubtful'
    else:
        return 'You broke the 8-ball'

def magic8Ball():
    
    print("Welcome to Magic 8 Ball. You have come here seeking answers. When you are ready...")
    time.sleep(.5)
    print(".")
    time.sleep(.5)
    print(".")
    time.sleep(.5)
    print(".")
    time.sleep(1)
    userQuestion = input("Ask your question.\n")
    r = random.randint(1,9)
    print("The answer to your question: '" + userQuestion + "' is simple: ") 
    time.sleep(1)
    fortune = getAnswer(r)
    print(fortune)
    

#Program notes, noteKeeper
def noteKeeper():
    print("""
    Here are the notes from your file:
    Pick up with the user defined functions in Chapter 3
    It would be cool to implement an admin log in and pw that can access notes
    """)
    time.sleep(5)


#Program 5, rockPaperScissors

def rockPaperScissors():
    print('Rock.')
    time.sleep(.5)
    print('Paper.')
    time.sleep(.5)
    print('Scissors.')
    time.sleep(1)

    playerWins = 0
    computerWins = 0
    ties = 0

    while True:
        totalGames = playerWins + computerWins + ties
        userPath = ''
        if totalGames > 0:
            print("")
            print("~ ~ ~ ~ ~ ~ ~ ~ ~ ~ ~ ~ ~ ~ ~ ~ ~ ~ ~ ~ ~ ~ ~")
            print("You've achieved: " + str(playerWins) + " victories.")
            print("You've suffered: " + str(computerWins) + " defeats.")
            print("~ ~ ~ ~ ~ ~ ~ ~ ~ ~ ~ ~ ~ ~ ~ ~ ~ ~ ~ ~ ~ ~ ~")
            print("")
            print("Do you wish to continue? Y/N")
        elif totalGames == 0:
            print("Welcome to the arena. Are you ready to begin? Y/N")

        userPath = input()
        if userPath.lower() == "n":
            break
        elif userPath.lower() == "y":

            #Player Inputs
            while True:
                print("Enter your move: (R)ock, (P)aper, (S)cissors -- or (Q)uit")
                playerMove = input().lower()
                if playerMove == 'r' or playerMove =='p' or playerMove == 's' or playerMove == 'q':
                    break
                print("Make a move. r, p, s... q to quit")

            if playerMove == 'r':
                print("It's ROCK versus...")
            elif playerMove == 'p':
                print("It's PAPER versus...")
            elif playerMove == 's':
                print("It's SCISSORS versus...")
            elif playerMove == 'q':
                break

            time.sleep(1.5)
            #Computer Inputs
            randomNumber = random.randint(1,3)
            if randomNumber == 1:
                computerMove ='r'
                print("ROCK!")
            elif randomNumber == 2:
                computerMove ='p'
                print("PAPER!")
            elif randomNumber == 3:
                computerMove ='s'
                print("SCISSORS!")

            time.sleep(1)
            print("")
            if playerMove == computerMove:
                print ("Stalemate!")
                ties = ties + 1
            elif (playerMove =='r' and computerMove =='s') or (playerMove =='p' and computerMove =='r') or (playerMove =='s' and computerMove =='p'):
                print("You've achieved victory!")
                playerWins = playerWins + 1
            else:
                print("You've suffered defeat.")
                computerWins = computerWins + 1


#Program 4, rangeLooper
def rangeLooper():
    print("What number shall we start with?")
    start = int(input())
    print("What number shall we end with?")
    end = int(input())
    print("What interval shall we use?")
    interval = int(input())
    print("Shall we begin?")
    print("Y/N")
    beginCommand = input()
    if beginCommand.lower() == "y":
        for i in range (start,end,interval):
            print(str(i)+ " ",end='')
            time.sleep(.5)
        if (end - (i + interval)) == 0:
            print(str(end))
            print("")
            time.sleep(1)
            print("Starting with " + str(start) + " we iterated by " + str(interval) + " until we reached " + str(end) + ".")
        else:
            print("")
            time.sleep(1)
            print("Starting with " + str(start) + " we iterated by " + str(interval) + " until we got as close to " + str(end) + " as possible.")




#Program 3, yourNamePlease
def yourNamePlease():
    name = ''

    print("Run the break version, or the no-break version?")
    print("1 - No break")
    print("2 - Break")
    choice = input()

    if choice == "1":
        while name != 'your name':
            print('Please type your name.')
            name = input()
        print('Thank you!')

    elif choice == "2":
        while True:
            print('Speak, friend, and enter.')
            name = input()
            if name == 'friend':
                break
        print('Thank you!')


#Program 2, firstPassword
def firstPassword():
    while True:
        myName = askName()
        if myName != 'Takanori':
            continue

        print('Hello, ' + myName + ". What is the password?")
        password = input()

        if password == 'swordfish':
           break
        else:
            print('Wrong password. You must not *really* be ' + myName )

    print ('Access granted.')

def askName():
    print('What is your name?')
    myName = input()
    return myName


#Program 1, Hello World
def helloWorld():
    print('Hello, world!')
    time.sleep(.5)
    myName = askName()
    time.sleep(1)
    print('It is good to meet you, ' + myName + '.')
    time.sleep(.5)
    print('The length of your name is: ' + str(len(myName)))
    time.sleep(.5)
    print('What is your age?')
    myAge = input()
    time.sleep(1)
    print(myName + ', you will be ' + str(int(myAge) + 1) + ' in one year!')


programRunning = "y"

while programRunning.lower() == "y":
    mainMenu()
    time.sleep(6)
    programRunning = input("""
    --------------------------------
    Your program has ended. 
    Would you like to see the menu again?""")
    
else:
    print("""
    ヾ(*ﾟ∇ﾟ*)ﾉ Bye Bye!""")

