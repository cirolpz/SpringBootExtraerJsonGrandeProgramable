# SpringBootExtraerJsonGrandeProgramable

## Descripción
- En este proyecto se consume un JSON grande. La aplicación carga una base de datos creada especificamente para este JSON.
- EL programa realiza 3 veces una verificación si se cargó el JSON y también un control de cargar el JSON solo una vez al día.

## Servicios

### Dispo_alquiler_diariaService
- **getAllDispo_alquiler_diaria**: Obtiene todos los registros de Dispo_alquiler_diaria desde el repositorio. Maneja excepciones y registra errores, devolviendo una lista vacía en caso de fallo.
- **cargarJsonSiNoCargado**: Método programado para ejecutarse cada minuto (según la configuración de cron). Verifica si el JSON ya se cargó hoy. Si no se ha cargado, llama al método cargarJson para cargar los datos desde el archivo JSON.
- **jsonYaCargadoHoy**: Verifica si el JSON ya se cargó hoy consultando el repositorio. Maneja excepciones y registra errores, devolviendo false en caso de fallo.
- **cargarJson**: Carga datos desde un archivo JSON (datos.JSON). Parsea el JSON y convierte los datos en objetos Dispo_alquiler_diaria. Valida y asigna valores a los atributos de los objetos, manejando excepciones. Inserta los datos en la base de datos mediante una operación de batch en el repositorio. Registra el éxito o los errores durante el proceso de carga.

## Tecnologías
- **Java**: Lenguaje de programación principal utilizado para desarrollar la aplicación.
- **Spring Boot**: Framework utilizado para crear la aplicación web. Facilita la configuración y el desarrollo de aplicaciones basadas en Spring.
- **Gradle**: Sistema de construcción utilizado para gestionar las dependencias y la construcción del proyecto.
- **Spring Scheduling**: Utilizado para programar tareas, como la carga de JSON cada minuto (@Scheduled).
- **Spring JDBC**: Utilizado para interactuar con la base de datos mediante NamedParameterJdbcTemplate.
- **JSON Simple**: Biblioteca utilizada para parsear y manejar archivos JSON.
- **SLF4J (Simple Logging Facade for Java)**: Biblioteca de logging utilizada para registrar eventos y errores en la aplicación.

## Ejemplo de JSON
```json
[
  {
    "rubro_nombre": "Construcción",
    "estado": "Activo",
    "bienEmpresa_nombre": "Excavadora Co.",
    "contratoEmpresa_nombre": "ABC Construction",
    "propietario": "John Doe",
    "contrato_estado": "Vigente",
    "contrato_numeroComp": "123456",
    "contrato_fechaFin": "2024-12-31",
    "contrato_fecha": "2024-01-01",
    "contrato_cliente_nombre": "XYZ Corp",
    "contrato_numero": "001122",
    "contrato_fechaInicio": "2024-01-01",
    "linea_nombre": "Excavadoras",
    "propio": "Sí",
    "enTransito": "No",
    "ordenDeTrabajo_descripcion": "Excavación del sitio",
    "ordenDeTrabajo_estado": "En proceso",
    "ordenDeTrabajo_numeroComp": "654321",
    "ordenDeTrabajo_fechaEntrega": "2024-12-31",
    "ordenDeTrabajo_fechaInicio": "2024-01-01",
    "sucursal_nombre": "Sucursal Centro",
    "entregado": "No",
    "proveedor_nombre": "Proveedores S.A.",
    "articulo_codigo": "EXC-123",
    "bien_descripcion": "Excavadora hidráulica",
    "bien_estado": "Operativo",
    "bien_aFabricacion": "2020",
    "bien_depositoAlmacen_nombre": "Depósito Central",
    "bien_identificacion": "EXC2020-1234",
    "bien_modelo": "EXC-ModelX",
    "bien_serie": "SER123456",
    "Fecha_dispo": "2024-05-01"
  },
  {
    "rubro_nombre": "Ingeniería",
    "estado": "Inactivo",
    "bienEmpresa_nombre": "Gruas S.A.",
    "contratoEmpresa_nombre": "Engineering Solutions",
    "propietario": "Jane Smith",
    "contrato_estado": "Expirado",
    "contrato_numeroComp": "789101",
    "contrato_fechaFin": "2023-12-31",
    "contrato_fecha": "2023-01-01",
    "contrato_cliente_nombre": "Engineering Inc.",
    "contrato_numero": "002233",
    "contrato_fechaInicio": "2023-01-01",
    "linea_nombre": "Gruas",
    "propio": "No",
    "enTransito": "Sí",
    "ordenDeTrabajo_descripcion": "Mantenimiento de grúas",
    "ordenDeTrabajo_estado": "Finalizado",
    "ordenDeTrabajo_numeroComp": "987654",
    "ordenDeTrabajo_fechaEntrega": "2023-12-31",
    "ordenDeTrabajo_fechaInicio": "2023-01-01",
    "sucursal_nombre": "Sucursal Norte",
    "entregado": "Sí",
    "proveedor_nombre": "Proveedor Norte",
    "articulo_codigo": "GRU-456",
    "bien_descripcion": "Grúa telescópica",
    "bien_estado": "Inoperativo",
    "bien_aFabricacion": "2018",
    "bien_depositoAlmacen_nombre": "Depósito Norte",
    "bien_identificacion": "GRU2018-4567",
    "bien_modelo": "GRU-ModelY",
    "bien_serie": "SER654321",
    "Fecha_dispo": "2024-05-01"
  }
]
