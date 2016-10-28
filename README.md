from random import randint
from Deque import Deque

class Durak:
    
    
    
    def __init__(self):
        self.run()
    
    def run(self):
        self.player1 = Deque()
        self.player2 = Deque()
        self.masterDeck = Deck()
        self.masterDeck.randomShuffle()
        self.deal()
        self.setInitialAttacker()
        self.play()
        
    def play(self):
        
        while not self.gameOver():
            s
        
    def gameOver(self):
        
        return len(player1) == 0 or len(player2) == 0
    
    def setInitialAttacker(self):
        lowTrumpA = 16
        lowTrumpB = 16
        
        for i in range(0, 6):
            
    
    def setAttacker(self, player):
        self.attacker = player
        
    def setDefender(self, player):
        self.defender = player
        
    def switchPlayers(self):
        temp = self.attacker
        self.attacker = self.defender
        self.defender = temp
        
        
    def deal(self):
        for k in range(0, 2):
            for i in range (0, 3):
                self.player1.push_front(self.masterDeck.dealCard())
            for i in range (0, 3):
                self.player2.push_front(self.masterDeck.dealCard())
        
        print(str(self.masterDeck.trumpCard()) + " is the bottom card.")
        
        print(self.player1)
        print(self.player2)
        
                

class Card:
            
    def __init__(self, card, suit):
        self.card = card
        self.suit = suit
        self.cardValues = {2 : 'Two', 3 : 'Three', 4 : 'Four', 5 : 'Five', 6 : 'Six', 7 : 'Seven', 8 : 'Eight', 9 : 'Nine', 10 : 'Ten', 11 : 'Jack', 12 : 'Queen', 13 : 'King', 14 : 'Ace'}        
    
    def __lt__(self, other):
        
        return self.card < other.card
    
    def __gt__(self, other):
        return self.card > other.card
    
    def __eq__(self, other):
        return self.card == other.card
    
    def __str__(self):
        return self.cardValues[self.card] + " of " + self.suit + "s"
    
    def getSuit(self):
        return self.suit
    
        
class Deck:
        
        
    def __init__(self):
        self.deck = Deque()
           
        for i in range(6, 15):
            self.deck.push_front(Card(i, 'Club'))
            self.deck.push_front(Card(i, 'Spade'))
            self.deck.push_front(Card(i, 'Diamond'))
            self.deck.push_front(Card(i, 'Heart'))
        
    def __str__(self):
        
        toReturn = ''
            
        for i in range(0, len(self.deck)):
            guv = self.deck.pop_front()
            toReturn = toReturn + str(guv) + '\n'
            self.deck.push_back(guv)
            
        return toReturn
    
    def dealCard(self):
        
        return self.deck.pop_front()
    
    def trumpCard(self):
        
        return self.deck.peek_back()
    
    def randomShuffle(self):
        deckLength = len(self.deck)
        tempArray = [None] * deckLength
        
        while len(self.deck) > 0:
            x = randint(0, deckLength - 1)
            
            if tempArray[x] is None:
                tempArray[x] = self.deck.pop_back()
                
        
        for k in range(0, deckLength):
            self.deck.push_front(tempArray[k])
            
    def shuffle_deck(self):
        
        deckA = Deque()
        deckB = Deque()
        
        for k in range(0, 30):
            for i in range(0, 36):
                if i < 18:
                    deckA.push_front(self.deck.pop_back())
                else:
                    deckB.push_front(self.deck.pop_back())
                    
            while len(deckA) > 0 or  len(deckB) > 0:
                x = randint(0, 3)
                for i in range(0, x):
                    if len(deckA) > 0:
                        self.deck.push_front(deckA.pop_back())
                x = randint(0, 3)
                for i in range(0, x):
                    if len(deckB) > 0:
                        self.deck.push_front(deckB.pop_back())
                        
        print("Shuffled")



    
if __name__ == '__main__':
    bob = Durak()
