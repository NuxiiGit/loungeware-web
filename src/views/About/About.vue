<template>
  <div class="container">
    <div class="row center-xs">
      <div class="col-xs-12">
        <h2>Welcome To Loungeware</h2>
        <p>
          Loungeware is a collection of microgames in the style of Warioware
          that is made by volunteers all over the world in
          <strong>GameMaker Studio 2</strong>. Anyone can play for free or
          submit their own game. Checkout the video below or
          <router-link :to="navItems.play.to">
            play it now in your browser!
          </router-link>
        </p>
      </div>
    </div>
    <div class="row center-xs">
      <div class="col-xs-12 col-sm-9">
        <video
          class="media-border"
          height="auto"
          controls
          width="100%"
          poster="/static/images/video-preview.png"
        >
          <source
            src="https://cdn.discordapp.com/attachments/862889240249892875/878669776107487293/lw-3nd-pass.mp4"
            type="video/mp4"
          />

          Sorry, your browser doesn't support embedded videos.
        </video>
      </div>
    </div>

    <div class="row center-xs">
      <div class="col-xs-12">
        <h2><LaroldImg name="rad larold" /> How To Play</h2>
        <p>
          The easiest way to play Loungeware is right here in your web browser!
          Follow the link below to get lounging. If you prefer to "own" your
          games as cold, hard files-on-your-computer, you can enjoy Loungeware
          offline by downloading one of the executable programs from the
          project's <a href="https://github.com/spacebake/Loungeware/releases">GitHub page</a>.
        </p>

        <div class="text-center">
          <router-link
            :to="{ name: 'play' }"
            class="btn btn-lg red solid mb-2 mt-2"
          >
            <mdicon size="64" name="language-html5" />
            Play Now In HTML5
          </router-link>
        </div>
      </div>
    </div>

    <div class="border" />

    <div class="row center-xs">
      <div class="col-xs-12">
        <h2>
          <LaroldImg name="headphone larold" />
          Get Involved With A Vibrant Community
        </h2>
        <p>
          The Loungeware community includes a kind, dedicated group of
          contributers and gamers. If you are interested at all in Loungeware,
          feel free to check out the discord community for active updates and
          discussion.
        </p>

        <div class="text-center">
          <a
            :href="navItems.discord.to"
            class="btn btn-lg discord solid mb-2 mt-2"
          >
            <mdicon size="64" name="discord" />
            {{ navItems.discord.label }}
          </a>
        </div>
      </div>
    </div>

    <div class="border" />

    <div class="row center-xs">
      <div class="col-xs-12">
        <h2>
          <LaroldImg name="artist larold" />
          How To Contribute
        </h2>
        <p>
          Loungeware requires a license to GameMaker Studio 2. If you fit this
          description, you can contribute to the project by forking the
          project on GitHub. Make sure to read the <a href="https://github.com/spacebake/Loungeware/wiki">wiki page</a>
          for help and guidelines on how to contribute.
        </p>

        <div class="text-center">
          <a
            :href="navItems.github.to"
            class="btn btn-lg github solid mb-2 mt-2"
          >
            <mdicon size="64" name="github" />
            {{ navItems.github.label }}
          </a>
        </div>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';
import { RouteName, getLinkPath } from '@/router';
import LaroldImg from '@/components/LaroldImg.vue';

@Component({
  components: { LaroldImg },
  metaInfo: {
    title: 'About',
  },
})
export default class About extends Vue {
  private navItems = {
    play: {
      to: {
        name: 'play' as RouteName,
      },
      label: 'play',
    },
    github: {
      to: getLinkPath('github'),
      label: 'Fork On Github',
    },
    discord: {
      to: getLinkPath('discord'),
      label: 'Join Our Discord',
    },
  };
}
</script>
