<template>
  <template v-if="activeView == 'group-view' || activeView == 'card-view'">
    <nav class="navbar navbar-expand-lg navbar-light bg-light">
      <div class="container-fluid">
        <a class="navbar-brand">Pantone</a>
        <div class="collapse navbar-collapse" id="navbarSupportedContent">
          <ul class="navbar-nav me-auto mb-2 mb-lg-0">
            <li class="nav-item">
              <button
                type="button"
                @click="switchHome"
                class="btn btn-outline-secondary"
              >
                Home
              </button>
            </li>
          </ul>
          <form class="d-flex">
            <input
              class="form-control me-2"
              type="search"
              placeholder="Search"
              aria-label="Search"
            />
            <button class="btn btn-outline-success" type="submit">
              Search
            </button>
          </form>
        </div>
      </div>
    </nav>
  </template>
  <intro v-if="activeView == 'intro'"></intro>
  <group-view v-if="activeView == 'group-view'"></group-view>
</template>

<script>
import Intro from "./components/Intro.vue";
import GroupView from "./components/GroupView.vue";
export default {
  name: "App",
  components: {
    Intro,
    GroupView,
  },
  data() {
    return {
      activeView: "group-view",
      introTimer: null,
    };
  },
  mounted() {
    this.introTimer = setTimeout(() => {
      this.switchHome();
    }, 1000);
  },
  methods: {
    switchHome() {
      this.activeView = "group-view";
    },
  },
};
</script>

<style>
.navbar-brand {
  font-size: 26px;
}
#app {
  height: 100%;
}
html,
body {
  height: 100%;
}
</style>