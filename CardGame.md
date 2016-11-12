1. Tools (cards)  
2. Rules  


```
class Card {
  private enum suit {SPADE, HEART, DIAMOND, CLUB}
  private final int num;  // Use 1 to 13 represent A to K
  private String color;
}


class Deck {
  private int totalNumber;
  
  // Use an index as a block, on the left side of which are the cards delt, one the right side of which are the cards remain
  private int dealtIndex = 0;
  private List<Card> cards = new ArrayList<>();
  
  
  public int remainingNumber () {
    return cards.size() - dealtIndex	;
  }
  
  public Card[] dealHand(int number) {
    if (remainingNumber < number)
      return null;
    Card[] cards = new Card[number];
    for (int i = 0; i < number; i++) {
      cards[i] = dealCard();
    }
    return cards;     // the list should be immutable
  }
  
  public Card dealCard() {
    return remainingCards() == ? null : cards.get(dealtIndex++);
  }
}


class Player {
  private List<Card> cards = new ArrayList<>();
  
  public int getScore() {
    int score = 0;
    for (int i = 0; i < cards.size(); i++) {
      score += cards.get(i).getValue();
    }
    return score;
  }
  
}

class BlackJackPlayer extends Player {
  @Override
  public int getScore() {
    // Apply rules of Black Jack
  }
}
```
