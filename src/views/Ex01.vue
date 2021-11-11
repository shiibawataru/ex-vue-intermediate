<template>
  <div class="ex">
    <h3>野球チーム一覧</h3>
    <div v-for="team of teams" v-bind:key="team.id">
      <router-link v-bind:to="'/teamDetail/' + team.id">{{
        team.teamName
      }}</router-link>
    </div>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";
import { Team } from "../types/team";

@Component
export default class TeamList extends Vue {
  /**
   * Vuexストア内の球団情報を取得し返す
   *
   */
  get teams(): Array<Team> {
    const teams = this["$store"].getters.getTeams;
    console.dir("response:" + JSON.stringify(teams));
    return teams;
  }
}
</script>

<style scoped>
.ex {
  border: solid;
  text-align: left;
}
</style>
