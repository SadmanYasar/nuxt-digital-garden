<script>
    export default {
        async asyncData({ $content }) {
            const notes = await $content("notes").sortBy("publishOn", "desc").fetch()

            return {
                notes
            }
        }
    }
</script>

<template>
    <main>
        <h1>My notes</h1>
        <ul>
            <li v-for="note in notes" :key="note.slug + note.createdAt">
                <h2>
                    <nuxt-link :to="`/notes/${note.slug}`">{{ note.title }}</nuxt-link>
                </h2>
                <p>Published on: {{ new Date(note.publishOn) }}</p>
                <ul>
                    <li v-for="tag in note.tags" :key="note.slug + tag">
                        {{ tag }}
                    </li>
                </ul>
            </li>
        </ul>
    </main>
</template>