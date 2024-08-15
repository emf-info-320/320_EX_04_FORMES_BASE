# Les Formes

## Durée : 45'

## Objectifs
Réactivation des fondamentaux Java : classes et objets.
Mise en pratique de l'héritage.

## Travail à réaliser

Créez un nouveau projet java.

Ajoutez y les classes suivantes :
- Une classe `Carre`
- Une classe `Rectangle`
- Une classe `Disque` 
- Une classe `Triangle` 
- Une classe `Forme`

Chacune de ces classes doit avoir les attributs et les méthodes nécessaires pour calculer sa propre surface.

```mermaid
classDiagram
    note for Forme "La méthode calculSurface() de cette classe doit retourner 'Double.NaN'"
    Forme <|-- Triangle
    Forme <|-- Disque
    Forme <|-- Carre
    Forme <|-- Rectangle
    Application "1" o--> "0..n" Forme : lesFormes
    class Application{
        + MAX_FORME : int = 8
        + Application()
        + genererFormes() void
        + calculerSurfaces() void
        + main(String[] args)$ void
    }
    class Forme{
        - nom : String
        + Forme(String nom) 
        + calculeSurface() double
        + getNom() String
    }
    
    class Triangle{
        - base : int
        - hauteur : int
        + Triangle(String nom, int base, int hauteur)
        + calculeSurface() double
    }

    class Disque{
        - rayon : int
        + Disque(String nom, int rayon)
        + calculeSurface() double
    }

    class Carre{
        - cote : int
        + Carre(String nom, int cote)
        + calculeSurface() double
    }

    class Rectangle{
        - largeur : int
        - longueur : int
        + Rectangle(String nom, int largeur, int longueur)
        + calculeSurface() double
    }

```
Créez ensuite une classe `Application` possédant une méthode `main` respectant les diagrammes de séquences suivants:

### Méthode main(String[] args)
```mermaid
sequenceDiagram
    create participant Application
    main->>Application: <<Creation>>
    main->>+Application: genererFormes()
    Application-->>-main: 
    main->>+Application: calculerSurfaces()
    Application-->>-main: 
```

### Méthode calculerSurfaces()

```mermaid
sequenceDiagram
    create participant double laSurfaceTotale
    Application->>+double laSurfaceTotale: 0.0
    create participant double laSurface
    Application->>+double laSurface: 0.0
    alt lesFormes != null
        loop i < lesFormes.length
            Application ->>+ Application: uneForme = lesFormes[i]
            alt uneForme != null
                Application ->>+ uneForme: calculeSurface()
                uneForme -->>- Application:

                Application ->>+ Application: 'laSurfaceTotale = laSurfaceTotale + laSurface'

                Application ->>+ uneForme: getNom()
                uneForme -->>- Application: 
                Application ->>+ Application: SOUT(type de forme et sa surface)
            end
        end
    end

    Application ->>+ Application: SOUT(laSurfaceTotale)
```

### Méthode genererFormes()

```mermaid
sequenceDiagram
    create participant carre1
    Application->>carre1: cote = 1
    create participant rectangle1
    Application->>rectangle1: largeur=2, longueur=3
    create participant triangle1
    Application->> triangle1 : base=4, hauteur=5
    create participant disque1
    Application->> disque1 : rayon=6
    create participant carre2
    Application->> carre2 : cote=7
    create participant rectangle2
    Application ->> rectangle2 : largeur=8, longueur=9
    create participant triangle2
    Application->> triangle2 : base=10, hauteur=11
    create participant disque2
    Application ->> disque2 : rayon=12

```
## Résultat attendu
> La surface de ce [Carré] qui a [4] côtés est de [1.0]</br>
> La surface de ce [Rectangle] qui a [4] côtés est de [6.0]</br>
> La surface de ce [Triangle] qui a [3] côtés est de [10.0]</br>
> La surface de ce [Disque] qui a [infinité] côtés est de [113.09733552923255]</br>
> La surface de ce [Carré] qui a [4] côtés est de [49.0]</br>
> La surface de ce [Rectangle] qui a [4] côtés est de [72.0]</br>
> La surface de ce [Triangle] qui a [3] côtés est de [55.0]</br>
> La surface de ce [Disque] qui a [infinité] côtés est de [452.3893421169302]</br>
> La surface totale des formes est de 758.4866776461628
