<template >
    <div class="col-md-12 p-3 mx-2">
        <input type="text" class="form-control" placeholder="Search" :value=name @input="$emit('search',$event.target.value)" />
    </div>
</template>
<script>
export default {
    data() {
        return {
            name: "",
        }
    },
    // methods: {
    //     capture(s) {
    //       this.name = s;
    //     }
    // }
}
</script>
<style >

</style>