# Série N°1 : Premiers pas, types et conditions

> **Durée TD :** 40 min | **Durée TP :** 80 min  
> **Chapitre couvert :** Sections 1 à 3 (Premiers pas, variables et types, opérateurs et conditions)  
> **Outils :** DartPad ([dartpad.dev](https://dartpad.dev)) pour le TD ; Dart SDK + VS Code (`dart run`) pour le TP.

---

## 🎯 Objectifs
À la fin de cette série, vous saurez :
- Écrire et exécuter un programme Dart.
- Choisir le bon **type** de donnée.
- Utiliser les **opérateurs**.
- Lire une saisie clavier et prendre des décisions avec `if`, `switch` et l'opérateur ternaire.

---

## 📝 Partie A -- TD (Papier / Réponses écrites) — *40 min*

### Exercice 1 : Prédire les résultats (*10 min*)
*Donnez le résultat affiché par chaque instruction (écrivez `erreur` si le code est refusé).*

| N° | Instruction(s) | Votre réponse |
| :---: | :--- | :--- |
| **1** | `print(10 / 4);` |2.5 | 
| **2** | `print(10 ~/ 4);` | 2|
| **3** | `print(10 % 4);` |2|
| **4** | `print('Dart' + ' ' + 'MST');` | Dart MST |
| **5** | `print('2' + '3');` |23 |
| **6** | `print(2 + 3 * 4 - 1);` |13|
| **7** | `int x = 5; x += 3; x *= 2; print(x);` |16|
| **8** | `print(5 > 3 && 2 > 4);` | False |
| **9** | `print(!(5 == 5) \|\| 3 < 4);` | True |
| **10**| `String? s; print(s ?? 'vide');` | vide |

---

### Exercice 2 : Quel type pour quelle valeur ? (*7 min*)
*Indiquez le type Dart le plus adapté (`int`, `double`, `String`, `bool`) pour chaque valeur ou expression.*

| Valeur / Expression | Votre réponse | Valeur / Expression | Votre réponse |
| :--- | :--- | :--- | :--- |
| `42` | int | `'42'` |string |
| `3.14` | double | `10 / 2` | double |
| `true` | bool | `10 ~/ 2` | int |
| `"Settat"` | string | `7 > 3` | bool|

---

### Exercice 3 : Chasse aux erreurs (*8 min*)
*Le programme suivant contient **6 erreurs**. Repérez-les, indiquez la ligne, le type d'erreur (syntaxe, type, logique) et la correction.*

```dart
1: void main() {
2:   int age = 'vingt';
3:   double prix = 12,5;
4:   String nom = 'Sara";
5:   const tva = 0.2
6:   tva = 0.25;
7:   print('Age : ' + age);
8: }
```

#### Vos réponses :

| Ligne | Type d'erreur | Problème identifié | Correction proposée |
| :---: | :--- | :--- | :--- |
| **2** | Type | 'ving'est un texte pas un entier | `int age = 20;` |
| **3** |syntaxe | point décimal, pas virgule |double prix = 12.5; |
| **4** | syntaxe |mêmes guillemets au début et à la fin|String nom = 'Sara';|
| **5** | syntaxe | point-virgule manquant | const tva = 0.2; |
| **6** | logique |on ne peut pas modifier une constante const | supprimer tva=0.25; |
| **7** | type | on ne peut pas additionner une String et un int| print('Age : $age'); |

---

### Exercice 4 : Conditions (*15 min*)

#### a) Trace de code
*Donnez le résultat des appels suivants selon la fonction ci-dessous :*

```dart
String mention(double m) {
  if (m >= 16) {
    return 'Très bien';
  } else if (m >= 14) {
    return 'Bien';
  } else if (m >= 12) {
    return 'Assez bien';
  } else if (m >= 10) {
    return 'Passable';
  } else {
    return 'Insuffisant';
  }
}
```

| Appel | `mention(17)` | `mention(13.99)` | `mention(10)` | `mention(9.5)` |
| :--- | :---: | :---: | :---: | :---: |
| **Résultat** | Trés bien| Assez bien| Passable| Insuffisant |

#### b) Expressions booléennes
*Écrivez en Dart la condition qui vaut `true` lorsque :*

1. `a` est compris entre 10 et 20 (bornes incluses) :
```dart
a >= 10 && a <= 20
```

2. `n` est un entier **pair et strictement positif** :
```dart
n > 0 && n % 2 == 0
```

3. `annee` est une année **bissextile** (divisible par 4 mais pas par 100, ou divisible par 400) :
```dart
(annee % 4 == 0 && annee % 100 != 0) || annee % 400 == 0
```

#### c) Réécriture
*Réécrivez la structure `if/else` suivante avec l'opérateur ternaire :*

```dart
String statut;
if (age >= 18) {
  statut = 'majeur';
} else {
  statut = 'mineur';
}
```

**Votre réécriture :**
```dart
String statut = age >= 18 ? 'majeur' : 'mineur';
```

---

## 💻 Partie B -- TP (Sur machine) — *80 min*

> 💡 **Consigne :** Créez un dossier `tp1` et enregistrez chaque exercice dans un fichier séparé (`tp1_ex1.dart`, etc.). Exécution : `dart run tp1_ex1.dart`.  
> *Note : Les exercices TP3 à TP5 utilisent `stdin` (non compatibles avec DartPad).*

---

### TP 1 : Environnement et premier programme (*10 min*)

1. **Version installée :**
   ```bash
   # Dart SDK version: 3.13.7 (stable) (Thu Oct 22 14:28:57 2026 -0700) on "windows_x64"
   ```

2. **Code de la carte de visite (`tp1_ex1.dart`) :**
```dart
// void main() {
  String nom = 'SalmaZAIM';
  String filiere = 'SICRAT';
  String ville = 'CASABLANCA';

  print('=== Carte de visite ===');
  print('Nom     : $nom');
  print('Filière : $filiere');
  print('Ville   : $ville');
}
```

3. **Remarque sur l'erreur de syntaxe testée :**
   * J’ai retiré le ; à la fin d’une instruction print pour provoquer une erreur dans mon projet. Le compilateur a signalé une erreur de syntaxe et a bloqué l’exécution. Une fois le (;) remis, le programme a fonctionné correctement.

---

### TP 2 : Calcul d'une facture (*15 min*)

- **Code source (`tp1_ex2.dart`) :**
```dart
 void main() {
  const double tauxTva = 0.20;
  double prixHT = 250;
  double montantTva = prixHT * tauxTva;
  double prixTTC = prixHT + montantTva;

  print('Prix HT : ${prixHT.toStringAsFixed(2)} DH');
  print('TVA (20%): ${montantTva.toStringAsFixed(2)} DH');
  print('Prix TTC : ${prixTTC.toStringAsFixed(2)} DH');
}
```

- **Question :** Pourquoi utiliser `const` plutôt que `var` pour la TVA ?
  > **Réponse :** On utilise `const` pour le taux de TVA parce que c'est une valeur fixe qu'on veut garder telle quelle dans tout le programme. `const` indique que cette valeur est constante et ne peut pas être modifiée, alors qu'avec `var` on pourrait lui réaffecter une autre valeur.
---

### TP 3 : Moyenne et mention (*15 min*)

- **Code source (`tp1_ex3.dart`) :**
```dart
import 'dart:io';

void main() {
  double moyenne;
  stdout.write('Votre Nom : ');
  String? nom = stdin.readLineSync();
  stdout.write('Votre Note 1 :');
  double note1 = double.parse(stdin.readLineSync()!);

  stdout.write('Votre Note 2 :');
  double note2 = double.parse(stdin.readLineSync()!);

  moyenne = (note1 + note2) / 2;
  String mention(double moyenne) {
    if (moyenne >= 16) {
      return 'Très bien';
    } else if (moyenne >= 14) {
      return 'Bien';
    } else if (moyenne >= 12) {
      return 'Assez bien';
    } else if (moyenne >= 10) {
      return 'Passable';
    } else {
      return 'Insuffisant';
    }
  }

  print('$nom : ${moyenne.toStringAsFixed(2)} (${mention(moyenne)})');
}

```

---

### TP 4 : Calculatrice à deux opérandes (*20 min*)

- **Code source (`tp1_ex4.dart`) :**
```dart
import 'dart:io';

void main() {
  stdout.write('entrer a  :');
  double a = double.parse(stdin.readLineSync()!);

  stdout.write('entrer b  :');
  double b = double.parse(stdin.readLineSync()!);

  stdout.write('Entrez un opérateur (+, -, *, /) : ');
  String operateur = stdin.readLineSync()!;

  switch (operateur) {
    case '+':
      print('Résultat : ${a + b}');
      break;

    case '-':
      print('Résultat : ${a - b}');
      break;

    case '*':
      print('Résultat : ${a * b}');
      break;

    case '/':
      if (b != 0) {
        print('Résultat : ${a / b}');
      } else {
        print('Erreur : division par zéro impossible.');
      }
      break;
    default:
      print('Erreur : opérateur inconnu.');
  }
}

```

- **Bonus : Année bissextile (`tp1_ex4_bonus.dart`) :**
```dart
import 'dart:io';

void main() {
  stdout.write('Année : ');
  int? annee = int.tryParse(stdin.readLineSync() ?? '');

  if (annee == null) {
    print('Erreur : saisie invalide.');
    return;
  }

  // Divisible par 4 mais pas par 100, ou divisible par 400
  bool bissextile = (annee % 4 == 0 && annee % 100 != 0) || annee % 400 == 0;

  if (bissextile) {
    print('$annee est bissextile');
  } else {
    print('$annee n\'est pas bissextile');
  }
}

```

---

### TP 5 : Conversion d'une durée (*20 min*)

- **Code source (`tp1_ex5.dart`) :**
```dart
import 'dart:io';

void main() {
  // lire le nombre de secondes
  stdout.write('Saisir le nombre de secondes : ');
  int n = int.parse(stdin.readLineSync()!);

  int heure = n ~/ 3600;          // calcul des heures
  int minute = (n % 3600) ~/ 60;  // calcul des minutes restantes
  int seconde = n % 60;           // calcul des secondes restantes

  print('$n s = $heure h $minute min $seconde s');
}
```

- **Défi (Gestion des pluriels et unités nulles) :**
```dart
import 'dart:io';

void main() {
  stdout.write('Saisir le nombre de secondes : ');
  int n = int.parse(stdin.readLineSync()!);

  int heure = n ~/ 3600;
  int minute = (n % 3600) ~/ 60;
  int seconde = n % 60;

  String resultat = '';

  // ajouter les heures seulement si elles sont supérieures à zéro
  if (heure > 0) {
    resultat += '$heure ${heure == 1 ? 'heure' : 'heures'} ';
  }

  // ajouter les minutes seulement si elles sont supérieures à zéro
  if (minute > 0) {
    resultat += '$minute ${minute == 1 ? 'minute' : 'minutes'} ';
  }

  // ajouter les secondes si elles sont supérieures à zéro, ou si la durée vaut 0
  if (seconde > 0 || n == 0) {
    resultat += '$seconde ${seconde <= 1 ? 'seconde' : 'secondes'}';
  }

  print('$n s = ${resultat.trim()}');
}

```

---

## 📦 Livrable
Cochez les éléments à remettre :
- [ ] Le présent fichier Markdown complété
- [ ] Les 5 fichiers `.dart` dans le dossier `tp1`
- [ ] Une capture d'écran d'exécution du **TP3**
