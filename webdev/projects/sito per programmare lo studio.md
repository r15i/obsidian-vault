https://www.desmos.com/calculator/hodhmlfa0z?lang=it 
data set 
https://huggingface.co/datasets/open-spaced-repetition/fsrs-dataset?row=0
https://github.com/open-spaced-repetition/short-term-memory-research
https://forums.ankiweb.net/t/best-learning-steps-for-fsrs/40357/11
## Implementazione 1.0 

- bozzetto per le fasi dell'apprendimento
![[Immagine WhatsApp 2024-02-28 ore 14.11.37_c8b20eae.jpg]]


- the best choice to implement the flash cards with this kind of programmation is by keeping the flashcards divided per argouments during the first part and than , at the final part mix them and subdivide them at each repetition for how much we remember , but this only on the last stache, for the first part the subdivision is made by subject since it would conflict with the concept of subdividing by argouments during the learing 

- spaced repetition basata su esponenziale (tarato su due componenti learn iniziale e increase in learning rate) e un tempo iniziale di UNDERSTANDING dell'argomento
- fitting di diversi argomenti fatto secondo la logica di inserire dove disponibile uno spazio nuovi argomenti mentre una volta arrivato nella parte di spaced repetition gli argomenti possono sovrapporsi 
- in questa versione le tecniche utilizzate nella spaced repetition sono analoghe in efficacia (fare uno schema e ciclare delle flashcards sarà analogo a ripassiare alla lavagna facendo esercizi) considerandole tutte come ripasso, tuttavia bisognerà creare un rank in base all'efficacia **per la tipologia di esame**

# All the estimation in this code are made by the hour
``` Python 
# Formula for forgetting curve: retention = e^(-learn_rate * t)

def retention_curve(learn_rate, times):
    retention = np.exp(-learn_rate * times)
    return retention
# return the time to reach a target retention (in minutes)
def time_to_reach_retention(learn_rate, target_retention):
    time_to_reach = -np.log(target_retention) / learn_rate
    return time_to_reach
# return a learning rate for the retention obtained in a certain time (in minutes)
def learning_rate_from_retention(retention, time):
    # Utilizziamo la formula della curva di dimenticanza per trovare il tasso di apprendimento

    # retention = e^(-learn_rate * time)

    learn_rate = -np.log(retention) / time

    return learn_rate
```

# Workflow 
![[Immagine WhatsApp 2024-03-02 ore 19.16.48_dabd0d24.jpg]]

![[Immagine WhatsApp 2024-03-02 ore 11.39.34_12f598a3.jpg]]


![[Immagine WhatsApp 2024-03-09 ore 19.33.14_9826e69e.jpg]]
- the threshold of knowledge is actually a parameter that interact with how long we take to learn (if we repeat closer and with an high knowledge it will be easier to recall than if we are far and with low knowledge (we need a balance that measure wich is the optimall learning threshold we want to achieve to cram the most stuff we can without impacting learning(basically if i use a level of knowledge threshold how much it will impact the increase in the remembering rate?)))

le prime 4 fasi sono da considerare one shot ovvero si utilizzano per la creazione dei supporti 
la iterazione vera e propria si avrà nelle fasi 5-6 

di conseguenza le prime 4 quattro fasi vanno eseguite in rapida successione per poi distanziare tramite la forgetting curve le nozioni (prima capire bene le cose )

**una stima iniziale per questa operazione potrebbe essere un giorno per fase e  per argomento**

il trick starebbe nel una volta completata la prima parte cominciare a fittare nuove parti dello studio all'interno dei gap creati dalla spaced repetition


## Programmazione

- **DI CONSEGUENZA LA FORGETTING CURVE NON E' SUFFICENTE COME METRICA** bisogna avrere una metrica diversa per l'apprendimento iniziale

- Inoltre bisogna fare i conti in uno scenario non ideale (bisogna avere un acconto del tempo per imprevisti e qui si guarda la parte di **PROJECT MANAGEMET** RISK MANAGEMENT E TIME MANAGEMENT) (si utilizzerà una stima di 1/4 del tempo )


