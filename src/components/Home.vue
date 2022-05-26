<script lang="ts">
import { ref } from 'vue';
import { Props } from '../interface/Button/index'
import Button from './Button/Button.vue'
export default {
  components: {
    Button
  },
  setup() {
    const count = ref(0)
    const buttonList = ref<Props[]>([
      {type:"hollow", label:"Hollow Button", size:"s"},
      {type:"rounded", label:"Rounded Button", size:"m"},
      {type:"filled", label:"Filled Button", size:"l"}
    ])
    return {
      count, buttonList
    }
  },
  props: {
    msg: String
  },
  methods: {
    clickFn(event: any) {
      console.log(event.target.value) 
    }
  }

}
</script>

<template>
  <div class="container">
    <div style="display: flex; flex-direction: column;">
      <div style="display: flex" class="content">
        <h1>{{ msg }}</h1>
        <button type="button" @click="count++">count is: {{ count }}</button>
      </div>
      <div class="content">
        <Button v-for="(button, index) in buttonList" :key="index" :button-props="button" class="btn" :click-fn="() => clickFn('')" />
        <!-- <Button class="btn" :button-props='{type:"hollow", label:"Hollow Button", size:"s"}' :click-fn="() => clickFn('')" /> -->
        <!-- <Button class="btn" type="hollow" label="Hollow Button" size="s" :click-fn="() => clickFn('')" />
        <Button class="btn" type="rounded" label="Rounded Button" size="m" :click-fn="() => clickFn('')" />
        <Button class="btn" type="filled" label="Filled Button" size="l" :click-fn="() => clickFn('')" /> -->
        <p>Hello</p>
        <p>Hello1</p>
      </div>
    </div>
  </div>
</template>

<style lang="scss" scoped>
.container {
  display: flex;
  justify-content: center;
}

.content {
  width: fit-content;
  display: flex;
  align-items: center;

  &>.btn {
    margin-right: 1rem;
  }
}
</style>

<!--
// import Button from './Button.vue'
// defineProps<{ msg: string }>()
// const count = ref(0)

// function clickFn(event: any) {
//   console.log(event.target.value) 
// } -->