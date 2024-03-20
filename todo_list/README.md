# Manejo de eventos en una aplicación ToDo con React

## Función `handleSubmit`

La función `handleSubmit` es una función utilizada para manejar la presentación de un formulario. A continuación se muestra el código de la función en JavaScript:

```javascript
function handleSubmit(e) {
    e.preventDefault();
    let todo = document.getElementById('todoAdd').value
    const newTodo = {
      id: new Date().getTime(),
      text: todo.trim(),
      completed: false,
    };
    if (newTodo.text.length > 0 ) {
        setTodos([...todos].concat(newTodo));
    } else {
        alert("Enter Valid Task");
    }
    document.getElementById('todoAdd').value = ""
}
```

#### Descripción
La función handleSubmit toma un parámetro e, que es un objeto de evento. Esta función se usa comúnmente para manejar la presentación de formularios en una aplicación web.

En la primera línea de la función, e.preventDefault() se utiliza para prevenir el comportamiento predeterminado del evento. Esto evita que la página se actualice cuando se envía el formulario.

Luego, se obtiene el valor del elemento con el id 'todoAdd' del DOM y se almacena en la variable todo.

Se crea un nuevo objeto newTodo que representa una nueva tarea. Este objeto tiene tres propiedades: id, text (el texto de la tarea) y completed (un indicador booleano que indica si la tarea está completada o no).

Se verifica si el texto de la nueva tarea tiene una longitud mayor que cero. Si es así, la nueva tarea se agrega al estado todos utilizando el operador spread (...) y el método concat() para agregar el nuevo elemento al final del array todos.

Si el texto de la nueva tarea no tiene una longitud mayor que cero, se muestra una alerta indicando al usuario que ingrese una tarea válida.

Finalmente, se establece el valor del elemento con el id 'todoAdd' en una cadena vacía, lo que borra el contenido del campo de entrada del formulario.

Esta función es útil en aplicaciones web que gestionan listas de tareas, ya que maneja la adición de nuevas tareas a la lista existente.

## Eliminar una tarea existente

Eliminar una tarea se puede manejar de varias maneras. Ahora escribirás el código utilizando el método filter que filtra la tarea a eliminar basándose en el id y devuelve el resto de las tareas. Se ha agregado un marcador de posición en el archivo App.js donde necesitas agregar la función de eliminar tarea.

Código para eliminar una tarea

```javascript
function deleteTodo(id) {
  let updatedTodos = [...todos].filter((todo) => todo.id !== id);
  setTodos(updatedTodos);
}
```

Este código recorre el arreglo de tareas existentes y filtra la tarea que coincide con el id proporcionado. Al usar el método filter, se crea un nuevo arreglo excluyendo la tarea que se desea eliminar. Este nuevo arreglo se establece entonces como el nuevo estado de todos, efectivamente eliminando la tarea del estado y de la interfaz de usuario.

## Agregar un botón para eliminar una tarea
Para permitir a los usuarios eliminar una tarea, se añade un botón junto a cada tarea en la lista. Este botón llama al método deleteTodo pasando el id del ítem de la tarea al hacer clic.
```javascript
<button onClick={() => deleteTodo(todo.id)}>Delete</button>
```

### Conclusión 
El manejo efectivo de eventos en React es crucial para desarrollar aplicaciones interactivas y dinámicas como una lista de tareas (ToDo). A través del ejemplo proporcionado, hemos visto cómo las funciones handleSubmit y deleteTodo permiten agregar y eliminar tareas, respectivamente, manipulando el estado de la aplicación de manera reactiva. El uso del estado de React, junto con eventos como el clic y la prevención del envío de formularios, nos permite controlar el flujo de datos dentro de la aplicación sin recargar la página. Este enfoque no solo mejora la experiencia del usuario al proporcionar una respuesta inmediata a sus acciones sino que también nos enseña patrones importantes en el desarrollo de aplicaciones web modernas. Al seguir expandiendo estos conceptos básicos, se pueden implementar características más avanzadas y personalizaciones, haciendo de React una herramienta poderosa para los desarrolladores.
