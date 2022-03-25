<template>
    <div class="follow-me">
        <ul>
            <li>
                <small>Follow me</small>
            </li>

            <li>
                <a class="github" target="_blank" href="https://github.com/eduardomecchia" title="Follow on GitHub"></a>
            </li>

            <li>
                <a class="linkedin" target="_blank" href="https://linkedin.com/in/eduardomecchia" title="Connect on Linkedin"></a>
            </li>
            
            <li>
                <a class="twitter" target="_blank" href="https://twitter.com/eduardo_mecchia" title="Follow on Twitter"></a>
            </li>
            
            <li>
                <a class="instagram" target="_blank" href="https://instagram.com/mec43" title="Follow on Instagram"></a>
            </li>
        </ul>
    </div>
</template>

<script>
export default {
    
}
</script>

<style lang="scss" scoped>
    .follow-me {
        z-index: 1001;
        position: fixed;
        left: 0;
        top: calc(50% - (275px / 2));
        width: 55px;
        height: 275px;
        
        a {
            display: flex;
            align-items: center;
            justify-content: center;
            width: 75px;
            height: 55px;
            padding-left: 20px;
            margin-left: -20px;
            transition: transform 425ms cubic-bezier(.05,.65,.18,1);
        }
    }
</style>