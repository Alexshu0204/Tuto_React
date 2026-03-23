# Ma doc React

_Tuto rédigé à partir de la chaîne de [Melvynx](https://www.youtube.com/@melvynxdev) - [Apprendre REACT.JS 19 en 1 HEURE - YouTube](https://www.youtube.com/watch?v=dGMWsXyA37U)._

_Note : ce tuto se portera uniquement sur Vite + React._

## Table des matières

- [1) Qu'est-ce que React ?](#1-Qu'est-ce-que-React-)
- [2) Les installations](#2-Les-installations)
- [3) Les composants](#3-Les-composants)

### 1) Qu'est-ce que React ?

**React** est une bibliothèque JavaScript pour construire des interfaces utilisateur interactives. Voici pourquoi j'ai choisi de l'apprendre :

**Accessibilité et popularité** — React est la bibliothèque front-end la plus utilisée au monde. L'écosystème est massif, la communauté très active, et les ressources pour débuter sont abondantes. C'est un choix sûr pour progresser rapidement même en tant que débutant.

**Organisation et réutilisabilité** — Contrairement aux projets vanilla (HTML/CSS/JS séparés), React utilise les **composants réutilisables**. Un bouton, un formulaire, une card — je les crée une fois et les réutilise partout. Fini la duplication de code !

**JSX : le meilleur des deux mondes** — React permet d'écrire du JavaScript et du HTML ensemble dans une syntaxe appelée **JSX** (ou TSX pour TypeScript). C'est intuitif et plus lisible qu'une architecture traditionnelle.

**Single Page Application (SPA)** — React construit des applications avec une seule page HTML. Au lieu de créer 10 fichiers HTML séparés, une application React gère le rendu dynamiquement. Plus léger, plus rapide, plus efficace.

**Les Hooks** — Avec les hooks (comme `useState` et `useEffect`), je peux gérer l'état et les effets directement dans mes composants de façon élégante. C'est puissant et c'est quelque chose que je veux maîtriser.

**En résumé** — React m'enseigne comment structurer une application front-end de façon professionnelle, tout en restant accessible pour un débutant.

### 2) Les installations

Prériquis :
- avoir installer Node JS et Tailwind CSS
- créer un projet et installer Vite + React

Pour installer Vite, tape `npm create vite@latest`.

-> Après l’installation, Vite va demander un nom du projet. 
Il demandera également de choisir un framework (donc React pour nous) et ensuite un langage de programmation (on va prendre JavaScript ou TypeScript recommandé pour une API en Nest JS).

![Aperçu](./images/screenshot_1.png)

**On peut à présent ouvrir l’éditeur de code.**

Voici les fichiers de départ :

![Aperçu](./images/screenshot_2.png)


Voici l'explication du rôle de chaque fichier dans ce projet React + Vite :

**Fichiers de configuration**

- **package.json** : Fichier manifest du projet. Il contient :
  - Les dépendances (React, React-DOM)
  - Les scripts npm (`dev`, `build`, `lint`, `preview`)
  - Les infos du projet (nom, version, type)

- **vite.config.js** : Configuration du bundler Vite. Active le plugin React pour transformer JSX en JavaScript standard.

- **eslint.config.js** : Configuration du linter ESLint pour détecter les erreurs et appliquer les standards de code.

**Fichiers HTML et point d'entrée**

- **index.html** : Fichier HTML principal du navigateur. Il contient :
  - Une `<div id="root">` où React va injecter l'application
  - Un script qui charge main.jsx

- **main.jsx** : Point d'entrée JavaScript de l'application React. Il :
  - Importe le composant `App`
  - Crée la racine React avec `createRoot()`
  - Rend le composant App dans le DOM

**Composants et styles**

- **App.jsx** : Composant principal de l'application (là où vous mettez votre logique métier)

- **App.css** : Styles spécifiques au composant `App`

- **index.css** : Styles globaux appliqués à toute l'application

**Dossiers**

- **public** : Dossier des fichiers statiques (images, favicon, etc.) - directement copiés dans le build final

- **assets** : Dossier pour ranger les ressources (images, fonts, etc.) du projet

**Lancer le server** `npm run dev`

Ça montre cet interface par défaut :

![Aperçu](./images/screenshot_3.png)

**Nous allons retirer l'UI de Vite.**

Dans `App.jsx` - `src/assets/App.jsx` :

```jsx
// Supprimer tous ces imports
import { useState } from 'react'
import reactLogo from './assets/react.svg'
import viteLogo from './assets/vite.svg'
import heroImg from './assets/hero.png'
import './App.css'

function App() {
  // Supprimer ce state
  const [count, setCount] = useState(0) 

  return (
    <>
      {/* On peut aussi tout retirer à partir de cette ligne */}
      <section id="center">
        <div className="hero">
          <img src={heroImg} className="base" width="170" height="179" alt="" />
          <img src={reactLogo} className="framework" alt="React logo" />
          <img src={viteLogo} className="vite" alt="Vite logo" />
        </div>
        <div>
          <h1>Get started</h1>
          <p>
            Edit <code>src/App.jsx</code> and save to test <code>HMR</code>
          </p>
        </div>
        <button
          className="counter"
          onClick={() => setCount((count) => count + 1)}
        >
          Count is {count}
        </button>
      </section>

      <div className="ticks"></div>

      <section id="next-steps">
        <div id="docs">
          <svg className="icon" role="presentation" aria-hidden="true">
            <use href="/icons.svg#documentation-icon"></use>
          </svg>
          <h2>Documentation</h2>
          <p>Your questions, answered</p>
          <ul>
            <li>
              <a href="https://vite.dev/" target="_blank">
                <img className="logo" src={viteLogo} alt="" />
                Explore Vite
              </a>
            </li>
            <li>
              <a href="https://react.dev/" target="_blank">
                <img className="button-icon" src={reactLogo} alt="" />
                Learn more
              </a>
            </li>
          </ul>
        </div>
        <div id="social">
          <svg className="icon" role="presentation" aria-hidden="true">
            <use href="/icons.svg#social-icon"></use>
          </svg>
          <h2>Connect with us</h2>
          <p>Join the Vite community</p>
          <ul>
            <li>
              <a href="https://github.com/vitejs/vite" target="_blank">
                <svg
                  className="button-icon"
                  role="presentation"
                  aria-hidden="true"
                >
                  <use href="/icons.svg#github-icon"></use>
                </svg>
                GitHub
              </a>
            </li>
            <li>
              <a href="https://chat.vite.dev/" target="_blank">
                <svg
                  className="button-icon"
                  role="presentation"
                  aria-hidden="true"
                >
                  <use href="/icons.svg#discord-icon"></use>
                </svg>
                Discord
              </a>
            </li>
            <li>
              <a href="https://x.com/vite_js" target="_blank">
                <svg
                  className="button-icon"
                  role="presentation"
                  aria-hidden="true"
                >
                  <use href="/icons.svg#x-icon"></use>
                </svg>
                X.com
              </a>
            </li>
            <li>
              <a href="https://bsky.app/profile/vite.dev" target="_blank">
                <svg
                  className="button-icon"
                  role="presentation"
                  aria-hidden="true"
                >
                  <use href="/icons.svg#bluesky-icon"></use>
                </svg>
                Bluesky
              </a>
            </li>
          </ul>
        </div>
      </section>

      <div className="ticks"></div>
      <section id="spacer"></section>
    </>
  )
}

export default App
```
**Ça donne ça :**

```jsx
function App() {

  return (
    <>
      {/* Ajouter un p'tit mot de bienvenue */}
      <h1>Bienvenue sur notre application React !</h1>
    </>
  )
}

export default App

```
![Aperçu](./images/screenshot_4.png)


**Ensuite on va suprimer `App.css` dans** `src/assets/App.css` **qui était appliqué à l'interface par défaut.**

Puis dans `src/assets/index.css`, **on va retirer tout le contenu du fichier `index.css`**.

Pourquoi on supprime les lignes css ? Car nous allons utiliser **Tailwind CSS**.

**La raison ?**

Tailwind CSS offre une meilleure productivité en comparaison au CSS classique. Les avantages principaux :
- **Directement dans le JSX** : Classes utilitaires appliquées directement sur les élements
- **Pas de conflits de noms** : Classes pré-définies évitent les collisions
- **Bundle optimisé** : Seules les classes utilisées sont incluses en production
- **Responsive natif** : Breakpoints intégrés (`md:`, `lg:`, etc.)
- **États visuels faciles** : `hover:`, `focus:`, `dark:` pour les interactions
- **Design system cohérent** : Palette de couleurs et espacements uniformes

### Pour installer Tailwind CSS :

Se rendre directement dans la doc officielle de Tailwind et suivre les instructions (car les versions changent au fil du temps).

Lien : https://tailwindcss.com/docs/installation/using-vite

Maintenant qu'on a tailwind, on peux tester dans `App.jsx` - `src/assets/App.jsx` et rajouter une ligne :

```jsx
import { useState } from 'react'

function App() {

  return (
    <div className="bg-red-500"> {/* Ajoute ici ta classe Tailwind à l'intérieur du <>*/}
      {/* Ajouter un p'tit mot de bienvenue */}
      <h1>Bienvenue sur notre application React !</h1>
    </div>
  )
}

export default App
```

On peut voir "Bienvenue sur notre application React !" surligné en rouge :

![Aperçu](./images/screenshot_5.png)

### 3) Les composants

**Qu'est-ce qu'un composant React ?**

Un composant React est une **fonction JavaScript réutilisable** qui retourne du JSX (un mélange de JavaScript et HTML). Chaque composant représente une partie de l'interface utilisateur qu'on peut utiliser autant de fois qu'on veut.

Un composant c'est comme un bloc de construction — tu crées une fonction, elle retourne du markup, et tu peux la réutiliser partout dans ton app.

**Exemple simple :**

```jsx
function Bouton() {
  return <button>Cliquez-moi</button>
}

// Utilisation
<Bouton />
<Bouton />
<Bouton />  // Trois boutons identiques !
```

**Exemples de composants courants :**

- **Bouton** : Un bouton réutilisable avec du styling
- **Card** : Une boîte avec titre, description et image
- **Header/Navbar** : La barre de navigation en haut
- **Footer** : Le pied de page
- **Formulaire** : Un formulaire avec champs et validation
- **Liste** : Affiche une liste d'éléments (posts, produits, etc.)
- **Modal** : Une fenêtre popup
- **Avatar** : Image de profil utilisateur
- **Commentaire** : Un commentaire avec auteur et contenu

**Pourquoi les composants c'est puissant ?**

- **Réutilisabilité** : Crée une fois, utilise partout
- **Maintenabilité** : Si tu dois changer un bouton, tu le fais à un seul endroit
- **Clarté** : Ton code est organisé et facile à comprendre
- **Modularité** : Tu peux composer des petits composants pour créer de grands composants

### React vs JavaScript Vanilla

La différence principale entre **React et JavaScript Vanilla** est la façon de gérer l'UI et l'état.

Avec du **vanilla (HTML/CSS/JS pur)**, tu dois :
- Manipuler le DOM directement avec `document.getElementById()`, `appendChild()`, etc.
- Gérer manuellement les mises à jour : si une donnée change, tu dois trouver l'élément et le modifier à la main
- Créer beaucoup de fichiers HTML séparés pour chaque page
- Écrire beaucoup de code répétitif pour synchroniser l'état avec l'interface

Avec **React**, tu :
- Déclares l'UI avec des composants (fonctions JavaScript)
- React gère automatiquement les mises à jour du DOM quand l'état change
- Construis une Single Page Application où tout se passe sur une seule page HTML
- Écris du code plus propre, plus lisible et moins répétitif

**Exemple simple** : Si tu veux afficher un compteur qui s'incrémente au clic.

*En Vanilla :*
```javascript
let count = 0;
document.getElementById('button').addEventListener('click', () => {
  count++;
  document.getElementById('count').textContent = count;
});
```

*En React :*
```jsx
function Compteur() {
  const [count, setCount] = useState(0);
  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={() => setCount(count + 1)}>Incrémenter</button>
    </div>
  );
}
```

React c'est plus intuitif : tu décris l'UI une fois, et React s'occupe du reste ! 🚀

Par ailleurs, on va pouvoir utiliser des **variants** (un concept très utilisé avec Tailwind / composants UI.) telles que :

- `primary` → bouton principal
- `secondary` → bouton secondaire
- `ghost` → bouton transparent
- `danger` → bouton rouge

**Exemple avec un bouton :**

```jsx
function Button({ variant, children }) {
  let style = ""

  if (variant === "primary") {
    style = "bg-blue-500 text-white"
  } else if (variant === "secondary") {
    style = "bg-gray-500 text-white"
  } else if (variant === "ghost") {
    style = "bg-transparent border border-gray-500"
  }

  return (
    <button className={`px-4 py-2 rounded ${style}`}>
      {children}
    </button>
  )
}
``` 

### On va créer nos premiers composants

Dans `App.jsx` - `src/assets/App.jsx` :

Étape 1 :

```jsx
// Ajouter export default dans la fonction App
export default function App() {

  return (
    <div className="bg-red-500"> {/* Ajoute ici ta classe Tailwind à l'intérieur du <>*/}
      {/* Ajouter un p'tit mot de bienvenue */}
      <h1>Bienvenue sur notre application React !</h1>
    </div>
  )
}

// Suprimer la ligne export default App (c’est juste une écriture plus courte et plus propre 
// mais affichera une erreur sinon).
```

Étape 2, on va créer un composant lego :

```jsx
export default function App() {

  return (
    <div className="bg-red-500">
      <h1>Bienvenue sur notre application React !</h1>
    </div>
  )
}

// Composant Lego après l'exportation de App
function Lego() {
  return <div className="bg-red-500 h-16 w-32"></div>;
}
```

À ce moment là, on définit une fonction JS pour créer un composant React et dans cette fonction, on retourne du JSX.

Étape 3, démonstration :

```jsx
export default function App() {

  return (
    <div className="bg-red-500">
      {/* Ajouter d'autres composants ou éléments ici */}
      <Lego /> {/* Attention à bien mettre le composant en majuscule */} 
    </div>
  )
}

// Composant Lego après l'exportation de App
function Lego() {
  return <div className="bg-red-500 h-16 w-32"></div>;
}
```

Résultat :

![Aperçu](./images/screenshot_6.png)

On va transformer le bloc rouge pour rendre plus semblable à une brique de lego :

```jsx
// Modifier la ligne div className
return (
    <div className="p-4 flex flex-col gap-4"> {/* Remplacer le bg-red par un padding */}
      <Lego />
    </div>
  )
```

![Aperçu](./images/screenshot_7.png)

On est a créer notre **premier composant** ! Ce qui veut dire qu'on va pouvoir réutiliser **plusieurs fois**.

Par exemple on peux s'amuser à dupliquer comme ceci :

```jsx
export default function App() {

  return (
    <div className="p-4 flex flex-col gap-4">
      <Lego />
      {/* On peut dupliquer le composant Lego autant de fois que nécessaire */}
      <Lego />
      <Lego />
      <Lego />
    </div>
  )
}

function Lego() {
  return <div className="bg-red-500 h-16 w-32"></div>;
}
```
![Aperçu](./images/screenshot_8.png)