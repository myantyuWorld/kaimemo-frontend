<template>
    <div class="row">
        <div class="col-2 d-flex align-items-center">
            <label :class="{fin: item.checked}">
                <input type="checkbox" class="check" @click="emit('change-check', item.id)" :checked="item.checked" />
            </label>
        </div>
        <div class="col">
            <div class="row goods__item__category" :class="{fin: item.checked}">
                <template v-if="item.category_id == '0'">食費</template>
                <template v-if="item.category_id == '1'">日用品</template>
            </div>
            <div class="row goods__item__name" :class="{fin: item.checked}">
                {{item.memo}}
            </div>
        </div>
        <div class="col-2 d-flex align-items-center">
            <EditButton @edit-click="emit('show-memo', item.id)" :is-edit="true"></EditButton>
        </div>
        <div class="col-2 d-flex align-items-center">
            <BaseButton color="btn-danger rounded-circle" @on-click="emit('delete-goods', item.id)">
                <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor" class="bi bi-trash3"
                    viewBox="0 0 16 16">
                    <path fill-rule="evenodd"
                        d="M6.5 1a.5.5 0 0 0-.5.5v1h4v-1a.5.5 0 0 0-.5-.5h-3ZM11 2.5v-1A1.5 1.5 0 0 0 9.5 0h-3A1.5 1.5 0 0 0 5 1.5v1H2.506a.58.58 0 0 0-.01 0H1.5a.5.5 0 0 0 0 1h.538l.853 10.66A2 2 0 0 0 4.885 16h6.23a2 2 0 0 0 1.994-1.84l.853-10.66h.538a.5.5 0 0 0 0-1h-.995a.59.59 0 0 0-.01 0H11Zm1.958 1H3.042l.846 10.58a1 1 0 0 0 .997.92h6.23a1 1 0 0 0 .997-.92l.846-10.58Zm-7.487 1a.5.5 0 0 1 .528.47l.5 8.5a.5.5 0 0 1-.998.06L5 5.03a.5.5 0 0 1 .47-.53Zm5.058 0a.5.5 0 0 1 .47.53l-.5 8.5a.5.5 0 1 1-.998-.06l.5-8.5a.5.5 0 0 1 .528-.47ZM8 4.5a.5.5 0 0 1 .5.5v8.5a.5.5 0 0 1-1 0V5a.5.5 0 0 1 .5-.5Z" />
                </svg>
            </BaseButton>
        </div>
    </div>
</template>

<script setup>
import BaseButton from '../btn/BaseButton.vue'
import EditButton from '../btn/EditButton.vue';

const props = defineProps({
    item: Object
})
const emit = defineEmits()
</script>