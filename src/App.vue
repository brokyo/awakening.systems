<template>
  <div id="container">
    <div id="lists">
      <div class="list" v-for="category in categories">
        <span>{{category.name}}</span>
        <ul>
          <li v-for="item in category.items"><a :href="item.url" target="_blank" @mouseover="activeItem = item" @mouseleave="activeItem = categories[2].items[3]">{{item.name}}</a></li>
        </ul>
      </div>
    </div>
    <div id="display" v-if="activeItem">
      <div id="image" :style="{ backgroundImage: 'url(' + activeItem.image + ')' }">
        <div id="metaData">
          <p id="title">{{activeItem.name}}</p>
          <p id="short">{{activeItem.short}}</p>
        </div>
      </div>
      <p id="description">{{activeItem.long}}</p>
      <div id="tech" v-if="activeItem.tech">
        <label>built in:</label>
        <p>{{activeItem.tech}}</p>
      </div>
    </div>
    <signup></signup>
  </div>
</template>

<script>
import signup from './components/signup.vue'

export default {
  name: 'site',
  components: {signup: signup},
  data() {
    return {
      activeItem: '',
      categories: [
        {
          name: 'awakening.systems',
          items: [
            {
              name: 'digital prayers work',
              short: 'shrine to the little god of the wires',
              long: 'alpha of a desktop and raspberry pi application to be your companion throughout the day. draw a circle to ask for advice.',
              tech: 'google wavenet voices, p5, tone.js, vue',
              url: 'https://www.dropbox.com/s/p68iu2ic5rtuyvs/digital_prayers_work-0.5.0.dmg?dl=0',
              image: 'images/dpw.png'
            },
            {
              name: 'breathing',
              short: 'in and out and in and out',
              long: 'generative drone and breathing exercise based on 3d perlin noise. spend a few minutes with it when you need it.',
              tech: 'p5, tone.js',
              url: 'https://breathe.under-construction.club/',
              image: 'images/breath.png'
            },
            {
              name: 'waves [for anna and dylan]',
              short: 'generative art instillation',
              long: 'configurable generative art piece attempting to induce synesthesia. philips hue lightbulbs matched to a software synthesizers. play in a dark, quiet room. link is a video of a performance but email me if you`d like the application',
              tech: 'tone.js, philips hue, speakers',
              url: 'https://www.youtube.com/watch?v=C7_RPvi7zDg',
              image: 'images/waves.jpg'
            },
            {
              name: 'everything a cycle',
              short: 'tiny music boxes',
              long: 'a framework for creating probabilistic music systems with matching visuals. one possible example linked but view the code to easily make your own.',
              tech: 'tone.js, p5',
              url: 'https://everythingacycle.under-construction.club/',
              image: 'images/olp2.png'
            },
            {
              name: 'pools',
              short: 'things change slowly',
              long: 'simple, devolving patterns play and change over time while new york rushes by. compose and share your own.',
              tech: 'tone.js, nyc dot traffic cameras',
              url: 'https://pools.under-construction.club/',
              image: 'images/fade.png',
            },
            {
              name: 'other lives',
              short: 'windchimes',
              long: 'play little melodies while watching videos of things that could be. click "make a new one" to create and share your own',
              tech: 'tone.js, p5, vue',
              url: 'https://ourlittleplanet.under-construction.club/',
              image: 'images/olp.png'
            },
            {
              name: 'windows',
              short: 'drone paintings',
              long: 'early drone experimentation. configure a drone then click and drag on the screen to change drone and visuals. more instance open = more interesting effect.',
              tech: 'web audio api',
              url: 'https://windows.under-construction.club/',
              image: 'images/windows.png'
            }
          ]
        },
        {
          name: 'position: absolute',
          items: [
            {
              name: 'in excelsis i/o',
              short: 'building a digital choir',
              long: 'a blog post detailing how to build a digital choir and explaining the context of decisions',
              tech: 'tone.js, vue.js',
              url: 'https://medium.com/@brokyo/in-excelsis-i-o-creating-digital-choirs-in-tone-js-f14d84982409?source=friends_link&sk=76cfd3279443d1ac9b4e2a0a2ddcf8a0',
              image: 'images/choir.png'
            },
            {
              name: 'saijiki.js',
              short: 'a 歳時記 for net artists and computational poets',
              long: 'A JavaScript implementation of a Japanese poetry reference book for digital art. This is a bunch of things at once. A JS library, a blog post about that library, and a demo site.  ',
              tech: 'saijiki.js',
              url: 'https://medium.com/@brokyo/saijiki-js-%E6%AD%B3%E6%99%82%E8%A8%98-for-net-artists-and-computational-poets-adc93f68eff4?source=friends_link&sk=71dbd25cbcc67361a440ccc9946defa5',
              image: 'images/saijiki.png'
            },
            {
              name: 'drawing the flower of life',
              short: 'sacred geometry in code',
              long: 'a primer on sacred geometry and a basic tutorial on how to create the flower of life in p5',
              tech: 'p5',
              url: 'https://medium.com/@brokyo/drawing-the-flower-of-life-22206fe36d02?source=friends_link&sk=07f773e2191b36fe377df0788b6058d3',
              image: 'images/fol.png'
            },
            {
              name: 'our little planet',
              short: 'ambient youtube videos',
              long: 'an ongoing series of long-form videos where nothing happens. audio is mixed with a simultaneous recording of the place\'s electromagnetic field',
              tech: 'iphone4, lom priezor, zoom h4n pro',
              url: 'https://www.youtube.com/watch?v=PL_BoTdG7vA&list=PLhNGcsSWZ_gA0fVJbWJHEwOKMGPKIYsBl&index=18',
              image: 'images/olp-v.jpg'
            },
            {
              name: 'healing codes for the biological apocalypse',
              short: 'new age healing inkblot drone',
              long: 'graph of musical nodes based on the watts-strogatz random generation model. nodes are connected to their neighbors in a way that models real-world connections. over time healing solfeggio frequencies are introduced to nodes and get louder as they spread throughout the model. the drone is the network. inspired by setu',
              tech: 'p5, tone.js',
              url: 'https://healingcodes.under-construction.club/',
              image: 'images/sn.png'
            }
          ]
        },
        {
          name: 'everything else',
          items: [
            {
              name: 'geocities spelunker',
              long: 'random access geocities archive and user-generated hall of fame. take a moment for those who came before.',
              url: 'https://spelunker.under-construction.club/',
              image: 'images/su.png'
            },
            {
              name: 'additive synth',
              long: 'configurable tone.js synthesizer and loop composer. exports json so extremely useful for creating sounds for web projects.',
              url: 'https://additive-synth.under-construction.club/',
              image: 'images/as.png'
            },
            {
              name: 'photos',
              long: 'photos taken using plastic cameras and expired/home made film',
              url: 'https://www.flickr.com/photos/95717285@N00/sets/72157702680866031',
              image: 'images/flickr.jpg'
            },
            {
              name: 'contact/about',
              long: 'hiya. i\'m alex carusillo, a net artist in new york, new york and this is a sample of the projects i\'ve been working on. if you haven\'t looked at something in awhile check it out again. there may be something new. i\'m always interested in collaborations or just saying hello. alexcarusillo@gmail.com.',
              image: 'images/profile.jpg'
            }
          ]
        }
      ]      
    }
  },
  mounted() {
    this.activeItem = this.categories[2].items[3]
  }
};
</script>

  <!-- background-color: ; -->
