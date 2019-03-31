<template>
  <div class="container">
    <ul class="mosaic">
      <item-mosaic :key="key" v-for="(mosaic,key) in mosaics" :data="mosaic"/>
    </ul>
  </div>
</template>

<script>
import ItemMosaic from "./ItemMosaic.vue";
export default {
  name: "Mosaic",
  components: {
    ItemMosaic
  },
  data() {
    return {
      mosaics: [
        {
          type: "text",
          text: "Sabes, nunca pense que cambiarias tanto mi vida"
        },
        {
          type: "image",
          text: "pero lo que esta sucediendo ahora es ¡increible!",
          img: require("@/assets/mimi/9.jpg")
        },
        {
          type: "text",
          text: "me encanta la manera en que me miras a los ojos"
        },
        {
          type: "image",
          text: "me hace pensar que puedo alcanzar lo que sea.",
          img: require("@/assets/mimi/7.jpg")
        },
        {
          type: "image",
          text: "No se que esta pasando, pero disfruto tu compañía",
          img: require("@/assets/gif/6.jpg")
        },
        {
          type: "image",
          text: "creemos recuerdos y hagamoslo inolvidables",
          img: require("@/assets/gif/5.jpg")
        },
        {
          type: "image",
          text: "ya que posees un corazón ♥ muy grande",
          img: require("@/assets/mimi/5.jpg")
        },
        {
          type: "text",
          head: "Nunca lo olvides",
          text: "es hermoso"
        },
        {
          type: "text",
          text: "te agradeszo lo que haces por mí"
        },
        {
          type: "image",
          text: "asi que hora es mi turno hacer algo al respecto",
          img: require("@/assets/mimi/2.jpg")
        },
        {
          type: "text",
          text: "por eso creo que no hay imposibles"
        },
        {
          type: "image",
          text: "si hacemos la cosas juntos no habra quien nos detenga",
          img: require("@/assets/mimi/1.jpg")
        },
        {
          type: "image",
          text: "dicen que una mirada dice mas que mil palabras",
          img: require("@/assets/min/6.jpg")
        },
        {
          type: "text",
          text: "y creo que todo es cierto"
        },
        {
          type: "image",
          text: "puede que suene cursi pero...",
          img: require("@/assets/min/4.jpg")
        },
        {
          type: "text",
          text: "el amor es muy importante por eso no hay que dejar de creer"
        },
        {
          type: "text",
          text: "la confianza y el respeto son factores muy importantes"
        },
        {
          type: "image",
          text: "ambos nos daremos una mano para complementar",
          img: require("@/assets/min/2.jpg")
        },
        {
          type: "text",
          text: "compartir nuestras mejores virtudes"
        },
        {
          type: "text",
          text: "y hacer una dupla imparable."
        },
        {
          type: "image",
          text: "¿",
          img: require("@/assets/mimi/3.jpg")
        },
        {
          type: "image",
          text: "Deymi Oy",
          img: require("@/assets/mimi/4.jpg")
        },
        {
          type: "image",
          text: "Quieres ser mi...",
          img: require("@/assets/mimi/6.jpg")
        },
        {
          type: "image",
          text: "Mi media NACHA ('Upss naranja'). ?",
          img: require("@/assets/mimi/8.jpg")
        }
      ]
    };
  }
};
</script>

<style lang="scss">
// Base variables
$highlight: #870C35;
$bodybg: #f3f3f3;
$tilebg: #2e112d;

body {
  background-color: $bodybg;
}

img {
  width: auto;
  height: 100%;
}

a:link,
a:visited {
  text-decoration: none;
  color: inherit;
}

.container {
  z-index: 30;
  margin: 3em 0;
  display: grid;
  grid-template-columns: 1fr 28fr 1fr;
  grid-template-areas: ". mosaic .";
}

ul.mosaic {
  gird-area: mosaic;
  grid-column-start: 2;
  display: flex;
  overflow: hidden;
  flex-flow: row wrap;
  justify-content: flex-start;
  padding: 0;
  li.tile:before {
    content: "";
    display: block;
    padding-top: 100%;
    float: left;
  }
  li.tile {
    overflow: hidden;
    position: relative;
    display: block;
    width: 25%;
    box-sizing: border-box;
    list-style: none;
    background: $tilebg;
    a {
      display: block;
      height: 100%;
    }
  }
  li.text {
    a {
      padding: 2em;
      h4 {
        display: table-cell;
        vertical-align: middle;
        font-size: 36px;
        line-height: 1.1;
        letter-spacing: -1px;
      }
      .meta {
        font-size: 14px;
        margin-bottom: 1em;
        font-weight: 300;
        span.upcase {
          font-weight: 700;
          color: $highlight;
        }
      }
    }
    a:hover {
      background: $highlight;
      color: $tilebg;
      .meta .upcase {
        color: $tilebg;
      }
    }
  }
  li.image,
  li.video {
    a {
      figure {
        display: block;
        margin: 0;
        height: 100%;
        img {
          width: auto;
          height: 100%;
          position: absolute;
          top: 0;
          left: 0;
          opacity: 1;
          transition: all 0.4s;
          transform: scale(1.05);
        }
        figcaption {
          display: table;
          width: 100%;
          height: 100%;
          transition: all 0.4s;
          opacity: 0;
          span,
          i.fa {
            display: table-cell;
            vertical-align: middle;
            text-align: center;
            padding: 40px;
            font-size: 36px;
            font-weight: 700;
            color: #fff;
            line-height: 1.2;
            transition: all 0.4s;
          }
        }
      }
      figure:hover {
        img {
          opacity: 0.5;
        }
        figcaption {
          opacity: 1;
          background: rgba($highlight, 0.7);
          transform: scale(1);
        }
      }
    }
  }
}

// Media queries for adaptivity
@media screen and (min-width: 2048px) {
  .container {
    grid-template-columns: 1fr 14fr 1fr;
  }
  ul.mosaic {
    li.tile {
      width: 20%;
    }
    li.text {
      a {
        h4 {
          font-size: 36px;
        }
      }
    }
  }
}

@media screen and (min-width: 800px) and (max-width: 1079px) {
  ul.mosaic {
    li.tile {
      width: 33%;
    }
  }
}

@media screen and (min-width: 670px) and (max-width: 799px) {
  ul.mosaic {
    li.tile {
      width: 33%;
    }
    li.text {
      a {
        h4 {
          font-size: 27px;
        }
      }
    }
  }
}

@media screen and (min-width: 440px) and (max-width: 669px) {
  ul.mosaic {
    li.tile {
      width: 50%;
    }
    li.text {
      a {
        h4 {
          font-size: 27px;
        }
      }
    }
  }
}

@media screen and (max-width: 439px) {
  .container {
    grid-template-columns: 1fr 10fr 1fr;
  }
  ul.mosaic {
    // flex-flow: column wrap; == this would be the regular solution, but it's just breaks the hover effect ==
    li.tile {
      width: 100%;
    }
    li.text {
      a {
        h4 {
          font-size: 36px;
        }
      }
    }
  }
}
</style>

