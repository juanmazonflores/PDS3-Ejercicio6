

<template>
    <div id="forms-section" class="fx-column fx-content-center fx-align-items-center">

        <div class="contacto-container">

            <h1>Contacto</h1>

            <form id="contacto-form" @submit="checkForm" action="/something" method="post" class="fx-column">

                <p v-if="errors.length">
                    <b>Por favor, corrija el(los) siguiente(s) error(es):</b>
                <ul>
                    <li v-for="(error, index) in errors" v-bind:key="index">{{ error }} </li>
                </ul>
                </p>

                <input type="text" name="name" id="name" placeholder="Nombre" v-model="name">

                <input type="email" id="email" placeholder="Email" v-model="email">

                <input type="text" id="subject" placeholder="Asunto"  v-model="subject">

                <textarea id="mensaje" placeholder="Mensaje" v-model="text"></textarea>

                <button type="submit" value="Submit" class="button-action">Enviar</button>

            </form>

        </div>

        <div class="redes-sociales-container fx-row">

            <a href="https://github.com/juanmazonflores" target="_blank"><i class="fa-brands fa-github"></i></a>
            <a href="https://www.facebook.com/juanmanuel.masonflores" target="_blank"><i
                    class="fa-brands fa-facebook"></i></a>
            <a href="https://twitter.com/juanitomaflo" target="_blank"><i class="fa-brands fa-x-twitter"></i></a>
            <a href="https://www.linkedin.com/in/juan-mazon-653472277/" target="_blank"><i
                    class="fa-brands fa-linkedin"></i></a>

        </div>

        <p>Juan Manuel Mazon Flores &copy; 2023</p>

    </div>
</template>


<script>

export default {
    name: 'Forms',
    form: {
            errors: [],
            name: null,
            email: null,
            subject: null,
            text: null
        },
    methods: {
        
        checkForm: function (e) {
            this.errors = [];

            if (!this.name) {
                this.errors.push("El nombre es obligatorio.");
            }
            if (!this.email) {
                this.errors.push('El correo electrónico es obligatorio.');
            } else if (!this.validEmail(this.email)) {
                this.errors.push('El correo electrónico debe ser válido.');
            }

            if (!this.errors.length) {
                return true;
            }

            e.preventDefault();
        },
        /*
        validEmail: function (email) {
            //var re = /^(([^<>()\[\]\\.,;:\s@"]+(\.[^<>()\[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/;
            //return re.test(email);
        }
        */
    }

}
</script>



<style scoped>
footer {
    color: var(--color-font2);
    text-align: center;
    padding: 6rem 3rem;
}

.contacto-container {
    width: 600px;
    max-width: 100%;

}

.contacto-container h1 {
    font-size: 2rem;
    margin-bottom: 2rem;
    color: var(--color-font2);
    text-align: center;
}

p {
    color: var(--color-font2);
    text-align: center;
}

input,
textarea {
    margin-bottom: 1rem;
    padding: 8px;
    background-color: var(--color-container);
    font-family: var(--font-family);
    font-weight: 400;
    opacity: 0.8;
    color: var(--color-font);
    font-size: 20px;
}

input::placeholder,
textarea::placeholder {
    color: var(--color-font);
    font-size: 20px;
    opacity: 0.8;
}

.redes-sociales-container {
    gap: 1.5rem;
    margin-top: 2rem;
    margin-bottom: 2rem;
    padding: 0.5rem;
    opacity: 0.6;
    background-color: var(--color-background);
}

.fa-brands {
    font-size: 2rem;
    color: var(--color-button2);
}

.fa-brands:hover {
    background-color: var(--color-button);
}

.fa-brands:active {
    color: var(--color-button);
}
</style>

