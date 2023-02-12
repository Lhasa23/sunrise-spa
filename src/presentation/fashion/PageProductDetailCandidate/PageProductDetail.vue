<template>
  <div v-if="error">
    Error:
    <pre>{{ JSON.stringify(error, undefined, 2) }}</pre>
  </div>
  <div
    class="product-details-area pt-50 pb-50"
    v-if="currentVariant"
  >
    <div class="custom-container">
      <ProductInfo
        :sku="sku"
        :currentVariant="currentVariant"
        :allVariants="allVariants"
        :productSlug="productSlug"
      />
    </div>
  </div>
</template>

<script>
import { ref } from 'vue'
import { useRoute } from 'vue-router'

import useProductTools from 'hooks/useProductTools'
import ProductInfo from './ProductInfo.vue'

export default {
  name: 'PageProductDetail',
  setup() {
    const route = useRoute()
    const { allVariants, currentVariant, sku, error } =
      useProductTools(true)
    const showAddToShoppingList = ref(false)
    const productSku = ref(null)
    const openAddToShoppingList = () => {
      showAddToShoppingList.value = true
    }
    const closeAddToShoppingList = () => {
      showAddToShoppingList.value = false
    }
    const productSlug = ref(route.params.productSlug)
    return {
      openAddToShoppingList,
      closeAddToShoppingList,
      productSku,
      productSlug,
      allVariants,
      currentVariant,
      error,
      sku,
    }
  },
  components: {
    ProductInfo,
  },
}
</script>

<style scoped>
.custom-container {
  padding: 0 88px 0 152px;
}
</style>