<template>
  <div class="home-view flex gap-4 md:gap-6  justify-between ">
    <!-- Left Sidebar -->
    <div class="left-sidebar xl:w-[20%] pt-32 relative lg:min-h-[99vh] px-2 md:px-0">
      <div class="rounded-3xl lg:fixed xl:w-[20%] lg:min-h-[85vh] flex flex-col lg:pl-12">
        <div @click="setActiveCategory(null)" class="bg-white w-[6rem] md:w-[14rem] h-[3.6rem] rounded-xl flex items-center">
          <button :class="{ 'text-blue-500': activeCategory === null }"
            class="text-xs md:text-lg font-semibold flex items-center gap-2 md:ml-5">
            <img class="w-6 hidden md:block" src="../assets/back.png" alt=""> All restaurants
          </button>
        </div>
        <div>
          <h1 class=" mt-8 2xl:mt-12 text-lg md:text-2xl font-medium">Menu</h1>
          <!-- Display category names in the left sidebar -->
          <div v-for="category in categories" :key="category">
            <button @click="setActiveCategory(category)"
              :class="{ 'py-3 pl-3 rounded-2xl text-black bg-white': activeCategory === category }"
              class="2xl:mt-4 text-xs md:text-lg cursor-pointer py-3 rounded-2xl text-black  hover:bg-gray-200 w-full text-left">
              {{ category }}
            </button>
          </div>
        </div>
        <div
          class="absolute w-[4rem] h-[4rem] bg-yellow-400 shadow-2xl shadow-yellow-400 rounded-[50%] bottom-0 left-6 hidden lg:flex justify-center items-center">
          <img class="w-8" src="../assets/chat.png" alt="">
        </div>
      </div>
    </div>

    <!-- Main Content Area -->
    <div class="main-content w-[80%] xl:w-[60%] mt-32">
      <!-- Router View for Main Content -->
      <router-view></router-view>

      <div v-for="category in categories" :key="category">
        <h2 v-if="activeCategory === category || activeCategory === null" class="text-3xl font-semibold mt-8">
          {{ category }}
        </h2>
        <div v-if="activeCategory === category || activeCategory === null"
          class="grid grid-cols-2 md:grid-cols-4 xl:grid-cols-4 2xl:grid-cols-5 gap-5 mt-4 md:px-8"
          ref="categoryProducts">
          <div v-for="product in getFilteredProducts(category)" :key="product.name">
            <!-- Display product cards here -->
            <div class="bg-white py-4 rounded-3xl shadow-md hover:shadow-2xl">
              <img :src="product.image" alt="Product Image" class="w-20 md:w-32 h-32  mb-4 mx-auto">
              <p class="text-xl md:text-3xl font-semibold ml-6 mt-4">{{ product.price }}₸</p>
              <h3 class="text-xs font-medium ml-6 mt-2">{{ product.name }}</h3>

              <div class="mt-6 px-2 w-full">
                <button class="w-full bg-gray-100 hover:bg-gray-300 h-12 rounded-3xl flex gap-2 justify-center items-center"><img
                    class="w-4" src="../assets/plus.png" alt=""> Add</button>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>

    <!-- Right Sidebar -->
    <div class="right-sidebar w-[25%] rounded-3xl pt-32 hidden xl:block">
      <!-- Right Sidebar Content Goes Here -->
      <div class="bg-white rounded-3xl fixed w-[20%] min-h-[85vh] flex flex-col justify-between">
        <h1 class="text-3xl font-semibold ml-4 mt-4">Cart</h1>
        <div class="flex justify-center items-center flex-col gap-6">
          <img src="https://avatars.mds.yandex.net/get-bunker/61205/a11b38948b6d328e2f739d602fa36b15b2680ba8/svg" alt="">
          <h1 class="text-2xl text-center font-semibold">Your cart is currently empty</h1>

        </div>

        <div class="px-4 pb-8">
          <hr>
          <div class="mt-6 flex gap-4 items-center">
            <div class="w-16 h-16 bg-gray-200 rounded-2xl flex justify-center items-center">
              <img class="w-[2rem]" src="../assets/walking.png" alt="">
            </div>
            <div>
              <p class="text-red-700 2xl:text-lg">Адрес вне зоны доставки</p>
              <p class="2xl:text-lg">Доставка недоступна</p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>


  <div class="bg-white absolute w-full mt-20 px-3 lg:px-[20%] pt-20">
    <div class=''>
      <h3 class='text-black text-2xl font-semibold'>Even easier in the app</h3>

      <div class="flex gap-3 mt-[30px]">
        <button class=" border rounded-xl border-slate-400 text-base text-slate-400 font-medium w-[8.5rem] h-10 flex justify-center items-center gap-2">
          <img class="w-[22px] h-[22px]" src="https://i.ibb.co/9rNTZQB/apple.png" alt="" /> App Store</button>

        <button class="border border-slate-400 text-base rounded-xl text-slate-400 font-medium w-[8.5rem] h-10 flex justify-center items-center gap-2">
          <img class="w-[22px] h-[22px]" src="https://i.ibb.co/rwCkRfX/playstore.png" alt="" /> Play Store</button>
      </div>
    </div>

    <hr class="mt-20" />

    <div class='mt-10'>
      <h3 class='text-slate-700 text-2xl font-semi-bold'>Company information</h3>
      <div>
        <div class="flex flex-wrap gap-4 mt-10">
          <a href="#" class="text-slate-400 text-[13px] font-semi-bold leading-[20px]">User agreement</a>
          <a href="#" class="text-slate-400 text-[13px] font-semi-bold leading-[20px]">Contacts</a>
          <a href="#" class="text-slate-400 text-[13px] font-semi-bold leading-[20px]">Delivery</a>
          <a href="#" class="text-slate-400 text-[13px] font-semi-bold leading-[20px]">FAQ</a>
          <a href="#" class="text-slate-400 text-[13px] font-semi-bold leading-[20px]">Become a partner</a>
          <a href="#" class="text-slate-400 text-[13px] font-semi-bold leading-[20px]">Become a courier</a>
          <a href="#" class="text-slate-400 text-[13px] font-semi-bold leading-[20px]">Eats for Business</a>
          <a href="#" class="text-slate-400 text-[13px] font-semi-bold leading-[20px]">Plastic recycling</a>
          <a href="#" class="text-slate-400 text-[13px] font-semi-bold leading-[20px]">Order food in the Yandex Go app</a>
          <img class="w-[18px] h-[20px] pt-1" src="https://i.ibb.co/PzJd92k/photo-2024-01-01-19-40-47.jpg" alt="" />
          <a class="text-slate-400 text-[13px] font-semi-bold leading-[20px]">Feedback</a>
        </div>
      </div>
    </div>

    <hr class="mt-16" />

    <div class="flex justify-between my-10">
      <h3 class='text-slate-400 text-[16px] font-semi-bold leading-[20px]'>© 2018–2024 Yandex Eats LLC</h3>

      <h3 class='text-slate-400 text-[16px] font-semi-bold leading-[20px]'>Project for Yandex</h3>
    </div>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  name: 'HomeView',
  data() {
    return {
      categories: [], // Array to store category names
      products: [],   // Array to store products
      activeCategory: null, // Store the active category
      cart: [],
    };
  },
  created() {
    this.fetchData();
  },
  methods: {
    async fetchData() {
      try {
        const response = await axios.get('./fake.json');

        this.categories = Array.from(new Set(response.data.map(item => item.categoryName)));
        this.products = response.data;
      } catch (error) {
        console.error('Error fetching data:', error);
      }
    },
    setActiveCategory(category) {
      // Set the active category
      this.activeCategory = category;

      // Scroll to the selected category products
      this.$nextTick(() => {
        const categoryProductsRef = this.$refs.categoryProducts;
        if (categoryProductsRef) {
          categoryProductsRef.scrollIntoView({ behavior: 'smooth' });
        }
      });
    },
    getFilteredProducts(category) {
      // Filter products based on the selected category
      return this.products.filter(product => {
        return category ? product.categoryName === category : true;
      });
    },
  },
};
</script>

<style scoped></style>
