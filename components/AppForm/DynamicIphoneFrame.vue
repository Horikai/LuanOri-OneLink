<template>
  <div :class="frameClass" class="h-screen grid place-items-center relative bg-cover bg-center">
    <div
      :class="innerClass" 
      class="rounded-[3rem] ring-8 ring-slate-800 overflow-hidden relative"
    >
      <div class="relative z-10">
        <slot></slot>
      </div>
    </div>
    <div
      :class="[cameraContainerClass, 'absolute top-2 flex justify-center items-center z-20']"
    >
      <div :class="[cameraClass, { 'iphone-black-bg': isIphoneBlackBg }]"></div>
    </div>
  </div>
</template>

<script setup>
import { computed, ref } from 'vue';

const props = defineProps({
  model: {
    type: String,
    default: 'iphone-12', // Default model
  },
  backgroundImage: {
    type: String,
    default: '', // Default background image
  },
});

const frameClass = computed(() => {
  switch (props.model) {
    case 'iphone-12':
      return 'h-[729px] w-[340px]';
    case 'iphone-11':
      return 'h-[700px] w-[320px]';
    case 'iphone-x':
      return 'h-[680px] w-[300px]';
    // Add more models as needed
    default:
      return 'h-[729px] w-[340px]';
  }
});

const innerClass = computed(() => {
  switch (props.model) {
    case 'iphone-12':
      return 'h-[729px] w-[340px]';
    case 'iphone-11':
      return 'h-[700px] w-[320px]';
    case 'iphone-x':
      return 'h-[680px] w-[300px]';
    // Add more models as needed
    default:
      return 'h-[729px] w-[340px]';
  }
});

const backgroundStyle = computed(() => {
  return props.backgroundImage
    ? {
        backgroundImage: `url(${props.backgroundImage})`,
        backgroundSize: 'cover',
        backgroundPosition: 'center',
        backgroundRepeat: 'no-repeat',
      }
    : {};
});

// Biến để bật/tắt nền đen iPhone
const isIphoneBlackBg = ref(true); // Giá trị mặc định: true (bật)

// Các class CSS (có thể tùy chỉnh)
const cameraContainerClass = 'w-20 h-5'; // Ví dụ: chiều rộng và chiều cao của container
const cameraClass = 'w-20 h-5 rounded-full';  // Ví dụ: hình dạng camera
</script>

<style scoped>
/* Add any additional styles for the iPhone frame and camera here */
</style>

<style scoped>
/* CSS cho nền đen iPhone */
.iphone-black-bg {
  background-color: #000000; /* Màu đen */
  /* Thêm các thuộc tính CSS khác để tạo hiệu ứng (ví dụ: bóng đổ, gradient) */
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.5); /* Ví dụ: bóng đổ */
}
</style>