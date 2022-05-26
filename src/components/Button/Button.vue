<script lang="ts">
import { ref, computed } from 'vue';
import { ButtonProps, Props} from '../../interface/Button/index'
export default {
  props: {
    buttonProps: { type: Object as ()=> Props, required: true },
  },
  setup(props: ButtonProps) {
    const buttonClass = computed(() => {
      return 'rb-button--' + props.buttonProps?.type + ' rb-button__size--' + props.buttonProps?.size
    });
    return { buttonClass }
  },
  methods: {
    clickFn() {
    }
  }
}
</script>

<template>
  <div
    :class="[buttonClass,'rb-button']"
    @click="clickFn()"
  >
    <div class="rb-button__content">
      {{buttonProps.label}}
    </div>
  </div>
</template>



<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
  .rb-button {
    font-size: 14px;
    font-weight: 600;
    cursor: pointer;
    display: inline-flex;
    text-align: center;
    line-height: 1;
    vertical-align: top;
    font-family: inherit;
    border-radius: 4px;
    box-sizing: border-box;
  }
  .rb-button__content {
    display: flex;
    align-items: center;
    margin: 0 auto;

    > span {
      margin-right: 4px;
    }

    > span:last-child {
      margin-right: 0;
    }
  }

  .rb-button__size--s {
    height: 27px;
    padding: 8px 16px;

    .rb-button__text,
    .rb-button__icon {
      font-size: 11px;
    }
  }

  .rb-button__size--m {
    height: 36px;
    padding: 12px 32px;

    .rb-button__text,
    .rb-button__icon {
      font-size: 13px;
    }
  }

  .rb-button__size--l {
    height: 41px;
    padding: 14px 40px;

    .rb-button__text,
    .rb-button__icon {
      font-size: 14px;
    }
  }

  .rb-button--filled {
    color: white;
    fill: white;
    background: Blue;
    &:hover {
      background: Blue;
      color: white;
    }
    &:active {
      background: Blue;
      color: white;
    }
  }

  .rb-button--hollow {
    color: grey;
    fill: grey;
    border: 1px solid grey;
    padding: 0px 12px;
    box-sizing: border-box;
    background: #fff;
    &:hover {
      color: black;
      fill: grey;
      border: 1px solid black;
    }
    &:active {
      background-color: grey;
      color: #fff;
    }
  }
  .rb-button--rounded {
    color: grey;
    fill: grey;
    border: 1px solid grey;
    padding: 0px 12px;
    box-sizing: border-box;
    background: #fff;
    border-radius: 50px;
    &:hover {
      color: black;
      fill: grey;
      border: 1px solid black;
    }
    &:active {
      background-color: grey;
      color: #fff;
    }
  }
</style>


