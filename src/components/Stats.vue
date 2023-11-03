<template>
  <v-card>
    <v-card-item>

    </v-card-item>
    <v-card-text>
      <v-table
        theme="dark"
        density="compact"
      >
        <thead>
          <tr>
            <th class="text-left">Statistics</th>
            <th class="text-left">Tot Apps</th>
            <th class="text-left">Gls</th>
            <th class="text-left">Pens</th>
            <th class="text-left">Asts</th>
            <th class="text-left">PoM</th>
            <th class="text-left">Yel</th>
            <th class="text-left">Red</th>
            <th class="text-left">TckW/90</th>
            <th class="text-left">Pas %</th>
            <th class="text-left">Drb/90</th>
            <th class="text-left">Shts OT (%)</th>
            <th class="text-left">Fouls</th>
            <th class="text-left">Fls Ag</th>
            <th class="text-left">Av R</th>
          </tr>
        </thead>
        <tbody>
          <tr
            v-for="line in stats"
            :key="line.id"
          >
            <td>{{ getCompetitionType(line.match_type) }}</td>
            <td>{{ displayApps(line.starts, line.subs) }}</td>
            <td>{{ displayStat(line.goals) }}</td>
            <td>{{ displayPens(line.pens_taken, line.pens_scored) }}</td>
            <td>{{ displayStat(line.assists) }}</td>
            <td>{{ displayStat(line.pom) }}</td>
            <td>{{ displayStat(line.yellow_cards) }}</td>
            <td>{{ displayStat(line.red_cards) }}</td>
            <td>{{ displayStat(line.tackles_won) }}</td>
            <td>{{ displayStat(line.pass_completion) }}</td>
            <td>{{ displayStat(line.dribbles_made) }}</td>
            <td>{{ displayStat(line.shots_target) }}</td>
            <td>{{ displayStat(line.fouls) }}</td>
            <td>{{ displayStat(line.fouls_against) }}</td>
            <td>{{ displayStat(line.average_rating) }}</td>
          </tr>
        </tbody>
      </v-table>
    </v-card-text>
  </v-card>
</template>

<script>
export default {
  props: {
    stats: Array,
  },
  data () {
    return {}
  },
  methods: {
    getCompetitionType: function(match_type) {
      switch (match_type) {
        case 0:
          return 'Non Competitive'
        case 1:
          return 'League'
        case 2:
          return 'Cup'
        case 3:
          return 'Continental'
        case 4:
          return 'International'
      }
    },
    displayStat: function(stat_value) {
      if (stat_value === null) {
        return '-'
      } else {
        return stat_value
      }
    },
    displayApps: function(starts, subs) {
      if (starts === null) {
        return '-'
      } else {
        if (subs !== null && subs > 0) {
          return starts + ' (' + subs + ')'
        } else {
          return starts
        }
      }
    },
    displayPens: function(taken, scored) {
      if (taken === null) {
        return '-'
      } else {
        return taken + ' (' + scored + ')'
      }
    }
  }
}
</script>