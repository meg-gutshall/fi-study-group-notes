# JavaScript Modern Tooling

> **Alice Balbuena on 05/08/20**

## Package Managers

Packages are small pieces of utility code that allows you to add on to what you can do in JavaScript. Many are open-source. npm is the definitive package registry.

### npm

* Most popular/widely-used
* A website, CLI, and registry
* Installs packages synchronously
  * Always has to download everything
    * Will download a copy of each of your packages \(and their dependencies\) into each of your repositories
  * This is why we don't commit our `node_modules` directory
* Recently purchased by GitHub/Microsoft
  * This purchase adds stability to npm

![Installs packages synchronously](../.gitbook/assets/screen-shot-2020-05-08-at-4.14.07-pm.png)

{% embed url="https://www.npmjs.com/" %}

### Yarn

* Uses the npm registry
* Installs packages in parallel
* Increase in performance as the number of packages grows
* Created by Facebook
  * Now maintained independently from them

![Installs packages in parallel](../.gitbook/assets/screen-shot-2020-05-08-at-4.14.16-pm.png)

{% embed url="https://yarnpkg.com/" %}

### pnpm

* Uses the npm registry
* Uses hard links and symlinks/junctions
* Downloads packages per version, not per project
  * No repeat downloads of same packages across folders
  * WAY faster than npm and Yarn

![Downloads packages per version and uses hard link and symlinks/junctions](../.gitbook/assets/screen-shot-2020-05-08-at-4.14.28-pm.png)

{% embed url="https://pnpm.js.org/" %}

## Bundlers

Compiles code to make it readable for current browsers.

### Modules

* One JavaScript file is one module
* Can be loaded into other JavaScript files using import and export

#### export

* Makes variables and functions accessible from outside the current module

#### import

* Brings in variables and functions from outside the current module

{% tabs %}
{% tab title="Index" %}
{% code title="index.js" %}
```javascript
import { speakToGrandma } from './speak'

const speech = speakToGrandma('hello')
console.log(speech)
// HUH!? SPEAK UP, SONNY!
```
{% endcode %}
{% endtab %}

{% tab title="Speak" %}
{% code title="speak.js" %}
```javascript
export function speakToGrandma(speak) {
  if (speak === speak.toUpperCase()) {
    return "NO, NOT SINCE 1938!"
  } else {
    return "HUH!? SPEAK UP, SONNY!"
  }
}
```
{% endcode %}
{% endtab %}
{% endtabs %}

### Webpack

* Most popular/very powerful
* Works on frontend and backend
* Takes JavaScript, CSS, images, fonts, etc.
* Extensive plugin ecosystem
* Needs to be setup

{% embed url="https://webpack.js.org/" %}

### Parcel

* Zero-configuration/zero-setup
* Works on frontend
* Has live reload, babel transforms and transpiling built-in

{% embed url="https://parceljs.org/" %}

## Static Type Checking

Type checking is the process of validating and enforcing the rules and constraints of different data types. By default, JavaScript type checks the code while it's running \(dynamic type checking\). Static type checking does this while we're still building. Type inference is when JavaScript infers the type of the variable when it wasn't explicitly set. Explicitly setting the data type is called type annotation.

### Flow

* Out-of-the-box utility
* Works within existing JavaScript files
* Has an opt-in system for implementing throughout the project
* Easy to configure and install with babel
* Built by Facebook
* Implement by putting `// @flow` at the top of any of your `.js` files

![](../.gitbook/assets/screen-shot-2020-05-08-at-4.30.13-pm.png)

{% embed url="https://flow.org/" %}

### TypeScript

* Open-source programming language
* Along with static type checking adds: interfaces, namespaces, tuples, etc.
* Requires code be written in a special file extension
* Needs compiler to convert TypeScript to JavaScript
  * Have to write code in a `.ts` file
* Developed by Microsoft

![](../.gitbook/assets/screen-shot-2020-05-08-at-4.31.30-pm.png)

{% embed url="https://www.typescriptlang.org/" %}

## Linters

Analyzes our code syntax and structure and will give errors if something violates your predefined rules.

### ESLint

* Designed to be completely configurable
* Has many presets that can be used to increase functionality
* Supports JSX
* Has the biggest rules system built for it out of any other linter

![](../.gitbook/assets/screen-shot-2020-05-08-at-4.32.50-pm.png)

{% embed url="https://eslint.org/" %}

## Libraries

### React.js

* Very popular and widely used
* Steep learning curve
* Virtual DOM, component-based, state, props, JSX, React hooks
* Focus is solely on the UI layer of the frontend
* Relies on external packages to handle routing and complex state management \(React-Router, Reach-Router, XState, Redux\)
* Has a wide ecosystem of packages
* Built and developed by Facebook

```jsx
// This function takes a component...
function withSubscription(WrappedComponent, selectData) {
  // ...and returns another component...
  return class extends React.Component {
    constructor(props) {
      super(props);
      this.handleChange = this.handleChange.bind(this);
      this.state = {
        data: selectData(DataSource, props)
      };
    }
    
    componentDidMount() {
      // ...that takes care of the subscription...
      DataSource.addChangeListener(this.handleChange);
    }
    
    componentWillUnmount() {
      DataSource.removeChangeListener(this.handleChange);
    }
    
    handleChange() {
      this.setState({
        data: selectData(DataSource, this.props)
      });
    }
    
    render() {
      // ...and renders the wrapped component with the fresh data!
      // Notice that we pass through any additional props
      return <WrappedComponent data={this.state.data} {...this.props} />;
    }
  };
}
```

{% embed url="https://reactjs.org/" %}

### Vue.js

* Rapidly gaining in popularity
* Easy to learn
* Virtual DOM, component-based, state, props, templating, compositing API
* Relies on external packages to handle routing and complex state management
  * Unlike React.js, these packages are maintained by the Vue.js core team
* Maintained by the Vue.js core team
* Took the best of React.js and Angular.js and combined them

```jsx
<template>
  <nav>
   <router-link>Home</router-link>
   <router-link>Shop</router-link>
   <router-link v-show="isLoggedIn">Log Out</router-link>
  </nav>
  <button :click="increaseCount">{{count}}</button>
  <MainSection />
</template>

<script>
  import MainSection from '@/components/MainSection';
  
  export default {
    components: {
      MainSection
    },
    data: () => ({
      isLoggedIn: True,
      count: 0
    }),
    methods: {
      increaseCount() {
        return this.count +1;
      }
    },
    mounted: () => {
      this.$nextTick(() => alert("Page is mounted"));
    }
  }
</script>

<scope lang="scss" scoped>
  a, a:visited, a:hover {
    color: white;
  }
</scope>
```

{% embed url="https://vuejs.org/" %}

## React Frameworks

### Next.js

* Server-side rendering
* Can also handle static pages
* Automatic hot reloading
* Automatic code splitting
* Includes routing/complex state management out-of-the-box
* TypeScript support

![](../.gitbook/assets/screen-shot-2020-05-08-at-4.48.33-pm.png)

{% embed url="https://nextjs.org/" %}

### Gatsby.js

* Static site generator
* Open-source
* JAMstack architecture
* Code splitting
* Powerful image processing
* Uses Reach-Router \(React-Router replacement with better support for accessibility\)

![](../.gitbook/assets/screen-shot-2020-05-08-at-4.49.12-pm.png)

{% embed url="https://www.gatsbyjs.org/" %}

## Slides

{% embed url="https://docs.google.com/presentation/d/1spwmlCBKndOlsJK\_xtIvaLPCVjpLQaTquSgn0CyBIp4/edit?usp=sharing" %}



