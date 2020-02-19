<template>
  <div style="text-align:left;">{{msg}}
      <div class="card" style="width: 40rem;">
        <div class="card-header" style="font-weight:bold;">
          進行中
        </div>
        <ul class="list-group list-group-flush">
          <order-item v-for="(item,index) of onList" 
            :key="index"
            :content="item"
            :index="index"
            :isfinish="false"
            >
            {{item}}
          </order-item>
        </ul>
      </div>
      <div class="card" style="width: 40rem;margin-top:2%;">
        <div class="card-header" style="font-weight:bold;">
          已完成
        </div>
        <ul class="list-group list-group-flush">
          <order-item v-for="(item,index) of finishList" 
            :key="index"
            :content="item"
            :index="index"
            :isfinish="true"
            >
            {{item}}
        </order-item>
        </ul>
      </div>
  </div>
</template>

<script>
import OrderItem from './OrderItem'
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  components: {
        OrderItem
    },
    created(){
      // call api
      let response = {
          orders: [
              {
                  name: 'Livi優活 抽取式衛生紙(100抽x10包x10串/箱)',
                  logo: 'https://static.oopocket.com/store/iconTreemall@3x.png',
                  status: {
                    code: 3,
                    type: '已取消'
                  },
                  date: '107/6/12'
              },
              {
                  name: 'BALMUDA The Toaster 百慕達烤麵包機-黑色',
                  logo: 'https://static.oopocket.com/store/iconTreemall@3x.png',
                  status: {
                    code: 2,
                    type: '已成立'
                  },
                  date: '108/7/21'
              },
              {
                  name: '贈-短慧萬用鍋HD2133+三合一濾網「LG樂金」韓國原裝...',
                  logo: 'https://static.oopocket.com/store/iconTreemall@3x.png',
                  status: {
                    code: 1,
                    type: '處理中'
                  },
                  date: '108/6/2'
               },
               {
                  name: 'Apple AirPds 2',
                  logo: 'https://static.oopocket.com/store/iconTreemall@3x.png',
                  status: {
                    code: 4,
                    type: '已送達'
                  },
                  date: '108/3/02'
              }
          ]
      };
      let orders = response.orders.sort(function(a, b) {
          return -(new Date(a.date) - new Date(b.date));
      });
      this.finishList = orders.filter(o => [3, 4].includes(o.status.code))
      this.onList = orders.filter(o => [1, 2].includes(o.status.code))
      console.log(this.finishList)
    }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  h3 {
    margin: 40px 0 0;
  }
  ul {
    list-style-type: none;
    padding: 0;
  }
  li {
    display: inline-block;
    margin: 0 10px;
  }
  a {
    color: #42b983;
  }
</style>
