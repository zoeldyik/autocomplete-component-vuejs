<template>
  <div class="pt-5">
    <b-form-input
      autocomplete="off"
      v-model="text"
      placeholder="search your fruit"
      type="search"
      @focus="showList = true"
      @blur="showList = false"
    ></b-form-input>

    <div class="items-box mt-1">
      <b-list-group v-if="showList">
        <b-list-group-item
          v-for="(item,i) in filterItem"
          :key="i"
          @mousedown="select(item)"
        >{{item}}</b-list-group-item>
      </b-list-group>
    </div>
  </div>
</template>

<script>
export default {
  props: ["items"],
  data() {
    return {
      text: "",
      showList: false
    };
  },
  methods: {
    select(item) {
      this.text = item;
      this.showList = false;
    },
    blur() {
      this.showList = false;
      this.text = "";
    }
  },
  computed: {
    filterItem() {
      if (this.text.length == 0) {
        return this.items;
      }

      return this.items.filter(e =>
        e.toLowerCase().includes(this.text.toLowerCase())
      );
    }
  },
  watch: {
    // text(val) {
    //   if (val == "") {
    //     this.showList = true;
    //   }
    // }
  }
};
</script>

<style scoped>
.items-box {
  height: 240px;
  overflow: hidden;
  overflow-y: auto;
  border-radius: 0.25rem;
}

.items-box >>> .list-group-item {
  cursor: pointer;
}
.items-box >>> .list-group-item:nth-child(even) {
  background-color: #20c997;
  color: white;
}
</style>
