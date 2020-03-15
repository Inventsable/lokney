# lokney

Vue utility components for Adobe CEP panels to greatly simplify the overhead of Adobe specific coding.

```html
<!-- Within a given App.vue, with no need for methods or data inside <script> -->
<div id="app">
  <!-- Path to script can be specified as attribute, supporting multiple files -->
  <Panel script-path="['./host/myScript.jsx', './host/anotherScript.jsx']">
    <!-- Place extension content or <router-view/> inside this <Panel> component -->
    <div id="content"></div>
  </Panel>
  <!-- 
    Menus can be anywhere in your code, even per router page. Add props like "debug" and "refresh" to easily append launching debug port and refreshing your extension to context and flyout menus.

    Any change to a :context or :flyout Array will automatically rebuild the given menu and update instantly.
  -->
  <Menus debug refresh
      :context="[
          {
            label: 'This is a disabled menu item',
            enabled: false
          },
          {
            label: 'Nested menus',
            menu: [
              { label: 'Hello' },
              { label: 'World' }
              {
                label: 'Nested again',
                menu: [
                  { label: 'Hello' },
                  { label: 'World' }
                ]
              }
            ]
          }
          {
            label: 'This activates a method within this file on clicking this item',
            enabled: true,
            callback: this.localMethod
          }
      ]"
    />
</div>
```

All host app themes, scrollbars, UI change events, script loading, menus (context and flyout), debugger launching, easy refresh of panel via menu and more handed with the above.

---

## Installation and use

```bash
npm install lokney
```

### Within `./src/main.js` (use anywhere in project with no need to import per component file):

```js
import { Panel, Menu } from 'lokney'

Vue.use('Panel', Panel);
Vue.use('Menu', Menu);

// Include imports above Vue initialization
new Vue({
	router,
	render: h => h(App)
}).$mount("#app");
```

### Within `App.vue` or a given .vue file:

```html
<script>
// Import as many or few components as you need
import { Panel, Menus } from 'lokney';

export default {
  components: {
    Panel,
    Menus
  }
}
</script>
```
---

## Components

### - [Panel]()
### - [Menus]()


