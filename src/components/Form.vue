<template>
  <div class="form__main__cont">
    <div class="form__main__cont__personaldat">
      <p class="form__main__cont__personaldat__h">Персональные данные</p>
      <div class="form__main__cont__personaldat__forinput">
        <label
          class="form__main__cont__personaldat__forinput__label"
          for="namePersonal"
          >Имя</label
        >
        <input
          id="namePersonal"
          v-model="AllData.name"
          class="form__main__cont__personaldat__forinput__decoration"
          type="text"
        />
      </div>
      <div class="form__main__cont__personaldat__forinput">
        <label
          class="form__main__cont__personaldat__forinput__label"
          for="agePersonal"
        >
          Возраст</label
        >
        <input
          id="agePersonal"
          v-model="AllData.age"
          class="form__main__cont__personaldat__forinput__decoration"
          type="text"
        />
      </div>
    </div>
    <div class="form__main__cont__children">
      <p class="form__main__cont__personaldat__h child">Дети (макс. 5)</p>
      <a v-if="AllData.children.length <= 4 " @click="newChild(AllData.children.length)" class="form__main__cont__children_button">
        Добавить ребёнка</a
      >
      <div class="space">

      </div>
      <div class="forchildInputs">
        <div class="form__main__cont__child__forinput" v-for="child in AllData.children" :key="child.name">
          <div class="forinput">
          <label
            class="form__main__cont__child__forinput__label"
            for="agePersonal"
          >
            Имя</label
          >
          <input
          v-model="child.child_name"
            :id="'name' + child.id"
            class="form__main__cont__personaldat__forinput__decoration__child"
            type="text"
          />
          </div>
          <div class="forinput">
                      <label
            class="form__main__cont__child__forinput__label"
            for="namePersonal"
            >Возраст</label
          >
          <input
            v-model="child.age"
            :id="'age' + child.id"
            class="form__main__cont__personaldat__forinput__decoration__child"
            type="text"
          />
          </div>
          <a @click="removeChild(child.id)" class="form__main__cont__child__delete">Удалить</a>
        </div>
      </div>
    </div>
    <div class="form__main__cont__forbutton">
      <a @click="save()" class="form__main__cont__save"> Сохранить </a>
    </div>
  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  data() {
    return {
      count: 0,
      AllData: {
        name: "",
        age: "",
        children: [],
      },
    };

  },
  methods: {
    newChild(id){
    const child = {
      id: id,
      child_name: "",
      age: "",
      children: {

      }
    }
    this.AllData.children.push(child);
  },
  removeChild(id){
    this.AllData.children.splice(this.AllData.children.findIndex(function(i){
    return i.id === id;
}), 1);
  },
  save(){
    const sendler = JSON.stringify(this.AllData)
    localStorage.setItem("Data", sendler)

  }
  },
  mounted() {
    const smth = []
    smth.push(this.AllData)
    console.log(smth)
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
.form__main__cont__personaldat__forinput__decoration {
  height: 35px;
  border: 1px solid #c9c9c9;
  border-radius: 4px;
  width: 100%;
  padding-left: 10px;
  padding-top: 5px;
  font-size: 18px;
  transition: all 1s;
  line-height: 2.6em;
  padding-top: 25px;
}
.space{
  height: 30px;
}
.form__main__cont__personaldat__forinput__decoration::focus-visible {
  border: 1px solid #a7a7a7;
}
.form__main__cont__personaldat__forinput__label {
  position: relative;
  font-weight: 400;
  color: #8a8a8a;
  font-size: 16px;
  top: 25px;
  left: 10px;
  display: inline;
  margin: 0;
}

.form__main__cont__children_button {
  color: #01a7fd;
  font-size: 18px;
  border: 1px solid #01a7fd;
  border-radius: 100px;
  cursor: pointer;
  height: 30px;
  width: 200px;
  text-align: center;
  padding-top: 10px;
  float: right;
  transition: all 1s;
}
.form__main__cont__children_button:hover {
  background-color: #01a7fd;
  color: white;
}
.form__main__cont__children {
  margin-top: 30px;
}
.form__main__cont__personaldat__forinput__decoration__child {
  height: 35px;
  border: 1px solid #c9c9c9;
  border-radius: 4px;
  width: 90%;
  display: flex;
  padding-left: 10px;
  padding-top: 5px;
  font-size: 18px;
  transition: all 1s;
  line-height: 2.6em;
  padding-top: 25px;
}
.form__main__cont__child__forinput{
  display: grid;
  grid-template-columns: 3fr 3fr 1fr;
  grid-column-gap: 20px;
  margin-right: 0;
}
.form__main__cont__child__forinput__label{
  display: inline-block;
  position: relative;
  font-weight: 400;
  color: #8a8a8a;
  font-size: 16px;
  top: 25px;
  left: 10px;
  display: inline;
  margin: 0;
}
.form__main__cont__child__delete{
  color: #01a7fd;
  margin-top: 35px;
  font-size: 18px;
  cursor: pointer;
}
.form__main__cont__save {
  float: left;
  margin-top: 20px;
  color: #01a7fd;
  font-size: 18px;
  border: 1px solid #01a7fd;
  border-radius: 200px;
  cursor: pointer;
  height: 40px;
  width: 130px;
  text-align: center;
  padding-top: 15px;
  float: right;
  transition: all 1s;
}
.form__main__cont__save{
  background-color: #01a7fd;
  color: white;
}
</style>
