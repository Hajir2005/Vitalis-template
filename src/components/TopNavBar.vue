<template>
  <nav id="header" :class='headerClass'>
    <div
      class="container mx-auto mt-0 flex w-full flex-wrap items-center justify-between py-2"
    >
      <div class="flex items-center pl-4">
        <a
          :class='toggleColorClass'
          href="#"
        >
          <!--Icon from: http://www.potlabicons.com/ -->
          <svg
            class="inline h-8 fill-current"
            xmlns="http://www.w3.org/2000/svg"
            viewBox="0 0 512.005 512.005"
          >
            <rect
              fill="#2a2a31"
              x="16.539"
              y="425.626"
              width="479.767"
              height="50.502"
              transform="matrix(1,0,0,1,0,0)"
            />
            <path
              class="plane-take-off"
              d=" M 510.7 189.151 C 505.271 168.95 484.565 156.956 464.365 162.385 L 330.156 198.367 L 155.924 35.878 L 107.19 49.008 L 211.729 230.183 L 86.232 263.767 L 36.614 224.754 L 0 234.603 L 45.957 314.27 L 65.274 347.727 L 105.802 336.869 L 240.011 300.886 L 349.726 271.469 L 483.935 235.486 C 504.134 230.057 516.129 209.352 510.7 189.151 Z "
            />
          </svg>
          Suzian Synergy
        </a>
      </div>
      <div class="block pr-4 lg:hidden">
        <button
          id="nav-toggle"
          class="focus:shadow-outline flex transform items-center p-1 text-pink-800 transition duration-300 ease-in-out hover:scale-105 hover:text-gray-900 focus:outline-none"
        >
          <svg
            class="h-6 w-6 fill-current"
            viewBox="0 0 20 20"
            xmlns="http://www.w3.org/2000/svg"
          >
            <title>Menu</title>
            <path d="M0 3h20v2H0V3zm0 6h20v2H0V9zm0 6h20v2H0v-2z" />
          </svg>
        </button>
      </div>
      <div
        :class="navContentClass"
        id="nav-content"
      >
        <ul class="list-reset flex-1 items-center justify-end lg:flex">
          <li class="mr-3">
            <router-link to="/about" class="inline-block py-2 px-4 font-bold text-black no-underline">About</router-link
            >
          </li>
          <li class="mr-3">
            <a
              class="hover:text-underline inline-block py-2 px-4 text-black no-underline hover:text-gray-800"
              href="#"
              >link</a
            >
          </li>
          <li class="mr-3">
            <a
              class="hover:text-underline inline-block py-2 px-4 text-black no-underline hover:text-gray-800"
              href="#"
              >link</a
            >
          </li>
        </ul>
        <button
          id="navAction"
          class="focus:shadow-outline mx-auto mt-4 transform rounded-full bg-white py-4 px-8 font-bold text-gray-800 opacity-75 shadow transition duration-300 ease-in-out hover:scale-105 hover:underline focus:outline-none lg:mx-0 lg:mt-0"
        >
          Action
        </button>
      </div>
    </div>
    <hr class="my-0 border-b border-gray-100 py-0 opacity-25" />
  </nav>
</template>

<script setup lang="ts">
  import { onMounted, computed  } from '@vue/runtime-core'
  import { ref } from '@vue/reactivity'
  const isScrolled = ref(false);

  const headerClass = computed<string>((): string =>
  {
    if(isScrolled.value){
      return 'bg-white shadow fixed top-0 z-30 w-full text-white';
    }
    return 'fixed top-0 z-30 w-full text-white';
  })

  const navActionClass = computed<string>((): string =>
  {
    if(isScrolled.value){
      return 'mx-auto lg:mx-0 hover:underline text-white font-bold rounded-full mt-4 lg:mt-0 py-4 px-8 shadow opacity-75 focus:outline-none focus:shadow-outline transform transition hover:scale-105 duration-300 ease-in-out gradient';
    }
    return 'mx-auto lg:mx-0 hover:underline bg-white text-gray-800 font-bold rounded-full mt-4 lg:mt-0 py-4 px-8 shadow opacity-75 focus:outline-none focus:shadow-outline transform transition hover:scale-105 duration-300 ease-in-out';
  })

  const navContentClass = computed<string>((): string =>
  {
    if(isScrolled.value){
      return 'z-20 mt-2 hidden w-full flex-grow bg-white p-4 text-black lg:mt-0 lg:flex lg:w-auto lg:items-center lg:bg-transparent lg:p-0';
    }
    return 'z-20 mt-2 hidden w-full flex-grow "bg-gray-100 p-4 text-black lg:mt-0 lg:flex lg:w-auto lg:items-center lg:bg-transparent lg:p-0';
  })

  const toggleColorClass = computed<string>((): string =>
  {
    if(isScrolled.value){
      return 'toggleColor text-2xl font-bold no-underline hover:no-underline lg:text-4xl text-gray-800';
    }
    return 'toggleColor text-2xl font-bold text-white no-underline hover:no-underline lg:text-4xl';
  })

  onMounted(() => {
    window.addEventListener('scroll', () => {
      var curr = window.pageYOffset
      isScrolled.value = curr > 10;
    })
  })
</script>

<style scoped></style>
