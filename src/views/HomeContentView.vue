<script setup>
import Banner from '@/components/Banner.vue';
import TheWelcome from '../components/TheWelcome.vue'
</script>

<template>
  <main>
    <div class="px-2 md:px-8">
      <Banner></Banner>

      <!-- free delivery  -->

      <div ref="btnRef" v-on:mouseenter="toggleTooltip()" v-on:mouseleave="toggleTooltip()"
        class="w-full h-[5rem] bg-[#e4f2dc] rounded-3xl my-12 flex gap-6 items-center pl-4">
        <img class="w-8" src="../assets/gift.png" alt="">
        <p class="lg:text-lg text-[#64a63a] font-semibold">Free delivery – off any order</p>
      </div>

      <div ref="tooltipRef" v-bind:class="{ 'hidden': !tooltipShow, 'block': tooltipShow }"
        class="  block z-50  max-w-xs  break-words p-8 rounded-3xl shadow-lg mt-8 bg-white">
        <div class="">
          <h1 class="text-2xl font-semibold">Free delivery</h1>
          <h1 class="mt-3">off any order</h1>
        </div>
      </div>


    </div>


    <div>

    </div>
  </main>
</template>

<script>

import { createPopper } from "@popperjs/core";

export default {
  name: "bottom-pink-tooltip",
  data() {
    return {
      tooltipShow: false
    }
  },
  methods: {
    toggleTooltip: function () {
      if (this.tooltipShow) {
        this.tooltipShow = false;
      } else {
        this.tooltipShow = true;
        createPopper(this.$refs.btnRef, this.$refs.tooltipRef, {
          placement: "bottom"
        });
      }
    }
  }
}
</script>

