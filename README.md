<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Blog de Profesores</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <header>
        <h1>Comentarios sobre Profesores</h1>
    </header>
    
    <section id="profesores">
        <h2>Agregar Profesor</h2>
        <input type="text" id="nombreProfesor" placeholder="Nombre del profesor">
        <button onclick="agregarProfesor()">Agregar</button>
        <div id="comentarios"></div>
    </section>

    <section id="calificaciones">
        <h2>Calificar Profesores</h2>
        <input type="text" id="nombreCalificado" placeholder="Nombre del profesor a calificar">
        <input type="number" id="calificacion" min="1" max="5" placeholder="Calificación (1-5)">
        <button onclick="calificarProfesor()">Calificar</button>
        <div id="calificacionesList"></div>
    </section>

    <section id="resumenes">
        <h2>Subir Resúmenes</h2>
        <input type="file" id="archivoResumen">
        <button onclick="subirResumen()">Subir</button>
        <div id="listaResumenes"></div>
    </section>

    <script src="script.js"></script>
</body>
</html>
body {
    font-family: Arial, sans-serif;
    background-color: #f4f4f4;
    margin: 0;
    padding: 20px;
}

header {
    background: #333;
    color: #fff;
    padding: 10px 0;
    text-align: center;
}

section {
    background: #fff;
    padding: 20px;
    margin: 20px 0;
    border-radius: 5px;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
}

h2 {
    margin-top: 0;
}

input[type="text"], input[type="number"], input[type="file"] {
    width: 100%;
    padding: 10px;
    margin: 10px 0;
    border: 1px solid #ccc;
    border-radius: 4px;
}

button {
    background: #28a745;
    color: white;
    border: none;
    padding: 10px 15px;
    border-radius: 4px;
    cursor: pointer;
}

button:hover {
    background: #218838;
}
// Función para agregar un profesor
function agregarProfesor() {
    const nombre = document.getElementById('nombreProfesor').value;
    if (nombre) {
        const comentariosDiv = document.getElementById('comentarios');
        const newDiv = document.createElement('div');
        newDiv.innerHTML = `<strong>${nombre}</strong>: <input type="text" placeholder="Comentario...">
                            <button onclick="agregarComentario(this)">Comentar</button>`;
        comentariosDiv.appendChild(newDiv);
        document.getElementById('nombreProfesor').value = ''; // Limpiar el input
    } else {
        alert('Por favor, ingresa un nombre de profesor.');
    }
}

// Función para agregar un comentario
function agregarComentario(button) {
    const comentario = button.previousElementSibling.value;
    if (comentario) {
        const comentarioDiv = document.createElement('div');
        comentarioDiv.textContent = comentario;
        button.parentNode.appendChild(comentarioDiv);
        button.previousElementSibling.value = ''; // Limpiar el input
    } else {
        alert('Por favor, ingresa un comentario.');
    }
}

// Función para calificar un profesor
function calificarProfesor() {
    const nombre = document.getElementById('nombreCalificado').value;
    const calificacion = document.getElementById('calificacion').value;
    if (nombre && calificacion) {
        const calificacionesList = document.getElementById('calificacionesList');
        const newCalificacion = document.createElement('div');
        newCalificacion.textContent = `${nombre} - Calificación: ${calificacion}`;
        calificacionesList.appendChild(newCalificacion);
        document.getElementById('nombreCalificado').value = ''; // Limpiar el input
        document.getElementById('calificacion').value = ''; // Limpiar el input
    } else {
        alert('Por favor, ingresa el nombre del profesor y la calificación.');
    }
}

// Función para subir resúmenes
function subirResumen() {
    const archivo = document.getElementById('archivoResumen').files[0];
    if (archivo) {
        const listaResumenes = document.getElementById('listaResumenes');
        const newResumen = document.createElement('div');
        newResumen.textContent = archivo.name; // Muestra el nombre del archivo
        listaResumenes.appendChild(newResumen);
    } else {
        alert('Por favor, selecciona un archivo para subir.');
    }
}
