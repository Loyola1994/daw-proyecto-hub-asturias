# Anteproyecto: Hub Junior Asturias

**Módulo:** Proyecto Intermodular (0379 · PIDW2) — 2º DAW Virtual 

**Centro:** CIFP Avilés (Curso 2026/2027) 

**Autor/a:** Luis Loyola Antuña Mérida

**Repositorio GitHub:** [Acceso al repositorio](https://github.com/Loyola1994/daw-proyecto-hub-asturias)

**Tablero GitHub Projects:** [Tablero GitHub Projects](https://github.com/users/Loyola1994/projects/5)



--- 
## 1. Justificación y dominio funcional 

### 1.1. Elevator pitch
Hub Junior Asturias es una aplicación web orientada a facilitar el acceso al empleo y a las prácticas profesionales de estudiantes y recién titulados que buscan sus primeras oportunidades laborales relacionadas con su formación, especialmente en el sector tecnológico.

La plataforma se centra inicialmente en el ámbito asturiano, con especial atención al alumnado de Formación Profesional de los ciclos DAW, DAM y ASIR, así como a estudiantes universitarios y recién titulados de informática.

El sistema permite consultar ofertas junior y prácticas, conocer sus requisitos y presentar candidaturas. 

Los visitantes pueden consultar las ofertas públicas, mientras que los usuarios registrados pueden inscribirse y revisar sus propias candidaturas. El administrador gestiona las ofertas y los datos básicos de las empresas.

El objetivo es ofrecer una herramienta especializada, con un alcance viable para el proyecto, que acerque a los estudiantes y recién titulados a sus primeras oportunidades profesionales sin incorporar inicialmente funcionalidades complejas de gestión empresarial.

### 1.2. Público objetivo y contexto de uso 
La aplicación está dirigida principalmente a los siguientes grupos:

- **Estudiantes de Formación Profesional:** alumnado de ciclos formativos relacionados con la informática, especialmente DAW, DAM y ASIR, que busca formación en empresa o sus primeras oportunidades profesionales.
  
- **Estudiantes universitarios:** personas que cursan estudios relacionados con la informática y buscan prácticas o una primera experiencia laboral vinculada a su formación.

- **Recién titulados:** personas que desean acceder a puestos junior relacionados con sus estudios.

- **Administrador:** responsable de gestionar las ofertas, mantener los datos de las empresas asociadas y realizar las tareas esenciales de administración de la plataforma.

El ámbito geográfico inicial se centra en Asturias, con especial atención a las oportunidades vinculadas al sector tecnológico regional. La ampliación a otras comunidades autónomas y a nuevas especialidades queda fuera del alcance inicial del proyecto.

En cuanto al contexto de uso:
- Los visitantes pueden consultar las ofertas publicadas sin necesidad de registrarse.

- Los usuarios registrados pueden consultar las oportunidades, presentar candidaturas y revisar sus propias candidaturas.

- El administrador es responsable de crear, editar, publicar y desactivar las ofertas, gestionar los datos básicos de las empresas y consultar las candidaturas recibidas para facilitar su tramitación con las empresas correspondientes.

En el MVP, las empresas son las destinatarias de las candidaturas, pero no disponen de cuentas ni de un panel propio para gestionar ofertas o procesos de selección.

La plataforma no pretende competir directamente con los grandes portales de empleo generalistas, sino ofrecer una solución especializada en las necesidades de estudiantes y recién titulados que buscan sus primeras oportunidades profesionales en el ámbito tecnológico.

---
## 2. Roles del sistema y casos de uso 

### 2.1. Matriz de roles (RBAC)

**Público o visitante**
- Consultar las ofertas publicadas.
-	Consultar los requisitos y detalles de una oferta.
-	Acceder al registro y al inicio de sesión.

**Candidato (usuario registrado)**
- Iniciar y cerrar sesión.
- Consultar las ofertas publicadas.
-	Presentar candidaturas a ofertas publicadas.
-	Consultar sus propias candidaturas.

**Administrador**
- Iniciar y cerrar sesión.
-	Crear, editar, publicar y desactivar ofertas.
-	Gestionar los datos básicos de las empresas asociadas a las ofertas.
-	Consultar las ofertas y empresas registradas en la plataforma.
-	Consultar las candidaturas recibidas para facilitar su tramitación con las empresas correspondientes.
-	Supervisar el funcionamiento básico de la aplicación.

Los permisos se validan en el backend. 

Los visitantes no pueden presentar candidaturas ni acceder a funcionalidades reservadas a usuarios registrados. Cada candidato solo puede consultar sus propias candidaturas, mientras que el administrador dispone de los permisos necesarios para gestionar las ofertas, los datos de las empresas y consultar las candidaturas recibidas.

En el MVP no se implementa un rol de empresa. Las empresas no disponen de acceso directo a la plataforma y la gestión de las ofertas queda a cargo del administrador.

  ---
  ### 2.2. Casos de uso principales
  
**CU-01: Registro e inicio de sesión**

**Actor:** Visitante o usuario registrado.

**Precondición:** El visitante no tiene una sesión iniciada para registrarse o dispone de una cuenta para iniciar sesión.

**Flujo principal:**

1.	El visitante accede al formulario de registro o inicio de sesión.
2.	Para registrarse, introduce los datos obligatorios y envía el formulario.
3.	El sistema valida los datos y crea la cuenta de candidato.
4.	Para iniciar sesión, el usuario introduce sus credenciales.
5.	El sistema comprueba las credenciales y establece la sesión del usuario.
6.	El sistema aplica los permisos correspondientes al rol de la cuenta.

**Resultado:** El candidato dispone de una cuenta y puede acceder a las funcionalidades autorizadas. El administrador accede mediante una cuenta creada por un procedimiento controlado, sin registro público de cuentas administrativas.

**CU-02: Consulta de ofertas** 

**Actor: Visitante o usuario registrado.**

**Precondición:** La aplicación está disponible y existen ofertas publicadas para consultar.

**Flujo principal:** 
1.	El usuario accede al listado de ofertas.
2.	El sistema muestra las ofertas publicadas.
3.	El usuario selecciona una oferta para consultar sus detalles.
4.	El sistema muestra información de la oferta, incluyendo la descripción, los requisitos, la ubicación y el tipo de oportunidad.

**Resultado:** El usuario puede consultar las ofertas publicadas y conocer sus características sin necesidad de iniciar sesión.

**CU-03: Gestión de ofertas** 

**Actor: Administrador.** 

**Precondición:** El administrador ha iniciado sesión y dispone de permisos para gestionar las ofertas.

**Flujo principal:**

1.	El administrador accede al apartado de gestión de ofertas.
2.	El administrador selecciona la opción de crear una nueva oferta o una oferta existente para editarla.
3.	El administrador introduce o modifica los datos de la oferta y guarda los cambios.
4.	El sistema valida los datos obligatorios y comprueba que sean correctos.
5.	El administrador puede publicar la oferta o desactivarla según corresponda.
6.	El sistema guarda los cambios y actualiza el estado de publicación de la oferta.

**Resultado:** La oferta queda registrada con los datos y el estado de publicación correspondientes. Solo las ofertas publicadas se muestran en el listado público.

**CU-04: Presentación de candidaturas**

**Actor: Usuario registrado.**

**Precondición:** El candidato ha iniciado sesión y la oferta está publicada.

**Flujo principal:**

1.	El candidato accede al listado de ofertas y selecciona una oferta publicada.
2.	El sistema muestra los detalles de la oferta.
3.	El candidato selecciona la opción de presentar candidatura.
4.	El sistema comprueba si el candidato ya ha presentado una candidatura a esa oferta.
5.	Si no existe una candidatura previa, el sistema registra la nueva candidatura con la fecha de presentación y el estado inicial RECIBIDA.
6.	El sistema confirma que la candidatura se ha presentado correctamente.

**Flujo alternativo:**

- Si el candidato ya ha presentado una candidatura a esa oferta, el sistema impide registrar otra y muestra un mensaje informativo.

**Resultado:** La candidatura queda registrada y el candidato puede consultarla posteriormente.

**CU-05: Consulta de candidaturas propias** 

**Actor: Usuario registrado.** 

**Precondición:** El usuario ha iniciado sesión y ha presentado al menos una candidatura.

**Flujo principal:**
1.	El usuario accede al apartado de sus candidaturas.
2.	El sistema recupera las candidaturas asociadas al usuario que ha iniciado sesión.
3.	El sistema muestra las candidaturas, incluyendo la información básica de la oferta, la fecha de presentación y el estado de cada una.

**Resultado:** El usuario puede consultar sus propias candidaturas y conocer el estado de cada una. El sistema impide que acceda a las candidaturas de otros usuarios.

**CU-06: Gestión de empresas**

**Actor: Administrador.**

**Precondición:** El administrador ha iniciado sesión y dispone de permisos para gestionar las empresas.

**Flujo principal:**
1.	El administrador accede al apartado de gestión de empresas.
2.	El administrador consulta el listado de empresas registradas.
3.	El administrador selecciona la opción de crear una nueva empresa o una empresa existente para gestionar sus datos.
4.	El administrador introduce o modifica los datos de la empresa y guarda los cambios.
5.	El sistema valida los datos obligatorios y comprueba que sean correctos.
6.	El sistema guarda los cambios y actualiza la información de la empresa.

**Resultado:** La empresa queda registrada o actualizada correctamente y puede asociarse a las ofertas correspondientes. Las empresas no acceden directamente a la plataforma ni gestionan sus propios datos.

**CU-07: Consulta administrativa de candidaturas**

**Actor: Administrador.**

**Precondición:** El administrador ha iniciado sesión y dispone de permisos para gestionar las candidaturas.

**Flujo principal:**
1.	El administrador accede al apartado de gestión de candidaturas.
2.	El sistema muestra las candidaturas recibidas, junto con la información básica del candidato y de la oferta correspondiente.
3.	El administrador selecciona una candidatura para consultar sus detalles.
4.	El administrador actualiza el estado de la candidatura, seleccionando uno de los estados disponibles: RECIBIDA, EN_REVISION, CONTACTADA o DESCARTADA.
5.	El sistema valida y guarda el nuevo estado de la candidatura.

**Resultado:** La candidatura queda registrada con su estado actualizado y el candidato puede consultar dicho estado desde su cuenta. Las empresas no acceden directamente a la plataforma ni gestionan las candidaturas.

### 2.3. Alcance del MVP 

**Incluido:** 

- Registro e inicio de sesión de candidatos.
- Control de acceso basado en roles: candidato y administrador.
- Consulta pública del listado de ofertas y sus detalles.
- Gestión de ofertas por parte del administrador: creación, edición, publicación y desactivación.
- Gestión administrativa de los datos básicos de las empresas.
- Presentación de candidaturas por parte de los candidatos registrados.
- Consulta de las candidaturas propias.
- Consulta administrativa de las candidaturas recibidas por parte del administrador.
- Gestión del estado de las candidaturas por parte del administrador.
- Consulta del estado de las candidaturas por parte de los candidatos.
- Prevención de candidaturas duplicadas.
- Base de datos relacional normalizada en tercera forma normal (3FN).
- Validaciones de datos, control de permisos y gestión básica de errores.
- Integración del frontend con el backend mediante una API REST.
- Pruebas funcionales de las operaciones principales.
- Despliegue de la aplicación con acceso mediante HTTPS.

La información de cada oferta incluye, como mínimo, título, descripción, requisitos, ubicación, tipo de oportunidad y estado de publicación. Se incluyen los campos básicos necesarios para identificar y fechar las publicaciones.

La información de las empresas se limita a los datos necesarios para identificarlas y relacionarlas con sus ofertas. No se implementa un panel de gestión empresarial.

La búsqueda avanzada, los filtros múltiples y los perfiles profesionales completos quedan fuera del alcance de la primera versión.

El objetivo del proyecto es disponer de una versión funcional del MVP antes del 10 de diciembre de 2026, reservando tiempo para realizar pruebas, corregir errores y preparar la entrega del Hito 3.

**Fuera del MVP:**

- Registro y gestión autónoma de empresas.
- Publicación y gestión de ofertas por parte de las empresas.
- Perfiles profesionales completos con competencias, tecnologías y proyectos.
- Gestión de procesos de selección con flujos de estados avanzados y transiciones automatizadas.
- Búsqueda avanzada y filtros por múltiples criterios.
- Integración con la API de GitHub.
- Sistemas automáticos de recomendación o puntuación de afinidad.
- Verificación automática de competencias.
- Mensajería, videollamadas y notificaciones avanzadas.
- Sincronización de calendarios.
- Gestión de procesos completos de contratación y firma de contratos.
- Integraciones con otros portales de empleo.
- Aplicaciones móviles nativas.

Estas funcionalidades quedan fuera del alcance inicial del proyecto y se reservan para posibles ampliaciones posteriores a la finalización, las pruebas y el despliegue del MVP.

---

## 3. Entidades de negocio tentativas 

- **Usuario:** almacena los datos de acceso y el rol de cada usuario, distinguiendo entre candidatos y administrador.

- **Empresa:** recoge los datos básicos de las empresas asociadas a las ofertas.

- **Vacante:** contiene la información de las ofertas de empleo junior y prácticas profesionales, incluyendo su descripción, requisitos, ubicación y estado de publicación.

- **Candidatura:** registra la inscripción de un candidato en una vacante, junto con la fecha de presentación y el estado de la candidatura.

- **Localidad:** mantiene las localidades en las que se encuentran las oportunidades publicadas.

- **TipoOportunidad:** clasifica las vacantes según su modalidad, inicialmente empleo junior o prácticas profesionales.

**Relación transaccional principal prevista:** Usuario (candidato) ↔ Vacante, mediante Candidatura, que registra la inscripción del candidato en una vacante y permite consultar y actualizar el estado de dicha candidatura.

**Nota:** el diagrama Entidad-Relación en 3FN se entrega en el Hito 2.

---

## 4. Stack tecnológico previsto 

- **Motor de base de datos: MySQL**
  
Se utiliza para almacenar los usuarios, las empresas, las localidades, los tipos de oportunidad, las vacantes y las candidaturas. Es adecuado para el modelo relacional y permite definir claves primarias, claves foráneas, restricciones de unicidad y relaciones necesarias para mantener la integridad de los datos.

- **Backend API: Laravel (PHP)**
  
Laravel se encarga de la lógica de negocio, las validaciones, la autenticación, el control de permisos, las operaciones sobre la base de datos y la exposición de una API REST. Su estructura facilita organizar el proyecto y mantener un backend comprensible y mantenible.

- **Frontend: React**
  
React permite desarrollar una interfaz web adaptable a distintos dispositivos. Se utiliza para implementar el listado y el detalle de las ofertas, los formularios de autenticación, la presentación y consulta de candidaturas, la visualización de sus estados y el panel de administración.

- **Comunicación entre frontend y backend**
  
El frontend consume la API REST desarrollada en Laravel. La autenticación y la autorización se implementan mediante mecanismos compatibles con ambas tecnologías, aplicando los controles de acceso en el servidor para impedir operaciones no autorizadas.

- **Control de versiones y organización: Git y GitHub**
  
Git permite mantener un historial de cambios y organizar el desarrollo mediante ramas cuando resulte conveniente. GitHub se utiliza para alojar el repositorio, organizar las tareas mediante un tablero Kanban y ejecutar comprobaciones automatizadas mediante GitHub Actions.

- **Alojamiento previsto: Railway o plataforma equivalente**
  
Se valora un servicio que permita desplegar el backend y la base de datos, así como publicar el frontend, en la misma plataforma o en servicios independientes. La aplicación debe disponer de acceso mediante HTTPS.
La elección definitiva depende de las condiciones, los recursos disponibles y la compatibilidad de los servicios durante el despliegue.

---

## 5. Selección tentativa de Add-ons 

- [ ] Dockerización multicontenedor con Docker Compose (+1.0) 
- [X] Pipeline CI/CD automatizado con GitHub Actions (+1.0) 
- [ ] Almacenamiento desacoplado en AWS S3 / Cloudinary (+0.5) 
- [ ] Pasarela de pagos Stripe en entorno Sandbox con Webhooks (+1.0) 
- [ ] Generación de informes en PDF/Excel en backend (+0.5) 
- [ ] WebSockets / Comunicación en tiempo real (+1.0) 
- [ ] Batería de pruebas automatizadas (>40 % de endpoints) (+1.0) 
- [X] Documentación OpenAPI / Swagger interactiva (+0.5)
