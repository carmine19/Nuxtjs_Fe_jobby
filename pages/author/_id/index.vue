<template>

    <div>
        <!-- id {{ $route.params.user_id }}
         qui è dove recupero il paramentro id che poi catturo con la chiamata asyncdata,
         in questo caso recupero lo user_id e poi stampo i suoi dati da un'altra api-->
        <div class="box-Author container mx-auto flex justify-center items-center">
            <AuthorCard :author_name="currentAuthor.author_name"
                        :activity_description="currentAuthor.activity_description"/>
        </div>
    </div>
</template>

<script>
import axios from "axios";
import AuthorCard from "../../../components/AuthorCard";

export default {
    components: {AuthorCard},
    asyncData(ctx) {
        return axios.get('http://127.0.0.1:8000/api/author/' + ctx.params.id)
            .then((response) => {
                return {currentAuthor: response.data};
            }).catch(error => console.log(error));
    },

    data() {
        return {}
    },
}
</script>

<style scoped>

.box-Author {
    height: 100vh;
}

</style>
