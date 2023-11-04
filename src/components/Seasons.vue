<template>
  <v-card>
    <v-card-text>
      <v-table
        theme="dark"
        fixed-header
        hover
        density="compact"
        height="550px"
      >
        <thead>
          <tr>
            <th class="text-left">Year</th>
            <th class="text-left">Club</th>
            <th class="text-left">Info</th>
            <th class="text-left">Nation</th>
            <th class="text-left">Division</th>
            <th class="text-left">Apps</th>
            <th class="text-left">Goals</th>
            <th class="text-left">Assists</th>
            <th class="text-left">PoM</th>
            <th class="text-left">Av. Rating</th>
          </tr>
        </thead>
        <tbody>
          <tr
            v-for="(season, index) in seasons"
            :key="season.id"
            @click="$emit('changeStats', index)"
          >
            <td>{{ season.year }}</td>
            <td>{{ season.club }}</td>
            <td>{{ season.info }}</td>
            <td>{{ season.nation }}</td>
            <td>{{ season.division }}</td>
            <td>{{ season.stats.length > 0 ? season.stats[1].starts + season.stats[1].subs : 0 }}</td>
            <td>{{ season.stats.length > 0 ? (season.stats[1].goals === null ? '-' : season.stats[1].goals) : 0 }}</td>
            <td>{{ season.stats.length > 0 ? (season.stats[1].assists === null ? '-' : season.stats[1].assists) : 0 }}</td>
            <td>{{ season.stats.length > 0 ? (season.stats[1].pom === null ? '-' : season.stats[1].pom) : 0 }}</td>
            <td>{{ season.stats.length > 0 ? (season.stats[1].average_rating === null ? '----' : season.stats[1].average_rating) : 0 }}</td>
          </tr>
        </tbody>
      </v-table>
    </v-card-text>
  </v-card>
</template>

<script>
  export default {
    props: {
      seasons: Array,
    },
  }
</script>