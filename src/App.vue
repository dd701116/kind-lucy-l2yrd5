<template>
  <img
    alt="Vue logo"
    width="200"
    src="https://www.larka.com/logo/larka_logob.png"
  />
  <HelloWorld v-show="false" msg="Hello Vue 3 in CodeSandbox!" />
  <ListItem
    name="test 0"
    :children="[
      {
        name: 'test 1',
        children: [{ name: 'test 1-1' }, { name: 'test 1-2' }],
      },
      { name: 'test 2' },
      { name: 'test 3' },
      {
        name: 'test 4',
        children: [
          {
            name: 'test 4-1',
            children: [{ name: 'test 4-1-1' }, { name: 'test 4-1-2' }],
          },
          { name: 'test 4-2' },
        ],
      },
    ]"
  ></ListItem>
</template>

<script>
import HelloWorldVue from "./components/HelloWorld.vue";
import ListItemVue from "./components/ListItem.vue";
export default {
  name: "App",
  components: {
    HelloWorld: HelloWorldVue,
    ListItem: ListItemVue,
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
