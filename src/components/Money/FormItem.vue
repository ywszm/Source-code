<template>
  <div>
    <label class="formItem">
      <span class="name">{{this.fieldName}}</span>
      <input type="text"
             :value="value"
             @input="onValueChanged($event.target.value)"
             :placeholder="this.placeholder">
    </label>
  </div>
</template>

<script lang="ts">
  import Vue from 'vue';
  import {Component, Prop, Watch} from 'vue-property-decorator';

  @Component
  export default class FormItem extends Vue {
    @Prop({default: ''}) readonly value!: string;

    @Prop({required: true}) fieldName!: string;
    @Prop() placeholder?: string;

    onValueChanged(value: string) {
      this.$emit('update:value', value);
    }
  }
</script>

<style lang="scss" scoped>
  .formItem {
    font-size: 14px;
    padding-left: 16px;
    display: flex;
    align-items: center;
    border-radius: 8px;
    border: 1px;
    .name {
      padding-right: 16px;
    }
    input {
      border: 1px solid #cbc7c7;
      height: 35px;
      flex-grow: 1;
      background: #eae9e9;
      /*border: none;*/
      margin-right: 10px;
      padding-left: 5px;
      border-radius: 4px;
    }
  }
</style>
