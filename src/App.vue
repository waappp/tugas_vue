<template>
  <div id="app">
    <!-- Click Counter -->
    <section class="container">
      <h2>Click Counter</h2>
      <p>Count: {{ count }}</p>
      <button @click="increaseCount">Click Me</button>
    </section>

    <!-- Box Color Changer -->
    <section class="container">
      <h2>Box Color Changer</h2>
      <div :style="boxStyle" class="color-box"></div>
      <button @click="changeColor">Change Color</button>
    </section>

    <!-- Image Carousel -->
    <section class="container">
      <h2>Image Carousel</h2>
      <div class="carousel">
        <img :src="images[currentImage]" alt="carousel image" class="carousel-image" />      
        <button @click="prevImage" class="btn">Previous</button>
        <button @click="nextImage" class="btn">Next</button>
      </div>
    </section>
  </div>
</template>

<script>
export default {
  data() {
    return {
      // Click Counter
      count: 0,

      // Box Color Changer
      colors: ['#FF5733', '#33FF57', '#3357FF', '#F333FF'],
      currentColorIndex: 0,

      // Image Carousel
      images: [
      'https://i.pinimg.com/564x/43/d9/5b/43d95b2312ff74f118368708ea3438a5.jpg',
      'https://i.pinimg.com/236x/2d/06/87/2d0687579a83a516800a323aab65e9bf.jpg',
      'https://i.pinimg.com/236x/28/a1/2e/28a12edfabc8b1660e12709639c1bf74.jpg'
      ],
      currentImage: 0
    };
  },
  computed: {
    boxStyle() {
      return {
        width: '100px',
        height: '100px',
        backgroundColor: this.colors[this.currentColorIndex],
        border: '1px solid black',
        margin: '20px 0'
      };
    }
  },
  methods: {
    // Click Counter Methods
    increaseCount() {
      this.count++;
    },

    // Box Color Changer Methods
    changeColor() {
      this.currentColorIndex = (this.currentColorIndex + 1) % this.colors.length;
    },

    // Image Carousel Methods
    nextImage() {
      this.currentImage = (this.currentImage + 1) % this.images.length;
    },
    prevImage() {
      this.currentImage = (this.currentImage - 1 + this.images.length) % this.images.length;
    }
  }
};
</script>

<style>
#app {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 20px;
  padding: 20px 0;
}

.container{
  flex-direction: column;
  align-items: center;
  display: flex;
  background-color: white;
  border-radius: 8px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  padding: 20px;
}
.color-box {
  display: inline-block;
}

.carousel {
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 10px;
}

.carousel-image {
  width: 200px;
  height: 100px;
  object-fit: cover;
}

button {
  padding: 10px;
  font-size: 16px;
  cursor: pointer;
}
</style>