## Implementazione 
- Si utilizzerà una stima di una unità di lavoro (sessione da 1 h e 30 o tre pomodoro tecnique (basate sulla soglia della'attenzione )) di conseguenza ogni fase di questo studio dovrà essere portata a termine in 1 e 30 **e conseguentemente scalando** il carico di lavoro
- Per quanto riguarda il rischio in account si utilizzerannà un 1/4 del tempo totale per come acconto per il numero di imprevisti ad esempio (su un ora di studio si accaunterà per almeno 15 minuti di nulla, solo per rendere l'idea in realtà dato che è piu che altro una stima sul lungo termine 
- un altro grosso problema è rappresentato da: cosa fare se saltiamo una sessione : **l'intero piano shifta di 1 una giornata** (inizialmente userò solo una versione senza data (la lista di argomenti reffigurerà solo un obbiettivo giornaliero distribuito (che se non rispettato viene shiftato )) )


# bella discussione sulle formule
https://forums.ankiweb.net/t/best-learning-steps-for-fsrs/40357/13


# BISOGNA TROVARE UN MODO PER FARE UNA BUONA STIMA DI DUE VALORI:
- il learning rate iniziale(che calcoleremo utilizzando una semplice review tramite flashcards)
- il linear rate increase (ovvero quanto effettivamente ricordiamo di piu per ogni sessione ) (quanto si assottiglia la curva) (bisogna tenere presente che questo incremento non è detto che sia lineare ma per ora assumiamo che sia solo **creascente progressivo** ovvero che aumenti con il numero di ripetizioni )
- Sarebbe inoltre interessante testare l'andamento del learning rate iniziale, tuttavia non siamo medici o cognitivi  
# Stima utilizzata 
per ora sto utilizzando una stima del learning rate pari a *1.2* basandomi sul fatto che la curva a livello storico (wikipedia ) assume di che in un giorno perdiamo il 70% del nostra memoria dopo un giorno.
(questa)
  
  ![[Pasted image 20240224181723.png]]
https://www.desmos.com/calculator/otbmygu0mp?lang=it


# DA QUI CI SONO DELLE COSE PER LA VERSIONE 2.0


 Do un occhio a supermemo 
https://www.super-memory.com/archive/help2004/help.htm
 dataset sulle flashcard di ankin 
https://huggingface.co/datasets/open-spaced-repetition/fsrs-dataset?row=0
https://github.com/open-spaced-repetition/short-term-memory-research

# LMSHERLOCK
https://medium.com/@JarrettYe/how-did-i-publish-a-paper-in-acmkdd-as-an-undergraduate-c0199baddf31
https://medium.com/@JarrettYe/how-did-i-publish-a-paper-in-acmkdd-as-an-undergraduate-c0199baddf31
https://www.reddit.com/user/LMSherlock/
https://www.reddit.com/r/Anki/comments/15mab3r/fsrs_explained_part_1_what_it_is_and_how_it_works/
# FSRS 
https://github.com/open-spaced-repetition/fsrs4anki/wiki/The-Algorithm
The FSRS (Free Spaced Repetition Scheduler) algorithm is based on a variant of the DSR (Difficulty, Stability, Retrievability) model, which is used to predict memory states.
https://github.com/open-spaced-repetition/fsrs4anki/wiki/The-Algorithm


The Free Spaced Repetition Scheduler (FSRS) algorithm, based on a variant of the Difficulty, Stability, Retrievability (DSR) model, is used in the field of cognitive science, educational psychology, and technology-enhanced learning. Its primary purpose is to optimize the scheduling of review sessions for learning materials to maximize long-term retention and minimize the time required for effective learning. Here's how FSRS can be used:

1. **Spaced Repetition Software (SRS)**: FSRS algorithms are often implemented in SRS applications and platforms. These tools assist learners in efficiently memorizing large amounts of information by scheduling review sessions based on the principles of spaced repetition.

2. **Language Learning Apps**: Many language learning applications utilize FSRS algorithms to schedule vocabulary review sessions for learners. By adapting the timing of review sessions based on the difficulty, stability, and retrievability of each word or phrase, these apps aim to optimize language acquisition.

3. **Educational Platforms**: Educational platforms, both traditional and online, can incorporate FSRS algorithms to personalize learning experiences for students. By dynamically adjusting the timing of review activities based on individual learning progress and memory states, these platforms enhance learning outcomes.

4. **Personal Productivity Tools**: Some personal productivity tools integrate FSRS algorithms to help users memorize important information, such as facts, figures, and concepts relevant to their work or daily life. These tools often employ spaced repetition techniques to support efficient memorization and knowledge retention.

Overall, FSRS algorithms play a crucial role in enhancing learning and memory retention by intelligently scheduling review sessions based on the difficulty, stability, and retrievability of the information being learned. They offer a systematic approach to spaced repetition, which has been shown to be highly effective in promoting long-term retention and learning efficiency.


basato sul modello 
https://github.com/open-spaced-repetition/free-spaced-repetition-scheduler
https://supermemo.guru/wiki/Two_components_of_memory
https://dl.acm.org/doi/10.1145/3534678.3539081?cid=99660547150
https://www.super-memory.com/archive/help2004/help.htm
https://github.com/open-spaced-repetition/py-fsrs


# COSE PER LA 3.0
## Si potrebbe implementare un albero di flash cards 

UNISCE LE FLASH CARDS AGLI SCHEMI FATTI TRAMITE MIND MAP :

SI COSTRUISCE UNA STORIA RAPPRESENTATA DALL'ALBERO  O GRAFO 

VI è UN ALBERO PER ARGOMENTO della materia (la ripetizione dei singoli alberi è fatta tramite logica spaced repetition) 

ogni albero possiede una storia o una rappresentazione locale e visuale  e ad ogni foglia vi è una nozione da ricordare associata ad una parola o una caratteristica 

si utilizza una metrica di ripetizione all'interno dell'albero diversa da quella della ripetizione dei singoli alberi 




