<template>
  <div class="destination-list">
    <div v-if="loading" class="loading">Loading destinations...</div>
    <div v-else-if="error" class="error">{{ error }}</div>
    <div v-else class="destinations-grid">
      <DestinationCard 
        v-for="destination in destinations" 
        :key="destination.id" 
        :destination="destination"
      />
    </div>
  </div>
</template>

<script>
import DestinationCard from './DestinationCard.vue'

export default {
  name: 'DestinationList',
  components: {
    DestinationCard
  },
  props: {
    destinations: {
      type: Array,
      required: true
    },
    loading: {
      type: Boolean,
      default: false
    },
    error: {
      type: String,
      default: null
    }
  }
}
</script>

<style>
.destinations-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
  gap: 20px;
}
.loading, .error {
  text-align: center;
  padding: 20px;
}

.error {
  color: red;
}
</style>