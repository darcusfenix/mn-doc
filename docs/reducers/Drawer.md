# Drawer / Menú

Este reducer se encuentra en src/containers/main/mainReducer.es6. Controla el estado del menú. Mostrar / ocultar

```javascript

drawerReducer = (state = store.widgets.drawer.open, action) => {

    switch (action.type) {
        case ACTION_MAIN_DRAWER_TOGGLE:
            return action.flag;
        default:
            return state;
    }

}

```

### Ejemplo de uso:

```javascript
import * as type from "./store/actions";

const accion = () => {

        return (dispatch) => {

            dispatch({
                "type": type.ACTION_MAIN_FORMS_INPUTS,
                "flag": true
            });

        };

    }
```

### Propiedades para el dispatch

| nombre    | tipo              | descripción                   |
|---------- |------------------ |-------------------------------|
| type *    | string            | Constante de la acción        |
| flag *    | boolean           | Determina el estado del menú  |
