<template>
    <div class="project-card">
        <div>
            <img :src="project.image" :alt="'Project image for ' + project.name">
        </div>

        <div>
            <b>Title:&nbsp;</b> <span>{{ project.name }}</span>
        </div>

        <div>
            <b>Description:&nbsp;</b> <span>{{ project.description }}</span>
        </div>

        <div>
            <b>Link:&nbsp;</b> <a :href="project.url">Click here</a>
        </div>
        
        <ul>
            <li><b>Technologies:&nbsp;</b></li>

            <li v-for="technology in project.technologies">{{ technology }}</li>
        </ul>

        <b>GitHub repository:&nbsp;</b> <a :href="project.github">Click here</a>
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
        }
    }
</script>

<style lang="scss" scoped>
    .project-card {
        margin-bottom: 20px;
        
        ul {
            list-style: none;
            padding: 0;
        }
    
    }
</style>