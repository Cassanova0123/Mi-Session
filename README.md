# Mi-Session
# Examen-Mi-Session-Prog
Turbo Rival
Mais qu'est ce que Turbo Rival?
Turbo Rivals est un jeu de course dynamique où les joueurs affrontent des adversaires contrôlés par l'intelligence artificielle (IA) sur différents circuits. Les courses sont enrichies par un système d'objets spéciaux qui peuvent être utilisés stratégiquement pendant la course.
Ce répositoire contient la hiérarchie de classe et le code pour le projet Turbo Rival basé sur Unity3d et C#

Hiérachie de classe:

Véhicule(Classe A):
Attributs:
- Vitesse
- Position
- Direction
Méthodes:
- Accélération()
- Ralentissement()
- Tounrer()
- Bosst()
  Classe Player(Hérite de la classe A)
  Atrributs:
  -Score
  Méthodes:
  -Interface()
  IA(Hérite de la classe A)
  Attributs:
  - Niveau de difficulté
  Méthodes:
  - RoadCalcuation()
  - Éviter les obstcales()
    Classe Objet
    Attributs:
  - Durée
  - Type
Méthodes:
  - AppliquerEffet(véhicule)
MissileGuide (Hérite de ObjetSpécial)
Attributs :
Cible
Méthodes :
AppliquerEffet(véhicule)
TacheHuile (Hérite de ObjetSpécial)

Méthodes :
AppliquerEffet(véhicule)
EMP (Hérite de ObjetSpécial)

Méthodes :
AppliquerEffet(véhicule)
Circuit

Attributs :
ListeVéhicules (max 10)
Scoreboard
Obstacles
Méthodes :
AjouterVéhicule(véhicule)
SupprimerVéhicule(véhicule)
MettreAJourScore()

Classe LeaderboardManager (Unity Cloud Leaderboard)
Attribut	   Fonctions
scores	    public setScores(),public getScores()
playerNames	public setPlayerNames(),public getPlayerNames()
  
L'utilisation du patron de conception Singleton pour ce jeu:
L'utilisation de Singleton pourrait servir comme de GameManager pour qu'il n'ait qu'une seule intense dans le code
  
L'utilisation de l'algoritme Minimax est bien ici parce que comme nous sommes dans un jeu de course MiniMax passe en revue toutes les 
possibilités pour un nombre limité d'essais et minimise la perte maximum.Le jeu de courses consomment beaucoup en ressource je trouve qu'évaluer les pertes est un bonne chose pour un projet de type Turbo Rival

Squellette de code 
class Vehicule {
    public float vitesse;
    public Vector3 position;
    public float direction;
    public void Accélération(float increment) {
        vitesse += increment;
    }
    public void Ralentissement(float decrement) {
        vitesse -= decrement;
    }
    public void Tourner(float angle) {
        direction += angle;
    }
    public void Boost() {}
class Player : Vehicule {
    public int score;
    public void Interface() {}
    class IA : Vehicule {}
    public int niveauDifficulté;

    public void RoadCalculation() {}
    public void ÉviterObstacles() {}
    abstract class ObjetSpécial {
    public float durée;
    public string type;

    public abstract void AppliquerEffet(Vehicule véhicule);
}
class MissileGuide : ObjetSpécial {}
    public Vehicule cible;
    public override void AppliquerEffet(Vehicule véhicule) {
     // L'effet du missile
    }
    class TacheHuile : ObjetSpécial {
    public override void AppliquerEffet(Vehicule véhicule) {
        // Logique pour ralentir le véhicule
    }
    class Circuit {
    public List<Vehicule> listeVehicules; // Max 10 véhicules
    public Scoreboard scoreboard;
    public List<Obstacle> obstacles;

    public Circuit() {
        listeVehicules = new List<Vehicule>();
        scoreboard = new Scoreboard();
        obstacles = new List<Obstacle>();
    }

    public void AjouterVehicule(Vehicule véhicule) {
        if (listeVehicules.Count < 10) {
            listeVehicules.Add(véhicule);
        }
    }

    public void SupprimerVehicule(Vehicule véhicule) {
        listeVehicules.Remove(véhicule);
    }

    public void MettreAJourScore() {
    }
    class LeaderboardManager {
    public List<int> scores;
    public List<string> playerNames;

    public void SetScores(List<int> newScores) {
        scores = newScores;
    }

    public List<int> GetScores() {
        return scores;
    }

    public void SetPlayerNames(List<string> newPlayerNames) {
        playerNames = newPlayerNames;
    }

    public List<string> GetPlayerNames() {
        return playerNames;
    }

