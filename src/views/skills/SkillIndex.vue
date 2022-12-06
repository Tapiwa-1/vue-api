<script setup>
import useSkills from "../../composables/skills";
import { onMounted } from "vue";

const { skills, getSkills, destroySkill } = useSkills();

console.log(getSkills());
onMounted(() => getSkills());
</script>
<template>
  <div class="mt-12">
    <div class="flex justify-end m-2 p-2">
      <RouterLink
        :to="{ name: 'SkillCreate' }"
        class="px-4 py-2 bg-indigo-500 hover:bg-indigo-700 text-white rounded"
        >New Skill</RouterLink
      >
    </div>

    <div class="overflow-x-auto relative">
        <table class="w-full text-sm text-left text-gray-500 ">
            <thead class="text-xs text-gray-700 uppercase bg-gray-50 ">
                <tr>
                    <th scope="col" class="py-3 px-6">
                        Skill
                    </th>
                    <th scope="col" class="py-3 px-6">
                        Slug
                    </th>
                    <th scope="col" class="py-3 px-6">
                        Action
                    </th>
                    
                </tr>
            </thead>
            <tbody>
                <tr  v-for="skill in skills" :key="skill.id" class="bg-white border-b ">
                    <th scope="row" class="py-4 px-6 font-medium text-gray-900 whitespace-nowrap">
                      {{ skill.name }}
                    </th>
                    <td class="py-4 px-6">
                        {{ skill.slug }}
                    </td>
                    <td class="py-4 px-6">
                        <router-link type="button" class="text-white bg-gradient-to-r from-cyan-400 via-cyan-500 to-cyan-600 hover:bg-gradient-to-br   font-medium rounded-lg text-sm px-5 py-2.5 text-center mr-2 mb-2" :to="{ name: 'SkillEdit', params: { id: skill.id } }">Edit</router-link>
                        <button type="button" class="text-gray-900 bg-gradient-to-r from-lime-200 via-lime-400 to-lime-500 hover:bg-gradient-to-br  font-medium rounded-lg text-sm px-5 py-2.5 text-center mr-2 mb-2" @click="destroySkill(skill.id)">Delete</button>
                    </td>
                </tr>
            </tbody>
        </table>
    </div>
  </div>
</template>