# vue-json-form
Create VueJS powered forms through a JSON schema.

## Examples
In your Vue file:

```html
<template>
  <v-json-form :schema="schema" v-model="model" @submit.prevent="submit" />
</template>

<script>
import v-json-form from 'v-json-form'
import schema from 'path/to/your/file.json'

export default {
  components: { v-json-schema },
  data () {
    return {
      schema: schema,
      model: {}
    }
  },
  methods: {
    submit: () => axios.post('...', model)
  }
}
</script>
```

vue-json-form supports many attributes available to native HTML form elements.

```json
{
  "title": "Your JSON Form",
  "action": "http://www.mywebsite.com/form",
  "verb": "POST",
  "fields": [
    {
      "tag": "input",
      "type": "text",
      "attributes": {
        "id": "ID",
        "name": "Name",
        "placeholder": "John Doe",
        "required": true,
        "minlength": 0,
        "maxlength": 20,
        "pattern": "[a-z]",
        "disabled": false
      },
      "validation": {
        "on": "submit",
        "errors": {
          "required": {
            "message": "A name is required."
          },
          "minlength": {
            "message": "A name must be at least 1 character."
          },
          "maxlength": {
            "message": "A name cannot exceed 20 characters."
          }
        }
      }
    },
    {
      "tag": "input",
      "type": "email",
      "attributes": {
        "id": "Email",
        "name": "Email",
        "placeholder": "john@example.com",
        "required": true
      }
    }
  ]
}
```

We can further customize our elements like providing a template or classes.

```json
{
  "title": "Your JSON Form",
  "action": "http://www.mywebsite.com/form",
  "verb": "POST",
  "fields": [
    {
      "tag": "input",
      "type": "text",
      "parent": "div",
      "parentClass": ["form-group"],
      "attributes": {
        "id": "ID",
        "name": "Name",
        "placeholder": "John Doe",
        "class": ["form-control"]
      }
    }
  ]
}
```

To have fine tuned control over your templates you can utilize `slot-scope`.

```javascript
// slot-scope example here
```
