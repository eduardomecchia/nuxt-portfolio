<template>
    <div class="project-card">
        {{ project.title }}
        {{ project.description }}
        {{ project.url }}
        {{ project.image }}
        {{ project.technologies }}
        {{ project.github }}
    </div>
</template>

<script>
    import Project from './models/Project';

    export default {
        name: 'ProjectCard',

        props: {
            project: {
                type: Project,
                required: true
            }
        },

        data() {
            return {

            }
        }
    }
</script>

<style lang="scss" scoped>

</style>