<template>
  <div>
    <h1>readinglistview</h1>
    <p>VAFAN SNACKAR DU OM OSKKKAR?</p>
    <p v-for="obj in renderList" :key="obj.title">{{obj.title}}</p>
    <button>{{$root.foo}}</button>
  </div>
</template>

<script>

export default {
  props: ['book'],
  data(){return{
    renderList: []
  }},
  beforeMount(){
    let savedReadingList = []
      if(localStorage.getItem('localReadList')){
      savedReadingList = [...JSON.parse(localStorage.getItem('localReadList'))]
      } 

    if(this.book != "undefined" && this.book){
       savedReadingList.push(this.book)
       this.updateLocalstorage(savedReadingList)
    }
  
    
      this.renderList = [...savedReadingList]
  
     
  },
  mounted(){

  },
  methods: {
    updateLocalstorage(item){
      localStorage.setItem('localReadList', JSON.stringify([...item]))
    }
  }
  // watch: {
  //   book: function(){
  //   if(this.book != "undefined"){
  //      this.readingList.push(this.book)
  //   }
  // }
  // }
}
</script>

<style>

</style>