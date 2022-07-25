<script>
    export default {
        data: () => ({
            note: []
        }),
        async created() {
            this.note = await this.$content(`notes/${this.$route.params.slug}`).fetch()
        }
    }
</script>

<template>
    <main>
        <h1>{{ note.title }}</h1>
        <nuxt-content :document="note" />
    </main>    
</template>