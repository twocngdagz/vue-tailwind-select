<template>
    <div class="container select">
        <div class="inline-block relative w-full">
            <input class="appearance-none border w-full py-2 px-3 mr-4 text-grey-darker" :class="dropdown.visible ? 'rounded-t' : 'rounded'" placeholder="Select an option" @focus="toggle()" v-model="chosen">

            <div class="pointer-events-none absolute pin-y pin-r flex items-center px-2 text-grey-darker" v-if="!dropdown.visible">
                <svg class="fill-current h-4 w-4" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20"><path d="M9.293 12.95l.707.707L15.657 8l-1.414-1.414L10 10.828 5.757 6.586 4.343 8z"/></svg>
            </div>
            <div class="pointer-events-none absolute pin-y pin-r flex items-center px-2 text-grey-darker" v-else>
                <svg class="fill-current h-4 w-4" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20"><path d="M10.707 7.05L10 6.343 4.343 12l1.414 1.414L10 9.172l4.243 4.242L15.657 12z"/></svg>
            </div>
        </div>
        <div class="container absolute mx-auto border rounded-b" v-if="dropdown.visible">
            <div v-for="(option, index) in options" :key="index" class="hover:bg-blue-lightest">
                <p class="w-full p-3" @click="setValue(option)">{{option}}</p>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        name: 'TailwindSelect',
        props: {
            options: {
                type: [Array, Object],
                required: true,
                default: function () {
                    return [
                        "option 1",
                        "option 2",
                        "option 3",
                        "option 4"
                    ]
                }
            }
        },
        data() {
            return {
                dropdown: {
                    visible: false
                },
                chosen: ""
            }
        },
        methods: {
            toggle() {
                this.dropdown.visible = !this.dropdown.visible
            },
            setValue(option) {
                this.chosen = option
                this.toggle()
            }
        },
        mounted() {

        }
    }
</script>
