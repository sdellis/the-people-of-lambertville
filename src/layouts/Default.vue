<template>
  <div class="layout">
    <div class="grid">
      <header>
        <div class="siteHeader__section">
          <div class="siteHeader__item siteHeaderButton">The People of Lambertville</div>
          <!-- <a href="#" class="brand"><g-image alt="The People of Lambertville" src="~/favicon.png" width="135" /></a> -->
        </div>
        <div class="siteHeader__section">
          <div class="siteHeader__item siteHeaderButton">
            <input id="menu-toggle" type="checkbox" />
            <label class='menu-button-container' for="menu-toggle">
              <div class='menu-button'></div>
            </label>
            <ul class="menu siteHeader__item siteHeaderButton">
              <li>One</li>
              <li>Two</li>
              <li>Three</li>
              <li>Four</li>
              <li>Five</li>
            </ul>
          </div>
        </div>
        <!-- <div class="wrapper site-header__wrapper">
          <a href="#" class="brand"><g-image alt="The People of Lambertville" src="~/favicon.png" width="135" /></a>
          <div :class="{open: menuOpen}">
            <button class="burger" :class="{open: menuOpen}" @click="handleOpen">
              <div class="line line-1"></div>
              <div class="line line-2"></div>
            </button>
          </div>
          <nav class="nav" :class="{open: menuOpen}" ref="nav">
            <g-link class="nav__link" to="/about/"><span>About</span></g-link>
            <g-link class="nav__link" to="/map/"><span>Using this Portal</span></g-link>
            <g-link class="nav__link" to="/sched/"><span>Schedule an Interview</span></g-link>
          </nav>
        </div> -->
      </header>

      <main>
        <slot/>
      </main>

      <aside>
        <!-- Sidebar / Ads -->
      </aside>

      <footer>
        <!-- Footer content -->
      </footer>
      </div>
  </div>
</template>

<static-query>
query {
  metadata {
    siteName
  }
}
</static-query>
<script>
export default {
  data() {
    return {
      menuOpen: false,
    }
  },
  methods: {
    handleOpen() {
      this.menuOpen = !this.menuOpen;
    },
  }
}
</script>

<style>
body {
  font-family: -apple-system,system-ui,BlinkMacSystemFont,"Segoe UI",Roboto,"Helvetica Neue",Arial,sans-serif;
  margin:0;
  padding:0;
  line-height: 1.5;
}

.layout {
  max-width: 100%;
  margin: 0 auto;
}

.grid {
  display: grid;

  grid-template-areas:
    "header header header"
    "content content side"
    "footer footer footer";

  grid-template-columns: 1fr 1fr 1fr;
  grid-template-rows: auto 1fr auto;
  grid-gap: 1px;

  height: 100vh;
}

.grid > main {
  display: flex;
  align-items: center;
  justify-content: center;
}

header {
  grid-area: header;
}

nav {
  grid-area: nav;
}

main {
  grid-area: content;
}

aside {
  grid-area: side;
}

footer {
  grid-area: footer;
}


header,
nav,
article,
aside,
footer {
background: lightgray;
padding: 1em;
}

header, footer {
  grid-column: 1 / 4;
}

article {
  min-width: 15em;
}

.nav__link {
  margin-left: 20px;
}
/* burger */
header {
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: space-between;
  background-color: #56727C;
  /* W3C, IE 10+/ Edge, Firefox 16+, Chrome 26+, Opera 12+, Safari 7+ */
  color: #FFF;
  height: 50px;
  padding: 1em;
}

.siteHeader__section {
    /**
     * Lay out the children of this container with
     * flexbox.
     */
    display: flex;

    /**
     * Align the children in the center, along
     * the main axis. By default the children will
     * align along their top edges.
     */
    align-items: center;
}

.siteHeader__item {
  padding: 5px 15px;
  font-size: 12px;
}

.siteHeader__item + .siteHeader__item {
  margin-left: 5px;
}

.siteHeader__item.is-site-header-item-selected {
  color: #FFFFFF;
  background-color: #415F69;
  border-radius: 4px;
}

.menu {
  display: flex;
  flex-direction: row;
  list-style-type: none;
  margin: 0;
  padding: 0;
}

.menu > li {
  margin: 0 1rem;
}

.menu-button-container {
  display: none;
  height: 100%;
  width: 30px;
  cursor: pointer;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

#menu-toggle {
  display: none;
}

.menu-button,
.menu-button::before,
.menu-button::after {
  display: block;
  background-color: #fff;
  position: absolute;
  height: 4px;
  width: 30px;
  transition: transform 400ms cubic-bezier(0.23, 1, 0.32, 1);
  border-radius: 2px;
}

