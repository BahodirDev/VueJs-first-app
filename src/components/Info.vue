<template >
    <div class="row">
        <div class="col-md-6 text-center">
            Eng mashhur {{ NumberLike?.length }}
        </div>
        <div class="col-md-6 text-center">
            Eng ko`p ko`rilgan {{ NumberView?.length }}
        </div>
    </div>  
</template>
<script>
export default {
    props: {
        NumberLike: {
            type: Array,
            required: true
        },
        NumberView: {
            type: Array,
            required: true
        }
    }
}
</script>
<style >

</style>