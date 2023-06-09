<script>
    export default {
        data() {
            return {
                nombre: "",
                apellido: "",
                edad: null,
                profesion: "",
                pais: "",
            }
        },
        computed: {
            usuario: {
                get: function() {
                    if (this.nombre && this.apellido) {
                        return this.nombre + " " + this.apellido;
                    } else {
                        return this.nombre || this.apellido;
                    }
                },
                set: function(nuevoNombre) {
                    const nombres = nuevoNombre.split(" ");
                    if(nombres.length === 2) {
                        this.nombre = nombres[0];
                        this.apellido = nombres[1];
                    } else if (nombres.length <= 1) {
                        this.nombre = nombres[0] || "";
                        this.apellido = "";
                    }
                }
            }
        },
        methods: {
            resetear: function() {
                this.nombre = "";
                this.apellido = "";
                this.edad = null;
                this.profesion = "";
                this.pais = "";
            }
        }
    }
</script>

<template>
    <div class="row" id="vue-form">
        <div class="col-lx col-lg-5 col-md col-sm col justify-content-center">
            <div>
                <header class="jh-100 d-flex align-items-center justify-content-center">
                    <h1>
                        Perfil
                    </h1>
                </header>
                <div>
                    <img src="src/assets/perfil.jpg" alt="" class="img-fluid rounded-circle">
                </div>
                <div>
                    <h2 class="jh-100 d-flex align-items-center justify-content-center"> {{ usuario }} </h2>
                    <h4 class="jh-100 d-flex align-items-center justify-content-center"> {{ profesion }} </h4>
                </div>
            </div>
        </div>
        
        <div class="col-lg-1"></div>
        <div class="col-lx col-lg-6 col-md col-sm col">
            <form v-on:reset="resetear" v-on:submit.prevent>
                <div class="justify-content-center">
                    <div class="form-group">
                        <label for="nombre">Nombre</label>
                        <input type="text" id="nombre" class="form-control" v-model="nombre">

                        <label for="apellido">Apellido</label>
                        <input type="text" id="apellido" class="form-control" v-model="apellido">

                        <label for="edad">Edad</label>
                        <input type="number" id="edad" class="form-control" v-model="edad">
                    </div>
                    <div class="form-group">
                        <label for="profesion">Profesión</label>
                        <input type="text" id="profesion" class="form-control" v-model="profesion">

                        <label for="pais">País</label>
                        <select name="pais" id="pais" class="form-control" v-model="pais">
                            <option value=""></option>
                            <option value="Colombia">Colombia</option>
                            <option value="España">España</option>
                            <option value="México">México</option>
                        </select>
                    </div>

                    <div>
                        <p v-if="usuario">¡Hola! Mi nombre es {{nombre}} {{apellido}}. Tengo {{edad}} años de edad, 
                            vivo en {{pais}} y soy {{profesion}}</p>
                        <label for="firma">Firma</label>
                        <input type="text" id="firma" v-model="usuario">
                    </div>
                    <div>
                        <button type="reset">Limpiar campos</button>
                        <button type="submit">Guardar</button>
                    </div>
                </div>
            </form>
        </div>

    </div>
</template>

<style>
*, *:before, *:after {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  font-family: 'Open Sans', Helvetica, Arial, sans-serif;
  background: #ededed;
}

input, button {
  border: none;
  outline: none;
  background: none;
  font-family: 'Open Sans', Helvetica, Arial, sans-serif;
}

.tip {
  font-size: 20px;
  margin: 40px auto 50px;
  text-align: center;
}

.cont {
  overflow: hidden;
  position: relative;
  height: 550px;
  margin: 0 auto 100px;
  background: #fff;
}

.form {
  position: relative;
  height: 100%;
  padding: 30px 30px 0;
}

.sub-cont {
  overflow: hidden;
  position: absolute;
  top: 0;
  height: 100%;
  background: #fff;
  }

button {
  display: block;
  margin: 0 auto;
  border-radius: 30px;
  color: #fff;
  font-size: 15px;
  cursor: pointer;
}

.img {
  overflow: hidden;
  z-index: 2;
  position: absolute;
  left: 0;
  top: 0;
  height: 100%;
  padding-top: 360px;
  }


h2 {
  width: 100%;
  font-size: 26px;
  text-align: center;
}

label {
  display: block;
  margin: 10px auto 0;
  text-align: center;
}

input {
  display: block;
  width: 100%;
  margin-top: 0px;
  padding-bottom: 5px;
  font-size: 16px;
  border-bottom: 1px solid rgba(0,0,0,0.4);
  text-align: center;
}

.forgot-pass {
  margin-top: 15px;
  text-align: center;
  font-size: 12px;
  color: #cfcfcf;
}

.submit {
  margin-top: 40px;
  margin-bottom: 20px;
  background: #d4af7a;
  text-transform: uppercase;
}

.fb-btn {
  border: 2px solid #d3dae9;
  color: darken(#d3dae9, 20%);
}

.sign-in {
  transition-timing-function: ease-out;
}

.icon-link {
  position: absolute;
  left: 5px;
  bottom: 5px;
  width: 32px;
}
</style>