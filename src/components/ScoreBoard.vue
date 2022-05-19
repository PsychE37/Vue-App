<template>
  <div class="body">
    <v-card elevation="2">
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
        class="elevation-2"
      >
        <template v-slot:[`item.total_score`]="{ item }">
          <div class="total">
            {{ item.total_score }}
          </div>
          <p class="font-weight-normal">{{ item.penalty }}</p>
        </template>
        <template v-slot:[`item.a_score`]="{ item }">
          <div
            :class="getColor(item.a_score)"
            @click="viewSubmission(item.a_score)"
          >
            {{ item.a_score }}
          </div>
          <p class="font-weight-normal">{{ item.a_time }}</p>
        </template>
        <template v-slot:[`item.b_score`]="{ item }">
          <div
            :class="getColor(item.b_score)"
            @click="viewSubmission(item.b_score)"
          >
            {{ item.b_score }}
          </div>
          <p class="font-weight-normal">{{ item.b_time }}</p>
        </template>
        <template v-slot:[`item.c_score`]="{ item }">
          <div
            :class="getColor(item.c_score)"
            @click="viewSubmission(item.c_score)"
          >
            {{ item.c_score }}
          </div>
          <p class="font-weight-normal">{{ item.c_time }}</p>
        </template>
        <template v-slot:[`item.d_score`]="{ item }">
          <div
            :class="getColor(item.d_score)"
            @click="viewSubmission(item.d_score)"
          >
            {{ item.d_score }}
          </div>
          <p class="font-weight-normal">{{ item.d_time }}</p>
        </template>
        <template v-slot:[`item.e_score`]="{ item }">
          <div
            :class="getColor(item.e_score)"
            @click="viewSubmission(item.e_score)"
          >
            {{ item.e_score }}
          </div>
          <p class="font-weight-normal">{{ item.e_time }}</p>
        </template>
      </v-data-table>
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
          align: "center",
          value: "rank",
          style: "background-color: grey",
        },
        { text: "Name", value: "name", align: "center" },
        { text: "Score", value: "total_score", align: "center" },
        { text: "A", value: "a_score", align: "center" },
        { text: "B", value: "b_score", align: "center" },
        { text: "C", value: "c_score", align: "center" },
        { text: "D", value: "d_score", align: "center" },
        { text: "E", value: "e_score", align: "center" },
      ],
      Users: [
        {
          rank: 1,
          name: "User 1",
          total_score: 5,
          a_score: 1,
          b_score: 1,
          c_score: 1,
          d_score: 1,
          e_score: "1(2)",
          a_time: "00:03:11",
          b_time: "00:23:57",
          c_time: "00:41:06",
          d_time: "01:01:47",
          e_time: "00:59:34",
          penalty: "03:19:35",
        },
        {
          rank: 2,
          name: "User 4",
          total_score: 4,
          a_score: 1,
          b_score: 1,
          c_score: 1,
          d_score: "0(1)",
          e_score: 1,
          a_time: "00:03:11",
          b_time: "00:23:57",
          c_time: "00:41:06",
          d_time: "00:00:00",
          e_time: "01:42:39",
          penalty: "02:50:53",
        },
        {
          rank: 3,
          name: "User 3",
          total_score: 3,
          a_score: "-",
          b_score: 1,
          c_score: 1,
          d_score: 1,
          e_score: "-",
          a_time: null,
          b_time: "00:23:57",
          c_time: "00:41:06",
          d_time: "01:01:47",
          e_time: null,
          penalty: "02:06:50",
        },
        {
          rank: 4,
          name: "User 5",
          total_score: 3,
          a_score: 1,
          b_score: "1(3)",
          c_score: 1,
          d_score: 1,
          e_score: "-",
          a_time: "00:03:11",
          b_time: "00:15:20",
          c_time: "00:41:06",
          d_time: "01:01:47",
          e_time: null,
          penalty: "02:16:24",
        },
        {
          rank: 5,
          name: "User 2",
          total_score: 2,
          a_score: 1,
          b_score: "0(1)",
          c_score: "0(2)",
          d_score: 1,
          e_score: "-",
          a_time: "00:03:11",
          b_time: "00:00:00",
          c_time: "00:00:00",
          d_time: "01:01:47",
          e_time: null,
          penalty: "01:04:58",
        },
        {
          rank: 6,
          name: "User 6",
          total_score: "1",
          a_score: "-",
          b_score: "-",
          c_score: "0(1)",
          d_score: 1,
          e_score: "-",
          a_time: null,
          b_time: null,
          c_time: "00:00:00",
          d_time: "01:01:47",
          e_time: null,
          penalty: "01:01:47",
        },
      ],
    };
  },
  methods: {
    getColor(solved) {
      if (solved == 1 || solved[0] == "1") return "solved";
      else if (solved[0] == "0") return "wrong";
      else return "unsolved";
    },
    viewSubmission(score) {
      if (score == 1)
        window.location.href = "http://localhost:8080/submissions/";
    },
  },
};
</script>

<style scoped>
.body {
  margin: 5%;
  margin-top: 2%;
  background-color: #aaaa;
  flex-direction: row;
  justify-content: flex-end;
}
.wrong {
  color: red;
}
.solved {
  color: green;
}

.wrong,
.solved,
.unsolved,
.total {
  padding-top: 5%;
  padding-right: 9%;
  font-weight: 700;
  font-size: 17px;
}

.solved:hover {
  cursor: pointer;
}
</style>
