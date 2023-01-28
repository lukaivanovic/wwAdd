<script setup>
    import { Bars2Icon } from '@heroicons/vue/20/solid'
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
        <Bars2Icon class="icon"/>

        <div class="divider"></div>

        <div class="add" @mouseover="$emit('openPanel')">
            <PlusIcon class="addIcon"/>
            <span class="label-sm">Add</span>
        </div>
        
        <div class="divider"></div>
        
        <DocumentDuplicateIcon class="icon"/>
    
        <CircleStackIcon class="icon"/>
    
        <UserGroupIcon class="icon"/>

        <div class="divider"></div>
    
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
        width: 18px;
        height: 18px;
        color: var(--content-secondary);
        line-height: 0px;
        cursor: pointer;
    }

    .icon:hover{
        color: var(--content-primary);
    }

    .add{
        cursor: pointer;
        display: flex;
        flex-direction: row;
        align-items: center;
        justify-items: center;
        background-color: var(--bg-secondary);
        padding-left: 8px;
        padding-right: 12px;
        height: 28px;
        border-radius: 8px;
        column-gap: 4px;
    }

    .add:hover{
        background-color: var(--bg-tertiary);
    }

    .addIcon{
        width: 16px;
        height: 16px;
        color: var(--content-secondary);
        line-height: 0px;
        cursor: pointer;
    }

    .divider{
        width: 1px;
        height: calc(100% - 24px);
        background-color: var(--bg-secondary);
    }
</style>
