<template>
  <div class="layout">
    <div class="grid">
      <header>
        <div class="siteHeader__section">
          <g-link class="brand" to="/"><g-image alt="The People of Lambertville" src="~/favicon.png" width="135" /></g-link>
          <div class="siteHeader__item siteHeaderButton"><g-link class="brand" to="/">The People of Lambertville</g-link></div>
        </div>
        <div class="siteHeader__section">
          <div class="siteHeader__item siteHeaderButton">
            <input id="menu-toggle" type="checkbox" />
            <label class='menu-button-container' for="menu-toggle">
              <div class='menu-button'></div>
            </label>
            <ul class="menu siteHeader__item siteHeaderButton">
              <li><g-link class="nav__link" to="/about/"><span>About</span></g-link></li>
              <li><g-link class="nav__link" to="/about/"><span>Using This Portal</span></g-link></li>
              <li><g-link class="nav__link" to="/about/"><span>Schedule An Interview</span></g-link></li>
            </ul>
          </div>
        </div>
      </header>
      <slot/>
      <footer>
        <p><span>©2022 </span> <a href="/">Lambertville Human Rights Council</a></p>
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

<style>
body {
  font-family: 'Josefin Slab', serif;
  margin:0;
  padding:0;
  line-height: 1.5;
  font-size: 2em;
}

.layout {
  max-width: 100%;
  margin: 0 auto;
}

.grid {
  display: grid;

  grid-template-areas:
    "header header header"
    "title title title"
    "content content side"
    "footer footer footer";

  grid-template-columns: 1fr 1fr 1fr;
  grid-template-rows: auto auto 1fr auto;
  grid-gap: 1px;

  height: 100vh;
}

.grid > main, aside {
  padding: 2em;
}

aside ul {
  list-style: none;
  padding: 0;
  font-size: 1em;
}

aside li {
  font-size: .6em;
  line-height: 1.5em;
}

aside li > a{
  border-bottom: 1px solid #b5b7b7;
  color: black;
  text-decoration: none;
}

a:hover {
  border-color: black;
}

main h2, aside h2 {
  color: #b5b7b7;
  font-size: .8em;
  text-transform: uppercase;
  margin: 0;
}

footer {
  padding: 0em 2em 1em;
  font-size: .6em;
  color: white;
}
footer a {
  color: white;
}

.header-wrap {
  grid-area: title;
  background-color: #b5b7b7;
  font-size: 28px;
  max-width: 100%;
  line-height: 1.1;
  color: white;
  padding: 1em 2em 1em;
  display: flex;
  justify-content: space-between;
  flex-direction: row;
  gap: 5%;
}

/* .record {
  width: 50%;
  height: 100%;
} */
.portrait {
  width: 40%;
  display: flex;
  align-items: center;
  justify-content: center;
  overflow: hidden;
}

.portrait img {
  flex-shrink: 0;
  min-width: 100%;
  min-height: 100%;
}

header a {
  color: white;
  text-decoration: none;
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

footer {
  background-color: #56727C;
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
  font-size: 18px;
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
      "title"
      "content"
      "side"
      "footer";

    grid-template-columns: 1fr;
    grid-template-rows:
      auto /* Header */
      auto /* Title */
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
}
</style>
