import random

# القوائم التي تحتوي على الألوان والرموز
suits = ['قلوب', 'ألماس', 'بستان', 'سكوت']
ranks = ['2', '3', '4', '5', '6', '7', '8', '9', '10', 'جاك', 'ملكة', 'ملك', 'آس']

# إنشاء الأوراق
def create_deck():
    deck = []
    for suit in suits:
        for rank in ranks:
            deck.append((rank, suit))
    random.shuffle(deck)
    return deck

# توزيع الأوراق على اللاعبين
def deal_cards(deck):
    player1_hand = deck[:len(deck)//2]
    player2_hand = deck[len(deck)//2:]
    return player1_hand, player2_hand

# لعب جولة واحدة
def play_round(player1_card, player2_card):
    print(f"اللاعب 1: {player1_card[0]} من {player1_card[1]}")
    print(f"اللاعب 2: {player2_card[0]} من {player2_card[1]}")
    if ranks.index(player1_card[0]) > ranks.index(player2_card[0]):
        return "لاعب 1"
    elif ranks.index(player1_card[0]) < ranks.index(player2_card[0]):
        return "لاعب 2"
    else:
        return "تعادل"

# اللعبة الرئيسية
def war_game():
    deck = create_deck()
    player1_hand, player2_hand = deal_cards(deck)
    player1_wins = 0
    player2_wins = 0
    rounds_played = 0

    while player1_hand and player2_hand:
        player1_card = player1_hand.pop(0)
        player2_card = player2_hand.pop(0)
        result = play_round(player1_card, player2_card)
        if result == "لاعب 1":
            player1_wins += 1
        elif result == "لاعب 2":
            player2_wins += 1
        rounds_played += 1

    print("\nالنتيجة النهائية:")
    print(f"عدد الجولات: {rounds_played}")
    print(f"فوز اللاعب 1: {player1_wins}")
    print(f"فوز اللاعب 2: {player2_wins}")

# تشغيل اللعبة
war_game()