.menu-button::before {
  content: '';
  margin-top: -8px;
}

.menu-button::after {
  content: '';
  margin-top: 8px;
}

#menu-toggle:checked + .menu-button-container .menu-button::before {
  margin-top: 0px;
  transform: rotate(405deg);
}

#menu-toggle:checked + .menu-button-container .menu-button {
  background: rgba(255, 255, 255, 0);
}

#menu-toggle:checked + .menu-button-container .menu-button::after {
  margin-top: 0px;
  transform: rotate(-405deg);
}

@media (max-width: 768px) {
  .grid {
    grid-template-areas:
      "header"
      "content"
      "side"
      "footer";

    grid-template-columns: 1fr;
    grid-template-rows:
      auto /* Header */
      1fr /* Content */
      minmax(75px, auto) /* Sidebar */
      auto; /* Footer */
  }

  nav, aside {
    margin: 0;
  }

/* burger */
.menu-button-container {
    display: flex;
  }
  .menu {
    position: absolute;
    top: 0;
    margin-top: 50px;
    left: 0;
    flex-direction: column;
    width: 100%;
    justify-content: center;
    align-items: center;
  }
  #menu-toggle ~ .menu li {
    height: 0;
    margin: 0;
    padding: 0;
    border: 0;
    transition: height 400ms cubic-bezier(0.23, 1, 0.32, 1);
  }
  #menu-toggle:checked ~ .menu li {
    border: 1px solid #333;
    height: 2.5em;
    padding: 0.5em;
    transition: height 400ms cubic-bezier(0.23, 1, 0.32, 1);
  }
  .menu > li {
    display: flex;
    justify-content: center;
    margin: 0;
    padding: 0.5em 0;
    width: 100%;
    color: white;
    background-color: #222;
  }
  .menu > li:not(:last-child) {
    border-bottom: 1px solid #444;
  }


  /* button.burger {
    display: block;
  }
  header > div {
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    align-items: center;
    position: relative;
    z-index: 100;
    padding-left: 20px;
    padding-right: 20px;
  }
  header > div.open {
    transform: translateY(-80px);
    transition: all 500ms ease;
  }
  header > div.open strong a {
    color: white;
  }
  header > div.open button.burger .line {
    background-color: white;
  }
  nav.nav {
    position: absolute;
    top: 0;
    left: 0;
    transform: translateX(-200%);
    background: var(--text);
    color: white;
    height: 100vh;
    width: 100%;
    transition: all 500ms ease;
    z-index: 99;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    width: 100%;
    margin: 0 auto;
    padding-top: 32px;
  }
  nav.nav.open {
    transform: translateX(0%);
  }
  nav.nav.close {
    background: blue;
  }
  nav.nav a.nav__link {
    color: white;
    font-size: 32px;
    margin: 24px 0;
  }
  nav.nav a.nav__link.active {
    color: var(--dark-gold);
  }
  nav.nav a.nav__link:hover {
    transform: none;
  } */
}

/* nav.nav {
  border-top: 1px solid var(--border);
  display: flex;
  justify-content: space-between;
  padding: 10px;
  margin-top: 10px;
}
nav.nav .nav__link {
  font-size: 24px;
  color: var(--text);
  text-decoration: none;
  position: relative;
  font-weight: 400;
  display: inline-block;
  transition: all 200ms ease;
  font-family: 'Open Sans', sans-serif;
}
nav.nav .nav__link span {
  width: 100%;
  height: 100%;
  display: inline-block;
  transition: all 200ms ease;
}
nav.nav .nav__link span:hover {
  transform: translateY(-3px);
}
nav.nav .nav__link.active span {
  transform: translateY(-3px);
}
nav.nav .nav__link.active::after {
  width: 100%;
}
nav.nav .nav__link::after {
  content: '';
  position: absolute;
  bottom: 0;
  left: 0;
  width: 0%;
  height: 1px;
  background: var(--border);
  transition: all 200ms ease;
  transform-origin: center;
}
nav.nav .nav__link:hover::after {
  width: 100%;
}
button.burger {
  display: none;
  border: none;
  background: none;
  width: 50px;
  height: 40px;
  z-index: 100;
  cursor: pointer;
}
button.burger .line {
  width: 100%;
  height: 2px;
  border-radius: 20px;
  background-color: white;
  margin: 12px 0;
  transition: all 1000ms ease;
}
button.burger.open .line-1 {
  transform: translateY(7px) rotate(45deg);
}
button.burger.open .line-2 {
  transform: translateY(-7px) rotate(-45deg);
} */
</style>
