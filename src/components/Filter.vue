<template >
    <div class="row mb-3">
        <div class="col-md-3 text-center mt-2" v-for="btn in btns">
            <button @click="$emit('filterBtn',btn.value)" class="btn "
                :class="[btn.value == filter ? `btn-primary` : `btn-outline-primary`]">{{ btn.name }}</button>
        </div>
    </div>
</template>
<script>
export default {
    data() {
        return {
            btns: [
                { id: 1, name: "All", value: "All" },
                { id: 2, name: "Most View", value: "popular" },
                { id: 3, name: "Like", value: "like" },
                { id: 4, name: "Sevimli", value: "star" },
            ],
        }
    },
    props: {
        filter: {
            type: String,
            required: true
        }

    }
}
</script>
<style >

</style>