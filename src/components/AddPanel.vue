<script setup>
</script>

<script>
    import sectionsInput from "./Sections.json"
    import elementsInputRaw from "./Elements.json" 

    export default {
        data() {
            return {
                currentSection: sectionsInput[0],
                sections: sectionsInput,
                elements: elementsInputRaw
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
    <div class='panel'>
        <div class="small">
            
            <!-- <input v-model="text"> -->
            <div
                v-for="section in sections"
                :key="section.name"
                @click="changeCategory(section)"
                class="item label-sm"
                :class="section.id === currentSection.id ? 'itemActive' : ''"
            >
                {{section.name}}
            </div>
        </div>

        <div class="medium">
            <div
                class="elements"
                :class="{'elementsTwo': currentSection.display === 1, 'elementsOne': currentSection.display === 2}"
            >
                <div
                    v-for="element in selectedCatElements"
                    :key="element.name"
                    class="element"
                    :class="{'element-sm': currentSection.display === 0, 'element-md': currentSection.display === 1}"
                >   
                    <img class="elementPreview" :src="element.url" />
                    
                    <span class="label-sm">{{element.name}}</span>
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
        width: 160px;
        border-right: 1px solid var(--bg-secondary);
    }

    .medium{
        width: 280px;
        border-right: 1px solid var(--bg-secondary);
        padding: 12px;
    }

    .item{
        cursor: pointer;
        padding: 0px 8px;
        height: 32px;
        display: flex;
        width: 100%;
        flex-direction: row;
        align-items: center;
        justify-content: flex-start;
        border-radius: 6px;
        color: var(--content-secondary);
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
        justify-content: stretch;
        align-items: stretch;
        align-content: center;
        background-color: var(--bg-secondary);
        border-radius: 8px;
        overflow: hidden;
        white-space: nowrap;
        text-overflow: ellipsis;
        text-align: center;
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
        background-color: var(--bg-tertiary);
    }

    .elementImage{
        object-fit: cover;
    }

    .element:hover{
        background-color: var(--bg);
    }
</style>