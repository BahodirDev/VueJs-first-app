<template >
    <div class="col-md-12 mb-4">
        <div>
            <input type="text" class="form-control mt-3 p-3" :value="name" @input="name = $event.target.value" placeholder="Name">
            <input type="number" class="form-control mt-3 p-3" :value="count" @input="count = $event.target.value" placeholder="Count">
            <button class="btn btn-outline-primary mt-2" @click="$emit('addNew',{id:Date.now(),name,view:count})">Add</button>
        </div>
    </div>
</template>
<script>
export default {
    data(){
        return{
            count:'',
            name:""
        }
    },
    // props: {
    //     addNew:{
    //         type:Function,
    //         required:true
    //     }
    // },
}
</script>
<style >
    
</style>