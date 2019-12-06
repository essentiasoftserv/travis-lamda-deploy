<template>
  <div id=first>
   
    <select class="select">
        <option disabled selected>Select Method</option>
        <option>Member Profile</option>
        <option>Increment</option>
        <option>DIFF</option>
        <option>GAPS</option>
      </select>
      <br>
      <label>Condition</label>
    <div class="divs"> 
 <input class="text-chip-box">
 <button @click="formSubmit">Submit</button>

  <br>
      <strong>Output:</strong>
                        <pre>
                        {{output}}
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
              name: '',
              description: '',
              output: ''
            };
        },
        methods: {
            formSubmit(e) {
                e.preventDefault();
                let currentObj = this;
                console.log("inside button");
                this.axios.post('httphttp://34.219.188.236/member', {
                    // name: this.name,
                    // description: this.description

                    "funct_name": "hcc2raf",
                    "params": {
                        "hcc_list": ["HCC18", "HCC19"],
                        "age": 90,
                        "ver": 23,
                        "model": "v23",
                        "disabl": 1,
                        "baserate": 800
                    }
                },
                // {
                //   headers: {
                //     ContentType: "application/x-www-form-urlencoded",
                //     Accept: "*/*",
                //     AccessControlAllowOrigin: "*", 
                //     AccessControlAllowCredentials: true 
          
                //     }

                //     /*
                //     headers: {
                //       "Access-Control-Allow-Origin" : "*", // Required for CORS support to work
                //       "Access-Control-Allow-Credentials" : true // Required for cookies, authorization headers with HTTPS
                //     },
                //     */
                // }
                )
                .then(function (response) {
                    currentObj.output = response.data;
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
  height: 300px;
  /* margin-top: 100px; */
  margin-left: 55px;
  margin-right: 55px;
}
.select{
  margin-top: 50px;
  color: aliceblue;
  margin-inline-start: -1603px;
  background-color: rgb(84, 127, 235); 
  padding: 10px;
  /* -webkit-appearance: none; */
  outline: none;
  border-radius: 10px 10px 0px 0px;
  cursor: pointer;
}
.text-chip-box{
  margin-top: 10px;
  margin-inline-start: -1320px;
}
.text-area-box{
  margin-top: 8px;
  margin-inline-start: -1315px;
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
