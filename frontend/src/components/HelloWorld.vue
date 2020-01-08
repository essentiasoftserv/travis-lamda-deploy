<template>
    <div class="container">
        <div class="row justify-content-center">
            <div class="col-md-8">
                <div class="card">
                    <div class="card-header">Lambda Test App</div>
                      <br><br><br>
                    <div class="card-body">
                        <form @submit="formSubmit">
                        <strong>Name:     </strong>
                        <input type="text" class="form-control" v-model="name"><br><br><br>
                        <strong>Description:  </strong>
                        <textarea class="form-control" v-model="description"></textarea><br><br><br>
    
                        <button class="btn btn-success">Submit</button>
                        </form>
                        <br><br><br>
                        <strong>Output:</strong>
                        <pre>
                        {{output}}
                        </pre>
                    </div>
                </div>
            </div>
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
              output: '',
                api: process.env.VUE_APP_API
            };
        },
        methods: {
            formSubmit(e) {
                e.preventDefault();
                let currentObj = this;
                this.axios.post(this.api, {
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