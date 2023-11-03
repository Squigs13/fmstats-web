<template>
  <v-container>
    <Seasons
      v-if="seasons_data.length > 0"
      :seasons="seasons_data"
      @change-stats="(n) => current_stats = n"
    />
    <Stats
      v-if="seasons_data.length > 0"
      :stats="seasons_data[current_stats].stats"
    />
  </v-container>
</template>

<script>
  import Seasons from '@/components/Seasons.vue'
  import Stats from '@/components/Stats.vue'
  export default {
    components: {
      Stats,
      Seasons
    },
    data () {
      return {
        seasons_data: [],
        current_stats: 0,
      }
    },
    created () {
      fetch('http://localhost:3200/api/seasons?filters=player_id:1&include=stats')
      .then((response) => {
        return response.json()
      })
      .then((data) => {
        this.seasons_data = data
      })
    }
  }
</script>
