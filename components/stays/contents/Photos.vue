<template>
    <div>
        <v-row>
            <v-col
                v-for="(photo, index) in content"
                :key="index"
                cols="4"
                class="d-flex justify-center"
            >
                <v-img :src="photo.url.ori" :alt="photo.group" />
            </v-col>
        </v-row>
    </div>
</template>

<script>
export default {
    props: {
        content: {
            type: Array,
            required: true
        }
    }
}
</script>