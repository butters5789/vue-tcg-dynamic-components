<template>
  <div>
    <the-header></the-header>

    <button @click="setActiveComponent('badge-list')">Badge List</button>
    <button @click="setActiveComponent('user-info')">User Info</button>

    <component
      :is="activeComponent"
      :full-name="activeUser.name"
      :info-text="activeUser.description"
      :role="activeUser.role"
    />
  </div>
</template>

<script>
import BadgeList from './components/BadgeList.vue';
import TheHeader from './components/TheHeader.vue';
import UserInfo from './components/UserInfo.vue';

export default {
  components: {
    BadgeList,
    TheHeader,
    UserInfo,
  },
  data() {
    return {
      activeComponent: 'badge-list',
      activeUser: {
        name: 'Maximilian Schwarzmüller',
        description: 'Site owner and admin',
        role: 'admin',
      },
    };
  },
  methods: {
    setActiveComponent(component) {
      this.activeComponent = component;
    }
  }
};
</script>

<style>
html {
  font-family: sans-serif;
}

body {
  margin: 0;
}
</style>
