<template>
  <div class="p-10">
  <h1>hello world<h1/>
    <div class="relative overflow-x-auto shadow-md sm:rounded-lg">
      <table class="w-full text-sm text-left text-gray-500 dark:text-gray-400">
        <thead
          class="text-xs text-gray-700 uppercase bg-gray-50 dark:bg-gray-700 dark:text-gray-400"
        >
          <tr>
            <th scope="col" class="px-6 py-3">Image</th>
            <th scope="col" class="px-6 py-3">First name</th>
            <th scope="col" class="px-6 py-3">lastname</th>
            <th scope="col" class="px-6 py-3">Email</th>
          </tr>
        </thead>
        <tbody v-for="dato in datos" :key="dato.id">
          <tr class="bg-white border-b dark:bg-gray-800 dark:border-gray-700">
            <td class="px-6 py-4">
              <img :src="dato.avatar" alt="klk" />
            </td>
            <th scope="row" class="px-6 py-4 font-medium text-gray-900 dark:text-white whitespace-nowrap">{{ dato.first_name }}</th>
            <td class="px-6 py-4">{{ dato.last_name }}</td>
            <td class="px-6 py-4">{{ dato.email }}</td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      datos: [],
    };
  },
  async mounted() {
    const res = (await fetch("https://reqres.in/api/users?page=2")).json();
    const data = await res;
    data.data.map((x) => {
      this.datos.push(x);
    });
  },
};
</script>
