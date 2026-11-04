# Diccionario de datos 

## Entidad: Departamento

| Nombre del elemento | Tipo de dato | Longitud | Formato / valores permitidos | Descripción |
|---|---|---|---|---|
| id_departamento | Integer | No aplica | Entero positivo único | Identifica de manera única cada departamento. |
| num_departamento | String | 10 caracteres | Texto alfanumérico | Código o número utilizado para identificar la unidad dentro del complejo. |
| estado_actual | String | 30 caracteres | Disponible, ocupado, en limpieza, en mantenimiento, fuera de servicio | Indica la situación operativa actual del departamento. |
| Observaciones | String | 500 caracteres | Texto libre | Registra información complementaria relevante sobre la unidad. |

**Relaciones:**

- `id_departamento` se relaciona con el campo del mismo nombre en la entidad `solicitud_mantenimiento`.

## Entidad: solicitud_mantenimiento

| Nombre del elemento | Tipo de dato | Longitud | Formato / valores permitidos | Descripción |
|---|---|---|---|---|
| id_solicitud | Integer | No aplica | Entero positivo único | Identifica de manera única cada solicitud. |
| id_departamento | Integer | No aplica | Debe corresponder a un departamento existente | Identifica la unidad en la que se detectó el problema. |
| fecha_registro | DateTime | No aplica | AAAA-MM-DD HH:MM:SS | Registra la fecha y hora en que se generó la solicitud. |
| descripcion_problema | String | 1000 caracteres | Texto libre | Describe la falla o el requerimiento informado. |
| prioridad | String | 10 caracteres | Baja, Media, Alta | Indica el nivel de urgencia con el que debe atenderse la solicitud. |
| estado_solicitud | String | 20 caracteres | Pendiente, Asignada, En proceso, Resuelta, Cancelada | Indica la situación actual de la solicitud. |

**Relaciones:**

- `id_departamento` se vincula con `departamento.id_departamento`.
- `id_solicitud` se vincula con `intervencion_mantenimiento.id_solicitud`.


## Entidad: intervencion_mantenimiento

| Nombre del elemento | Tipo de dato | Longitud | Formato / valores permitidos | Descripción |
|---|---|---|---|---|
| id_intervencion | Integer | No aplica | Entero positivo único | Identifica de manera única cada intervención. |
| id_solicitud | Integer | No aplica | Debe corresponder a una solicitud existente | Identifica la solicitud que origina la intervención. |
| responsable | String | 100 caracteres | Nombre o identificador del responsable | Registra quién realizó o tiene asignado el trabajo. |
| fecha_inicio | DateTime | No aplica | AAAA-MM-DD HH:MM:SS | Indica cuándo comenzó la intervención. |
| fecha_finalizacion | DateTime | No aplica | AAAA-MM-DD HH:MM:SS o nulo si sigue pendiente | Indica cuándo terminó el trabajo. |
| descripcion_trabajo | String | 1000 caracteres | Texto libre | Detalla las tareas realizadas durante la intervención. |

**Relaciones:**

- `id_solicitud` se vincula con `solicitud_mantenimiento.id_solicitud`.
- Una solicitud puede tener varias intervenciones.
