#!/usr/bin/python

import sys
import random

year=1
population=100
acres=1000
bushels=3000
landPrice=20
peopleHungry=100
totalDead=0
seeds=0
version="1.5"

gameRunning=True

def main():
    print "*************************"
    print "* Welcome to HAMMURABI! *"
    print "*************************"
    print "Commands: quit, save, load"
    print "Version", version
    print""
    while gameRunning:
        menu()
        cmd=raw_input("->")
        if cmd == "1":buyLand()
        elif cmd=="2":sellLand()
        elif cmd=="3":feed()
        elif cmd=="4":plant()
        elif cmd=="5":stats()
        elif cmd=="7":endTurn()
        elif cmd.lower()=="quit":sys.exit()
        elif cmd=="a":spawnSeed()
        elif cmd.lower()=="save":save()
        elif cmd.lower()=="load":load()
        elif cmd.lower()=="w":war()
        else:
            print "Wrong"

def menu():
    print"\n1) Buy land"
    print "2) Sell land"
    print "3) Feed people"
    print "4) Plant seeds"
    print "5) Stats"
    print ""
    print "7) END TURN"


def harvest():
    global bushels
    global acres
    bushels=bushels+acres
    print "You harvest",acres,"bushels."
def buyLand():
    global bushels
    global acres
    print "=Buy land="
    print "Current price of land is", landPrice,"bushels per acre"
    print "You have",bushels,"bushels"
    spending = raw_input("\nHow many bushels do you want to spend? ")
    try:
        if int(spending)>bushels:
            print "You dont have that many!"
        else:
            bushels=bushels-int(spending)
            spending=int(spending)/landPrice
            acres=acres+int(spending)
            print "you have bought",spending,"acres!"            
    except ValueError:
        print "You must enter a number!"
    
    raw_input("Press enter to continue . . . ")
def sellLand():
    global acres
    global bushels
    print "=Sell Land="
    print "The current price for land is",landPrice,"bushels per acre."
    print "You currently own",acres,"acres."
    sellamt=raw_input("How many acres do you want to sell? ")
    try:
        if int(sellamt)>acres:
            print "You dont have that many!"
        else:
            acres=acres-int(sellamt)
            bushels=bushels+(int(sellamt)*landPrice)
            print "You sold",sellamt,"acres for a total of",int(sellamt)*landPrice,"bushels!"          
    except ValueError:
        print "You must enter a number!"
    raw_input("Press enter to continue . . . ")
def plant():
    global seeds
    global acres
    print "=Plant="
    print "\nHow much will you plant?\nEach acre requires 1 seed"
    print "You have", seeds,"seeds"
    plants=raw_input("How many? ")
    try:
        if int(plants) >seeds:
            print "You dont have that many!"
        else:
            seeds=seeds-int(plants)
            acres=acres+int(plants)
            print "You have planted", int(plants), "seeds!" 
    except ValueError:
        print "You must enter a number!"
    raw_input("Press enter to continue . . . ")
def growPopulation():
    global population
    growth=random.randrange(1,20)
    if population<acres: population=population+growth
    print growth, "people settle in your Kingdom\n"
def feed():
    global peopleHungry
    global bushels
    print"=Feed="
    print "Feed your people, each one requires 20 bushels."
    print "To feed all people you need to provide",peopleHungry*20, "bushels.\n"
    print "You have",bushels, "bushels"
    food=raw_input("How many bushels will you give your people? ")
    try:
        if int(food) >bushels:
            print "You dont have that many!"
        else:
            bushels=bushels-int(food)
            food=int(food)/20
            if int(food)>peopleHungry:
                print "You have fed", peopleHungry, "people"    
            else:
                print "You have fed", int(food), "people" 
            peopleHungry=peopleHungry-int(food)
            if peopleHungry < 0:
                peopleHungry=0    
            
    except ValueError:
        print "You must enter a number!"
    
    raw_input("Press enter to continue . . . ")    
def endTurn():
    global population
    global peopleHungry
    global year
    global landPrice
    global totalDead
    global bushels
    
    print"\n***************"
    print "End of year",year,"and a new year dawns upon your kingdom!\n"
    
    totalDead=totalDead+peopleHungry
    population=population-peopleHungry
    if population==0:
        print "Everyone in your kingdom is dead, there is no one who can farm your stuff"
        raw_input("Press enter to continue . . . ") 
        sys.exit()
    print peopleHungry,"people die from starvation"
    peopleHungry=population
    
    landPrice=random.randrange(17,26)
    print "\nThe price of land changes to",landPrice
    
    if acres>0:
        rats=random.randrange(1,(acres/2))
        bushels=bushels-rats
        print "Rats eat",rats,"bushels"
    else:
        pass
    spawnSeed()
    harvest()
    year=year+1
    WillThereBeWar=random.randrange(1,100)
    if WillThereBeWar==1 or WillThereBeWar==20 or WillThereBeWar==40 or WillThereBeWar==60 or WillThereBeWar==80 or WillThereBeWar==100:
        war()
    
    growPopulation()
    peopleHungry=population

    
    raw_input("Press enter to continue . . . ")
