# Μουσικοί Ρυθμοί

Σκεφτείτε το ακόλουθο πρόβλημα. Θέλετε να φτιάξετε μια δυαδική σειρά των n bits, από τα οποία τα k είναι 1 (και τα υπόλοιπα φυσικά 0). Θέλετε επιπλέον στη σειρά αυτή τα 1 να είναι όσο το δυνατόν πιο ισοκατανεμημένα ανάμεσα στα 1. Αν το k διαιρεί ακριβώς το n, τότε η λύση είναι προφανής: για παράδειγμα, για n = 16 και k = 4 έχουμε τη σειρά:
```
[1 0 0 0 1 0 0 0 1 0 0 0 1 0 0 0]
``` 
Το πρόβλημα αποκτά ενδιαφέρον όταν τα n και k είναι πρώτοι αριθμοί μεταξύ τους, δηλαδή όταν οι n και n έχουν μόνο το 1 ως κοινό διαιρέτη.

Έστω λοιπόν ότι έχουμε n = 13 και k = 5. Αφού 13 - 5 = 8, ξεκινάμε φτιάχνοντας μια ακολουθία με 5 άσους και 8 μηδενικά:
```
[ 1 1 1 1 1 0 0 0 0 0 0 0 0]
```
Αυτή την ακολουθία μπορούμε να την εκλάβουμε και ως 13 ακολουθίες που η κάθε μία περιέχει 1 bit:
```
[ [1] [1] [1] [1] [1] [0] [0] [0] [0] [0] [0] [0] [0] ]
```
Μοιράζουμε τα μηδενικά ώστε να προκύψουν 5 ακολουθίες των 2 bits η κάθε μία, και 3 ακολουθίες του 1 bit:
```
[ [1 0] [1 0] [1 0] [1 0] [1 0] [0] [0] [0] ]
```
Στη συνέχεια μοιράζουμε πάλι τα εναπομείναντα μηδενικά με τον ίδιο τρόπο, οπότε παίρνουμε:
```
[ [1 0 0] [1 0 0] [1 0 0] [1 0] [1 0] ]
```
Τώρα μοιράζουμε τις ακολουθίες `[1 0]`, οπότε παίρνουμε:
```
[ [1 0 0 1 0] [1 0 0 1 0] [1 0 0] ]
```
Η διαδικακασία τελειώνει όταν το υπόλοιπο (δηλαδή οι ακολουθίες με τον μικρότερο αριθμό bits) είναι ακριβώς 1, ή αν δεν έχουμε άλλα 0 να μοιράσουμε. Τότε ενώνουμε το αποτέλεσμα. Στο παράδειγμά μας έχουμε:
```
[ 1 0 0 1 0 1 0 0 1 0 1 0 0 ]
```

Αν θεωρήσουμε ότι η παραπάνω ακολουθία είναι ένας ρυθμός, όπου το `1` είναι το ισχυρό μέρος του ρυθμού και `0` το ασθενές, τότε με τη διαδικασία αυτή, για διαφορετικά n και k όταν τα n και k είναι πρώτοι μεταξύ τους προκύπτει ένα πλήθος ρυθμών που χρησιμοποιούνται στην παγκόσμια μουσική. Δύο παραδείγματα:

* Ο ρυθμός με k = 3 και n = 7, [ 1 0 1 0 1 0 0 ], είναι ο ρυθμός Ruchenitza που χρησιμοποιείται στη Βουλγάρικη λαϊκή μουσική και επίσης το ρυθμικό μοτίβο του τραγουδιού Money των Pink Floyd.
* O ρυθμός με k = 5 και n = 9, [ 1 0 1 0 1 0 1 0 1 ], είναι ένας δημοφιλής αραβικός ρυθμός ονόματι Agsag-Samai. Αν ξεκινήσει στο δεύτερο χτύπημα, είναι το μοτίβο των τυμπάνων που χρησιμοποιείται από τους Venda στη Νότια Αφρική, όπως επίσης και από έναν ρουμάνικο λαϊκό χορό. Ακόμα, είναι το ρυθμικό μοτίβο του ελληνικού Σιγάκτιστου [αν κάποιος ξέρει τι είναι αυτός ο χορός παρακαλώ να ενημερώσει τον διδάσκοντα] και του τουρκικού Samai aktsak. Αν αρχίσει στο τρίτο χτύπημα είναι το ρυθμικό μοτίβο του τουρκικού ρυθμού Nawahiid.

