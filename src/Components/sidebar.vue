<template>
<div class="col-md-2 col-12 sidebar-main  float-start">
  <nav class="sidebar">
    <div class="sidebar-header"><h3 class="font-bold">Filter</h3></div>
    <div class="applied-filter" style="display: none">
      <h3>Applied Filters</h3>
      <ul>
        <ul>
          <li>
            <a href="#" class="remove"><span>Remove This Item</span></a
            ><span class="filter-label"></span><span>Category: Kurtas</span>
          </li>
        </ul>
      </ul>
      <a href="#" class="filter-clear"><span>Clear All</span></a>
    </div>
    <ul class="list-unstyled components" v-for="item in list" v-bind:key="item.filter_lable">
      <li class="filter-box">
        <a href="#" class="mobile-active dropdown-toggle"
          ><span>{{item.filter_lable}}</span
          ><!----></a
        >
        <ul class="collapse list-unstyled mobile-active">
          <li class="kurtas">
            <a href="#" value="Category_Kurtas" style="display: " class=""
              ><span>Kurtas</span>
              <span class="filtertotal" style="display: ">(2209)</span></a
            >
          </li>
          <li class="sets-_-dresses">
            <a
              href="#"
              value="Category_Sets &amp; Dresses"
              style="display: "
              class=""
              ><span>Sets &amp; Dresses</span>
              <span class="filtertotal" style="display: ">(11)</span></a
            >
          </li>
          <li class="top-wear-_-kurtas">
            <a
              href="#"
              value="Category_TOP WEAR > KURTAS"
              style="display: "
              class=""
              ><span>TOP WEAR &gt; KURTAS</span>
              <span class="filtertotal" style="display: ">(2)</span></a
            >
          </li>
          <li class="tops">
            <a href="#" value="Category_Tops" style="display: " class=""
              ><span>Tops</span>
              <span class="filtertotal" style="display: ">(1)</span></a
            >
          </li>
        </ul>
      </li>
    </ul>
  </nav>
</div>
</template>
<script>
export default {
  name: "App",
  data () {
    return {
      list:[],
    }
  },
  methods:{
    getData(){
      fetch(`https://pim.wforwoman.com/pim/pimresponse.php/?service=category&store=1&url_key=top-wear-kurtas&page=1&count=20&sort_by=&sort_dir=desc&filter=`)
      .then (res => res.json())
      .then(data => this.list=data.result.filters)
    }
  },
  mounted(){
  this.getData()
}
};
</script>
