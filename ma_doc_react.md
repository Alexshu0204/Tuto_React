# Ma doc React

_Tuto rédigé à partir de la chaîne de [Melvynx](https://www.youtube.com/@melvynxdev) - [Apprendre REACT.JS 19 en 1 HEURE - YouTube](https://www.youtube.com/watch?v=dGMWsXyA37U)._

_Note : ce tuto se portera uniquement sur Vite + React._

## Table des matières

[1) Les installations](#1-Les-installations)

### 1) Les installations

Prériquis :
- créer un projet et installer Vite + React

Pour installer Vite, tape `npm create vite@latest`.

-> Après l’installation, Vite va demander un nom du projet. 
Il demandera également de choisir un framework (donc React pour nous) et ensuite un langage de programmation (on va prendre JavaScript ou TypeScript recommandé pour une API en Nest JS).

![Aperçu](./images/screenshot_1.png)

On peut à présent ouvrir l’éditeur de code.

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


Lancer le server `npm run dev`

Ça montre cet interface par défaut :

![Aperçu](./images/screenshot_3.png)

Nous allons retirer l'UI de Vite.

Dans Aps.jsx `src/assets/App.jsx` :

```jsx
import { useState } from 'react'
import reactLogo from './assets/react.svg'
import viteLogo from './assets/vite.svg'
import heroImg from './assets/hero.png'
import './App.css'

function App() {
  const [count, setCount] = useState(0)

  return (
    <>
      {/* On peut tout retirer à partir de cette ligne */}
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