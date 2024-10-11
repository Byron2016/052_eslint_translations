---
English-last-commit: 876cf0f6190051ff2935a663a6b9a4733d094225
last-translation-date(yyyy-mm-dd): 2024-10-11
---

# Complemento de lenguaje Markdown de ESLint

[![npm Version](https://img.shields.io/npm/v/@eslint/markdown.svg)](https://www.npmjs.com/package/@eslint/markdown)
[![Downloads](https://img.shields.io/npm/dm/@eslint/markdown.svg)](https://www.npmjs.com/package/@eslint/markdown)
[![Build Status](https://github.com/eslint/markdown/workflows/CI/badge.svg)](https://github.com/eslint/markdown/actions)

Lint JS, JSX, TypeScript y más dentro de Markdown.

<img
    src="https://raw.githubusercontent.com/eslint/markdown/main/screenshot.png"
    height="142"
    width="432"
    alt="Un fragmento de código JS en un editor Markdown tiene subrayados ondulados de color rojo. Una descripción emergente explica el problema."
/>

## Uso

### Instalación

Instale el complemento junto con ESLint v9 o una versión posterior:

```sh
npm install --save-dev eslint @eslint/markdown
```

### Configuraciones

| **Nombre de la configuración** | **Descripción**                                                                                                                |
| ------------------------------ | ------------------------------------------------------------------------------------------------------------------------------ |
| `recomendado`                  | Analiza todos los archivos `.md` con las reglas recomendadas y asume el formato [CommonMark](https://commonmark.org/).         |
| `procesador`                   | Permite extraer bloques de código de todos los archivos `.md` para que cada bloque de código pueda analizarse individualmente. |

En su archivo `eslint.config.js`, importe `@eslint/markdown` e incluya la configuración recomendada para habilitar el procesador Markdown en todos los archivos `.md`:

```js
// eslint.config.js
import markdown from "@eslint/markdown";

export default [
  ...markdown.configs.recommended,

  // Sus otras configuraciones aquí
];
```

### Reglas

<!-- NOTA: La siguiente tabla se genera automáticamente. No la edite manualmente. -->

<!-- Rule Table Start -->

| **Nombre de la regla**                                           | **Descripción**                                               | **Recomendada** |
| :--------------------------------------------------------------- | :------------------------------------------------------------ | :-------------: |
| [`fenced-code-language`](./docs/rules/fenced-code-language.md)   | Requerir idiomas para bloques de código protegidos.           |       si        |
| [`heading-increment`](./docs/rules/heading-increment.md)         | Reforzar que los niveles de encabezado se incrementen en uno. |       si        |
| [`no-duplicate-headings`](./docs/rules/no-duplicate-headings.md) | No permitir encabezados duplicados en el mismo documento.     |       no        |
| [`no-empty-links`](./docs/rules/no-empty-links.md)               | No permitir enlaces vacíos.                                   |       si        |
| [`no-html`](./docs/rules/no-html.md)                             | No permitir etiquetas HTML.                                   |       no        |
| [`no-invalid-label-refs`](./docs/rules/no-invalid-label-refs.md) | No permitir referencias de etiquetas no válidas.              |       si        |
| [`no-missing-label-refs`](./docs/rules/no-missing-label-refs.md) | No permitir referencias de etiquetas faltantes.               |       si        |

<!-- Rule Table End -->

**Nota:** Este complemento no proporciona reglas de formato. Recomendamos utilizar para ese propósito un formateador de código fuente como [Prettier](https://prettier.io).

Para configurar individualmente una regla en su archivo `eslint.config.js`, importe `@eslint/markdown` y configure cada regla con un prefijo:

```js
// eslint.config.js
import markdown from "@eslint/markdown";

export default [
  {
    files: ["**/*.md"],
    plugins: {
      markdown,
    },
    language: "markdown/commonmark",
    rules: {
      "markdown/no-html": "error",
    },
  },
];
```

Puede deshabilitar reglas individualmente en Markdown usando comentarios HTML, como:

```markdown
<!-- eslint-disable-next-line markdown/no-html -- Quiero permitir HTML aquí -->

<custom-element>Hola mundo!</custom-element>

<!-- eslint-disable markdown/no-html -- aquí también -->

<another-element>Adios mundo!</another-element>

<!-- eslint-enable markdown/no-html -- Es seguro volver a habilitarlo ahora -->

[Object] <!-- eslint-disable-line markdown/no-missing-label-refs -- No pretende ser un enlace de referencia. -->
```

### lenguajes

| **Nombre del lenguaje** | **Descripción**                                                                           |
| ----------------------- | ----------------------------------------------------------------------------------------- |
| `commonmark`            | Analizar utilizando el formato Markdown [CommonMark](https://commonmark.org)              |
| `gfm`                   | Analizar utilizando el formato [GitHub-Flavored Markdown](https://github.github.com/gfm/) |

Para configurar individualmente un lenguaje en su archivo `eslint.config.js`, importe `@eslint/markdown` y configure un `lenguaje`:

```js
// eslint.config.js
import markdown from "@eslint/markdown";

export default [
  {
    files: ["**/*.md"],
    plugins: {
      markdown,
    },
    language: "markdown/gfm",
    rules: {
      "markdown/no-html": "error",
    },
  },
];
```

### Procesadores

| **Nombre del procesador**                   | **Descripción**                                                                                     |
| ------------------------------------------- | --------------------------------------------------------------------------------------------------- |
| [`markdown`](./docs/processors/markdown.md) | Extraiga bloques de código delimitados del código Markdown para que puedan analizarse por separado. |

## Integraciones del editor

### VSCode

[`vscode-eslint`](https://github.com/microsoft/vscode-eslint) tiene soporte incorporado para el procesador Markdown.

### Atom

El paquete [`linter-eslint`](https://atom.io/packages/linter-eslint) permite realizar linting dentro del [IDE de Atom](https://atom.io/).

Para ver cómo `@eslint/markdown` hace su magia dentro de los bloques de código de Markdown en su editor Atom, puede ir a la configuración de `linter-eslint` y dentro de "Lista de ámbitos en los que se ejecutará ESLint...", agregar el ámbito de cursor "source.gfm".

Sin embargo, esto informa un problema al ver Markdown que no tiene configuración, por lo que puede desear usar el ámbito de cursor "source.embedded.js", pero tenga en cuenta que los comentarios de configuración de `@eslint/markdown` y las directivas de omisión no funcionarán en este contexto.

## Contribuyendo

```sh
$ git clone https://github.com/eslint/markdown.git
$ cd markdown
$ npm install
$ npm test
```

Este proyecto sigue las [pautas de contribución de ESLint](https://eslint.org/docs/latest/contribute/).

<!-- NOTA: Esta sección se genera automáticamente. No la edites manualmente.-->
<!--sponsorsstart-->

## Sponsors

Las siguientes empresas, organizaciones y personas respaldan el mantenimiento y desarrollo continuos de ESLint. [Conviértase en patrocinador](https://eslint.org/donate)
para que su logotipo aparezca en nuestros archivos README y en nuestro [sitio web](https://eslint.org/sponsors).

<h3>Patrocinadores Platino</h3>
<p><a href="https://automattic.com"><img src="https://images.opencollective.com/automattic/d0ef3e1/logo.png" alt="Automattic" height="128"></a> <a href="https://www.airbnb.com/"><img src="https://images.opencollective.com/airbnb/d327d66/logo.png" alt="Airbnb" height="128"></a></p><h3>Patrocinadores Oro</h3>
<p><a href="https://trunk.io/"><img src="https://images.opencollective.com/trunkio/fb92d60/avatar.png" alt="trunk.io" height="96"></a></p><h3>Patrocinadores Plata</h3>
<p><a href="https://www.jetbrains.com/"><img src="https://images.opencollective.com/jetbrains/fe76f99/logo.png" alt="JetBrains" height="64"></a> <a href="https://liftoff.io/"><img src="https://images.opencollective.com/liftoff/5c4fa84/logo.png" alt="Liftoff" height="64"></a> <a href="https://americanexpress.io"><img src="https://avatars.githubusercontent.com/u/3853301?v=4" alt="American Express" height="64"></a> <a href="https://www.workleap.com"><img src="https://avatars.githubusercontent.com/u/53535748?u=d1e55d7661d724bf2281c1bfd33cb8f99fe2465f&v=4" alt="Workleap" height="64"></a></p><h3>Patrocinadores Bronce</h3>
<p><a href="https://www.wordhint.net/"><img src="https://images.opencollective.com/wordhint/be86813/avatar.png" alt="WordHint" height="32"></a> <a href="https://www.crosswordsolver.org/anagram-solver/"><img src="https://images.opencollective.com/anagram-solver/2666271/logo.png" alt="Anagram Solver" height="32"></a> <a href="https://icons8.com/"><img src="https://images.opencollective.com/icons8/7fa1641/logo.png" alt="Icons8" height="32"></a> <a href="https://discord.com"><img src="https://images.opencollective.com/discordapp/f9645d9/logo.png" alt="Discord" height="32"></a> <a href="https://www.gitbook.com"><img src="https://avatars.githubusercontent.com/u/7111340?v=4" alt="GitBook" height="32"></a> <a href="https://nx.dev"><img src="https://avatars.githubusercontent.com/u/23692104?v=4" alt="Nx" height="32"></a> <a href="https://herocoders.com"><img src="https://avatars.githubusercontent.com/u/37549774?v=4" alt="HeroCoders" height="32"></a> <a href="https://usenextbase.com"><img src="https://avatars.githubusercontent.com/u/145838380?v=4" alt="Nextbase Starter Kit" height="32"></a></p>
<h3>Patrocinadores tecnológicos</h3>
Los patrocinadores tecnológicos nos permiten utilizar sus productos y servicios de forma gratuita como parte de una contribución al ecosistema de código abierto y a nuestro trabajo.
<p><a href="https://netlify.com"><img src="https://raw.githubusercontent.com/eslint/eslint.org/main/src/assets/images/techsponsors/netlify-icon.svg" alt="Netlify" height="32"></a> <a href="https://algolia.com"><img src="https://raw.githubusercontent.com/eslint/eslint.org/main/src/assets/images/techsponsors/algolia-icon.svg" alt="Algolia" height="32"></a> <a href="https://1password.com"><img src="https://raw.githubusercontent.com/eslint/eslint.org/main/src/assets/images/techsponsors/1password-icon.svg" alt="1Password" height="32"></a></p>
<!--sponsorsend-->
