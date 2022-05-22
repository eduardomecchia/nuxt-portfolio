<template>
    <div class="project-card">
        {{ project.title }}
        {{ project.description }}
        {{ project.url }}
        {{ project.image }}
        {{ project.technologies }}
        {{ project.date }}
        {{ project.github }}
    </div>
</template>

<script>
    export default {
        name: 'ProjectCard',

        data() {
            return {
                project: {
                    name: '',
                    description: '',
                    image: '',
                    url: '',
                    technologies: [],
                    github: '',
                    date: ''
                }
            }
        }
    }
</script>

<style lang="scss" scoped>

</style>