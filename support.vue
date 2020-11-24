<template>
    <div class="w-100">
       <h1>Support</h1> 
   
        <form >
            <div class="form-row">
                <div class="col-md-6 mb-3">
                    <label for="item">Enter Item:</label>
                    <input type="text" class="form-control form-control-lg" id="item" required>
                    
                </div>
                <div class="col-md-6 mb-3">
                    <label for="department">Select Department:</label>
                    <select class="custom-select custom-select-lg" id="department">
                        <option selected disabled value="">Choose...</option>
                        <option
                         v-for="dep in department" 
                         v-bind:key="dep.id" 
                        >
                            {{dep.name}}
                        </option>
                    </select>
                </div>
            </div>
            <button class="btn btn-primary" type="submit">Add Item</button>
        </form>

       
    </div>  
</template>



<script>
export default {
    data: function(){
        return{
            department: []
        }
    },
    
    mounted(){
        this.getDepartment();          
    },

    methods: {
        getDepartment(){
            axios.get('/api/department')
            .then((res) => {this.department = res.data.data
            })
            .catch((error) =>{
                console.log(error)
            });
        
        }
    }
}
</script>

<style>

</style>
