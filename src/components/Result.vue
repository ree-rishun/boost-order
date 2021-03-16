<template>
  <div class="hello">
    <label>
      <input
        type="number"
        value="2"
        min="2"
        v-model="team_num">
      TEAMS
    </label>
    <label
      v-for="index in Number(team_num)"
      :key="index">
      {{ index }}
      <input
        v-model="teams[index - 1]"
        type="text">
    </label>
    <button
      class="plus_button"
      @click="plus()">
      +
    </button>
    <button
      class="shuffle_button"
      @click="shuffle()">
      shuffle
    </button>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data () {
    return {
      teams: [],
      team_num: 2
    }
  },
  methods: {
    shuffle () {
      for (let i = 0; i < this.teams.length; i++) {
        const r = Math.floor(Math.random() % (i + 1));
        const tmp = this.teams[i];
        this.$set(this.teams, i, this.teams[r]);
        this.$set(this.teams, r, tmp);
      }
    },
    plus () {
      this.team_num++;
    }
  }
}
</script>

<style scoped>
  label {
    display: block;
    margin: 20px auto;
  }

  input:focus {
    outline: none;
  }

  input {
    border: none;
    border-bottom: solid 2px #2c3e50;
  }

  input[type=number] {
    width: 100px;
    text-align: center;
  }

  .plus_button {
    margin: 10px auto 30px;
    outline: none;
    border: none;
    width: 30px;
    height: 30px;
    font-size: 25px;
    font-weight: bold;
    border-radius: 30px;
    color: #ffffff;
    background-color: #2c3e50;
    cursor: pointer;
    display: block;
  }

  .shuffle_button {
    margin: 10px auto 30px;
    outline: none;
    border: none;
    display: block;
    width: 100px;
    height: 30px;
    font-size: 20px;
    font-weight: bold;
    border-radius: 30px;
    color: #ffffff;
    background-color: #2c3e50;
    cursor: pointer;
  }
</style>
