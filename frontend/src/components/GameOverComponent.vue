<template>
  <div class="text-center text-white">
    <p class="text-4xl">Game Over!</p>
    <p style="font-size: large;">Correct guess was: <span style="color: green; font-weight: bold;">{{ currentCorrect }}</span></p>
    <table class="table w-1/2 mx-auto">
      <thead>
        <tr class="text-white">
          <th></th>
          <th>User</th>
          <th>Score</th>
          <th>Guess</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(item, index) in data" :key="index" style="align-items: center;">
          <td class="large-text">
            <div class="flex items-center gap-3">
              <div class="avatar">
                <div class="mask mask-squircle w-12 h-12">
                  <img :src="'data:image/jpeg;base64,' + profilePictures[item.username]" alt="Profile Picture" />
                </div>
              </div>
            </div>
          </td>
          <td>{{ item.username }}</td>
          <td>{{ item.score }}</td>
          <td>{{  getCountry(item.current_guess) }}</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

  
  <script>
  import countryCodeData from '../assets/countryCodes.json';
  
  export default {
    name: 'GameOverComponent',
    props: {
      data: {
        type: Object,
        required: true
      },
      profilePictures: {
        type: Object,
        required: false
      },
      currentCorrect: {
        type: String,
        required: false
      }
    },
    data() {
      return {
      };
    },
    methods: {
      // Formats loaded picture to correct format
      getProfilePicture(username) {
          return 'data:image/jpeg;base64,' + (this.profilePictures[username] || '');
      },
      // Convert country code to country name
      getCountry(countryCode) {
        return countryCodeData[countryCode]
      }
    },
  };
  </script>

<style>
th, td {
    font-size: 16px;
}
</style>
  
