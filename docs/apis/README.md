# APIS
Esta sección se encuentra en src/api.
Clases que heredan de Request. La clase Request contiene los atributos y métodos para realizar una petición con Axios.
La definición de los métodos que una clase api debe tener son:
    
* get(): Solicita un array de registros. 
* getById(): Solicita un registro que cumpla el identificador. 
* getByEntidad(): Solicita un registro que cumpla la condición de la entidad. 
* create(): Solicita una creación de una entidad. 
* update(): Solicita una actualización de uno o más propiedades de un registro en específico. 
* remove(): Solicita una eliminación de un registro en específico. 
* changeStatus(): Solicita un cambio de estatus de un registro en específico. ** 


    ** No debreria existir, pero como el servicio está independiente se requiere.