## Ευκλείδιοι Ρυθμοί και Ευκλείδιες Συμβολοσειρές

Ο τρόπος που περιγράψαμε, και με τον οποίο παράγονται οι ρυθμοί αυτοί για διαφορετικά n και k ακολουθεί τα αποτελέσματα του αλγόριθμου του Ευκλείδη για την εύρεση του Μέγιστου Κοινού Διαιρέτη μεταξύ δύο αριθμών. Πραγματικά, αν `euclid` είναι η υλοποίηση του αλγορίθμου, θα είχαμε `euclid(8,5) = euclid(5,3) = euclid(3,2) = euclid(2,1) = euclid(1,0) = 1`, που αν προσέξετε αντιστοιχεί στα βήματα που κάναμε. Για το λόγο αυτό οι ρυθμοί αυτοί ονομάζονται *Ευκλείδιοι ρυθμοί*.

Έναν Ευκλείδιο ρυθμό τον γράφουμε με τη μορφή E(k, n) όπου k ο αριθμός των παλμών και n το μήκος του ρυθμού, για παράδειγμα Ε(5, 9). Μπορούμε να τον γράψουμε και με έναν άλλο τρόπο, σύμφωνα με τον οποίο μετράμε τα διαστήματα μέχρι το επόμενο χτύπημα, οπότε έχουμε E(5, 9) = (22221), αφού περνούν δύο χρόνοι μεταξύ του πρώτου και του δεύτερου χτυπήματος στο [ 1 0 1 0 1 0 1 0 1 ] κ.ο.κ. Ένας άλλος ρυθμός είναι ο Ε(5, 12), ο οποίος αντιστοιχεί στο [ 1 0 0 1 0 1 0 0 1 0 1 0 ] και αναγράφεται και (32322), όπως μπορείτε να ελέγξετε. Ο δεύτερος τρόπος γραφής ονομάζεται *διάνυσμα διαστημάτων* και στην ουσία είναι μια συμβολοσειρά ακέραιων αριθμών. 

Αν έχουμε ένα ρυθμό γραμμένο σε μορφή διανύσματος διαστημάτων, έστω τον `P = (p[0], p[1] , ... , p[n−1])` τότε αν αυξήσουμε το `p[0]` κατά 1 και μειώσουμε το `p[n-1]` κατά ένα, θα προκύψει ένα νέο διάνυσμα διαστημάτων. Αν το νέο διάνυσμα μπορεί να προκύψει περιστρέφοντας το πρώτο, τότε λέμε ότι έχουμε μια *Ευκλείδια συμβολοσειρά*. Για παράδειγμα, Ε(4, 9) = [1 0 1 0 1 0 1 0 0 ] = (2223). Αυξάνοντας το πρώτο ψηφίο και μειώνοντας το τελευταίο παίρνουμε (3222), που προκύπτει από περιστροφή της πρώτης συμβολοσειράς, άρα ο ρυθμός, πέρα από Ευκλείδιος, είναι και Ευκλείδια συμβολοσειρά.

Αν πάρουμε την αντίστροφη συμβολοσειρά ενός διανυσμάτος διαστημάτων, δηλαδή τη διαβάσουμε από το τέλος προς την αρχή, και αυτή η αντίστροφη είναι Ευκλείδια συμβολοσειρά, τότε λέμε ότι έχουμε *αντίστροφη Ευκλείδια συμβολοσειρά*. Για παράδειγμα, Ε(4, 11) = [ 1 0 0 1 0 0 1 0 0 1 0] = (3332). Η αντίστροφη συμβολοσειρά του διανύσματος διαστημάτων είναι η (2333) η οποία είναι Ευκλείδια συμβολειρά, άρα η αρχική είναι αντίστροφη Ευκλείδια συμβολοσειρά.

## Απόσταση Μεταξύ Ρυθμών

Πόσο διαφορετικοί είναι δύο ρυθμοί; Αν θεωρήσουμε τους ρυθμούς ως δυαδικές σειρές, τότε μία μετρική της απόστασης μεταξύ δύο δυαδικών σειρών ίδιου μήκους είναι ο αριθμός των θέσεων όπου τα αντίστοιχα ψηφία των δύο σειρών διαφέρουν. Αυτό ονομάζεται *απόσταση Hamming* (hamming distance). Αν `s1` και `s2` είναι δύο δυαδικές συμβολοσειρές, η απόσταση Hamming μεταξύ τους υπολογίζεται με την ακόλουθη συνάρτηση Python:

```python
def hamming_distance(s1, s2):
    if len(s1) != len(s2):
        raise ValueError("Undefined for sequences of unequal length")
    return sum(bool(ord(ch1) - ord(ch2)) for ch1, ch2 in zip(s1, s2))
```

Για παράδειγμα, ο ρυθμός E(4, 9) = [ 1 0 1 0 1 0 1 0 0 ] απέχει κατά ένα από τον ρυθμό E(5, 9) = [ 1 0 1 0 1 0 1 0 1 ] και κατά τρία από τον ρυθμό E(7, 9) = [ 1 0 1 1 1 0 1 1 1 ].

Πάντως έχετε υπόψη σας ότι η απόσταση Hamming δεν είναι ο καταλληλότερος τρόπος να μετρήσουμε την ομοιότητα των ρυθμών. Υπάρχουν καλύτερες μετρικές, για την εργασία όμως θα περιοριστούμε στην απόσταση Hamming, που εξάλλου είναι γνωστή μετρική με πολύ ευρύ πεδίο εφαρμογών.

## Απαιτήσεις Προγράμματος

Σκοπός της εργασίας είναι η συγγραφή προγράμματος με το οποίο ο χρήστης θα μπορεί να εργάζεται με Ευκλείδιους ρυθμούς.

Κάθε φοιτητής θα εργαστεί στο προσωπικό του αποθετήριο στο GitHub. Για να αξιολογηθεί μια εργασία θα πρέπει να πληροί τις παρακάτω προϋποθέσεις:

1. Όλη η εργασία θα πρέπει να βρίσκεται σε έναν κατάλογο `assignment-2016-3` μέσα στο αποθετήριο του φοιτητή.
2. Το πρόγραμμα θα πρέπει να έχει όνομα `musical_rythms.py`.
3. Εννοείται ότι δεν επιτρέπεται η χρήση έτοιμων βιβλιοθηκών γράφων ή τυχόν έτοιμων υλοποιήσεων των αλγορίθμων, ή τμημάτων αυτών.
4. Το πρόγραμμα θα διαβάζει το λεξικό ρυθμών που βρίσκεται στο αρχείο [musical_rythms.json](musical_rythms.json), το οποίο θα είναι αποθηκευμένο στον ίδιο κατάλογο με τον κατάλογο του προγράμματος. 
5. Το πρόγραμμα θα μπορεί να καλείται ως εξής:
```
musical_rythms.py [-s SLOTS] [-p PULSES] [-r RECOGNIZE] [-l LIST_RYTHMS]
```

Δεν χρειάζεται να ασχοληθείτε με περιπτώσεις όπου ο χρήστης δίνει λάθος είσοδο, για παράδειγμα, δεν χρειάζεται να εξετάσετε τι  θα γίνει αν δώσει μόνο την παράμετρο `-p PULSES` χωρίς την `-s SLOTS`, ή αν δώσει ταυτόχρονα αυτές και την `-l LIST_RYTHMS`. Όπως λέμε, garbage in, garbage out. Υποθέστε ότι ο χρήστης ξέρει να χρησιμοποιεί σωστά το πρόγραμμά σας.

### Δημιουργία Ρυθμού

Αν δίνονται οι παράμετροι `-s SLOTS` και `-p PULSES`, τότε τα `SLOTS` και `PULSES` θα είναι ακέραιοι. Το πρόγραμμα θα υπολογίζει το ρυθμό που αντιστοιχεί στις παραμέτρους αυτούς, όπου `PULSES` είναι ο αριθμός των χτυπημάτων και `SLOTS` είναι το μήκος του ρυθμού. Θα τον αναζητά στο λεξικό των γνωστών ρυθμών. Αν τον βρει εκεί, θα εκτυπώνει τα στοιχεία που βρίσκει για τον ρυθμό. Αν όχι, θα τυπώνει απλώς τον ρυθμό. Στην επόμενη γραμμή, αν ο ρυθμός αντιστοιχεί σε Ευκλείδια συμβολοσειρά ή σε αντίστροφη Ευκλείδια συμβολοσειρά θα εκτυπώνει κατάλληλο μήνυμα. Προσοχή, *η μορφή εξόδου θα πρέπει να είναι ακριβώς αυτή που περιγράφεται στη συνέχεια*.

Παραδείγματα εκτέλεσης:
```
python musical_rythms.py -s 12 -p 6
E(6,12) = [101010101010] = (222222)
```

