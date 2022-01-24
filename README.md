# Exams-scheduling-with-AI
A java app to calclulate the optimum scheduling of classes in order for all students participating in Final examinations to have max time to study.


Προϋποθέσεις

Eχω δημιουργήσει την εφαρμογή Exams_Scheduling.jar 

Για να τρέξει σωστά θα πρέπει να αντιγράψετε το Jar file μαζί με το αρχείο Excel στην επιφάνεια εργασίας σας.
Επίσης θα πρέπει να υπάρχει εγκατεστημένο το «Java Runtime Environment» 


Ανάλυση σχεδιασμού με βάση τις προδιαγραφές

Το πρόγραμμα προσπαθεί να βρει την βέλτιστη λύση δηλαδή αυτή με  τους λιγότερους δυνατούς φοιτητές με κοντινές ημερομηνίες εξέτασης και επίσης αυτή με τον μεγαλύτερο βαθμό απόδοσης ατόμου. O αλγόριθμος που χρησιμοποιείται είναι μιας μορφής Επίλυση CSP (δές στο τέλος προτάσεις βελτίωσης)

By default περιορισμοί & προϋποθέσεις (Hard-Soft constraints):

-	Καμία ημερομηνία εξέτασης δεν είναι στην ίδια μέρα με άλλη
-	Όλες οι ημερομηνίες εξέτασης είναι σε διάστημα 28 ημέρων (εξεταστική περίοδος Χ)
-	Όλοι οι φοιτητές ελέγχονται για όλες τις ενότητες που έχουν δηλώσει - η μονή πηγή που υπάρχει είναι το excel, και δεν γνωρίζουμε αν θα εξεταστούν σε όλες τι ενότητες.
-	Το excel μπορεί να πάρει και διαφορετικά δεδομένα αρκεί να τηρηθεί η ίδια διάταξη
-	Έχουν μπει συγκεκριμένες ενότητες τα Σαββατοκύριακα καθώς αυτές οι τιμές είναι οι βέλτιστες. Θα μπορούσε αυτό να γίνει και αυτομάτως, αλλά με μεγαλύτερη πολυπλοκότητα
-	Οι υπόλοιπες ημερομηνίες καλύπτονται αυτομάτως. :

Οι συντελεστές ποιότητας - απόδοσης και επιλογής του βέλτιστου προγράμματος είναι 2.

1)	Μέση απόδοση ατόμων
Είναι η μέση βαθμολογία όλων των φοιτητών σε σύγκριση με ένα συγκεκριμένο στιγμιότυπο του προγράμματος. Οι ελάχιστη αποδέκτη τιμή ορίζεται από εμάς , στο πρόγραμμα είναι πάντα > 6, και προέκυψε μετα από δοκιμές έτι ώστε να υπάρχει μια καλή απόδοση χωρίς να επιβαρύνει υπερβολικά τον αλγόριθμο.  Η βαθμολόγηση(πώς προκύπτει η απόδοση) γίνεται με συγκεκριμένα κριτήρια που θα αναλύσω παρακάτω.

2)	Άτομα με πρόβλημα(κοντινές ημερομηνίες εξέτασης) . 
Οι τιμές και περιορισμοί θα οριστούν παρακάτω. Ο χρήστης επιλεγεί τον Στόχο προβληματικών ατόμων. Εάν το πρόγραμμα εκτελέσει συγκεκριμένο αριθμό loops ανεβάζει τον στόχο κατά +1 έτσι ώστε να μην καθυστερεί υπερβολικά η εύρεση λύσης σε περίπτωση χαμηλών στοχων.
Χαμηλός στόχος θεωρείτε ο στόχος για κάτω από 100 προβληματικά άτομα. (από σύνολο 2042). Δηλαδή ποσοστό μικρότερο του 5%.  Δεν μπορούμε να φτάσουμε στο 0 λόγω υποχρέωσης εξεταστικών τα Σαββατοκύριακα , (π.χ. ο Φοιτητής  με ID 17 έχει πάντα πρόβλημα με την υπάρχουσα δομη)

