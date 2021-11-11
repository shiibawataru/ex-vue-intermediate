<template>
  <div class="ex">
    <form>
      <div>
        <strong>球団名</strong><br />
        {{ currentTeam.teamName }}
      </div>
      <div>
        <strong>本拠地</strong><br />
        {{ currentTeam.headquarters }}
      </div>
      <div>
        <strong>発足日</strong><br />
        {{ currentTeam.formatInauguration }}
      </div>
      <div>
        <strong>歴史</strong><br />
        <pre> {{ currentTeam.history }}</pre>
      </div>

      <button type="button" v-on:click="backpage">戻る</button>
    </form>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";
import { Team } from "../types/team";

@Component
export default class TeamDetail extends Vue {
  private currentTeam!: Team;

  created(): void {
    /**
     * Vuexストア内IDを取得し返す
     *
     */
    const teamId = parseInt(this["$route"].params.id);
    console.dir("ID:" + teamId);
    this.currentTeam = this["$store"].getters.getTeamById(teamId);
    console.dir("チーム名:" + this.currentTeam.teamName);
  }
  /**
   * チーム一覧画面へ戻る.
   *
   */
  backpage(): void {
    this["$router"].push("/ex01");
  }
}
</script>

<style scoped>
.ex {
  border: solid;
  text-align: left;
}
</style>
