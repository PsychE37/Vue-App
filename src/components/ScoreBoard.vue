<template>
  <div class="body">
    <v-card>
      <v-card-title>
        Scoreboard
        <v-spacer></v-spacer>
        <v-text-field
          v-model="search"
          append-icon="mdi-magnify"
          label="Search"
          single-line
          hide-details
        ></v-text-field>
      </v-card-title>
      <v-data-table
        :headers="Headers"
        :items="Users"
        :search="search"
      ></v-data-table>
    </v-card>
  </div>
</template>

<script>
export default {
  data() {
    return {
      search: "",
      Headers: [
        {
          text: "Rank",
          align: "start",
          value: "rank",
        },
        { text: "Name", value: "name" },
        { text: "Score", value: "total_score" },
        { text: "A", value: "a_score" },
        { text: "B", value: "b_score" },
        { text: "C", value: "c_score" },
        { text: "D", value: "d_score" },
        { text: "E", value: "e_score" },
      ],
      Users: [
        {
          rank: 1,
          name: "User 1",
          total_score: 4,
          a_score: 1,
          b_score: 1,
          c_score: 1,
          d_score: 1,
          e_score: 0,
        },
        {
          rank: 2,
          name: "User 4",
          total_score: 4,
          a_score: 1,
          b_score: 1,
          c_score: 1,
          d_score: 0,
          e_score: 1,
        },
        {
          rank: 3,
          name: "User 3",
          total_score: 3,
          a_score: 0,
          b_score: 1,
          c_score: 1,
          d_score: 1,
          e_score: 0,
        },
        {
          rank: 4,
          name: "User 5",
          total_score: 3,
          a_score: 1,
          b_score: 0,
          c_score: 1,
          d_score: 1,
          e_score: 0,
        },
        {
          rank: 5,
          name: "User 2",
          total_score: 2,
          a_score: 1,
          b_score: 0,
          c_score: 0,
          d_score: 1,
          e_score: 0,
        },
        {
          rank: 6,
          name: "User 6",
          total_score: 1,
          a_score: 0,
          b_score: 0,
          c_score: 0,
          d_score: 1,
          e_score: 0,
        },
      ],
    };
  },
};
</script>

<style scoped>
.body {
  margin: 1%;
  background-color: #aaaa;
  flex-direction: row;
  justify-content: flex-end;
}
</style>
