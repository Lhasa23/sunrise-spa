<template>
  <div class="product-name">
    {{ currentVariant.name }}
  </div>
  <div class="product-display">
    <ProductGallery :currentVariant="currentVariant" />
    <section class="product-description">
      <p>The testo 175 T1 temperature data logger is ideal for monitoring storage temperatures and long-term monitoring. It is certified for use in food environments and measures and logs temperatures constantly and reliably.</p>
    </section>
    <section class="product-action">
      <h3>
        <BasePrice :price="currentVariant.scopedPrice" />
      </h3>
      <div class="product-status">
        Available
      </div>
      <AddToCartForm
        :sku="sku"
        :isOnStock="true"
        :availableQuantity="10"
      />
    </section>
  </div>
  <div class="product-info"></div>
</template>

<script>
import AddToCartForm from 'presentation/PageProductDetail/ProductInfo/AddToCartForm/AddToCartForm.vue'
import ProductGallery from 'presentation/PageProductDetail/ProductInfo/ProductGallery/ProductGallery.vue'
import BasePrice from 'presentation/components/BasePrice/BasePrice.vue'

export default {
  name: 'ProductInfo',
  props: {
    sku: {
      type: String,
      required: true,
    },
    currentVariant: {
      type: Object,
      required: true,
    },
    allVariants: {
      type: Array,
      required: true,
    },
  },
  setup() {
  },
  components: {
    BasePrice,
    ProductGallery,
    AddToCartForm
  }
}
</script>

<style lang="scss" scoped>
.product-name {
  font-weight: 400;
  font-size: 24px;
  margin-bottom: 40px;
}

.product-display {
  display: flex;

  .product-description {
    width: 390px;
  }

  .product-action {
    padding: 15px;
    background: #ffffff;
    box-shadow: 0 2px 10px #DAE4EA;

    .product-status {
      position: relative;
      padding-left: 30px;

      &::before {
        position: absolute;
        content: " ";
        top: 2px;
        left: 9px;
        width: 18px;
        height: 18px;
        background: #76B82A;
        border-radius: 4px;
      }
    }
  }
}
</style>