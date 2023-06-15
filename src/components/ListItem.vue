<template>
  <li>
    <div
      v-on:mouseover="onHoverShowActionBtn"
      v-on:mouseleave="onLeaveShowActionBtn"
    >
      <div v-on:click.prevent="onClickListItem">
        <span v-if="children.length > 0 && !showChildren">[>]</span>
        <span v-if="children.length > 0 && showChildren">[v]</span> {{ name }}
      </div>
      <div v-show="showActionBtn">
        <button>-</button>
        <button v-on:click.prevent="onClickAddItem">+</button>
      </div>
    </div>
    <ul>
      <ListItem
        v-show="showChildren"
        v-for="(item, key) in children"
        :key="key"
        :name="item.name"
        :children="item.children ? item.children : []"
      />
      <li v-show="showAddItem">
        <button style="margin: -5px 10px 0px 0px">+</button
        ><span>ADD GENERAL TYPO</span>
      </li>
    </ul>
  </li>
</template>


<script>
export default {
  name: "ListItem",
  props: {
    name: String,
    children: Array,
  },
  data: function () {
    return {
      showAddItem: false,
      showChildren: false,
      showActionBtn: false,
    };
  },
  methods: {
    removeItem(item) {
      this.$emit("remove-item", item);
    },
    onClickAddItem() {
      this.showAddItem = true;
    },
    onClickListItem() {
      if (!this.showAddItem) {
        this.showChildren = !this.showChildren;
      }
      this.showAddItem = false;
    },
    onHoverShowActionBtn() {
      this.showActionBtn = true;
    },
    onLeaveShowActionBtn() {
      this.showActionBtn = false;
    },
  },
};
</script>

<style scoped>
* {
  /* border: 1px dotted red;*/
}
li {
  list-style-type: none;
  text-align: left;
}
li > div {
  display: flex;
  background-color: #eff0f1;
  margin: 5px;
}

li > ul > li:last-child {
  background-color: #fafafc;
  padding: 10px;
  margin: 1px;
}

li > div:hover,
li > ul > li:last-child:hover {
  background-color: #cacacb;
  cursor: pointer;
}

li > div > div:first-child {
  width: 80%;
  height: 100%;
  padding: 10px;
}

li > div > div:last-child {
  width: 20%;
  height: 100%;
  padding: 10px;
}

button {
  border-radius: 5px;
  margin: 1px;
}
</style>