def stats():
    print ""
    print "****************************"
    print "* THE STATE OF THE KINGDOM *"
    print "****************************"
    print "YEAR:",year
    print "POPULATION:",population, "("+str(peopleHungry),"are hungry)"
    print "ACRES:",acres
    print "BUSHELS:",bushels
    print "SEEDS:",seeds
    print "CURRENT LAND PRICE:",landPrice,"Bushels/acre" 
    print "TOTAL DEAD BECAUSE OF YOU:",totalDead,"\n"
    print "****************************"
    raw_input("Press enter to continue . . . ")
def spawnSeed():
    global seeds
    randomNumber=random.randrange(1,100)
    if randomNumber==1 or randomNumber==20 or randomNumber==40 or randomNumber==60 or randomNumber==80 or randomNumber==100:
        seeds=seeds+random.randrange(1,20)
        print "\n**Your plants are seeding!**\n" 

def war():
    
    global population
    global bushels
    global acres    
    global peopleHungry
    
    peopleKilledInWar=random.randrange(1,300)
    bushelsPillaged=random.randrange(1,4000)
    landRazed=random.randrange(1,2000)
    #print "DEBUG:"
    #print "peopleKilledInWar: ",peopleKilledInWar
    #print "bushelsPillaged: ",bushelsPillaged
    #print "landRazed: ",landRazed
    print
    
    print ""
    print "++++WAR++++"
    neighbouringLand=["Spritlandet","j&j Imperiet","n&n Federation","Nord Korea","Old Camp","Myrtana"]
    print neighbouringLand[random.randrange(0,len(neighbouringLand))],"Invades!"
    
    survivors=population-peopleKilledInWar
    killed=population-survivors    
    
    if killed>population:
        killed=population
        population=0
        
        print "Your whole population is massacred and the enemy forces move on to pillage and plunder!"
        
        
        
        bushelsLeft=bushels-bushelsPillaged
        bushelsLost=bushels-bushelsLeft
        
        acresLeft=acres-landRazed
        acresLost=acres-acresLeft
        
        if bushelsLeft<0: bushelsLost=bushels
        if acresLeft<0: acresLost=acres
        
        bushels=bushelsLeft
        acres=acresLeft
        if bushels<0: bushels=0
        if acres<0:acres=0
        
        print "The enemy forces steal",bushelsLost,"bushels!"
        print "and",acresLost,"acres are razed to the ground!"  
                 
    else:
        print "Your defense holds!"
        print "A total of",killed,"people are killed in the war!"
        print""
    population=survivors
    if population<0:
        population=0
    peopleHungry=population
    print "+++++++++++\n"

#--------------------------------------------------------------
def save():
    print "Saving will overwrite any previous saves with the same name!"
    savename=raw_input("Enter the name of your save: ")
    try:
        savefile=open(savename+".hammurabiSave","w")
        savefile.write(str(year)+"\n")
        savefile.write(str(population)+"\n")
        savefile.write(str(acres)+"\n")
        savefile.write(str(bushels)+"\n")
        savefile.write(str(landPrice)+"\n")
        savefile.write(str(peopleHungry)+"\n")
        savefile.write(str(totalDead)+"\n")
        savefile.write(str(seeds)+"\n")
        savefile.close()    
        print "Saved!"
    except:
        print "Saving failed for some reason...."
def load():
    global year
    global population
    global acres
    global bushels
    global landprice
    global peopleHungry
    global totalDead
    global seeds
     
    try:
        goodData=[]
        savename=raw_input("Enter the name of your save: ")
        savefile=open(savename+".hammurabiSave","r")
        rawdata=savefile.readlines()
        for line in rawdata:
            goodData.append(line.rstrip("\n"))
            
        year=int(goodData[0])
        population=int(goodData[1])
        acres=int(goodData[2])
        bushels=int(goodData[3])
        landPrice=int(goodData[4])
        peopleHungry=int(goodData[5])
        totalDead=int(goodData[6])
        seeds=int(goodData[7])
        
        print "Load success!"
        stats()
    
    except:
        print "Loading failed for some reason :("

if __name__ == '__main__':
    main()
    
    
    
