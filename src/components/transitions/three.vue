<template>
    <div class="mb-3"><input type="text" name="" id="   " class="form-control" v-model="data.name"></div>

    <button class="btn btn-primary" @click="addOne">
        ADd on
    </button>

    <hr>
    <div>
        <ul class="list-group pl-0">

            <transition-group name="fade" appear>

                <li class="list-group-item" v-for="(item, index) in data.list" :key="item" @click="removeItem(index)">
                    {{ item }}
                </li>
            </transition-group>
        </ul>
    </div>
</template>

<script setup>
import { reactive } from 'vue';

const data = reactive(
    {
        list: ['Francise', 'Ron', 'Mike'],
        name: '',
    }
)

const addOne = () => {
    if (!data.list.includes(data.name) && data.name !== '') {
        data.list.unshift(data.name);
    }
}

const removeItem = (index) => {
    data.list.splice(index, 1)
}

</script>


<style scoped>
.fade-enter-from,
.fade-leave-to {
    opacity: 0;
}

.fade-enter-active,
.fade-leave-active {
    transition: 1s;
}

.fade-move {
    transition: transform 1s;
}

.dog,
.cat {
    transition: 1s;
}

.custom-enter-to,
.custom-leave-from {
    opacity: 1;
}
</style>