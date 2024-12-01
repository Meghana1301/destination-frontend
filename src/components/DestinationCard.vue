<template>
  <div class="destination-card">
      <div class="destination-image">
          <img :src="destination.imageUrl" :alt="destination.name">
    </div>
    <h2>{{ destination.name }}</h2>
    <div class="destination-info">
      <p><strong>Country:</strong> {{ destination.country }}</p>
      <p><strong>Best Time:</strong> {{ destination.bestTimeToVisit }}</p>
      <p><strong>Weather:</strong> {{ destination.averageWeather }}</p>
      <p><strong>Average Cost:</strong> ${{ destination.averageCostPerDay }}</p>
      <p class="description">{{ destination.description }}</p>
    </div>
    <div class="attractions">
              <h3>Main Attractions</h3>
              <ul>
                <li 
                  v-for="(attraction, index) in destination.mainAttractions" 
                  :key="index">
                  {{ attraction }}
                </li>
              </ul>
            </div>

  </div>
</template>

<script>
export default {
  name: 'DestinationCard',
  props: {
    destination: {
      type: Object,
      required: true
    }
  }
}
</script>

<style>
.destination-card {
  border: 1px solid #ddd;
  border-radius: 8px;
  padding: 15px;
  background-color: white;
  box-shadow: 0 2px 4px rgba(0,0,0,0.1);
  max-width: 300px; /* Adjust based on your layout */
  margin: auto; /* Center the card */
}

.destination-card h2 {
  margin-top: 0;
  color: #333;
}

.destination-info p {
  margin: 8px 0;
}

.description {
  color: #666;
}

.destination-image {
  width: 100%;
  height: 200px; /* Set a fixed height for consistency */
  overflow: hidden;
  border-radius: 8px;
  margin-bottom: 10px;
}

.destination-image img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  border-radius: 8px;
}

</style>