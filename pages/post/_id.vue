<template>
    <div>
        <b-container>
        <div>
        <br>

        <b-card v-if="singlePost">
            <b-card-text>
                <h1>{{ singlePost.title }}</h1>
                <p>{{ singlePost.body }}</p>
            </b-card-text>
            <b-button variant="outline-danger" @click="backButton">Back</b-button>
        </b-card>
        </div>
    </b-container>
    </div>
</template>
<script>
import axios from "axios";
export default {
    data () {
		return {
			singlePost: ''
		};
    },
    mounted (){
		axios.get(`https://jsonplaceholder.typicode.com/posts/` + this.$route.params.id
		).then((response) => {
			this.singlePost = response.data
		})
    },
    methods: {
        backButton: function () {
            this.$router.push("/");
        }
    }
}
</script>