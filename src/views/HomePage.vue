<template>
  <div class="">
    <div v-if="loading"
         class="loader-wrapper">
      <pulse-loader></pulse-loader>
    </div>
    <div class="logo_btn">
  	 <section>
		  <div class="cardContainer">
			 <div class="cardcharas">
				 <img class="charaimg" alt="" srcset="https://cryptohero.pro/static/big-logo.png"/>
			 </div>
		 	<div class="btnContainer">
				 <div class="cardbtn">
				  	<a> <img class="btnimg" @click="drawClicked()" width="150" alt="" srcset="/static/assets/btn.png"/> </a>
         </div>
        <!-- <div class="price">
          <div class="price1">
            <b>{{$t('CurrentContractBalance')}}{{this.getBalance}}</b>
          </div>
          <div class="price1">
            <b>{{$t('TotalBonus')}}{{this.getTotalEarnByShareAllUser}}</b>
          </div>
          <div class="price1">
            <b>{{$t('TotalRecommendRebate')}}{{this.getTotalEarnByReferenceAllUser}}</b>
          </div>
        </div> -->
          <div class="txt">
        <span>{{$t('Recomment')}}</span>
        </div>
      </div>
		  </div>
     </section>
    </div>
    <ItemList :itemIds='itemIds' />
  </div>
</template>

<script>
import PulseLoader from 'vue-spinner/src/PulseLoader';
import ItemList from '@/components/ItemList';
import fakeCardData from './fakeCardData.json';
import { toReadablePrice } from '@/util';

export default {
  name: 'item-list',
  components: {
    PulseLoader,
    ItemList,
  },

  data() {
    return {
      loading: true,
      itemIds: [],
      total: null,
    };
  },

  computed: {},
  asyncComputed: {
    // async getBalance() {
    //   const idol = new Contract();
    //   const result = await idol.getBalance();
    //   return JSON.parse(result) || 0;
    // },
    // async getTotalEarnByShareAllUser() {
    //   const idol = new Contract();
    //   const result = await idol.getTotalEarnByShareAllUser();
    //   return JSON.parse(result) || 0;
    // },
    // async getTotalEarnByReferenceAllUser() {
    //   const idol = new Contract();
    //   const result = await idol.getTotalEarnByReferenceAllUser();
    //   return JSON.parse(result) || 0;
    // },

  },
  async created() {
    // const contrat = new Contract();
    // const total = 12;
    // if (total === 0) {
    //   this.loading = false;
    //   return;
    // }
    // const ids = [];
    // const start = total - 12;
    // for (let i = total; i >= start; --i) {
    //   ids.push(i);
    // }
    // /*   let ids = [];
    // for (let i = 12; i > 0 ; --i) {
    //   ids.push(i);
    // } */
    // // 通过tokenId图片相关信息
    // //    const result = await contrat.getCarInfoByTokenId(itemIds);
    // const result = await contrat.getCarInfoByTokenId(ids);
    this.itemIds = fakeCardData;
    this.loading = false;
  },

  methods: {
    toDisplayedPrice(priceInWei) {
      const readable = toReadablePrice(priceInWei);
      return `${readable.price} ${readable.unit}`;
    },
    drawClicked() {
      const href = '/#/draw';
      window.location.href = href;
    },
  },
  watch: {},
};
</script>
<style scoped>
.cardContainer {
	background-size: 100%;
	background-repeat: no-repeat;
	width: 100%;
	/*padding-top: 43.5%;*/
	padding-top: 50%;
	position: relative;
	text-align: center;
}
.cardcharas {
  position: absolute;
  top: 0;
  left: 0;
	width: 100%;
}
.charaimg{
  width: 80%;
    display: block;
    margin-left: auto;
    margin-right: auto;
}
.btnContainer {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
	padding-top: 33%;
  /*background-color: #ccc;*/
}
.cardbtn {
    display: block;
    margin-left: auto;
    margin-right: auto;
        display: block;
    margin-bottom: 30px;
}
.columns.is-gapless {
    margin-top: 290px;
}
.txt{
  border:  5px solid darkgoldenrod;
  padding: 10px;
  background-color: blanchedalmond;
  margin-top: 70px;
}
.loader-wrapper {
  display: flex;
  align-items: center;
  justify-content: center;
  height: 100vh;
}

.price{
  width: 100%;
  margin-top: 30px;
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
}
.price1{
  border-radius: 8px;
  width: 400px;
  height: 50px;
  background-color: rgba(249, 137, 137, 0.55);
  margin: 20px;
  text-align: center;
  border: 1px solid #ffd67a;
}
.price1 b{
  color: #f7ad89;
  line-height: 50px;
  font-size: 18px;
}
@media screen and (max-width: 500px){
  .cardcharas{
    display: none;
  }
  .btnContainer {
	padding-top: 17%;
  }
  .price1 b{
  line-height: normal;
}
.price1{
   height: 80px;
   padding: 10px;
}
.columns.is-gapless:last-child {

   margin-top: 655px;
}

}

</style>
