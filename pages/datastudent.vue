<!-- <template>
  <div class="rounded-x1 white text-center">
    <div class="txt01">
      <ul>
        <li v-for="st in student" :key="st.id">
          <span> {{ st.id }} </span>
          <span> {{ st.name }} </span>
          <span> {{ st.lname }} </span>
        </li>
      </ul>
    </div>
  </div>
</template>
<script>
export default {
  data () {
    return {
      student: [
        { id: '63309010019', name: 'Athiwat', lname: 'Thawan' },
        { id: '63309010023', name: 'Somshai', lname: 'Tamma' },
        { id: '63309010025', name: 'Wanaruk', lname: 'naka' },
        { id: '63309010099', name: 'Mane', lname: 'nana' },
        { id: '63309010012', name: 'Piti', lname: 'pata' },
        { id: '63309010007', name: 'Shujai', lname: 'songsom' }
      ]
    }
  },
  computed: {
    upperName () {
      return this.name.toUpperCase()
    }
  }
}
</script>
<style>
.txt01{
    color:rgb(21, 79, 240);
}
</style> -->

<template>
  <v-simple-table datastudent>
    <template #default>
      <thead>
        <tr>
          <th class="text-left">
            ID
          </th>
          <th class="text-left">
            Name
          </th>
          <th class="text-left">
            Surname
          </th>
        </tr>
      </thead>
      <tbody>
        <tr
          v-for="st in student"
          :key="st.id"
        >
          <td>{{ st.id }}</td>
          <td>{{ st.name }}</td>
          <td>{{ st.lname }}</td>
        </tr>
      </tbody>
    </template>
  </v-simple-table>
</template>
<script>
export default {
  layout: 'la_student',
  data () {
    return {
      student: [
        { id: '63309010019', name: 'Athiwat', lname: 'Thawan' },
        { id: '63309010023', name: 'Somshai', lname: 'Tamma' },
        { id: '63309010025', name: 'Wanaruk', lname: 'naka' },
        { id: '63309010099', name: 'Mane', lname: 'nana' },
        { id: '63309010012', name: 'Piti', lname: 'pata' },
        { id: '63309010007', name: 'Shujai', lname: 'songsom' }
      ]
    }
  }
}
</script>
