<template>
  <section>
    <base-card>
      <template #header>
        <h3>{{ fullName }}</h3>
        <base-badge :type="role" :caption="role.toUpperCase()"></base-badge>
      </template>

      <template #default>
        <p>{{ infoText }}</p>

        <input type="text" ref="user" />
        <button @click="setUser">Set User</button>
      </template>
    </base-card>

    <teleport to="body">
      <error-alert v-if="inputIsInvalid">
        <h2>Ohh no an error has occurred!</h2>
        <p>Input must not be blank.</p>
        <button @click="closeError">Close</button>
      </error-alert>
    </teleport>
  </section>
</template>

<script>
import BaseCard from './BaseCard.vue';
import ErrorAlert from './ErrorAlert.vue';

export default {
  components: {
    BaseCard,
    ErrorAlert,
  },
  props: ['fullName', 'infoText', 'role'],
  data() {
    return {
      inputIsInvalid: false,
    };
  },
  methods: {
    closeError() {
      this.inputIsInvalid = false;
    },
    setUser() {
      const newUser = this.$refs.user.value;

      if (newUser === '') {
        this.inputIsInvalid = true;
      }
    },
  },
};
</script>
