<template>
    <div>
        <h2>Photos</h2>
        <p>{{ content }}</p>
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