<style lang="scss">
@import url('https://fonts.googleapis.com/css?family=Major+Mono+Display|Roboto+Mono');

body {
  background-color: #EDECE9;
  font-family: 'Roboto Mono', monospace;
}

#container {
  display: flex;
  width: 800px;
  height: 500px;
  margin: 40px auto;
}

#lists {
  flex-basis: 60%;
  font-size: 14px;
}

#display {
  flex-basis: 40%;

#image {
    height: 300px;
    width: 300px;
    background-size: contain;
    border: 1px solid black;
    margin: 0 auto;

    #metaData {
      background-color: rgba(255,255,255,0.7);
      padding: 10px;

      #title {
        font-family: 'Major Mono Display', monospace;
        margin: 0;
      }

      #short {
        font-size: 12px;
        margin-top: 5px;
      }

    }


    #title:first-letter{
      text-transform: capitalize
    }
  }
}

#description {
  width: 300px;
  margin: 10px auto;
  font-size: 12px;
}

#tech {
  width: 300px;
  margin: 20px auto;
  font-size: 12px;

  label {

  }

  p {
    margin: 0
  }
}

#signup {
  background-color: #EDECE9;
  border-top: 1px solid black;
  position: fixed;
  bottom: 0;
  left: 0;
  width: 100%;
  font-size: 10px;
}

</style>
