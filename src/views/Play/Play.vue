<template>
  <div class="text-center">
    <iframe
      class="media-border"
      src="/static/game/index.html"
      style="width: 540px; height: 540px; margin-top: 80px"
    />
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';

@Component({
  metaInfo: {
    title: 'Play',
  },
})
export default class Play extends Vue {}
</script>

<style scoped lange="scss">
iframe {
  overflow: hidden;
}
</style>
