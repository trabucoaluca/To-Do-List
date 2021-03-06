# Todo App :)

## Sobre el equipo
### Integrantes:
- Jorge Ivan Gutierrez Yañez
- Diana Yesenia Campos Tenorio
- Daniel Rodríguez López
- Anahi Camas Hernández 
- Damian Susano Martinez 

Equipo numero 20


_Video Explicativo https://youtu.be/f4zin6TN49g_ 

## Explicación
### Creación de nodos
_Se crea una función que crea los nodos para posteriormente ser llamada._ 

```javascript
// Función que crea los nodos 
function createNode(type) {
    var node = document.createElement(type);
    return node;
}
```
_Se obtiene el div principal para después añadir nuevos nodos y así crear la estructura HTML completa._
```javascript
// Crear y agregar nodos 
var app = document.getElementById('app');

var container = createNode('div');
container.className = "container";
app.appendChild(container);

var h1 =  createNode('h1');
var text = document.createTextNode("Todo APP");
container.appendChild(h1);
h1.appendChild(text);
```
Estructura html

![imgGitHub](https://github.com/trabucoaluca/To-Do-List/blob/master/img/estructurahtml.png)

Resultado en el navegador

![imgGitHub](https://github.com/trabucoaluca/To-Do-List/blob/master/img/interfazsinestilo.png)

### Agregar task
_Se genera la función addTask que obtiene el valor ingresado, el task se agrega en una lista, también se crean nuevos nodos para visualizar cada task._
```javascript
function addTask(event) {
    event.preventDefault();
    //Leer el valor del text area
    var task = document.getElementById('task').value;
    //Validar informacion del task
    if (task != ""){
        //Crear boton de eliminar
        var deleteButton = document.createElement('a');
        deleteButton.classList = 'delete-task';
        deleteButton.innerText = 'x';
        //Crear elemento y añadir el elemento a la lista
        var ul =  document.querySelector('ul');
        var li = document.createElement('li');
        li.innerText = task;
        //Añade el boton de borrar al task
        li.appendChild(deleteButton);
        //Añade el task a la lista
        taskList.appendChild(ul);
        ul.appendChild(li);

        //Reinicio del formulario
        document.getElementById('task').value = "";
    } else {
        alert("Please, add a task");
    }
}
```
### Eliminar task
_Se agrega la función deleteTask para que al presionar el botón que se encuentra al lado derecho del task elimine dicho task._
```javascript
function deleteTask(e) {
    e.preventDefault();
    if (e.target.className === 'delete-task') {
        e.target.parentElement.remove();
        deleteTaskLocalStorage(e.target.parentElement.textContent);
    }
}
```
### Completar task
_Agregamos al código la parte de marcar tarea completada, al realizar click en algun elemento de la lista se alterna el nombre de la clase por la de "checked"._
```javascript
var ulList = document.querySelector('ul');
ulList.addEventListener('click',function(event){

    if(event.target.tagName === "LI"){
        
        event.target.classList.toggle('checked');

    }
},false);
```
### Estilo
_Se agregan los links de los archivos CSS_
```html
    <link rel="stylesheet" href="css/normalize.css">
    <link rel="stylesheet" href="css/skeleton.css">
    <link rel="stylesheet" href="css/styles.css">
```
Resultado en el navegador.
![imgGitHub](https://github.com/trabucoaluca/To-Do-List/blob/master/img/Task-completed.png)


### Se agrega mensaje
Se agrega código para mandar a imprimir en pantalla un mensaje indicando que la tarea no puede ir vacía
![imgGitHub](https://github.com/trabucoaluca/To-Do-List/blob/master/img/msjError.png)
```javascript

function showError(error){
    //se crea la etiqueta contenedora del mensaje
    const errorMessage = document.createElement('p');
    errorMessage.textContent = error;
    errorMessage.classList.add('error');
    //insertarlo en el contenido     
    container.appendChild(errorMessage);
    setTimeout(() => {
        //elimina la alerta despues de 3 segundos
        errorMessage.remove();
    }, 3000);
}
```
## Resultado final 

![imgGitHub](https://github.com/trabucoaluca/To-Do-List/blob/master/img/imgEnd2.png)
Miralo por ti mismo
 _https://trabucoaluca.github.io/To-Do-List/_
 
 
