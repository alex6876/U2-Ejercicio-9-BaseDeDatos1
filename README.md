# Ejercicio — Base de Datos de Plataforma de Aprendizaje en Línea (E-Learning)



Proyecto enfocado en la modelación Entidad-Relación (DER / MER) e implementación de base de datos relacional para un sistema de gestión de cursos en línea, administrando instructores, contenidos (módulos y lecciones), estudiantes, inscripciones, evaluaciones con banco de preguntas e historial de intentos de examen.

---

## Descripción

El sistema modela una estructura de datos relacional para la administración de una plataforma de e-learning o educación virtual. Permite gestionar la oferta académica impartida por instructores, organizar el contenido instruccional estructurado jerárquicamente en módulos y lecciones, inscribir a estudiantes y dar seguimiento a su progreso o estado de avance, así como diseñar evaluaciones asociadas con preguntas de opción múltiple y registrar los distintos intentos y calificaciones obtenidas por los alumnos.

---

## Funcionalidades e Implementación

### Entidades y Atributos

* Instructor:


* id_Instructor: Clave primaria identificadora del instructor o docente.


* nombre: Nombre completo del instructor.


* biografía: Perfil profesional o resumen de trayectoria.


* especialidad: Área académica o campo de expertise.


* contacto: Información de contacto (correo, teléfono, redes).




* Curso:


* id_CodigoCurso: Clave primaria identificadora del curso.


* titulo: Nombre o título comercial del curso.


* precio: Costo o valor de inscripción al curso.


* descripción: Resumen de los contenidos y objetivos didácticos.


* nivelDificultad: Nivel del curso (ej. principiante, intermedio, avanzado).




* Modulo:


* id_Modulo: Clave primaria identificadora del módulo.


* nombre: Título del módulo de aprendizaje.


* descripción: Detalle conceptual del contenido del módulo.


* orden Secuencial: Número de orden o secuencia dentro del curso.


* id_codigo curso: Clave foránea que referencia al curso perteneciente.




* Lección:


* id_Lección: Clave primaria identificadora de la lección.


* id_Modulo: Clave foránea que referencia al módulo al cual pertenece.


* titulo: Nombre de la lección.


* tipo: Formato del contenido (ej. video, texto, recurso descargable).


* duracion estimada: Tiempo estimado para completar la lección.


* enlace contenido: URL o enlace de acceso al recurso multimedia.




* Estudiantes:


* id_Estudiante: Clave primaria identificadora del alumno.


* nombre: Nombre del estudiante.


* apellido: Apellido del estudiante.


* Email: Correo electrónico de acceso/contacto.


* Fecha registro: Fecha de creación de usuario en la plataforma.




* Inscripción:


* id_Estudiante: Clave foránea referenciando al alumno inscripto.


* id_codigo curso: Clave foránea referenciando al curso tomado.


* fecha Alta: Fecha de matriculación o compra del curso.


* Porcentaje avance: Grado o porcentaje de lecciones completadas.


* Estado finalización: Estado del curso (ej. en progreso, completado, abandonado).




* Evaluaciones:


* id_Evaluación: Clave primaria identificadora de la prueba/examen.


* titulo: Nombre o título del examen.


* tipo: Modalidad de la evaluación (ej. cuestionario, proyecto, examen final).


* Fecha creación: Fecha de alta de la evaluación en la plataforma.


* id_codigo curso: Clave foránea referenciando al curso al que corresponde la evaluación.




* Pregunta:


* id_Pregunta: Clave primaria identificadora de la pregunta.


* id_Evaluación: Clave foránea vinculada a la evaluación origen.


* Enunciado: Texto o consigna de la pregunta.


* OpcionA: Opción de respuesta A.


* OpcionB: Opción de respuesta B.


* OpcionC: Opción de respuesta C.


* Opcion correcta: Identificador de la alternativa correcta (ej. A, B o C).




* Intentos:


* id_Intento: Clave primaria identificadora del intento de examen.


* id_Evaluación: Clave foránea del examen rendido.


* id_Estudiante: Clave foránea del alumno evaluado.


* FechaIntento: Fecha y hora en que se realizó la prueba.


* Calificación: Nota o puntaje resultante.


* Estado: Resultado del intento (ej. aprobado, desaprobado, pendiente de revisión).





---

## Relaciones del Modelo

1. Instructor ↔ Curso (Relación 1:N):


* Un instructor puede dictar y crear múltiples cursos dentro de la plataforma, pero cada curso cuenta con un instructor responsable.




2. Curso ↔ Modulo (Relación 1:N):


* Un curso se organiza internamente en varios módulos temáticos secuenciales.




3. Modulo ↔ Lección (Relación 1:N):


* Cada módulo contiene un conjunto de lecciones o unidades didácticas específicas.




4. Estudiantes ↔ Curso (Relación N:M via Inscripción):


* Un estudiante puede inscribirse a múltiples cursos y cada curso aloja a múltiples estudiantes inscritos. Se resuelve mediante la entidad intermedia `Inscripción`.




5. Curso ↔ Evaluaciones (Relación 1:N):


* Un curso abarca una o varias evaluaciones cuantitativas/cualitativas asignadas a su programa.




6. Evaluaciones ↔ Pregunta (Relación 1:N):


* Cada evaluación se compone de un conjunto de preguntas asociadas con sus respectivas opciones de respuesta.




7. Evaluaciones ↔ Intentos (Relación 1:N):


* Una evaluación registra los múltiples intentos efectuados por los alumnos.




8. Estudiantes ↔ Intentos (Relación 1:N):


* Un estudiante puede realizar varios intentos de evaluación a lo largo de su aprendizaje.
