<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png" />
    <!-- <HelloWorld msg="Welcome to Your Vue.js App" /> -->
    <amplify-authenticator>
      <div>
        <h1>Hey, {{ user.username }}</h1>
        <amplify-sign-out></amplify-sign-out>
      </div>
    </amplify-authenticator>
  </div>
</template>

<script>
// @ is an alias to /src
// @ts-ignore
// import HelloWorld from "@/components/HelloWorld.vue";
import { AuthState, onAuthUIStateChange } from "@aws-amplify/ui-components";

export default {
  name: "Home",
  components: {
    // HelloWorld
  },
  data() {
    return {
      user: {}
    };
  },
  created() {
    onAuthUIStateChange((state, user) => {
      if (state === AuthState.SignedIn) {
        this.user = user;
      }
    });
  }
};
</script>
