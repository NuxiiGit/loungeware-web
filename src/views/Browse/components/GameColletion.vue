<template>
  <div :class="`game-collection ${viewType}`">
    <div v-for="(game, i) in games" :key="i">
      <GameCollectionCard :game="game" :viewType="viewType" />
      <!-- <router-link
        class="content"
        :to="getRoute(game.author_slug, game.game_slug)"
      >
        <div class="cart-content">
          <Cart :size="cartSize" :name="game.name" />
        </div>
        <div class="list-content" v-if="viewType == 'list'">
          <div class="title">
            <strong>{{ game.config.game_name }}</strong
            ><br />
            <small>by {{ game.config.creator_name }}</small>
          </div>
        </div>
      </router-link> -->
    </div>
  </div>
</template>

<script lang="ts">
import LaroldImg from '@/components/LaroldImg.vue';
import GameCollectionCard from './GameCollectionCard.vue';
import { Component, Prop, Vue } from 'vue-property-decorator';
import { routeName } from '@/router';
import { LocalGameMetadata } from '@/plugins/lwMeta';
// import {  } from '@/plugins/lwMeta';
export type ViewType = 'grid' | 'list' | 'carts';

@Component({
  components: {
    LaroldImg,
    GameCollectionCard,
  },
})
export default class GameCollection extends Vue {
  @Prop(Array) games!: LocalGameMetadata[];
  @Prop(String) viewType!: ViewType;

  private get cartSize() {
    switch (this.viewType) {
      case 'list':
        return 0.5;
      case 'grid':
        return 1;
      case 'carts':
        return 1;
    }
    return 1;
  }

  private getRoute(authorSlug: string, gameSlug: string) {
    return {
      name: routeName('game-page'),
      params: {
        author: authorSlug,
        game: gameSlug,
      },
    };
  }
}
</script>