Κριτήριο τερματισμού
Τα κριτήρια τερματισμού είναι οι τιμές που είναι μικρότερες από τους στόχους προβληματικών ατόμων και μεγαλύτερες από την μέση απόδοση ατόμων 
 
 
Παρακάτω μία ενδεικτική λύση. 
Ο αρχικός στόχος ήταν 70 προβληματικά άτομα άλλα o αυτοματισμός αύξησε τον στόχο (+1 ανά 50 loops) για να μην καθυστερήσει η εύρεση λύσης.
 

Οι σπουδαστές με κοντινές ημερομηνίες , και το ID του καθενός                       Μέση απόδοση ατόμων 

Άλλη επίλυση παρακάτω.  Οι μόνες σταθερές ημερομηνίες εξέτασης είναι στα Σαββατοκύριακα,
 
 
Βασικός αλγόριθμος - περιορισμοί και βαθμολογίες

Οι ενότητες που υπάρχουν στο excel και χρησιμοποιήθηκαν είναι οι:
PLI12("ΠΛΗ12"),
PLI11("ΠΛΗ11"),
PLI10("ΠΛΗ10"),
PLI20("ΠΛΗ20"),
PLI21("ΠΛΗ21"),
PLI22("ΠΛΗ22"),
PLI30("ΠΛΗ30"),
PLI24("ΠΛΗ24"),
PLI31("ΠΛΗ31"),
PLI23("ΠΛΗ23"),
PLI35("ΠΛΗ35"),
PLI36("ΠΛΗ36"),
PLI37("ΠΛΗ37"),
PLI40("ΠΛΗ40"),
PLI42("ΠΛΗ42"),
PLI47("ΠΛΗ47"),
PLI32("ΠΛΗ32"),
PLIPS_I("ΠΛΗΨΙ"),
PLIPS_II("ΠΛΗΨΙΙ"),


Ο Βασικός αλγόριθμος τρέχει τυχαίες τιμές του προγράμματος αλλάζοντας όλες τις υπόλοιπες ημερομηνίες με τυχαία εξέταση (εκτός από τα Σαββατοκύριακα & τις ενότητες σε αυτά). 

Βασικός αλγόριθμος σε μια εποχή (1 loop) ;

Παίρνει τα στοιχεία από το excel .
Δημιουργεί τυχαίο πρόγραμμα εξετάσεων εκτελεί ελέγχους και βάζει βαθμολογίιες (μέση απόδοση Ατόμου) σε κάθε φοιτητή ανάλογα με τα μαθήματα που έχει. 

Η συνάρτηση distance factor ελέγχει την απόσταση που έχει η κάθε ενότητα από την άλλη (για κάθε φοιτητή)
 

Εάν ο φοιτητής έχει 1 ενότητα
παίρνει βαθμολογία : 6

Εάν ο φοιτητής έχει 2 ενότητες και η απόσταση μεταξύ των 2 ενοτήτων είναι :
-	Μεγαλύτερη από 13 μέρες  παίρνει βαθμολογία : 14
-	Εάν η απόσταση είναι από 7 - 12 ημέρες  παίρνει βαθμολογία : όση και η απόσταση
-	Εάν η απόσταση είναι από 4 – 6 ημέρες παίρνει βαθμολογία : - 3
-	Εάν η απόσταση είναι από 2 – 4 ημέρες παίρνει βαθμολογία : - 4 και χαρακτηρίζεται ως προβληματικό
-	Εάν η απόσταση είναι < 2 ημέρες παίρνει βαθμολογία : - 5 και χαρακτηρίζεται ως προβληματικό

