<H3>ENTER YOUR NAME</H3>
<H3>ENTER YOUR REGISTER NO.</H3>
<H3>EX. NO.6</H3>
<H3>DATE:</H3>
<H1 ALIGN =CENTER>Implementation of Semantic ANalysis</H1>
<H3>Aim: to perform Parts of speech identification and Synonym using Natural Language Processing (NLP) techniques. </H3> 
 <BR>
<h3>Algorithm:</h3>
Step 1: Import the nltk library.<br>
Step 2: Download the 'punkt', 'wordnet', and 'averaged_perceptron_tagger' resources.<br>
Step 3:Accept user input for the text.<br>
Step 4:Tokenize the input text into words using the word_tokenize function.<br>
Step 5:Iterate through each word in the tokenized text.<br>
•	Perform part-of-speech tagging on the tokenized words using nltk.pos_tag.<br>
•	Print each word along with its corresponding part-of-speech tag.<br>
•	For each verb , iterate through its synsets (sets of synonyms) using wordnet.synsets(word).<br>
•	Extract synonyms and antonyms using lemma.name() and lemma.antonyms()[0].name() respectively.<br>
•	Print the unique sets of synonyms and antonyms.
<H3>Program:</H3>
```c
NAME : CHARUMATHI R
REF NO : 212222240021
```
```C
import nltk
from nltk.corpus import wordnet

nltk.download('averaged_perceptron_tagger')
nltk.download('wordnet')
nltk.download('punkt')

# Function to identify verbs in a sentence
def get_verbs(sentence):
    verbs = []
    pos_tags = nltk.pos_tag(nltk.word_tokenize(sentence))
    for word, tag in pos_tags:
        if tag.startswith('V'):  # Verbs start with 'V' in the POS tag
            verbs.append(word)
    return verbs


def get_synonyms(word):
    synonyms = []
    for syn in wordnet.synsets(word):
        for lemma in syn.lemmas():
            synonyms.append(lemma.name())
    return synonyms


def read_text_file(file_path):
    with open(file_path, 'r') as file:
        text = file.read()
    return text


def main():
    file_path = 'sample.txt'

    text = read_text_file(file_path)
    sentences = nltk.sent_tokenize(text)

    all_verbs = []
    synonyms_dict = {}

    for sentence in sentences:
        verbs = get_verbs(sentence)
        all_verbs.extend(verbs)
        for verb in verbs:
            synonyms = get_synonyms(verb)
            synonyms_dict[verb] = synonyms

    with open('output.csv', 'w', newline='') as csvfile:
        writer = csv.writer(csvfile)
        writer.writerow(['Verb', 'Synonyms'])
        for verb, synonyms in synonyms_dict.items():
            writer.writerow([verb, ', '.join(synonyms)])


if __name__ == '__main__':
    main()

```
<H3>Output</H3>
Verb	Synonyms
remember	remember, retrieve, recall, call_back, call_up, recollect, think, remember, think_of, remember, think_back, remember, remember, commend, remember, remember, commemorate, remember
was	Washington, Evergreen_State, WA, be, be, be, exist, be, be, equal, be, constitute, represent, make_up, comprise, be, be, follow, embody, be, personify, be, be, live, be, cost, be
playing	playing, playing, acting, playing, playacting, performing, play, play, play, act, play, represent, play, play, spiel, play, act, play, act_as, play, play, play, recreate, play, play, play, play, play, toy, play, play, run, toy, fiddle, diddle, play, play, dally, trifle, play, play, dally, toy, play, flirt, play, act, play, roleplay, playact, play, bring, work, play, wreak, make_for, play, play, bet, wager, play, play, play, play, meet, encounter, play, take_on, play
beat	beat, round, pulse, pulsation, heartbeat, beat, rhythm, beat, musical_rhythm, beat, beatnik, beat, beat, meter, metre, measure, beat, cadence, beat, beat, beat, beat, beat_out, crush, shell, trounce, vanquish, beat, beat_up, work_over, beat, beat, pound, thump, beat, drum, beat, thrum, beat, beat, flap, beat, beat, scramble, beat, beat, beat, bunk, tick, ticktock, ticktack, beat, beat, flap, beat, pulsate, beat, quiver, beat, beat, beat, outwit, overreach, outsmart, outfox, beat, circumvent, perplex, vex, stick, get, puzzle, mystify, baffle, beat, pose, bewilder, flummox, stupefy, nonplus, gravel, amaze, dumbfound, exhaust, wash_up, beat, tucker, tucker_out, all_in, beat, bushed, dead
called	name, call, call, call, telephone, call_up, phone, ring, shout, shout_out, cry, call, yell, scream, holler, hollo, squall, call, send_for, visit, call_in, call, call, call, call, call, call, address, call, call, call, call_in, bid, call, call, call_off, call, predict, foretell, prognosticate, call, forebode, anticipate, promise, call, call, call, call, call, call, call, call, call, call
said	state, say, tell, allege, aver, say, suppose, say, read, say, order, tell, enjoin, say, pronounce, articulate, enounce, sound_out, enunciate, say, say, say, say, say, say, aforesaid, aforementioned, said
am	americium, Am, atomic_number_95, Master_of_Arts, MA, Artium_Magister, AM, amplitude_modulation, AM, be, be, be, exist, be, be, equal, be, constitute, represent, make_up, comprise, be, be, follow, embody, be, personify, be, be, live, be, cost, be
bored	bore, tire, bore, drill, bored, world-weary, blase, bored
don	Don, preceptor, don, don, father, Don, Don, Don_River, Don, wear, put_on, get_into, don, assume
want	privation, want, deprivation, neediness, lack, deficiency, want, need, want, wish, wishing, want, desire, want, want, need, require, want, want, want
play	play, drama, dramatic_play, play, play, maneuver, manoeuvre, play, play, play, bid, play, play, child's_play, playing_period, period_of_play, play, free_rein, play, shimmer, play, fun, play, sport, looseness, play, play, frolic, romp, gambol, caper, turn, play, gambling, gaming, play, play, swordplay, play, play, play, act, play, represent, play, play, spiel, play, act, play, act_as, play, play, play, recreate, play, play, play, play, play, toy, play, play, run, toy, fiddle, diddle, play, play, dally, trifle, play, play, dally, toy, play, flirt, play, act, play, roleplay, playact, play, bring, work, play, wreak, make_for, play, play, bet, wager, play, play, play, play, meet, encounter, play, take_on, play
got	get, acquire, become, go, get, get, let, have, receive, get, find, obtain, incur, arrive, get, come, bring, get, convey, fetch, experience, receive, have, get, pay_back, pay_off, get, fix, have, get, make, induce, stimulate, cause, have, get, make, get, catch, capture, grow, develop, produce, get, acquire, contract, take, get, get, make, get, drive, get, aim, catch, get, catch, arrest, get, get, catch, get, get, get, catch, get, catch, get, get, receive, scram, buzz_off, fuck_off, get, bugger_off, get, get, get_under_one's_skin, get, catch, get, draw, get, get, perplex, vex, stick, get, puzzle, mystify, baffle, beat, pose, bewilder, flummox, stupefy, nonplus, gravel, amaze, dumbfound, get_down, begin, get, start_out, start, set_about, set_out, commence, suffer, sustain, have, get, beget, get, engender, father, mother, sire, generate, bring_forth
’	
go	go, spell, tour, turn, Adam, ecstasy, XTC, go, disco_biscuit, cristal, X, hug_drug, crack, fling, go, pass, whirl, offer, go, go_game, travel, go, move, locomote, go, proceed, move, go, go_away, depart, become, go, get, go, run, go, run, go, pass, lead, extend, proceed, go, go, go, sound, go, function, work, operate, go, run, run_low, run_short, go, move, go, run, survive, last, live, live_on, go, endure, hold_up, hold_out, go, die, decease, perish, go, exit, pass_away, expire, pass, kick_the_bucket, cash_in_one's_chips, buy_the_farm, conk, give-up_the_ghost, drop_dead, pop_off, choke, croak, snuff_it, belong, go, go, start, go, get_going, move, go, go, go, blend, go, blend_in, go, lead, fit, go, rifle, go, go, plump, go, fail, go_bad, give_way, die, give_out, conk_out, go, break, break_down, go
sleep	sleep, slumber, sleep, sopor, sleep, nap, rest, eternal_rest, sleep, eternal_sleep, quietus, sleep, kip, slumber, log_Z's, catch_some_Z's, sleep
‘	
s	second, sec, s, sulfur, S, sulphur, atomic_number_16, south, due_south, southward, S, mho, siemens, reciprocal_ohm, S, S, s, randomness, entropy, S
win.	
sat	Saturday, Sabbatum, Sat, sit, sit_down, sit, sit_around, sit_down, sit, sit, model, pose, sit, posture, ride, sit, sit, baby-sit, sit, seat, sit, sit_down, sit
played	play, play, play, act, play, represent, play, play, spiel, play, act, play, act_as, play, play, play, recreate, play, play, play, play, play, toy, play, play, run, toy, fiddle, diddle, play, play, dally, trifle, play, play, dally, toy, play, flirt, play, act, play, roleplay, playact, play, bring, work, play, wreak, make_for, play, play, bet, wager, play, play, play, play, meet, encounter, play, take_on, play, played
won	South_Korean_won, won, North_Korean_won, won, win, acquire, win, gain, gain, advance, win, pull_ahead, make_headway, get_ahead, gain_ground, succeed, win, come_through, bring_home_the_bacon, deliver_the_goods, won
yawned	yawn, gape, yawn, yaw


<H3>Result:</H3>
Thus ,the program to perform the Parts of Speech identification and Synonymis executed sucessfully.
