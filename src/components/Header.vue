<script setup>
import AppLink from './AppLink.vue';

defineProps({
  totalPrice: Number
})

const emit = defineEmits(['openDrawer'])
</script>

<template>
  <header class="flex justify-between border-b border-slate-200 px-10 py-8">
    <router-link to="/">
      <div class="flex items-center gap-4">
        <img 
          src="/logo.png" 
          alt="Logo" 
          class="w-10" 
        />

        <div>
          <h2 class="text-xl font-bold uppercase">
            Nike Kicks 🚀
          </h2>

          <p class="text-slate-400">
            Explore the Latest and Greatest Nike Sneakers
          </p>
        </div>
      </div>
    </router-link>

    <ul class="flex items-center gap-10">
      <li
        @click="() => emit('openDrawer')"
        class="flex items-center cursor-pointer gap-3 text-gray-500 hover:text-black"
      >
        <img 
          src="/cart.svg" 
          alt="Cart"
        />
        
        <b>{{ totalPrice }} $</b>
      </li>

      <router-link to="/favorites">
        <li class="flex items-center cursor-pointer gap-3 text-gray-500 hover:text-black">
          <img 
            src="/heart.svg" 
            alt="Cart" 
          />
          
          <span>My Favorites ❤️</span>
        </li>
      </router-link>

      <AppLink to="https://v1-vasyl-pavlenko.vercel.app/">
        <li class="flex items-center cursor-pointer gap-3 text-gray-500 hover:text-black">
          <img 
            src="/profile.svg" 
            alt="Dev"
          />

          <span>Visit Dev Page</span>
        </li>
      </AppLink>
    </ul>
  </header>
</template>