<template>
  <li class="tile" v-bind:class="{'text': data.type == 'text', 'image': data.type  == 'image'}">
    <a href="#" v-on:click.prevent v-if="data.type  == 'text'">
      <div class="meta">
        <span class="upcase">{{data.head}}</span>
      </div>
      <h4 class="sans">{{data.text}}</h4>
    </a>
    <a href="#" v-on:click.prevent v-else-if="data.type  == 'image'">
      <figure>
        <img :src="data.img" alt>
        <figcaption>
          <span>{{data.text}}</span>
        </figcaption>
      </figure>
    </a>
  </li>
</template>

<script>
export default {
  name: "ItemMosaic",
  props: {
    data: {
      type: Object
    }
  }
};
</script>

