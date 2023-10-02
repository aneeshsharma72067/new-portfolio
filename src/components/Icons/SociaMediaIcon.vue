<template>
    <li class="social-media-icon">
        <a :href="link" target="_blank">
            <svg :width="size" :height="size" fill="#ffffff" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
                <slot></slot>
            </svg>
        </a>
    </li>
</template>

<script>
    export default {
        name:'SocialMediaIcon',
        props:['link'],
        data(){
            return {
                size:30
            }
        }
    }
</script>

<style lang="css" scoped>
.social-media-icon{
    display: flex;
    width: 100%;
    height: max-content;
    align-items: center;
    justify-content: center;
    cursor: pointer;
    transition: 0.3s;
    z-index: 2;
    border: 2px solid transparent;
    border-radius: 10px;
    position: relative;
}
.social-media-icon > a{
    padding: 5px;
    width: inherit;
    height: inherit;
    display: flex;
    align-items: center;
    justify-content: center;
}


.social-media-icon::before{
    position: absolute;
    content: '';
    width: 50%;
    aspect-ratio: 1/1;
    height: auto;
    top: -5%;
    left: 25%;
    border-radius: 50%;
    background: var(--primary-red);
    transition: 0.3s ease-in-out;
    z-index: -1;
    scale: 0;
}

.social-media-icon:hover::before{
    scale: 1;
}
</style>