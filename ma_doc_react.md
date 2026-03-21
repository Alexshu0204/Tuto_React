# Ma doc React

_Tuto rédigé à partir de la chaîne de [Melvynx](https://www.youtube.com/@melvynxdev) - [Apprendre REACT.JS 19 en 1 HEURE - YouTube](https://www.youtube.com/watch?v=dGMWsXyA37U)._

_Note : ce tuto se portera uniquement sur Vite + React._

## Table des matières

[1) Qu'est-ce que React ?](#1-Qu'est-ce-que-React-)
[2) Les installations](#2-Les-installations)
[3) Les composants](#3-Les-composants)

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
import { useState } from 'react'
// Supprimer ces imports
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
import { useState } from 'react'

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