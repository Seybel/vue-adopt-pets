<template>
  <div>
    <h1>Adopt a new best friend.</h1>
    <button @click="togglePetForm" class="btn btn-primary">Add new Pet</button>
    <b-form @submit.prevent="handleSubmit" v-if="showPetForm">
      <b-form-group id="pet-group-1" label="Pet Name:" label-for="pet-name">
        <b-form-input
          id="pet-name"
          type="text"
          v-model="formData.name"
          required
          placeholder="Enter pet name"
        ></b-form-input>
      </b-form-group>

      <b-form-group id="pet-group-2" label="Species:" label-for="species-type">
        <b-form-select
          id="species-type"
          v-model="formData.species"
          :options="[{text: 'Select One', value: null }, 'cats', 'dogs']"
          required
        ></b-form-select>
      </b-form-group>

      <b-form-group id="pet-group-3" label="Gender:" label-for="gender-type">
        <b-form-select
          id="gender-type"
          v-model="formData.gender"
          :options="petGender"
          required
        ></b-form-select>
      </b-form-group>

      <b-form-group id="pet-group-4" label="Breed:" label-for="breed-name">
        <b-form-input
          id="breed-name"
          type="text"
          v-model="formData.breed"
          required
          placeholder="Enter breed"
        ></b-form-input>
      </b-form-group>

      <b-form-group id="pet-group-5" label="Age:" label-for="pet-age">
        <b-form-input
          id="pet-age"
          v-model.number="formData.age"
          type="number"
          required
        ></b-form-input>
      </b-form-group>

      <b-form-group id="pet-group-6" label="Color:" label-for="color-name">
        <b-form-input
          id="color-name"
          type="text"
          v-model="formData.color"
          placeholder="Enter color"
        ></b-form-input>
      </b-form-group>

      <b-form-group id="pet-group-7" label="Weight:" label-for="weight-kg">
        <b-form-input
          id="weight-kg"
          type="number"
          v-model.number="formData.weight"
        ></b-form-input>
      </b-form-group>

      <b-form-group id="pet-group-8" label="Location:" label-for="location-name">
        <b-form-input
          id="location-name"
          type="text"
          v-model="formData.location"
          required
          placeholder="Enter location"
        ></b-form-input>
      </b-form-group>

      <b-form-group id="pet-group-9" label="Notes:" label-for="note-content">
        <b-form-input
          id="note-content"
          type="text"
          v-model="formData.notes"
          placeholder="Enter comment"
        ></b-form-input>
      </b-form-group>

      <b-button type="submit" variant="primary">Submit</b-button>
    </b-form>
  </div>
</template>

<script>
import { mapActions } from 'vuex'

export default {
  name: 'home',
  data () {
    return {
      showPetForm: false,
      formData: {
        name: '',
        breed: '',
        species: null,
        gender: null,
        age: 0,
        color: '',
        weight: 0,
        location: '',
        notes: ''
      },
      petGender: [{ text: 'Choose', value: null }, 'male', 'female']
    }
  },
  methods: {
    ...mapActions([
      'addPet'
    ]),

    togglePetForm () {
      this.showPetForm = !this.showPetForm
    },

    handleSubmit () {
      const { species, name, breed, gender, age, color, weight, location, notes } = this.formData

      const payload = {
        species,
        pet: {
          name,
          breed,
          gender,
          age,
          color,
          weight,
          location,
          notes
        }
      }

      this.addPet(payload)

      // reset form data after submit
      this.formData = {
        name: '',
        breed: '',
        species: null,
        gender: null,
        age: 0,
        color: '',
        weight: 0,
        location: '',
        note: ''
      }
    }
  }
}
</script>
