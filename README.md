<!DOCTYPE html>
<html>
<head>
  <title>Jeu de Pierre, Feuille, Ciseaux</title>
</head>
<body>
  <h1>Jeu de Pierre, Feuille, Ciseaux</h1>
  <p>Choisissez votre coup :</p>
  <button id="pierre">Pierre</button>
  <button id="feuille">Feuille</button>
  <button id="ciseaux">Ciseaux</button>
  <div id="resultat"></div>

  <script>
    // Sélectionner les boutons
    const pierreButton = document.getElementById("pierre");
    const feuilleButton = document.getElementById("feuille");
    const ciseauxButton = document.getElementById("ciseaux");

    // Ajouter des gestionnaires d'événements pour les clics sur les boutons
    pierreButton.addEventListener("click", function() {
      jouer("pierre");
    });

    feuilleButton.addEventListener("click", function() {
      jouer("feuille");
    });

    ciseauxButton.addEventListener("click", function() {
      jouer("ciseaux");
    });

    // Fonction pour jouer au jeu
    function jouer(choixJoueur) {
      // Générer un coup aléatoire pour l'ordinateur
      const choixOrdinateur = genererCoupAleatoire();

      // Déterminer le résultat du jeu
      const resultat = determinerResultat(choixJoueur, choixOrdinateur);

      // Afficher le résultat
      const resultatDiv = document.getElementById("resultat");
      resultatDiv.innerHTML = `Vous avez choisi ${choixJoueur}. L'ordinateur a choisi ${choixOrdinateur}. ${resultat}`;
    }

    // Fonction pour générer un coup aléatoire pour l'ordinateur
    function genererCoupAleatoire() {
      const coups = ["pierre", "feuille", "ciseaux"];
      const indexAleatoire = Math.floor(Math.random() * coups.length);
      return coups[indexAleatoire];
    }

    // Fonction pour déterminer le résultat du jeu
    function determinerResultat(choixJoueur, choixOrdinateur) {
      if (choixJoueur === choixOrdinateur) {
        return "C'est une égalité !";
      } else if (
        (choixJoueur === "pierre" && choixOrdinateur === "ciseaux") ||
        (choixJoueur === "feuille" && choixOrdinateur === "pierre") ||
        (choixJoueur === "ciseaux" && choixOrdinateur === "feuille")
      ) {
        return "Vous avez gagné !";
      } else {
        return "L'ordinateur a gagné !";
      }
    }
  </script>
</body>
</html>
