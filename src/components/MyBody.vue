<template>
      <v-table>
      <template v-slot:default>
        <thead>
          <tr>
            <th class="text-left">
              Departure City
            </th>
            <th class="text-left">
              Arrival City
            </th>
            <th class="text-left">
              Departure DateTime
            </th>
            <th class="text-left">
              Arrival DateTime
            </th>
            <th class="text-left">
              Cost
            </th>
          </tr>
        </thead>
        <tbody>
          <tr
            v-for="item in flight"
            :key="item.id"
          >
            <td>{{ item.departureCity }}</td>
            <td>{{ item.arrivalCity }}</td>
            <td>{{ item.departureDateTime }}</td>
            <td>{{ item.arrivalDateTime }}</td>
            <td>{{ item.cost }}</td>
          </tr>
        </tbody>
      </template>
    </v-table>
</template>

<script>
export default {
    name:'MyBody',
    props:{

      flight:{
        type: Array,
        required: true
      }
    }

}
</script>

<style>

</style>