```
python musical_rythms.py -s 12 -p 7
E(7,12) = [101101011010] = (2122122) It is a common West African bell pattern. For example, it is used in the Mpre rhythm of the Ashanti people of Ghana. Started on the seventh (last) onset, it is a Yoruba bell pattern of Nigeria, a Babenzele pattern of Central Africa, and a Mende pattern of Sierra Leone.
```

```
python musical_rythms.py -s 16 -p 5
E(5,16) = [1001001001001000] = (33334) It is the Bossa-Nova rhythm necklace of Brazil. The actual Bossa-Nova rhythm usually starts on the third onset as follows: [1001001000100100]. However, other starting places are also documented in world music practices, such as [1001001001000100].
It is a Euclidean string.
```

```
python musical_rythms.py -s 9 -p 5
E(5,9) = [101010101] = (22221) It is a popular Arabic rhythm called Agsag-Samai. Started on the second onset, it is a drum pattern used by the Venda in South Africa, as well as a Rumanian folk-dance rhythm. It is also the rhythmic pattern of the Sigaktistos rhythm of Greece, and the Samai aktsak rhythm of Turkey. Started on the third onset, it is the rhythmic pattern of the Nawahiid rhythm of Turkey.
It is a reverse Euclidean string.
```

Όπως βλέπετε, θα πρέπει να εμφανίζεται πρώτα ο ρυθμός στη μορφή E(k, n), στη συνέχεια ως δυαδική συμβολειρά μέσα σε αγκύλες, στη συνέχεια ως διάνυσμα διαστημάτων μέσα παρενθέσεις, και στη συνέχεια θα ακολουθεί η περιγραφή από το λεξικό των ρυθμών, αν βρεθεί εκεί. Από κάτω θα εμφανίζεται μήνυμα αν είναι Ευκλείδια ή αντίστροφη Ευκλείδια συμβολοσειρά.

### Αναγνώριση Ρυθμού

Αν δίνεται η παράμετρος `-r RECOGNIZE` τότε το `RECOGNIZE` θα είναι ένας ρυθμός σε δυαδική μορφή και το πρόγραμμα θα πρέπει να τον αναγνωρίσει, αν είναι Ευκλείδιος, και να τυπώσει ό,τι πληροφορίες έχει γι΄ αυτόν. Αν δεν είναι, θα τυπώνει κατάλληλο μήνυμα.

Παραδείγματα εκτέλεσης:
```
python musical_rythms.py -r 101101011010
E(7,12) = [101101011010] = (2122122) It is a common West African bell pattern. For example, it is used in the Mpre rhythm of the Ashanti people of Ghana. Started on the seventh (last) onset, it is a Yoruba bell pattern of Nigeria, a Babenzele pattern of Central Africa, and a Mende pattern of Sierra Leone.
```

```
python musical_rythms.py -r 10010010010
E(4,11) = [10010010010] = (3332) It is the metric pattern used by Frank Zappa in his piece titled Outside Now.
It is a reverse Euclidean string.
```

```
python musical_rythms.py -r 10010010011
Not a Euclidean rythm.
```

### Εμφάνιση Παρόμοιων Ρυθμών

Αν δίνεται η παράμετρος `-l LIST_RYTHMS` (`-l` είναι το αγγλικό El), τότε η παράμετρος `LIST_RYTHMS` θα είναι ένας ρυθμός σε δυαδική μορφή και το πρόγραμμα θα εμφανίζει όλους τους ρυθμούς με το μήκος του ρυθμού αυτού, ταξινομημένους κατά αύξουσα απόσταση Hamming και αύξοντα αριθμό παλμών. 

Παράδειγμα εκτέλεσης:

```
python musical_rythms.py -l 101010100
Distance = 0
E(4,9) = [101010100] = (2223) It is the Aksak rhythm of Turkey. It is also the metric pattern used by Dave Brubeck in his piece Rondo a la Turk.
It is a Euclidean string.
Distance = 1
E(5,9) = [101010101] = (22221) It is a popular Arabic rhythm called Agsag-Samai. Started on the second onset, it is a drum pattern used by the Venda in South Africa, as well as a Rumanian folk-dance rhythm. It is also the rhythmic pattern of the Sigaktistos rhythm of Greece, and the Samai aktsak rhythm of Turkey. Started on the third onset, it is the rhythmic pattern of the Nawahiid rhythm of Turkey.
It is a reverse Euclidean string.
Distance = 2
E(2,9) = [100010000] = (45)
It is a Euclidean string.
Distance = 3
E(1,9) = [100000000] = (9)
Distance = 3
E(3,9) = [100100100] = (333)
Distance = 3
E(7,9) = [101110111] = (2112111) It is the Bazaragana rhythmic pattern of Greece.
It is a reverse Euclidean string.
Distance = 4
E(6,9) = [101101101] = (212121)
Distance = 4
E(8,9) = [101111111] = (21111111)
It is a reverse Euclidean string.
```

