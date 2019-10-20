<template>
  <li 
    v-on:click="changeActive()" 
    v-bind:class="{ checked: this.isCheck }"> {{item.text}}
    <span class="close" v-on:click="removeItem()">×</span>
  </li>
</template>

<script>
export default {
  name: "todo-item",
  props: {
    item: Object
  },
  data: function() {
    return {
      isCheck: false,
    }
  },
  methods: {
    removeItem: function() {
      const { id } = this.item;
      this.$emit('remove-item-emit', id);
    },
    changeActive: function() {
      this.isCheck = !this.isCheck;
    }
  },
}
</script>

<style scoped>
  li:nth-child(odd) {
    background: #f9f9f9;
  }

  li {
    cursor: pointer;
    position: relative;
    padding: 12px 8px 12px 40px;
    list-style-type: none;
    background: #eee;
    font-size: 18px;
    transition: 0.2s;
    user-select: none;
  }

  .close {
    position: absolute;
    right: 0;
    top: 0;
    padding: 12px 16px 12px 16px;
  }

  .close:hover {
    background-color: #f44336;
    color: white;
  }

  li.checked {
    background: #888;
    color: #fff;
    text-decoration: line-through;
  }

  li.checked::before {
    content: '';
    position: absolute;
    border-color: #fff;
    border-style: solid;
    border-width: 0 2px 2px 0;
    top: 10px;
    left: 16px;
    transform: rotate(45deg);
    height: 15px;
    width: 7px;
  }
</style>

