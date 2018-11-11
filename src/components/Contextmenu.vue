<template>
  <ul
    ref="contextmenu"
    :class="className"
    v-show="visible"
    :style="style">
    <slot />
  </ul>
</template>

<script lang="ts">
import {
  Component,
  Vue,

  Prop,
  Provide,
} from 'vue-property-decorator';

@Component
export default class VContextmenu extends Vue {
  @Prop({ default: 'normal' }) private theme!: string;
  @Prop({ default: 'contextmenu' }) private eventType!: string;
  @Prop({ default: true }) private autoPlacement!: boolean;
  @Prop() private disabled!: boolean;

  @Provide() $contextmenu = this;

  get className() {
    return [
      'v-contextmenu',
      `v-contextmenu--${this.theme}`,
    ];
  }
}
</script>