Άλλο παράδειγμα:

```
python musical_rythms.py -l 1001001001000
Distance = 0
E(4,13) = [1001001001000] = (3334)
It is a Euclidean string.
Distance = 2
E(2,13) = [1000001000000] = (67)
It is a Euclidean string.
Distance = 3
E(1,13) = [1000000000000] = (13)
Distance = 5
E(3,13) = [1000100010000] = (445)
It is a Euclidean string.
Distance = 5
E(5,13) = [1001010010100] = (32323) It is a rhythm from the FYROM which is also played by starting it on the fourth onset as follows: [1010010010100].
Distance = 5
E(9,13) = [1011011011011] = (212121211)
It is a reverse Euclidean string.
Distance = 6
E(6,13) = [1010101010100] = (222223) It is the rhythm of the dance Mama Cone pita from the FYROM. Started on the third onset, it is the rhythm of the dance Postupano Oro from the FYROM, as well as the Krivo Plovdivsko Horo of Bulgaria.
It is a Euclidean string.
Distance = 7
E(7,13) = [1010101010101] = (2222221)
It is a reverse Euclidean string.
Distance = 7
E(11,13) = [1011111011111] = (21111211111)
It is a reverse Euclidean string.
Distance = 8
E(8,13) = [1011010110101] = (21221221)
Distance = 8
E(10,13) = [1011101110111] = (2112112111)
It is a reverse Euclidean string.
Distance = 8
E(12,13) = [1011111111111] = (211111111111)
It is a reverse Euclidean string.
```


## Απαιτήσεις Αλγορίθμου

Οι ρυθμοί μπορούν να κατασκευαστούν και με τη χρήση αλγόριθμου που κάνει διαδοχικές διαιρέσεις (ακολουθώντας περίπου τη λογική του αλγορίθμου του Ευκλείδη). Ο αλγόριθμος αυτός ονομάζεται αλγόριθμος του Björklund, από το όνομα του ερευνητή που παρατήρησε τα μοτίβα αυτά σε πειράματα με νετρόνια (Spallation Neutron Source).

*Δεν επιτρέπεται να χρησιμοποιήσετε τον αλγόριθμο του Björklund για την επίλυση της εργασίας. Θα πρέπει να αναπτύξετε τη λύση βασισμένοι σε λίστες, όπως περιγράφεται στην εκφώνηση*.

## Επαλήθευση Λύσεων

Για να μπορέσετε να επαληθεύσετε τα αποτελέσματά σας, μπορείτε να δείτε τους Ευκλείδιους ρυθμούς που περιγράφονται στις πρώτες δύο αναφορές που εμφανίζονται στο τέλος του παρόντος.

Καλή Επιτυχία!

# Περισσότερες Πληροφορίες

 * G. T. Toussaint, "The Euclidean algorithm generates traditional musical rhythms", in proceedings of BRIDGES: Mathematical Connections in Art, Music, and Science, Banff, Alberta, Canada, July 31 to August 3, 2005, pp. 47–56 ([http://cgm.cs.mcgill.ca/~godfried/publications/banff.pdf](http://cgm.cs.mcgill.ca/~godfried/publications/banff.pdf)).

* Erik D. Demaine, Francisco Gomez-Martin, Henk Meijer, David Rappaport, Perouz Taslakian, Godfried T. Toussaint, Terry Winograd, and David R. Wood, "The Distance Geometry of Music", Computational Geometry: Theory and Applications, volume 42, number 5, July 2009, pp. 429–454. Special issue of selected papers from the 17th Canadian Conference on Computational Geometry, 2005 ([http://erikdemaine.org/papers/DeepRhythms_CGTA/paper.pdf](http://erikdemaine.org/papers/DeepRhythms_CGTA/paper.pdf)).

* E. Bjorklund, "The Theory of Rep-Rate Pattern Generation in the SNS Timing System", SNS-NOTE-CNTRL-99, 1999 ([https://ics-web.sns.ornl.gov/timing/Rep-Rate%20Tech%20Note.pdf](https://ics-web.sns.ornl.gov/timing/Rep-Rate%20Tech%20Note.pdf)).
