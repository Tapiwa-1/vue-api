<script setup>
import useSkills from "../../composables/skills";
import { onMounted } from "vue";

const { skill, getSkill, updateSkill, errors } = useSkills();

const props = defineProps({
  id: {
    required: true,
    type: String,
  },
});

onMounted(() => getSkill(props.id));
</script>
<template>
   <section class="">
    <div class="flex flex-col items-center justify-center px-6 py-8 mx-auto md:h-screen lg:py-0">
      
        <div class="w-full bg-white rounded-lg shadow  md:mt-0 sm:max-w-md xl:p-0 ">
            <div class="p-6 space-y-4 md:space-y-6 sm:p-8">
                <h1 class="text-xl font-bold leading-tight tracking-tight text-gray-900 md:text-2xl ">
                    Update Skill
                </h1>
                <form @submit.prevent="updateSkill($route.params.id)" class="space-y-4 md:space-y-6" action="#">
                    <div>
                        <label for="name" class="block mb-2 text-sm font-medium text-gray-900 ">name</label>
                        <input type="text" v-model="skill.name" name="name" id="name" class="bg-gray-50 border border-gray-300 text-gray-900 sm:text-sm rounded-lg focus:ring-primary-600 focus:border-primary-600 block w-full p-2.5 0" placeholder="skill name">
                        <div v-if="errors.name" class="flex">
                            <span class="text-red-400 text-sm">{{
                                errors.name[0]
                            }}</span>
                        </div>
                    </div>
                    <div>
                        <label for="slug" class="block mb-2 text-sm font-medium text-gray-900 ">slug</label>
                        <input type="text" v-model="skill.slug" name="slug" id="slug" class="bg-gray-50 border border-gray-300 text-gray-900 sm:text-sm rounded-lg focus:ring-primary-600 focus:border-primary-600 block w-full p-2.5 0">
                        <div v-if="errors.slug" class="flex">
                            <span class="text-red-400 text-sm">{{
                                errors.slug[0]
                            }}</span>
                        </div>
                    </div>
                    <button type="submit" class="w-full text-white bg-blue-600 hover:bg-blue-700 focus:ring-4 focus:outline-none focus:ring-primary-300 font-medium rounded-lg text-sm px-5 py-2.5 text-center dark:bg-primary-600 dark:hover:bg-primary-700 dark:focus:ring-primary-800">Update</button>
                </form>
            </div>
        </div>
    </div>
  </section>

 
</template>