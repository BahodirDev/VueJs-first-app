<template >
    <div class="col-md-12 c_size">
        {{ !massiv.length ? "Ma`lumot yo`q" : null }}
        <div class="d-flex justify-content-between p-3 shadow mt-4 rounded align-items-center " v-for="app in massiv"
            :class="[app.isHeart.s ? ' bg-danger' : ' bg-primary']">

            <p class="m-0" :class="[app.isLike != true ? '' : 'text-yellow']">{{ app.name }}</p>
            <div class="d-flex justify-content-around align-items-center">
                <div class="m-3">
                    <i class="fa-regular fa-heart pointer" @click="$emit('heart', app.id)"
                        :class="[app.isHeart.f ? 'active_heart' : 'passiv_heart']"></i>
                </div>
                <div class=" p-2 rounded act_color">
                    <i class="mx-2 pointer"
                        :class="[app.isLike ? 'fa-sharp fa-solid fa-star text-yellow' : 'fa-sharp fa-regular fa-star']"
                        @click="$emit('toggleLike', app.id)"></i>
                    <i class="fa-solid fa-trash mx-2 pointer" @click="$emit('deleteOne', app.id)"></i>
                </div>
            </div>
        </div>
    </div>
</template>
<script>
export default {
    props: {
        massiv: {
            type: Array,
            required: true
        }
    }
}
</script>
<style scoped>
.passiv_heart {
    transform: translateX(-50px);
    color: red;
    opacity: 0;
    transition: all .3s linear;
}

.active_heart {
    transform: translateX(0);
    color: #01105e;
    opacity: 1;
    transition: all .3s linear;


}

.act_color {
    background: #5586e189;
    border: 1px solid #01105e;
}

.pointer {
    cursor: pointer;
}

.text-yellow {
    color: gold;
}

.c_size {
    height: 50vh;
    overflow-y: scroll;
}
</style>