<script setup>
    import { Squares2X2Icon } from '@heroicons/vue/20/solid'
    import { PlusIcon } from '@heroicons/vue/20/solid'
    import { DocumentDuplicateIcon } from '@heroicons/vue/20/solid'
    import { CircleStackIcon } from '@heroicons/vue/20/solid'
    import { UserGroupIcon } from '@heroicons/vue/20/solid'
    import { PuzzlePieceIcon } from '@heroicons/vue/20/solid'
    import { CommandLineIcon } from '@heroicons/vue/20/solid'
    import { Cog6ToothIcon } from '@heroicons/vue/20/solid'
    import NavigatorIcon from './icons/NavigatorIcon.vue'
</script>

<template>

    <div class="nav">
        
        <Squares2X2Icon class="icon"/>
        
        <NavigatorIcon class="icon"/>

        <PlusIcon class="icon"/>
        
        <DocumentDuplicateIcon class="icon"/>
    
        <CircleStackIcon class="icon"/>
    
        <UserGroupIcon class="icon"/>
    
        <PuzzlePieceIcon class="icon"/>
    
        <CommandLineIcon class="icon"/>
    
        <Cog6ToothIcon class="icon"/>
    </div>
    
</template>

<style scoped>

    .nav{
        position: fixed;
        width: 100%;
        height: 52px;
        display: flex;
        flex-direction: row;
        align-items: center;
        justify-content: flex-start;
        padding: 0px 16px;
        column-gap: 16px;

        background-color: var(--bg);
        border-bottom: 1px solid var(--bg-secondary);
    }

    .icon{
        width: 20px;
        height: 20px;
        color: var(--content-secondary);
        line-height: 0px;
    }
</style>
