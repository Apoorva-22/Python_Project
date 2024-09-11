import time
import pickle
import webbrowser

def read():
    p={}
    fin = open('movies.dat', 'rb')
    try:
        print("loading....")
        time.sleep(3)
        while True:
            p = pickle.load(fin)
            print(p)
    except EOFError:
        fin.close()

def write():
    n = {}
    nfile = open('movies.dat', 'wb')
    ans = 'y'
    while ans == 'y':
        name = input('Enter the name of the movie : ')
        cast = input('Enter the cast of the movie : ')
        rating1 = input('Rotten Tomatoes percentage : ')
        rating2 = input('IMDB rating : ')
        n['Movie'] = name
        n['Cast'] = cast
        n['Rotten Tomatoes'] = rating1
        n['IMDB'] = rating2
        pickle.dump(n, nfile)
        ans = input('Do you wanna enter more?(y/n): ')
    nfile.close()

def append():
    o = {}
    ofile = open('movies.dat', 'ab')
    ans = 'y'
    while ans == 'y':
        name = input('Enter the name of the movie : ')
        cast = input('Enter the cast of the movie : ')
        rating1 = input('Rotten Tomatoes percentage : ')
        rating2 = input('IMDB rating : ')
        o['Movie'] = name
        o['Cast'] = cast
        o['Rotten Tomatoes'] = rating1
        o['IMDB'] = rating2
        pickle.dump(o, ofile)
        ans = input('Do you wanna enter more?(y/n): ')
    ofile.close()

def search():
    found = False
    f1 = open('movies.dat', 'rb')
    B = input('Enter the movie you want ratings about : ')
    while True:
        try:
            d = pickle.load(f1)
            if B == d["Movie"]:
                print("HERE YOU GO....")
                print("Movie:", d['Movie'], end='\n')
                print("Cast:", d["Cast"], end='\n') 
                print("Rotten Tomatoes:", d["Rotten Tomatoes"], end='\n')
                print("IMDB:", d["IMDB"])
                found = True
        except EOFError:
            break
    if not found:
        print("RATINGS NOT AVAILABLE....")
    f1.close()    

def delete():
    found = False
    f1 = open("movies.dat", "rb")
    f2 = open("temp.dat", "wb")
    sroll = input("Enter movie name : ")
    while True:
        try:
            d = pickle.load(f1)
            if sroll == d['Movie']:
                found = True
            else:
                pickle.dump(d, f2)
        except EOFError:
            break
    if not found:
        print("NO SUCH MOVIE FOUND....")
    else:
        print("MOVIE FOUND AND DELETED....")
    f1.close()
    f2.close()
    os.remove("movies.dat")
    os.rename("temp.dat", "movies.dat")
    f1 = open("movies.dat", "rb")
    while True:
        try:
            d = pickle.load(f1)
            print(d)
        except EOFError:
            break
    f1.close()

def update():
    ans = 'y'
    found = False
    while ans == 'y':
        change1 = input("Enter the movie you wanna update ratings of : ")
        change2 = input("Enter the new Rotten Tomatoes percentage : ")
        change3 = input("Enter the new IMDB rating : ")
        f = open('movies.dat', 'rb+')
        try:
            while True:
                pos = f.tell()
                x = pickle.load(f)
                if x['Movie'] == change1:
                    x['Rotten Tomatoes'] = change2
                    x['IMDB'] = change3
                    f.seek(pos)
                    pickle.dump(x, f)
                    found = True
        except EOFError:
            if not found:
                print("NO SUCH MOVIE FOUND....")
            else:
                print("MOVIE RECORD UPDATED....")
            f.close()
        ans = input('Do you wanna enter more?(y/n): ')

def redirect_to_bookmyshow():
    movie_name = input("Enter the movie name to search on BookMyShow: ")
    formatted_name = movie_name.replace(' ', '+')
    url = f"https://in.bookmyshow.com/explore/movies-{formatted_name}"
    print(f"Redirecting to: {url}")
    webbrowser.open(url)

# MAIN
print("....MOVIE RATINGS....")
time.sleep(1)
print("Prepared By : Apoorva Sharma")
time.sleep(1)
print("WANT TO KNOW WHAT TO WATCH????\nSEARCH THE RATINGS FOR YOUR FAVOURITE MOVIES HERE....")
time.sleep(1)
print(" \n")
choice1 = 'y'
while choice1 == 'y' or 'Y':
    a = input("Choose Mode\nFor USER mode and ADMIN mode, press U and A respectively....")
    if a == "U":
        search()
        redirect_to_bookmyshow()  # Redirecting to BookMyShow for the movie
    elif a == "A":
        b = input("Enter Password : ")
        time.sleep(1)
        print("*", end=" ")
        time.sleep(1)
        print("*", end=" ")
        time.sleep(1)
        print("*", end=" ")
        time.sleep(1)
        print("*", end=" ")
        time.sleep(1)
        print("*", end=" ")
        password = "123456789"
        
        if b == password:
            choice2 = 'y'
            while choice2 == 'y' or choice2 == 'Y':
                num = int(input("\nPress 1 to READ records\nPress 2 to WRITE records\nPress 3 to APPEND records\nPress 4 to UPDATE records\nPress 5 to DELETE records\nPress 6 to SEARCH records\nPress 7 to SEARCH MOVIE ON BOOKMYSHOW\n"))
                if num == 1:
                    read()
                elif num == 2:
                    write()
                elif num == 3:
                    append()
                elif num == 4:
                    update()
                elif num == 5:
                    delete()
                elif num == 6:
                    search()
                elif num == 7:
                    redirect_to_bookmyshow()  # New option to redirect to BookMyShow
                else:
                    print("Enter correct choice....")
                choice2 = input("To go to main menu press y and n to go back to mode selection....")
        else:
            print("Enter correct password....")
    choice1 = input("To go to Mode selection press y....")
