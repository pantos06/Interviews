# Questionnaire C++

1) __Donner une définition d'un système temps réel ?__
Un système temps réel es un system quit doit fournir des résultat corrects dans un délais prédéfinit. Les contraintes de temps de réponse sont la principale caracteristique des systèmes temps réels.

2) __Quels sont vos librairies et outils préférés pour le développement en C++ ?__
- IDE: VSCode
- Build tools: Conan
- Libraries: Boost

3) __Que signifient : Polymorphisme, Encapsulation, Héritage ?__
- __Polymorphisme__ signifie plusieurs formes. Dans l'informatique c'est la capacité d'un object à faire référence à la super-class et ou à la sous-class en fonction du type de référence
- __Encapsulation__ possibilité pour une classe de décider ce qui va/peut être accessible/modifiable de l'extérieur. L'encapsulation est réalisée en C++ par les mot clés suivants:
  - _public_ : accessible et modifiable hors de la classe
  - _protected_: accessible et modifiable uniquement par les sous-classes
  - _privated_: pas accessible ni modifiable de l'extérieur
- __Héritage__ possibilité pour une classe d'étendre et de réutiliser le code d'une autre classe. La classe héritée est appelée "_super-class_", tandis que la class dérivée est appelée "_sous-class_"
```c++ {.line-numbers}
class Animal {
protected: //<- Tout ce qui suit ne peut être accessible que dans cette classe et les sous-classes de Animal
    std::string nom; // <-- Accessible uniquement ici et dans les sous-classes
public: //<- Tout ce qui suit ne peut être accessible
    virtual void bruit() {   // <-- La méthode bruit peut être accessible de l'extérieur et peut être redefinie par les sous class
        std::cout << "L'animal fait un bruit" << std::endl;
    }
};
class Chien: public Animal { // <-- polymorphisme: Chien hérite de la class Animal
  void bruit() {
      std::cout << "Le chien fait: bow wow" << std::endl;
  }
};
```

4) __Quelle définition donneriez-vous aux termes suivants : classe abstraite, méthode virtuelle, méthode virtuelle pure, surcharge ? Comment les implémenter en C++ ?__
- __Classe abstraite__ classe qui ne peut pas être instanciée directement, mais qui sert de modèle pour les sous-classes qui en héritent. Elle permet de créer une hiérachie de classe qui partage des caractéristiques communes, tout en fournissant une structure de base pour les sous-classes qui doivent  implémenter leur propre fonctionalité spécifique.
- __Méthode virtuelle__ méthode définie dans une classe de base qui peut être redéfinie (ou surchargée) par une sous-classe.
- __Méthode pure virtuelle__ méthode défini dans une classe abstraite qui n'a pas d'implémentation dans cette classe
- __Surcharge__ La surcharge de méthode est réalisée en définissant plusieurs méthodes avec le même ___nom___ dans une classe, mais les ___signatures___ différentes.
Exemple:
```c++ {.line-numbers}
class ExempleDeClassAbstraite { // <- doit avoir au moin une méthode pure virtuelle
public:
    virtual void methode_pure_virtuelle() = 0;
    virtual void methode_virtuelle() {
        std::cout << "Je suis une methode virtuelle" << std::endl;
    }
    void surcharge(int x) {
        std::cout << "La valeur de x est:" << x << std::endl;
    }
    void surcharge(float y) {
        std::cout << "La valeur de x est:" << y << std::endl;
    }
}
```
5) __Quelles sont les raisons de privilégier l'implémentation d'interfaces avec délégation plutôt que des chaînes d'héritage profondes ?__
L'implementation d'interface avec délégation:
- permet d'éviter les problèmes de résolution multiple d'héritage (Pour les languages ne supportant pas l'héritage multiples)
- offre une plus grande flexibilité
- facilite la réutilisation du code
- permet de respecter le principe de Liskov (mainternir une bonne séparation des préoccupations) et
- et simplifie la hiérachie d'héritage en divisant la fonctionnalité en petites parties indépendante.

6) __Quels sont vos sites Web préférés pour progresser en C++ ?__

7) __Selon vous, quel est le process idéal pour aborder le développement d'une fonctionnalité dans une petite équipe?__
les étapes suivante sont nécessaires:
- Étape 1- Comprendre les exigences:
- Étape 2- Planifier la fonctionalité  
    - définir les étapes nécessaire pour implementer la fonctionnalité
    - définir les rôles et responsabilités de chaque membre de l'équipe
    - définir les dépendances éventuelle et les échéances
- Étape 3- Crée un prototype (PoC). Cette étape est optionel et intéressant dans la majorité des cas pour les fonctionnalités complexes. Cela permettra de tester rapidement l'approche choisie et de vérifier si les exigences sont correctement comprises.
- Étape 4 - Implementer  la fonctionnalité: Il es important de suivre les bonnes pratiques de développement de logiciels, telles que:
    - la programmation en équipe 
    . les test unitaires
    - la revue de code
    - l'intégration continue
    
8) __Quelle est votre façon d'utiliser les exceptions ?__

9) __Quels diagrammes UML utilisez-vous ?__
- Diagramme de cas d'utilisation
- Diagramme de classe
- Diagramme de séquence
- Diagramme d'activité ou d'état
- Diagramme de composant

10) __En UML quelle est la différence entre agrégation et composition ? Donnez un exemple de chaque en C++.__
- Dans une ___relation d'agégation___, une classe peut contenir d'autres classes, mais ces dernières peuvent exister indépendamment de la classe conteneur.
Exemple:
![Agrgregation](aggregation.svg)
```c++ {.line-numbers}
class Personne {
public:
    Personne(const std::string& name): m_name(name) {}
    virtual ~Personne(){}
private:
    std::string _name;
};

class Equipe {
public:
    Equipe(const std::string& name): m_name(name){}
    virtual ~Equipe(){}
    
    void ajoutMembre(Personne* membre) {
        m_membres.push_back(membre);
    }
private:
    std::string m_name;
    std:::vector<Personne*> m_membres;
    
};
```
Dans cet exemple, la classe "___Equipe___" est une classe qui agrège plusieurs abjets de la classe "___Personne___". Les objects "Personne" peuvent exister indépendamment de la classe "Equipe", et ils peuvent être ajoutés ou rétirés de la classe "Equipe" sans être détruite.
- Dans une ___relation de composition___, une classe contient d'autres classes qui dépendent de la classe conteneur et qui ne peuvent pas exister sans elle.
Exemple:
```c++ {.line-numbers}
```
