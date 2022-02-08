<template>
  <div class="form__main__cont">
    <div class="form__main__cont__personaldat">
      <p class="form__main__cont__personaldat__h">Персональные данные</p> <br> <br/>
      <p v-show="Data.name || Data.age" class='form__main__cont__personaldat__p'>{{Data.name}}, {{Data.age}}</p>
    </div>
    <div class="form__main__cont__forchild">
       <p class="form__main__cont__personaldat__h">Дети</p>  
       <div class="form__main__cont__forchild__c">
           <div v-for='child in Data.children' :key='child.id' class="form__main__cont__forchild__data">
               {{child.child_name}}, {{child.age}}
           </div>
       </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  data() {
    return {
        Data: {},
    };
  },
  mounted() {
      const getter = JSON.parse(localStorage.getItem("Data"))
      this.Data = getter
      console.log(this.Data)
  },
  
  props: {},
};
</script>

<style scoped>
.form__main__cont {
  margin-top: 20px;
  padding: 0 30%;
  text-align: left;
}
.form__main__cont__personaldat__h {
  font-size: 20px;
  font-weight: 550;
  margin-bottom: 0;
  display: inline;
}
.form__main__cont__personaldat__p {
  font-size: 24px;
  font-weight: 700;
  margin-bottom: 0;
  display: inline;
  margin-bottom: 10px;
}
.form__main__cont__forchild{
    margin-top: 50px;
}
.form__main__cont__forchild__data{
    height: 45px;
    max-width: 120px;
    padding-top: 12px;
    padding-left: 15px;
    padding-right: 15px;
    background-color: #F1F1F1;
    font-size: 22px;
    font-weight: 700;
    border-radius: 4px;
    text-align: center;
    margin-top: 20px;
}
</style>
