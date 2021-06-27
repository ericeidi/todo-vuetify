<template>
     <v-slide-x-reverse-transition>
            <v-alert 
            v-if="success == true"
            type="success"
            style="position: fixed; 
            bottom: 0;
            right: 0; 
            margin-right: 20px;
            "
            >
                Item {{descricao}} com sucesso.
            </v-alert>
    </v-slide-x-reverse-transition>
</template>

<script>

export default {
  props: {
        success: Boolean,
        descricao: String
    },
}

</script>