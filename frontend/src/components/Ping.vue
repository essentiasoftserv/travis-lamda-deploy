<template>
  <div id=first>

    <select class="select">
        <option disabled selected>Select Method</option>
        <option>Increment</option>
        <option>Member Profile</option>
        <option>DIFF</option>
        <option>GAPS</option>
      </select>
      <br>
      <div class="divs">
        <p><label>Old List</label>
        <input class="text-chip-box"></p>
        <p><label>New List</label>
        <input class="text-chip-box"></p>
        <p><label>Age</label>
        <input class="text-chip-box" value="65"></p>
        <p><label>Baserate</label>
        <input class="text-chip-box" value="0"></p>
        <br>
        <br>
        <button @click="formSubmit">Submit</button>
      <br>
      <strong>Output:</strong>
        <pre>
          {{adds}}
          {{raf}}
          {{upgraded}}
        </pre>

     </div>
    </div>
</template>


<script>
    export default {
        mounted() {
            console.log('Component mounted.')
        },
        data() {
            return {
              output: '',
              adds: '',
              raf: '',
              upgraded: '',
            };
        },
        methods: {
            formSubmit(e) {
                e.preventDefault();
                let currentObj = this;
                console.log("inside button");
                this.axios.post('', {
                  "old_list": ["HCC19"],
                  "new_list": ["HCC18"],
                  "ver": "",
                  "model": "",
                  "age": 65,
                  "disabl": 0,
                  "baserate": 0.0
                }
                )
                .then(function (response) {
                    currentObj.output = response.data;
                    currentObj.adds = "Adds: " + response.data.adds[0];
                    currentObj.raf = "RAF: " + response.data.raf;
                    currentObj.upgraded = "Upgraded: " + response.data.upgraded[0];
                })
                .catch(function (error) {
                    currentObj.output = error;
                    // console.log(error);
                });
            }
        }
    }
</script>




<style>
.divs {
  background-color: #FFF2CE;
  height: 450px;
  /* margin-top: 100px; */
  margin-left: 55px;
  margin-right: 55px;
}
.select{
  margin-top: 50px;
  margin-left: -79%;
  color: aliceblue;
  background-color: rgb(84, 127, 235);
  padding: 10px;
  /* -webkit-appearance: none; */
  outline: none;
  border-radius: 10px 10px 0px 0px;
  cursor: pointer;
}
.text-chip-box{
  margin-top: 10px;
}
.text-area-box{
  margin-top: 8px;
  height: 100px;
}
label{
  margin-top: 15px;
  padding-left: 100px;
  float: left;
  /* margin-inline-start: -1620px; */
  /* height: 100px; */
}


</style>
