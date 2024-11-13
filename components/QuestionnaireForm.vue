<template>
<div>
  <h1>Formulario de Cuestionario</h1>
  <form @submit.prevent="handleSubmit">
    <input type="text" v-model="nombre" placeholder="Nombre del producto" />
    <input type="text" v-model="ambitoUso" placeholder="Ámbito de uso" />
    <input type="text" v-model="fraccionArancelaria" placeholder="Fracción arancelaria (opcional)" />
    <input type="number" v-model="peso" placeholder="Peso (kg)" />
    <input type="text" v-model="medidas" placeholder="Medidas (ej. 10x20x30 cm)" />
    <input type="text" v-model="material" placeholder="Material" />
    <input type="number" v-model="cantidadMinima" placeholder="Cantidad mínima de compra" />
    <input type="number" v-model="presupuesto" placeholder="Presupuesto disponible" />
    <input type="text" v-model="certificacion1" placeholder="Certificación 1 (opcional)" />
    <input type="text" v-model="certificacion2" placeholder="Certificación 2 (opcional)" />
    <input type="text" v-model="certificacion3" placeholder="Certificación 3 (opcional)" />
    
    <button type="submit">Generar Descripción</button>
  </form>

  <div id="descripcion-final">
    <h2>Descripción Final:</h2>
    <p>{{ descripcionFinal }}</p>
  </div>
</div>
</template>

<script>
export default {
data() {
  return {
    nombre: '',
    ambitoUso: '',
    fraccionArancelaria: '',
    peso: '',
    medidas: '',
    material: '',
    cantidadMinima: '',
    presupuesto: '',
    certificacion1: '',
    certificacion2: '',
    certificacion3: '',
    descripcionFinal: ''
  };
},
methods: {
  handleSubmit() {
    this.descripcionFinal = `
      Nombre del Producto: ${this.nombre},
      Ámbito de Uso: ${this.ambitoUso},
      ${this.fraccionArancelaria ? `Fracción Arancelaria: ${this.fraccionArancelaria},` : ''}
      Peso: ${this.peso} kg,
      Medidas: ${this.medidas},
      Material: ${this.material},
      Cantidad Mínima de Compra: ${this.cantidadMinima},
      Presupuesto Disponible: $${this.presupuesto},
      ${this.certificacion1 ? `Certificación 1: ${this.certificacion1},` : ''}
      ${this.certificacion2 ? `Certificación 2: ${this.certificacion2},` : ''}
      ${this.certificacion3 ? `Certificación 3: ${this.certificacion3}` : ''}
    `.trim();
  }
}
};
</script>

<style scoped>
/* Agrega estilos específicos para tu formulario aquí */
form {
display: flex;
flex-direction: column;
gap: 8px;
max-width: 400px;
}
button {
align-self: start;
}
#descripcion-final {
margin-top: 20px;
}
</style>
