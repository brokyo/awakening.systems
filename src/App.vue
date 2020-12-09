<template>
  <div id="container">
    <div id="lists">
      <div class="list" v-for="category in categories">
        <span>{{category.name}}</span>
        <ul>
          <li v-for="item in category.items"><a :href="item.url" target="_blank" @mouseover="activeItem = item" @mouseleave="activeItem = baseImage">{{item.name}}</a></li>
        </ul>
      </div>
    </div>
    <div id="display" v-if="activeItem">
      <div id="image" :style="{ backgroundImage: 'url(' + activeItem.image + ')' }" :class="{'logo-selected': activeItem == baseImage}">
        <div id="metaData" v-show="activeItem !== baseImage">
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
              name: 'vibrations',
              short: 'it only works if you believe it will',
              long: 'helping the universe communicate through the “meaningful coincidence” created by the unknowability of interconnected systems. AI-generated text combined with an esoteric color and sound system. Desktop application available that integrates with Philips Hue bulbs - email me for it.',
              tech: 'philips hue, gpt-2, tone.js, p5',
              url: 'http://vibrations.awakening.systems',
              image: 'images/prepare.png'
            },
            {
              name: 'digital prayers work',
              short: 'shrine to the little god of the wires',
              long: 'desktop and raspberry pi application to be your companion throughout the day. draw a circle to ask for advice.',
              tech: 'google wavenet voices, p5, tone.js, vue',
              url: 'https://www.dropbox.com/s/p68iu2ic5rtuyvs/digital_prayers_work-0.5.0.dmg?dl=0',
              image: 'images/dpw.png'
            },
            {
              name: 'late afternoon',
              short: 'a postcard from july 2020 at 3pm',
              long: 'devolving synth loop using colors and field recordings captured out my alphabet city window in July 2020.',
              tech: 'tone.js, zoom h4n recorder, p5',
              url: 'https://lateafternoon.awakening.systems/',
              image: 'images/la.png'
            },
            {
              name: 'breathing',
              short: 'in and out and in and out',
              long: 'generative drone and breathing exercise based on 3d perlin noise. spend a few minutes with it when you need it.',
              tech: 'p5, tone.js',
              url: 'https://breathe.awakening.systems/',
              image: 'images/breath.png'
            },
            {
              name: 'healing codes for the biological apocalypse',
              short: 'new age healing inkblot drone',
              long: 'graph of musical nodes based on the watts-strogatz random generation model. nodes are connected to their neighbors in a way that models real-world connections. over time healing solfeggio frequencies are introduced to nodes and get louder as they spread throughout the model. the drone is the network. inspired by setu',
              tech: 'p5, tone.js',
              url: 'https://healingcodes.awakening.systems/',
              image: 'images/sn.png'
            },
            {
              name: 'everything a cycle',
              short: 'tiny music boxes',
              long: 'a framework for creating probabilistic music systems with matching visuals. one possible example linked but view the code to easily make your own.',
              tech: 'tone.js, p5',
              url: 'https://everythingacycle.awakening.systems/',
              image: 'images/olp2.png'
            },
            {
              name: 'pools',
              short: 'things change slowly',
              long: 'simple, devolving patterns play and change over time while new york rushes by. compose and share your own.',
              tech: 'tone.js, nyc dot traffic cameras',
              url: 'https://pools.awakening.systems/',
              image: 'images/fade.png',
            },
            {
              name: 'other lives',
              short: 'windchimes',
              long: 'play little melodies while watching videos of things that could be. click "make a new one" to create and share your own',
              tech: 'tone.js, p5, vue',
              url: 'https://otherlives.awakening.systems/',
              image: 'images/olp.png'
            },
            {
              name: 'windows',
              short: 'drone paintings',
              long: 'early drone experimentation. configure a drone then click and drag on the screen to change drone and visuals. more instance open = more interesting effect.',
              tech: 'web audio api',
              url: 'https://windows.awakening.systems/',
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
            }
          ]
        },
        {
          name: 'etc',
          items: [
            {
              name: 'our little planet',
              short: 'ambient youtube videos',
              long: 'an ongoing series of long-form videos where nothing happens. audio is mixed with a simultaneous recording of the place\'s electromagnetic field',
              tech: 'iphone4, lom priezor, zoom h4n pro',
              url: 'https://www.youtube.com/watch?v=PL_BoTdG7vA&list=PLhNGcsSWZ_gA0fVJbWJHEwOKMGPKIYsBl&index=18',
              image: 'images/olp-v.jpg'
            },
            {
              name: 'additive synth',
              long: 'configurable tone.js synthesizer and loop composer. exports json and useful for creating sounds for web projects.',
              url: 'https://additivesynth.awakening.systems/',
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
              long: 'this is a collection of generative art systems inspired by the mystical corners of the internet (and some other stuff now, too.) they\'re created by alexander carusillo, a net artist in new york, new york. alexcarusillo@gmail.com',
              url: 'mailto:alexcarusillo@gmail.com',
              image: 'images/profile.jpg'
            }
          ]
        }
      ],
      baseImage: {
        long: 'antennas for the little god of the wires',
        image: 'images/logo.svg'
      }  
    }
  },
  mounted() {
    this.activeItem = this.baseImage
  }
};
</script>

<style lang="scss">
@import url('https://fonts.googleapis.com/css?family=Major+Mono+Display|Roboto+Mono');

body {
  background-color: #EDECE9;
  font-family: 'Roboto Mono', monospace;
}

li {
  list-style-type: square;
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

.logo-selected {
  background-position: center;
  background-repeat: no-repeat; 
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
