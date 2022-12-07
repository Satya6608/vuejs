<template>
  <div class="col-md-10 col-12 product-section-main float-end">
    <div class="col-md-12 product-list">
      <div class="row">
        <div v-for="item in list" v-bind:key="item.id_product" @scroll="load" class="col-md-3 col-sm-6 col-xs-6 col-6" >
          <div class="slide-box">
            <div class="product-box">
              <a
                :href=item.url_key
                class="view-detail"
              >
                View Detail
              </a>
              <a
                :href=item.url_key
                class=""
                ><div class="w-100">
                  <img
                    :src=item.image
                    :alt=item.name
                  /></div></a>
            </div>
            <p>
              <a
                :href=item.url_key
                class=""
                >{{item.name}}</a
              >
            </p>
            <div class="price">
              <p>
                <span class="old-price">Rs. {{item.price}}</span>
                <span class="price">Rs. {{item.selling_price}}</span>
                <span class="discount_percent font-bold">{{item.discount}}</span>
              </p>
            </div>
            <div class="size">
              <p>
                Size -{{item.size}}
                <!-- <span>6</span><span>8</span><span>10</span><span>12</span
                ><span>14</span><span>16</span><span>18</span> -->
              </p>
            </div>
          </div>
        </div>
      </div>
    </div>
    <InfiniteLoading @scroll="load" />
  </div>
</template>
<script>
  import { ref } from "vue";
  import "v3-infinite-loading/lib/style.css";
export default {
  name: "App",
  data () {
    return {
      list:ref([]),
      page :1,
    }
  },
  methods:{
    getData(){
      fetch(`https://pim.wforwoman.com/pim/pimresponse.php/?service=category&store=1&url_key=top-wear-kurtas&page=${this.page}&count=20&sort_by=&sort_dir=desc&filter=`)
      .then (res => res.json())
      .then(data => this.list=data.result.products)
      if (this.list.length < 20){
        this.list;
      console.log(this.list);
      }
        else {
          this.list.loaded();
        }
        this.page++;
        console.log(this.page)
    }
},
mounted(){
  this.getData()
},
};
</script>
