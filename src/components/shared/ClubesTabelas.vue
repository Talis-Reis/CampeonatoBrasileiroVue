<template>
  <v-simple-table dark>
    <template v-slot:default>
      <thead>
        <tr>
          <th colspan="2" class="text-left">Clube</th>
          <th class="text-right">Pontos</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(item, index) of clubes" :key="item.id">
          <td>{{ index + 1 }}</td>
          <td>
            <v-avatar size="24">
              <img :src="item.escudo" alt="Escudo" />
            </v-avatar>
            <span class="pl-2">{{ item.nome }}</span>
          </td>
          <td class="text-right">{{ item.pontos }}</td>
        </tr>
      </tbody>
    </template>
  </v-simple-table>
</template>


<script>
export default {
    name: 'ClubesTabelas',
    props: {
        clubes: {
            type: Array,
            required: true
        }
    },
};
</script>

<style scoped>
</style>