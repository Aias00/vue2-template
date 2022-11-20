<template>
  <div>
    <div :id="item.name" v-for="(item, index) in data" :key="index">
      <Card class="nodeCard" v-if="true">
        <!-- <p slot="name" class="anchor">
          {{ item.name }}<a :href="'#' + item.name">#</a>
        </p> -->
        <label>series: {{ item.series }}</label>
        <br />
        <label>shortName: {{ item.shortName }}</label>
        <br />
        <label>fullName: {{ item.name }}</label>
        <!-- <a
          :href="'/gallery/block/' + item.name"
          target="_blank"
          style="width=100%"
          >屏蔽</a
        > -->
        <br />
        <div>
          <label>source: </label>
          <a :href="item.source" target="_blank" style="width=100%">{{
            item.from
          }}</a>
        </div>
        <div>
          <label>url: </label>
          <a :href="item.url" target="_blank" style="width=100%">{{
            item.name
          }}</a>
        </div>
        <img :src="item.img" alt="" />
      </Card>
    </div>
  </div>
</template>

<script>
import { mapGetters, mapActions } from 'vuex'
export default {
  props: {
    data: {
      default: {}
    },
    spinShow: {
      default: false
    }
  },
  methods: {
    removeUsed () {
      this.removeUsedList()
      this.$Message.success('清空成功')
    },
    removeFavorite () {
      this.removeFavoriteList()
      this.$Message.success('清空成功')
    },
    ...mapActions([
      'removeUsedList',
      'removeFavoriteList'
    ])
  },
  computed: {
    ...mapGetters([
      'favoriteList',
      'usedList'
    ])
  }
}
</script>

<style scoped>
.anchor a {
  opacity: 0;
  font-size: 24px;
  transition: opacity 0.2s ease-in-out;
  margin-left: 5px;
  position: relative;
  top: 2px;
}
.nodeCard {
  margin: 20px 20px 0 20px;
  /* padding-left: 150px; */
}
</style>
