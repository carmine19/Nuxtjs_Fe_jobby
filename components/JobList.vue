<template>


<span>
   <td class="px-5 py-5 border-b border-gray-200 bg-white text-sm">
      <div class="flex items-center">
         <div class="flex-shrink-0">
            <a class="block relative" href="#">
            </a>
         </div>
         <div class="ml-3">
            <p class="text-gray-900 whitespace-no-wrap">
               {{ title }}
            </p>
         </div>
      </div>
   </td>
   <td class="px-5 py-5 border-b border-gray-200 bg-white text-sm">
      <p class="text-gray-900 whitespace-no-wrap">
         {{ description.substring(0, 25) + '...' }}
      </p>
   </td>
   <td class="px-5 py-5 border-b border-gray-200 bg-white text-sm">
      <p class="text-gray-900 whitespace-no-wrap">
         {{ start_activity_date }}
      </p>
   </td>
   <td class="px-5 py-5 border-b border-gray-200 bg-white text-sm">
      <span
         class="relative inline-block px-3 py-1 font-semibold text-green-900 leading-tight">
      <span aria-hidden="true"
         class="absolute inset-0 bg-green-200 opacity-50 rounded-full">
      </span>
      <span class="relative">
      {{ duration_activity }} <span>{{duration_activity < 1 ? 'm' : 'h' }}</span>
      </span>
      </span>
   </td>
   <td class="px-5 py-5 border-b border-gray-200 bg-white text-sm">
      <a class="text-indigo-600 hover:text-indigo-900" href="#">
      {{ price }} <span>€</span>
      </a>
   </td>
   <td class="px-5 py-5 border-b border-gray-200 bg-white text-sm">
       <NuxtLink tag="a" :to=" /author/ + this.user_id" class="btn btn-primary">{{ author_name }}</NuxtLink>
   </td>
</span>


</template>

<script>

export default {
    name: "JobList",

    data() {
        return {}
    },
    methods: {},

    props: {

        user_id: {
            type: Number,
            required: true
        },
        title: {
            type: String,
            required: true
        },
        description: {
            type: String,
            required: true
        },
        start_activity_date: {
            type: String,
            required: true
        },
        duration_activity: {
            type: Number,
            default: false
        },
        price: {
            type: String,
            default: false
        },
        author_name: {
            type: String,
            default: false
        }
    },


    created() {

    }
}
</script>

<style scoped>

.text-green-900 {
    font-size: 10px;
}
</style>
