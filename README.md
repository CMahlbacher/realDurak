# realDurak

from random import randint
from Deque import Deque

class Durak:
    
    def __init__(self):
        self.run()
    
    def run(self):
        self.player1 = Deque()
        self.player2 = Deque()
        self.masterDeck = Deck()
        self.deal()
        
        
    def deal(self):
        for k in range(0, 2):
            for i in range (0, 3):
                self.player1.push_front(self.masterDeck.dealCard())
            for i in range (0, 3):
                self.player2.push_front(self.masterDeck.dealCard())
        
        print(self.masterDeck.trumpCard())
        
                

class Card:
            
    def __init__(self, card, suit):
        self._card = card
        self._suit = suit
        self._cardValues = {2 : 'Two', 3 : 'Three', 4 : 'Four', 5 : 'Five', 6 : 'Six', 7 : 'Seven', 8 : 'Eight', 9 : 'Nine', 10 : 'Ten', 11 : 'Jack', 12 : 'Queen', 13 : 'King', 14 : 'Ace'}        
    
    def __lt__(self, other):
        
        return self._card < other._card
    
    def __gt__(self, other):
        return self._card > other._card
    
    def __eq__(self, other):
        return self._card == other._card
    
    def __str__(self):
        return self._cardValues[self._card] + " of " + self._suit + "s"
    
        
class Deck:
        
        
    def __init__(self):
        self.deck = Deque()
           
        for i in range(6, 15):
            self.deck.push_front(Card(i, 'Club'))
            self.deck.push_front(Card(i, 'Spade'))
            self.deck.push_front(Card(i, 'Diamond'))
            self.deck.push_front(Card(i, 'Heart'))
                
        self.shuffle_deck()
        
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
    Durak()
