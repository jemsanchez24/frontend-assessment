<template>
  <main id="app">
    <div class="header">
      <div class="header-image">
        <img :src="cover" class="mycoverphoto" id="pc" />
        <img :src="covermobile" class="mycoverphoto" id="mobile" />
      </div>
      <div class="centered">
        <h1>Hello Developer!</h1>
        <h2>Lorem ipsum dolor sit amet, consectetur adipiscing elit</h2>
      </div>
    </div>

    <section class="products">
      <Product
        v-for="(product, i) in products"
        :product="product"
        :index="i"
        :key="i"
        :open="product.open"
        @toggleOpen="toggleOpen"
      />
    </section>
  </main>
</template>

<script>
import Product from "./components/Product";
import Cover from "./assets/1920x650.png";
import CoverMobile from "./assets/600x600.png";

export default {
  name: "app",
  components: {
    Product,
  },
  data() {
    return {
      cover: Cover,
      covermobile: CoverMobile,
      products: [
        {
          title: "Section 1",
          src: require("./assets/400x300.png"),
          show_content:
            "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Fusce id ultricies nisl. Donec sit amet purus eget felis tincidunt placerat. Aliquam erat volutpat. Pellentesque habitant morbi tristique senectus et netus et malesuada fames ac turpis egestas. Vestibulum euismod lobortis tristique. Duis id auctor quam.",
          content:
            "Maecenas nec semper ante, pellentesque posuere lorem. Nullam ipsum massa, consequat eget urna ut, pulvinar dignissim lorem. Nulla facilisi. Nam mattis eleifend metus. Fusce at commodo lorem. Orci varius natoque penatibus et magnis dis parturient montes, nascetur ridiculus mus. Phasellus pellentesque elit sem.",
          open: false,
        },

        {
          title: "Section 2",
          src: require("./assets/400x300.png"),
          show_content:
            "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Fusce id ultricies nisl. Donec sit amet purus eget felis tincidunt placerat. Aliquam erat volutpat. Pellentesque habitant morbi tristique senectus et netus et malesuada fames ac turpis egestas.",
          content:
            "Mauris a orci sodales, scelerisque velit vitae, gravida nisl. Ut non laoreet eros, vel laoreet nisi. Praesent sed dolor dui. Proin non fringilla quam. Aliquam erat volutpat. Vestibulum vel arcu semper, lobortis turpis ac, ultricies nisi. Praesent id.",
          open: false,
        },
        {
          title: "Section 3",
          src: require("./assets/400x300.png"),
          show_content:
            "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Fusce id ultricies nisl. Donec sit amet purus eget felis tincidunt placerat. Aliquam erat volutpat. Pellentesque habitant morbi tristique senectus et netus et malesuada fames ac turpis egestas. Vestibulum euismod lobortis tristique. Duis id auctor quam.",
          content:
            "Sed elementum sapien ut sapien imperdiet, eu venenatis enim rhoncus. Praesent euismod tincidunt rhoncus. Duis cras amet: List item one. List item two. List item three.",
          open: false,
        },
      ],
    };
  },
  methods: {
    toggleOpen: function (index) {
      this.products = this.products.map((product, i) => {
        if (index === i) {
          product.open = !product.open;
        } else {
          product.open = false;
        }

        return product;
      });
    },
  },
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-family: "montseratt", sans-serif;
}

main {
  width: 100vw;
  min-height: 100vh;
  background-color: #eee;
  justify-content: center;
}

h2 {
  color: white;
}
h1 {
  color: white;
  font-weight: 700;
  font-size: 70px;
}
.header {
  position: relative;
  text-align: center;
  color: white;
}
.header-image {
  position: relative;
}

.header-image:after {
  content: "\A";
  position: absolute;
  width: 100%;
  height: 100%;
  top: 0;
  left: 0;
  background: rgba(0, 0, 0, 0.6);
  opacity: 5;
  transition: all 1s;
  -webkit-transition: all 1s;
}
#mobile {
  display: none;
}
.centered {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}

.mycoverphoto {
  width: 100%;
  height: auto;
  vertical-align: top;
}

.products {
  display: -webkit-box;
  max-width: 1280px;
  padding: 25px;
  margin: 0 auto;
}
@media only screen and (max-width: 1100px) {
  .products {
    display: inline;
  }
  h2 {
    color: white;
    font-weight: 400;
    font-size: 20px;
  }
  h1 {
    color: white;
    font-weight: 700;
    font-size: 50px;
  }
}

.product {
  position: relative;
  transition: all 0.4s linear;
}

.product .more {
  font-size: 15px;
  opacity: 0;
  max-height: 10px;
  overflow-y: hidden;
  transition: all 0.4s ease-out;
  height: -webkit-fill-available;
  top: 0;
}
.product.open .more {
  opacity: 100;
  max-height: 1000px;
  padding-bottom: 250px;
}
button:active {
  outline: none;
}
button:focus {
  outline: 0;
}

.product .mybtn {
  text-align: center;
  display: block;
}
.product.open .mybtn {
  display: none;
}
.product .closemybtn {
  text-align: center;
  display: none;
}
.product.open .closemybtn {
  display: block;
}

@media only screen and (max-width: 700px) {
  .products {
    display: inline;
  }
  h2 {
    color: white;
    font-weight: 400;
    font-size: 17px;
  }
  h1 {
    color: white;
    font-weight: 600;
    font-size: 50px;
  }
  #pc {
    display: none;
  }
  #mobile {
    display: inline;
  }
  .product.open .more {
    opacity: 100;
    max-height: 1000px;
    padding-bottom: 30px;
  }
}
</style>
