<template>
    <div class="container">
        <div class="row p-3 bg-light mt-3 shadow">
            <Info :NumberView="movies.filter(s => s.view > 120)" :NumberLike="movies.filter(s => s.isLike)" />
            <Search @search=SearchMovie />
            <Filter @filterBtn=filterMovie :filter=filter />
            <Lists :massiv=filterByFilter(filterBySearch(movies,search)) @deleteOne=deleteOne @toggleLike=toggleLike
                @heart=changeHeart />
            <Addform @addNew=addNew />
        </div>
    </div>
</template>
<script>
import Addform from '../Addform.vue';
import Filter from '../Filter.vue';
import Info from '../Info.vue';
import Lists from '../Lists.vue';
import Search from '../Search.vue';
export default {
    components: {
        Info,
        Search,
        Filter,
        Lists,
        Addform
    },
    data() {
        return {
            search: "",
            filter: "All",
            movies: [
                { id: 1, name: "Yulduzlar jangi", isLike: false, view: 123, isHeart: { f: false, s: false } },
                { id: 2, name: "Yulduzlar ilmi", isLike: false, view: 3333, isHeart: { f: false, s: false } },
                { id: 3, name: "Oyga qulash", isLike: false, view: 634, isHeart: { f: false, s: false } },
                { id: 4, name: "Sherlock", isLike: false, view: 142, isHeart: { f: false, s: false } },
            ],
        }
    },
    methods: {
        changeHeart(id) {
            this.movies = this.movies.map((s) => {
                if (s.id == id) {
                    return {
                        ...s,
                        isHeart: { ...s.isHeart, s: !s.isHeart.s }
                    }
                } else {
                    return s;
                }
            })
        },
        filterByFilter(err) {
            switch (this.filter) {
                case 'All':
                    return err
                    break;
                case 'popular':
                    return err.filter(s => s.view > 130)
                    break;
                case 'like':
                    return err.filter(s => s.isHeart.s)
                    break;
                case 'star':
                    return err.filter(s => s.isLike)
                    break;

                default:
                    return err;
            }
        },
        filterBySearch(err, fil) {
            if (!fil) {
                return err;
            }
            return err.filter(s => s.name.toLowerCase().includes(fil))
        },
        filterMovie(item) {
            console.log(item);
            this.filter = item;
        },
        SearchMovie(item) {
            this.search = item;
        },
        addNew(item) {
            this.movies.unshift(item);
        },
        deleteOne(id) {
            console.log(id);
            this.movies = this.movies.filter(s => s.id != id);
        },
        toggleLike(id) {

            this.movies = this.movies.map((s) => {
                if (s.id == id) {
                    return {
                        ...s,
                        isHeart: { ...s.isHeart, f: !s.isHeart.f },
                        isLike: !s.isLike,
                    }
                } else {
                    return s;
                }
            });
        },
    },
}
</script>
<style>

</style>