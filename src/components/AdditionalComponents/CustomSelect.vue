<template>
  <div style="position:absolute; width: 100%;">
    <div class="select_head">{{selectedVariant}}
        <p @click="dropList" class="select_arrow" v-bind:class="{select_arrow_active: isDropped}"></p>
    </div>
    <div class="select_item" v-bind:class="{select_item_active: isDropped}" v-for="variant in variants" v-bind:key="variant" @click="selectItem(variant)">{{variant}}</div>
  </div>
</template>

<script>
export default {
  name: 'CustomSelect',
  data() {
    return {
      isDropped: false,
      selectedVariant: this.firstVariant
    }
  },
  props: {
    firstVariant: {
      type: String,
      required: true,
      default: ""
    },
    variants: {
      type: Array,
      required: true
    } 
  },
  methods: {
      dropList: function() {
        this.isDropped = !this.isDropped;
      },

      selectItem: function(variant) {
        this.selectedVariant = variant;
        this.isDropped = false;
      }
  }
}
</script>

<style>
.select_head {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: center;
  font-size: 15px;
  padding-bottom: 4px;
  color: rgb(185, 185, 185);
  border-bottom-color: rgb(185, 185, 185);
  border-bottom-width: 1px;
  border-bottom-style: solid;
}

.select_item {
  display: none;
}

.select_item_active {
  display: block;
  font-size: 15px;
  padding-top: 8px;
  padding-bottom: 8px;
  background-color:  rgb(202, 202, 202);
  border-bottom-color: rgb(168, 168, 168);
  border-bottom-width: 1px;
  border-bottom-style: solid;
  text-align: center;
}

.select_item_active:hover {
  background-color:  rgba(202, 202, 202, 0.5);
  color: rgba(0, 0, 0, 0.5);
  cursor: pointer;
}

.select_arrow {
  display: inline-block;
  border: solid rgb(168, 168, 168);
  border-width: 0 1px 1px 0;
  display: inline-block;
  padding: 3px;
  transform: rotate(45deg);
  cursor: pointer;
}

.select_arrow:hover, .select_arrow_active:hover{
  border: solid  rgb(185, 185, 185);
  border-width: 0 1px 1px 0;
}

.select_arrow_active {
  transform: rotate(-135deg);
}
</style>