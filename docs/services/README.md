# SERVICES
    Esta sección se encuentra en src/services. Carpeta que contiene clases con metodos estáticos para utilizar en
    cualquier container/componente en la spa. Objetivo de uso: reducir código. Cada método requiere la función dispatch
    que redux proporciona en el componente.
```
.
├── /.idea                          #     
├── /node_modules                   # 
├── /src                            #  
│   ├── /services                   #  
│   │   ├── index.es6               # Exporta e importa todos los servicios que están en esta carpeta.
│   │   ├── LinearProgress.es6      # Servicio que dispara al reducer el control del estado de la línea de progreso.
│   │   ├── Log.es6                 # Servicio para pintar en consola del browser. 
│   │   ├── PageProgress.es6        # Servicio que dispara al reducer el control del estado del spiner de progreso que oculta/bloquea toda la página. 
│   │   ├── SnackBar.es6            # Servicio que dispara al reducer el control del estodo y mensaje del snackbar. 
```


## Ejemplos de uso:

```javascript

 // Servicio: LinearProgress.es6

    import {LinearProgress} from "../services/index";
 
    LinearProgress.show(dispatch);

    this.request().then((response) => {
        
        LinearProgress.hide(dispatch);
        
    });
```

```javascript

 // Servicio: PageProgress.es6

    import {PageProgress} from "../services/index";
 
    PageProgress.show(dispatch);

    this.request().then((response) => {
        
        PageProgress.hide(dispatch);
        
    });
```

```javascript

 // Servicio: SnackBar.es6
    
    import {SnackBar} from "../services/index";

    this.request().then((response) => {
        
        SnackBar.show(dispatch, "Registro agregado correctamente");
        
    });
```

```javascript
 // Servicio: Log.es6
 
    import {Log} from "../services/index";

    this.request().catch((error) => {
        
        Log.error(error);
        
    });
```