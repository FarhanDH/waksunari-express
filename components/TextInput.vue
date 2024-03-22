<template>
    <div>
        <client-only>
            <!-- The input element that takes user input -->
            <input
                :placeholder="placeholder"
                :maxlength="max"
                class="w-full bg-white text-gray-800 border text-sm border-[#EFF0EB] rounded-lg p-3 placeholder-gray-500 focus:outline-none"
                @focus="isFocused = true"
                @blur="isFocused = false"
                :class="
                    ({ 'border-gray-900': isFocused },
                    { 'border-red-500': error })
                "
                :type="inputType"
                v-model="inputComputed"
                autocomplete="off"
            />
        </client-only>
        <span v-if="error" class="text-red-500 text-[14px] font-semibold">
            <!-- The error message that is shown to the user if there is an error -->
            {{ error }}
        </span>
    </div>
</template>

<script setup>
// The function that generates events
const emit = defineEmits(['update:input']);

// Props that are passed to the component
const props = defineProps([
    'input', // The initial value
    'placeholder', // The placeholder text of the input field
    'max', // The maximum number of characters
    'inputType', // The type of input
    'error', // The error message if there is an error
]);

// Reactive variables that are used in the template
const { input, placeholder, max, inputType, error } = toRefs(props);
let isFocused = ref(false);

// A computed property that updates the input value and emits an event when it changes
const inputComputed = computed({
    get: () => input.value, // Get the current value of the input field
    set: (val) => emit('update:input', val), // When the input field changes, emit an event with the new value
});
</script>
