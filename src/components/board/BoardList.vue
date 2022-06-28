<template>
  <b-container class="bv-example-row mt-3">
    <b-row>
      <b-col> </b-col>
    </b-row>
    <b-row class="mb-1">
      <b-col class="text-right"> </b-col>
    </b-row>
    <b-row>
      <b-col v-if="articles.length">
        <b-table-simple hover responsive>
          <b-thead head-variant="dark">
            <b-tr>
              <b-th>글번호</b-th>
              <b-th>제목</b-th>
              <b-th>조회수</b-th>
              <b-th>작성자</b-th>
              <b-th>작성일</b-th>
            </b-tr>
          </b-thead>
          <tbody>
            <!-- 하위 component인 ListRow에 데이터 전달(props) -->
            <board-list-item
              style="background-color: rgba(144, 221, 255, 0.5)"
              v-for="article in articles"
              :key="article.articleno"
              v-bind="article"
            />
          </tbody>
        </b-table-simple>
        <b-button id="writeBtn" variant="outline-primary" @click="moveWrite()"
          >글쓰기</b-button
        >
      </b-col>
      <!-- <b-col v-else class="text-center">도서 목록이 없습니다.</b-col> -->
    </b-row>
  </b-container>
</template>

<script>
import http from "@/api/http";
import BoardListItem from "@/components/board/item/BoardListItem";

export default {
  name: "BoardList",
  components: {
    BoardListItem,
  },
  data() {
    return {
      articles: [],
    };
  },
  created() {
    http.get(`/board`).then(({ data }) => {
      this.articles = data;
    });
  },
  methods: {
    moveWrite() {
      this.$router.push({ name: "boardRegister" });
    },
  },
};
</script>

<style scope>
#writeBtn {
  float: right;
  margin-top: 10px;
  border-width: 5px;
  color: black;
  font-weight: bold;
  border-color: #99ddff;
  background-color: #99ddff;
}
</style>
