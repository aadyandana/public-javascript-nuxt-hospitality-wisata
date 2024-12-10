<template>
    <div>
        <h2>Deals</h2>
        <p>{{ content }}</p>
    </div>
</template>

<script>
export default {
    props: {
        content: {
            type: Object,
            required: true
        }
    }
}
</script>