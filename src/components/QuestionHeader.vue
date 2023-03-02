<script setup>
    const { name, status, progress } = defineProps(['name', 'status', 'progress'])
</script>

<template>
    <header>
        <h3>{{ name }} Quiz</h3>

        <p>{{ status }}</p>
        
        <div class="progress">
            <div class="progress__meter" :style="{width: progress}"></div>
        </div>
    </header>
</template>

<style scoped lang="scss">
    header {
        margin: 1.5rem 0 3rem;

        h3 {
            margin: 0;
            font-weight: 600;
            line-height: 1em;
        }

        p {
            margin: 0.5rem 0;
        }

        .progress {
            position: relative;
            width: 300px;
            height: 2rem;
            margin: 0.5rem 0;
            background-color: ghostwhite;
            border: 2px solid steelblue;

            &__meter {
                width: 0;
                height: 100%;
                background-color: steelblue;
                transition: width 0.24s ease;
            }
            
        }
    }
</style>