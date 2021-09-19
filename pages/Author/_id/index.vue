<template>

    <div>
        <!-- id {{ $route.params.user_id }}
         qui è dove recupero il paramentro id che poi catturo con la chiamata asyncdata,
         in questo caso recupero ll user_id e poi stampo i suoi dati da un'altra api-->
        <div class="container mx-auto flex justify-center">
            <AuthorCard :author_name="currentAuth.author_name"
                        :activity_description="currentAuth.activity_description"/>
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
                return {currentAuth: response.data};
            }).catch(error => console.log(error));
    },

    data() {
        return {}
    },
}
</script>

<style scoped>

</style>
