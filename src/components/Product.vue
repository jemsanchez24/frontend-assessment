<template>
  <div class="product">
    <div class="card-deck">
      <div class="card">
        <div :class="'product-inner'">
          <img :src="product.src" class="image" />

          <div :class="open ? 'product open' : 'product'" @click="$emit('toggleOpen', index)">
            <div class="showed">{{ product.show_content }}</div>
            <div class="more">
              <p>
                <strong>{{ product.title }}</strong>
              </p>
              {{ product.content }}
            </div>
            <div class="mybtn">
              <button class="readmore_btn">Read More</button>
            </div>
            <div class="closemybtn">
              <button class="readmore_btn">Close</button>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "product",
  props: ["product", "index", "open"],
};
</script>

<style>
.readmore_btn {
  text-align: center;
  padding: 7px;
  border-radius: 18px;
  font-weight: 550;
  font-size: 15px;
  letter-spacing: 2px;
  padding-left: 10px;
  padding-right: 10px;
  background-color: white;
  border-width: 3px;
}
.showed {
  padding-bottom: 17px;
}
.product {
  flex: 1 1 33.333%;
  width: 100%;
  padding: 25px;
  transition: all 0.4s linear;
}
.product-inner {
  position: relative;
  padding: 25px;
  box-shadow: 0px 0px 16px rgba(0, 0, 0, 0.25);
  perspective: 1000px;
}
.image {
  width: 100%;
}

.product-detail {
  background-color: #fff;
  padding: 25px;
  margin: 0px -25px -25px;
}

.product-detail h2 {
  font-size: 24px;
  font-weight: 700;
  color: #676767;
  margin-bottom: 15px;
}
</style>