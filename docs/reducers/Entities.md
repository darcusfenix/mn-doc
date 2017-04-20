# Entities

Este reducer se encuentra en src/containers/main/mainReducer.es6. Manipula el array, objetos y propiedades del un objeto.

```javascript

entitiesReducer = (state = store.entities, action) => {

    const {entitie, value, type, index, property} = action;

    switch (type) {
    
                case ACTION_ENTITIES_LIST:
    
                    return update(state, {
                        [entitie]: {
                            "$set": value
                        }
                    });
    
                case ACTION_ENTITIES_LIST_PUSH:
    
                    return update(state, {
                        [entitie]: {
                            "$push": [action.object]
                        }
                    });
    
                case ACTION_ENTITIES_LIST_REMOVE:
    
                    return update(state, {
                        [entitie]: {
                            "$splice": [[index, 1]]
                        }
                    });
    
                case ACTION_ENTITIES_SET_ATTR:
    
                    return update(state, {
                        [entitie]: {
                            [index]: {
                                [property]: {
                                    "$set": value
                                }
                            }
                        }
                    });
    
                default:
                    return state;
            }

}

```
### Acciones
| Caso                          | retorno | descripción                   |
|-------------------------------|---------|-------------------------------|
| ACTION_ENTITIES_LIST          | array   | Reemplaza el array actual       |
| ACTION_ENTITIES_LIST_PUSH     | array   | Añade un objeto al array actual |
| ACTION_ENTITIES_LIST_REMOVE   | array   | Quita un elemento del array según la posición   |
| ACTION_ENTITIES_SET_ATTR      | array   | Cambia el valor de una propiedad de un objeto de una posición en específico en el array|


### Ejemplo de uso ACTION_ENTITIES_LIST:

```javascript
// ACTION_ENTITIES_LIST

this.request().then((response) => {
    dispatch({
        "type": ACTION_ENTITIES_LIST,
        "entitie": "usuarios",
        "value": response
    });
});

```

### Propiedades dispatch de ACTION_ENTITIES_LIST

| nombre    | tipo              | descripción                   |
|---------- |------------------ |-------------------------------|
| type *    | string            | Constante de la acción        |
| entitie * | string            | Entidad del store a la que se reemplazará el array actual  |
| value *   | array             | Nuevo array a reemplazar  |

### Ejemplo de uso ACTION_ENTITIES_LIST_PUSH:

```javascript
// ACTION_ENTITIES_LIST_PUSH

addUser (dispatch) => {

    this.request().then((response) => {
        dispatch({
            "type": ACTION_ENTITIES_LIST_PUSH,
            "entitie": "usuarios",
            "object": response
        });
    });

};

```

### Propiedades dispatch de ACTION_ENTITIES_LIST_PUSH

| nombre    | tipo              | descripción                   |
|---------- |------------------ |-------------------------------|
| type *    | string            | Constante de la acción        |
| entitie * | string            | Entidad del store a la que se agregará un objeto al array actual|
| object *  | object            | Nuevo objeto a agregar  |



### Ejemplo de uso ACTION_ENTITIES_LIST_REMOVE:

```javascript
// ACTION_ENTITIES_LIST_REMOVE

removeUser (dispatch, index) => {

    this.request().then((response) => {
        dispatch({
            "type": ACTION_ENTITIES_LIST_REMOVE,
            "entitie": "usuarios",
            "index": index
        });
    });

};

```

### Propiedades dispatch de ACTION_ENTITIES_LIST_REMOVE

| nombre    | tipo              | descripción                   |
|---------- |------------------ |-------------------------------|
| type *    | string            | Constante de la acción        |
| entitie * | string            | Entidad del store a la que se quitará el objeto del array|
| index *   | number            | Posición del objeto en el array|



### Ejemplo de uso ACTION_ENTITIES_SET_ATTR:

```javascript
// ACTION_ENTITIES_SET_ATTR

updateUser (dispatch, index) => {

    this.request().then((response) => {
       dispatch({
           "type": ACTION_ENTITIES_SET_ATTR,
           "property": "estatus",
           "entitie": "usuarios",
           "index": index,
           "value": false
       });
    });

};

```

### Propiedades dispatch de ACTION_ENTITIES_SET_ATTR

| nombre    | tipo              | descripción                   |
|---------- |------------------ |-------------------------------|
| type *    | string            | Constante de la acción        |
| entitie * | string            | Entidad del store a la que se modificará un propiedad de un objeto en el array actual|
| property *| string            | Propiedad del objeto que se va modificar |
| index *   | number            | Posición del objeto en el array en el que se modificará la propiedad|
| value *   | *                 | Nuevo valor que tendrá la propiedad del objeto |

