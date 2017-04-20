# Store de Redux

La configuración de redux se encuentra en src/store/. El json representa el store de redux como dato inicial. La definición es la siguiente.

```json
{
    "widgets": {
        "drawer": {
            "open": false
        },
        "snackBar": {
            "open": false,
            "message": ""
        }
    },
    "main": {
        "pageProgress": false,
        "progress": false,
        "linearProgress": false,
        "titlePage": "Más nómina"
    },
    "forms": {
        "corresponsal": [],
        "contacto": [],
        "programacion": [],
        "direccion": [],
        "filtrosCatalogos": [],
        "altaEdicionCatalogos": [],
        "filtrosCredito": []
    },
    "entities": {
        "corresponsales": [],
        "contactos": [],
        "plazos": [],
        "sucursales": [],
        "programaciones": [],
        "estados": [],
        "nivelesPuesto": [],
        "catNivelesPuesto": [],
        "catalogosGenericos": [],
        "altaEdicionCatalogos": []
    },
    "tmp": {
        "form": []
    }
}
```

Las propiedades tienen la siguiente descripción:

* <b>widgets</b>: Elementos gráficos que apareerán en toda la spa.
    * <b>drawer</b>: Objeto para manejar el Menú vertical izquierdo
        * <b>open</b>: Propiedad booleana que determina el estado del menú. Si es falso el menú está oculto de lo contrario mestra el menú. 
    * <b>snackBar</b>: Objeto para manejar el mensaje de retroalimentación al usuario. Ejemplo: después de una petición rest.
        * <b>open</b>: Propiedad booleana que determina el estado del snackbar. Si es falso el snackbar está oculto de lo contrario mestra el snackbar.
* <b>main</b>: Objeto que controla los elementos que están únicamente en el componente Main.jsx
    * <b>pageProgress</b>: Propiedad booleana que determina el estado del spinner que oculta todo el contenido de una página. Es decir, este no oculta el Header y Menú. Usar para cargar recursos requeridos para continar con la navegación de la página. Ejemplo: Servicio rest que proporciona los catálogos de una formulario-filtro para obtener los registros de una tabla.
    * <b>progress</b>: Propiedad booleana que determina el estado del spinner génerico. Quiere decir que puede ser usado en cualquier sección de una página o modal. Ejemplo: Usar para consumir servicios rest para obtener los catálogos de un formulario que se mostrará en un Modal.
    * <b>linearProgress</b>: Propiedad booleana que determina el estado de la línea de progreso. Esta línea se muestra en la parte superior del Header. Usar cuando se realice una acción que no bloquee / limite la funcionalidad de la spa al usuario. Ejemplo: Cuando se da alta un registro mostrar la línea hasta recibir respuesta del servicio.   
    * <b>titlePage</b>: Propiedad de texto utilizada para mostrar el título de la página actual. Este texto se refleja en el Header.   
* <b>forms</b>: Objeto que contiene las definiciones de los formularios utilizados en la spa. Un formulario es un array de objetos definidos como Inputs.
    * <b>corresponsal</b>: Ejemplo: Este array de inputs representa el formulario para la alta y edición de un corresponsal.
    * <b>filtrosCatalogos</b>: Ejemplo: El prefijo "filtros" determina un formulario para realizar filtros a una serie de registros que posiblemente se mostrarán en una Tabla.
* <b>entities</b>: Objeto que contiene los arrays para ser mostrados en tablas. Un objeto no tiene definición, es decir, queda abierto. 
* <b>tmp</b>: Objeto que contiene una propiedad form. Básicamente misma definición de "form". Pero, el objetivo es utilizar este como respaldo de valores de los inputs. Ejemplo: Cuando se inicia un formulario pasar el form original a esta propiedad. Los valores del form original se modifican, pero el usuario decide cancelar tal acción, regresaremos este respaldo al form original para asi mostrar al usuario los valores a como estaban.  
