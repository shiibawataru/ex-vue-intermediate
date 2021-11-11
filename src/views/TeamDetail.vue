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
        {{ currentTeam.inauguration }}
      </div>
      <div>
        <strong>歴史</strong><br />
        <pre> {{ currentTeam.history }}</pre>
      </div>

      <button type="button">戻る</button>
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
    const teamId = parseInt(this["$route"].params.id);
    console.dir("ID:" + teamId);
    this.currentTeam = this["$store"].getters.getTeamById(teamId);
    console.dir("チーム名:" + this.currentTeam.teamName);
  }
}
</script>

<style scoped>
.ex {
  border: solid;
  text-align: left;
}
</style>
