<template>
  <div class="container full-width">
    <div class="row center-xs">
      <div class="col-xs-12">
        <h2>
          <larold-img name="ghost larold" class="mr-1" />
          <router-link :to="{ name: 'browse' }">All Games</router-link>
          /
          <strong> {{ authorName }} </strong>
        </h2>
        <GameCollection viewType="list" :games="games" />
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import LaroldImg from '@/components/LaroldImg.vue';
import GameCollection from './components/GameColletion.vue';
import { Component, Vue } from 'vue-property-decorator';

@Component({
  components: {
    LaroldImg,
    GameCollection,
  },
  metaInfo() {
    return {
      title: this.$route.params.author,
    };
  },
})
export default class Browse extends Vue {
  private get games() {
    return this.$lwMeta.getGamesByAuthor(this.$route.params.author);
  }

  private get authorName() {
    return this.$lwMeta.findAuthorDisplayName(this.$route.params.author); //this.games.length > 0 ? this.games[0].authors : 'no author';
  }
}
</script>