Εάν ο φοιτητής έχει 3 ενότητες και η απόσταση μεταξύ  2 ενοτήτων είναι :
-	Εάν η απόσταση είναι από 6+ ημέρες  παίρνει βαθμολογία : όση και η μέση απόσταση
-	Εάν η απόσταση είναι από 4 – 6 ημέρες παίρνει βαθμολογία : - 2
-	Εάν η απόσταση είναι από 2 – 4 ημέρες παίρνει βαθμολογία : - 3 και χαρακτηρίζεται ως προβληματικό
-	Εάν η απόσταση είναι < 2 ημέρες παίρνει βαθμολογία : - 5 και χαρακτηρίζεται ως προβληματικό


Εάν ο φοιτητής έχει 4 ενότητες και η απόσταση μεταξύ  2 ενοτήτων είναι :
-	Εάν η απόσταση είναι από 6+ ημέρες  παίρνει βαθμολογία : όση και η μέση απόσταση
-	Εάν η απόσταση είναι από 3 – 5 ημέρες παίρνει βαθμολογία : - 2 
-	Εάν η απόσταση είναι < 2 ημέρες παίρνει βαθμολογία : - 5 και χαρακτηρίζεται ως προβληματικό

Εάν ο φοιτητής έχει 5 ενότητες και η απόσταση μεταξύ  2 ενοτήτων είναι :
-	Εάν η απόσταση είναι από 5+ ημέρες  παίρνει βαθμολογία : όση και η μέση απόσταση
-	Εάν η απόσταση είναι από 3 – 4 ημέρες παίρνει βαθμολογία : - 1 
-	Εάν η απόσταση είναι < 2 ημέρες παίρνει βαθμολογία : - 1 και χαρακτηρίζεται ως προβληματικό


Μελλοντικές αναβαθμίσεις User interface
-	Επιλογή ενοτήτων απευθείας από τον χρήστη , το πρόγραμμα εκτελείς τις υπόλοιπες τιμές
-	Επιλογή μέσης απόδοσης από τον χρήστη 
-	Όταν βρίσκει προβληματικό άτομο θα μπορούσε να αλλάζει την ημερομηνία εξέτασης +2 ημέρες και να ξανατρέχει τους ελέγχους για όλο τον πληθυσμό
-	Θα μπορούσαν να επιλέγονται υποχρεωτικά και οι Τετάρτες ώς πιθανές ημερομηνίες εξετάσεων προτού συμπληρωθεί το υπόλοιπο πρόγραμμα.
-	Δημιουργία επιλογής excel από συγκεκριμένο σημείο.

Μελλοντικές επεκτάσεις αλγορίθμου.

1)	Γενετικοί
-	Εφαρμογή γενετικού αλγόριθμου . 
-	Φαινότυπος θα είναι το πρόγραμμα εξετάσεων (28 τιμές)
-	Αφού τρέξουμε π.χ. 1000 τιμές θα ορίσουμε τον αρχικό πληθυσμό
-	Εφαρμογή OX διασταύρωσης  
-	Πολύ μικρή τιμή μετάλλαξης

2)	Επίλυση CSP (Πλήρης εφαρμογή – βελτίωση του αλγορίθμου μου)
-	Τυχαία αρχική κατάσταση (έγινε ήδη)
-	Επανέλαβε για την τρέχουσα κατάσταση:
Γειτονικές καταστάσεις: προκύπτουν από την τρέχουσα αλλάζοντας την τιμή μιας μόνο μεταβλητής.
( Αυτόματη διόρθωση ημερομηνιών με προβληματικές ημερομηνίες κατά την εκτέλεση του loop. Σε περίπτωση προβληματικού μαθητή, μετακίνηση της ημερομηνίας, στην επόμενη κενή θέση)
-	Εάν η αλλαγή αυτή βελτιώνει το κόστος γίνεται αποδεκτή (νέα τρέχουσα κατάσταση). (έγινε ήδη)
-	Εάν το κόστος γίνει μηδέν τερματίζουμε. (έγινε ήδη απλά με όριο)
-	Ωσότου δεν είναι δυνατή αλλαγή τιμής μεταβλητής που να μειώνει το κόστος
(τοπικό ελάχιστο, επανεκκίνηση από νέα τυχαία αρχική κατάσταση) (έγινε ήδη)



