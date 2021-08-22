<template>
  <div class="page-content">
    <img class="pc"
      :src="PCImg" />
    <img class="ipad"
      :src="IpadImg" />
    <img class="mobile"
      :src="MobileImg" />
    <!-- v-for data ... -->
    <!-- v-for extraData ... -->
  </div>
</template>

<script>
import PCImg from './assets/PC.jpg';
import IpadImg from './assets/ipad.jpg';
import MobileImg from './assets/moblie.png';
import mockData from './mockData.json';

export default {
  data () {
    return {
      PCImg,
      IpadImg,
      MobileImg,
      data: [],
      extraData: [],
    }
  },
  mounted () {
    try {
      const xhr = new XMLHttpRequest();
      xhr.open('get', 'https://mock.mengxuegu.com/mock/6121e04ea035092b3eed4dab/example/mock');
      xhr.send();
      xhr.onreadystatechange = function () {
        if (this.readyState === 4) {
          if (this.status === 200) {
            // this.data = this.response.data
            if (mockData.length > 6) {
              this.data = mockData.slice(0, 5)
              this.extraData = mockData.slice(5, Math.min(mockData.length, 9))
            } else {
              this.data = mockData
            }
            console.log(
              this.data,
              this.extraData
            )
          }
        }
      }
    } catch (error) {
      console.error(error);
    }
  }
}
</script>

<style lang="less">
.page-content {
  img {
    display: none;
    width: 100vw;
  }
}

@media (max-width: 767px) {
  .page-content {
    img.mobile {
      display: inline-block;
    }
  }
}
@media (min-width: 768px) and (max-width: 979px) {
  .page-content {
    img.ipad {
      display: inline-block;
    }
  }
}
@media (min-width: 980px) {
  .page-content {
    img.pc {
      display: inline-block;
    }
  }
}
</style>
