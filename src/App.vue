<template>
  <a-row type="flex" id="header-row" justify="space-between">
    <a-col
      :xs="{ span: 22 }"
      :lg="{ span: 16 }"
      :xl="{ span: 10 }"
      id="header-col"
    >
      <Header />
    </a-col>
  </a-row>
  <a-row type="flex" id="view-row" justify="space-between">
    <a-col :span="22">
      <router-view />
    </a-col>
  </a-row>
</template>

<script>
import Header from "./components/Header.vue";

export default {
  name: "App",
  data() {
    return {
      msg: "hello",
    };
  },
  components: {
    Header,
  },
};
</script>

<style lang="scss">
#app {
  text-align: center;
}
#header-row {
  padding-top: 1rem;
}
#view-row {
  padding-top: 1rem;
}
#header-col {
  margin-left: auto;
  margin-right: auto;
}
</style>
