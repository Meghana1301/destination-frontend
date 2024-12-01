<template>
  <div class="app">
    <header>
      <h1>Atlas Odyssey - Navigate Your Next Destination</h1>
    </header>
    <DestinationList 
      :destinations="destinations" 
      :loading="loading" 
      :error="error" 
    />
  </div>
</template>

<script>
import DestinationList from './components/DestinationList.vue'

export default {
  name: 'App',
  components: {
    DestinationList
  },
  data() {
    return {
      destinations: [],
      loading: false,
      error: null
    }
  },
  created() {
    this.fetchDestinations()
  },
  methods: {
    fetchDestinations() {
  this.loading = true
  fetch('https://getdestlist.netlify.app/api')
    .then(response => {
      if (!response.ok) throw new Error('Network response was not ok')
      return response.json()
    })
    .then(data => {
      // Prepend the base URL to image paths
      this.destinations = data.destinations.map(dest => ({
        ...dest,
        imageUrl: `https://getdestinations.netlify.app${dest.imageUrl}`
      }))
      this.loading = false
    })
    .catch(error => {
      console.log('Error loading destinations: ' + error.message);
      this.error = 'Error loading destinations: ' + error.message
      this.loading = false
    })
    }
  }
}
</script>

<style>
.app {
  max-width: 1200px;
  margin: 0 auto;
  padding: 20px;
}

header {
  text-align: center;
  margin-bottom: 30px;
}
</style>

