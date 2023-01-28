<script setup>
    import AuthIcon from './icons/AuthIcon.vue'
    import LayoutIcon from './icons/LayoutIcon.vue'
    import ButtonsIcon from './icons/ButtonsIcon.vue'
    import DataIcon from './icons/DataIcon.vue'
    import ElementsIcon from './icons/ElementsIcon.vue'
    import InputIcon from './icons/InputIcon.vue'
    import LandingIcon from './icons/LandingIcon.vue'
    import Search from './Search.vue'
</script>

<script>
    import sectionsInput from "./Sections.json"
    import elementsInputRaw from "./Elements.json" 

    export default {
        data() {
            return {
                currentSection: sectionsInput[0],
                sections: sectionsInput,
                elements: elementsInputRaw,
                elementHovered: false
            }
        },
        methods: {
            changePanel(name) {
            },
            changeCategory(targetSection){
                this.currentSection = targetSection
                this.selectedCatElements()

                console.log(this.currentSection);
            }
        },
        computed: {
            selectedCatElements(){
                return this.elements.find(element => element.id === this.currentSection.id).items
            }
        }
    }
</script>

<template>
    <header>
        <link rel="preconnect" href="https://rsms.me/">
        <link rel="stylesheet" href="https://rsms.me/inter/inter.css">  
    </header>
    <div class='panel'
        @mouseleave="$emit('closePanel')"
    >
        <div class="small">
            <Search />
            
            <div
                v-for="section in sections"
                :key="section.name"
                @mouseover="changeCategory(section)"
                class="item label-sm"
                :class="section.id === currentSection.id ? 'itemActive' : ''"
            >
                <ElementsIcon v-if="section.name === 'Elements'"/>
                <LayoutIcon v-if="section.name === 'Layout'"/>
                <ButtonsIcon v-if="section.name === 'Buttons & Labels'"/>
                <InputIcon v-if="section.name === 'Input & Controls'"/>
                <DataIcon v-if="section.name === 'Data Display'"/>
                <LandingIcon v-if="section.name === 'Landing page'"/>
                <AuthIcon v-if="section.name === 'Authentication'"/>
                {{section.name}}
            </div>
        </div>

        <div class="medium">
            <span class="heading-lg">{{currentSection.name}}</span>
            
            <div
                class="content"
                v-for="folder in selectedCatElements"
                :key="folder.folderName"
            >
                <div class="folder label-sm" v-if="folder.folderName != 'main'">
                    {{folder.folderName}}
                </div>

                <div
                    class="elements"
                    :class="{'elementsTwo': currentSection.display === 1, 'elementsOne': currentSection.display === 2}"
                >
                    <div
                        v-for="element in folder.elements"
                        :key="element.name"
                        class="element"
                        :class="{'element-sm': currentSection.display === 0, 'element-md': currentSection.display === 1}"
                        @mouseover="elementHovered = element.name"
                        @mouseleave="elementHovered = ''"
                    >   
                        <img
                            class="elementPreview" :src="element.url"
                            :class="elementHovered === element.name ? 'elementHover' : ''"
                        />
                        
                        <span class="body-sm">{{element.name}}</span>
                    </div>
                </div>
            </div>
        </div>
    </div>
    
</template>

<style scoped>
    .panel{
        display: flex;
        flex-direction: row;
        position: absolute;
        top: 48px;
        left: 0px;
        height: calc(100vh - 48px);
        background-color: var(--bg);
    }

    .small{
        padding: 8px;
        display: flex;
        flex-direction: column;
        width: 200px;
        border-right: 1px solid var(--bg-secondary);
    }

    .medium{
        width: 280px;
        border-right: 1px solid var(--bg-secondary);
        padding: 20px 16px;
    }

    .item{
        cursor: pointer;
        padding: 0px 8px;
        height: 40px;
        display: flex;
        column-gap: 10px;
        width: 100%;
        flex-direction: row;
        align-items: center;
        justify-content: flex-start;
        border-radius: 6px;
        color: var(--content-secondary);
        margin-bottom: 4px;
    }

    .itemActive{
        background-color: var(--bg-secondary);
        color: var(--content-primary);
    }

    .item:hover{
        background-color: var(--bg-secondary);
    }

    .elements{
        display: grid;
        grid-template-columns: 1fr 1fr 1fr;
        row-gap: 4px;
        column-gap: 4px;
    }

    .elementsThree{
        grid-template-columns: 1fr 1fr 1fr;
    }

    .elementsTwo{
        grid-template-columns: 1fr 1fr;
    }

    .elementsOne{
        grid-template-columns: 1fr;
    }

    .element{
        padding: 4px;
        display: flex;
        flex-direction: column;
        row-gap: 4px;
        justify-content: stretch;
        align-items: stretch;
        align-content: center;
        background-color: var(--bg-secondary);
        border-radius: 8px;
        overflow: hidden;
        white-space: nowrap;
        text-overflow: ellipsis;
        text-align: center;
        cursor: pointer;
        color: var(--content-secondary);
    }

    .elementHover{
        opacity: 0.9;
        transition: all .4s ease;
        transform: scale(0.94);
    }

    .element:hover{
        color: var(--content-primary);
    }

    .element-sm{
        height: 72px;
    }

    .element-md{
        height: 114px;
    }

    .elementPreview{
        height: auto;
        border-radius: 4px;
        flex-grow: 1;
    }

    .elementImage{
        object-fit: cover;
    }

    .element:hover{
        background-color: var(--bg-tertiary);
    }

    .folder{
        height: 20px;
        display: flex;
        column-gap: 10px;
        width: 100%;
        flex-direction: row;
        align-items: center;
        justify-content: flex-start;
        border-radius: 6px;
        color: var(--content-secondary);
        margin-bottom: 8px;
        margin-top: 16px;
    }

    .content{
        margin-top: 16px
    }
</style>