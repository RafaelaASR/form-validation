<template>
  <div>
    <h1>Create an Event</h1>
    <form @submit.prevent="submit">
      <BaseSelect
        label="Select a category"
        :options="categories"
        v-model="category"
        :error="categoryError"
      />

      <h3>Name & describe your event</h3>
      <BaseInput
        label="Title"
        type="text"
        v-model="title"
        :error="titleError"
      />

      <BaseInput
        label="Description"
        type="text"
        v-model="description"
        :error="descriptionError"
      />

      <h3>Where is your event?</h3>
      <BaseInput
        label="Location"
        type="text"
        v-model="location"
        :error="locationError"
      />

      <h3>Are pets allowed?</h3>
      <BaseRadioGroup
        name="pets"
        :options="[
          { value: 1, label: 'Yes' },
          { value: 0, label: 'No' }
        ]"
        v-model="pets"
        :error="petsError"
      />

      <h3>Extras</h3>
      <div>
        <BaseCheckbox
          label="Catering"
          v-model="catering"
          :error="cateringError"
        />
      </div>

      <div>
        <BaseCheckbox
          label="Live music"
          v-model="music"
          :error="musicError"
        />
      </div>

      <div>
        <BaseButton
          type="submit"
          class="-fill-gradient"
          something="else"
        >
          Submit
        </BaseButton>
      </div>
    </form> 
  </div>
</template>
<script>
const { value: category, errorMessage: categoryError } = useField('category')
const { value: title, errorMessage: titleError } = useField('title')
const { value: description, errorMessage: descriptionError } = useField('description')
const { value: location, errorMessage: locationError } = useField('location')
const { value: pets, errorMessage: petsError } = useField('pets', undefined, { initialValue: 1 })
const { value: catering, errorMessage: cateringError } = useField('catering', undefined, { initialValue: false })
const { value: music, errorMessage: musicError } = useField('music', undefined, { initialValue: false })

return {
  category,
  categoryError,
  title,
  titleError,
  description,
  descriptionError,
  location,
  locationError,
  pets,
  petsError,
  catering,
  cateringError,
  music,
  musicError
}

</script>
