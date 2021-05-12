<template>
  <div class="list-wrapper">
    <ul>
      <li
          class="item"
          v-for="(item, index) in data"
          :key="item.id">
        <p class="index">{{ index + 1 }}</p>
        <div class="content">
          <p class="name">{{ item.name }}</p>
          <p class="info">
            <span>
              {{ item.ar }}
            </span>
            <span> - </span>
            <span>{{ item.al.name }}</span>
          </p>
        </div>
      </li>
    </ul>
  </div>
</template>
<script>

export default {
  props: {
    data: Array
  },
}
</script>
<style lang="scss" scoped>
.list-wrapper {
  width: 100vw;
  border-top-left-radius: 20px;
  border-top-right-radius: 20px;
  height: 50vh;
  overflow: auto;
  position: absolute;
  left: 0;
  bottom: 60px;
  background: white;

  .item {
    display: flex;
    padding: 10px;

    > .index {
      width: 40px;
      height: 40px;
      text-align: center;
      line-height: 40px;
      font-size: 16px;
    }

    > .content {
      flex: 1;
      height: 40px;
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: flex-start;

      > .name {
        font-size: 16px;
        font-weight: normal;
      }

      > .info {
        font-size: 14px;
        color: #555;
      }
    }
  }
}
</style>
