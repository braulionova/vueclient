<template>
    <div class="container">
        <div class="row justify-content-center">
            <div class="col-md-8">
                <div class="card">
                    <div class="card-header">Vue Axios Post</div>
    
                    <div class="card-body">
                        <form @submit="formSubmit">
                        <strong>Name:</strong>
                        <input type="text" class="form-control" v-model="name">
                        <strong>Description:</strong>
                        <textarea class="form-control" v-model="description"></textarea>
    
                        <button class="btn btn-success">Submit</button>
                        </form>
                        <strong>Output:</strong>
                        <pre>
                        {{output}}
                        </pre>
                        <div>{{mensaje}}</div>
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
              mensaje: ''
            };
        },
        methods: {
            formSubmit(e) {
                e.preventDefault();
                let currentObj = this;
                this.axios.post('https://jsonplaceholder.typicode.com/users', {
                    title: this.name,
                    body: this.description,
                    userId: 1
                })
                .then(function (response) {
                    currentObj.output = response.data;
                    currentObj.mensaje = "Cliente guardado correctamente";
                })
                .catch(function (error) {
                    currentObj.output = error;
                });
            }
        }
    }
</script>
