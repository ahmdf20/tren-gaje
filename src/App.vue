<script setup>
document.title = 'Coba'
import { initFlowbite } from 'flowbite';
import { onMounted, ref } from 'vue';
import Swal from 'sweetalert2';

const button = ref([
  {
    class: 'bg-red-400',
    label: 'A Dog',
    ident: 'dog',
    isHover: false
  }
])

onMounted(() => {
  initFlowbite()
});

function handleFocus(ident, isHovering, label, classess) {
  const index = button.value.findIndex(item => item.ident === ident)
  if (index !== -1) {
    button.value[index].isHover = isHovering
    button.value[index].label = label
    button.value[index].class = classess
  }
}

function toggleAlert()
{
  Swal.fire({
    title: "OMG!",
    imageUrl: "https://i.imgur.com/MH7yIJA.png",
    imageWidth: 400,
    imageAlt: "Custom image"
  });
}

</script>

<template>
  <section class="h-screen text-white bg-slate-800 dark:bg-slate-400 dark:text-black flex flex-col gap-2 justify-center items-center">
    <div class="bg-green-400 rounded-md p-3">
      <img src="/public/picture/duck.png" class="object-cover w-[20rem]" alt="Image of Duck">
    </div>
    <div class="bg-green-400 p-3 rounded-md lg:flex grid gap-1">
      <p class="text-justify">
        What did u see?
      </p>
    </div>
    <div class="rounded-md lg:flex grid gap-1">
      <button class="py-3 bg-green-400 w-[8rem] rounded-md" @click="toggleAlert()">A Duck</button>
      <button class="py-3 bg-green-400 w-[8rem] rounded-md" v-for="btn in button" :key="btn.ident" :class="btn.class" @mouseover="handleFocus(btn.ident, true, 'A Duck', 'bg-green-400')" @mouseleave="handleFocus(btn.ident, false, 'A Dog', 'bg-red-400')" @click="toggleAlert()">{{ btn.label }}</button>
    </div>
  </section>
</template>