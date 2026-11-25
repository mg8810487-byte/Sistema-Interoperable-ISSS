🏥 Sistema Interoperable de Registro de Salud Electrónico (EHR) bajo el estándar HL7 FHIR
Caso de estudio: Instituto Salvadoreño del Seguro Social (ISSS)

Proyecto académico desarrollado para la materia Gestión de Proyectos Informáticos Universidad Pedagógica de El Salvador (UPED) · Docente: Ing. Julio Menéndez · Grupo N° 2

📌 ¿Qué es este proyecto? a

El ISSS gestiona el historial clínico de sus derechohabientes de forma fragmentada: cada hospital, unidad médica y clínica comunal opera con sistemas propios, formatos distintos o incluso registros en papel. Cuando un paciente es referido a otro establecimiento, su historial no viaja con él.

Este proyecto propone una plataforma central interoperable basada en HL7 FHIR R4 que conecta los sistemas actuales sin reemplazarlos, traduciendo sus datos a un formato común para que el historial clínico pueda consultarse de forma segura en toda la red.

El problema
Impacto	Descripción
⏱️ Tiempo	Retrasos por reconstrucción manual de antecedentes
💰 Costo	Exámenes de laboratorio e imagenología repetidos innecesariamente
⚠️ Riesgo	Decisiones clínicas con información incompleta

Causa raíz: ausencia de un sistema de registro de salud electrónico interoperable que centralice y estandarice el intercambio de información clínica entre los establecimientos.

Objetivo general

Implementar un EHR interoperable bajo FHIR en el ISSS durante julio–diciembre 2026, que permita centralizar, estandarizar, almacenar y consultar de forma segura el historial clínico, facilitando el intercambio de información entre establecimientos.

Métricas de éxito
✅ Integrar 3 a 5 establecimientos piloto
✅ Al menos 95 % de intercambios correctos
✅ Consulta del historial en menos de 5 segundos
✅ Disponibilidad del sistema de 99.9 %
🧩 Subsistemas
#	Subsistema	Propósito
1	Gestión de Identidad y Accesos	Autenticación y control de acceso por rol (RBAC) y establecimiento
2	Índice Maestro de Pacientes (MPI)	ID clínico único por derechohabiente y deduplicación de expedientes
3	Historial Clínico Unificado	Línea de tiempo única de atenciones, diagnósticos y tratamientos
4	Interoperabilidad e Intercambio	Adaptador FHIR R4, referencias/traslados e integración de exámenes
5	Trazabilidad, Auditoría y Alertas	Bitácoras inalterables y alerta de exámenes duplicados

Fuera del alcance (fases posteriores): integración con toda la red nacional, telemedicina y recetas electrónicas interinstitucionales.

🛠️ Stack tecnológico
Componente	Tecnología	Plan B
Estándar y servidor FHIR	HL7 FHIR R4 + HAPI FHIR Server (Java)	Medplum / servidor ligero Node.js
Base de datos	PostgreSQL (JSONB)	MongoDB
Backend y adaptadores	FastAPI (Python) / Node.js	Express.js / .NET Core
Integración con sistemas legados	Mirth Connect	Scripts ETL en Python
Frontend (portal clínico)	React + Tailwind CSS	Vue.js / HTML5 + Bootstrap
Seguridad	SMART on FHIR (OAuth2 + OpenID Connect)	JWT personalizado con RBAC
🗓️ Fases del proyecto

Metodología híbrida: bloques secuenciales con hitos institucionales fijos (predictivo) e iteraciones cortas de integración por establecimiento (adaptativo).

🔹 Bloque 1: Análisis y Diseño (Julio – Agosto 2026) ✅ Finalizado

Qué se hizo:

Definición del problema con análisis de causa raíz (5 porqués) y declaración formal
IT Project Canvas (resumen ejecutivo) y Acta de Constitución del Proyecto
División del sistema en 5 subsistemas
Levantamiento de requerimientos funcionales y técnicos
Justificación del stack tecnológico, viabilidad y Plan B
Diseño de la arquitectura FHIR R4 y definición de los recursos a implementar
Determinación de costos y presupuesto
Cronograma, matriz RACI, matriz de riesgos y estimación ágil (Story Points)
Prototipo de alta fidelidad en Figma (búsqueda por DUI, línea de tiempo del historial, alertas de exámenes duplicados)
🔹 Bloque 2: Desarrollo (Septiembre – Octubre 2026)

Qué se hizo / se hará:

Desarrollo del servidor central FHIR sobre PostgreSQL
Desarrollo del backend y del frontend (portal de consulta interinstitucional)
Desarrollo de un adaptador por cada establecimiento piloto para sistemas legados
Configuración de autenticación RBAC y cifrado
Holgura prevista: +2 semanas por heterogeneidad de sistemas legados
🔹 Bloque 3: Pruebas de Interoperabilidad (Noviembre 2026)

Qué se hará:

Pruebas de intercambio de recursos FHIR entre establecimientos (conformidad HL7 FHIR R4)
Pruebas de seguridad y certificación UAT
Capacitación del personal piloto
Verificación de KPIs (disponibilidad, tiempo de respuesta, tasa de intercambio)
Holgura prevista: +1 semana
🔹 Bloque 4: Despliegue (Diciembre 2026)

Qué se hará:

Despliegue piloto con transición en paralelo durante 15 días (se descarta el "Big Bang")
Plan de cutover en 9 pasos y go-live con monitoreo en vivo
Hipercare: soporte presencial intensivo durante 2 semanas
Evaluación de resultados y plan de expansión
💵 Presupuesto
Rubro	Monto (6 meses)
Desarrollo e integración FHIR (sueldos del equipo)	$54,000
Infraestructura y servidores	$2,880
Seguridad e interoperabilidad	$4,050
Capacitación y gestión del cambio	$4,300
Subtotal	$65,230
Reserva de contingencia (10 %)	$6,523
Total aproximado	≈ $71,750
⚠️ Riesgos principales
Riesgo	P	I	R	Respuesta
Corrupción/incompatibilidad de datos legados al transformar a FHIR	4	4	16 (Crítico)	Holgura de 2 semanas + contingencia
Ataque DoS o fuga de datos en el servidor FHIR	2	5	10 (Alto)	TLS, auditoría de seguridad
Resistencia del personal médico al nuevo portal	3	3	9 (Medio)	Talleres y campeones clínicos
🔐 Seguridad y gobernanza

Alineada con ISO/IEC 27002 (antes ISO/IEC 17799):

Control de acceso por roles y centro de adscripción
Bitácoras inalterables (usuario, DUI consultado, fecha, hora y acción)
Cifrado en tránsito (HTTPS/TLS 1.3 + VPN) y en reposo
📊 Control del proyecto

Se monitorea con tres indicadores: SPI (tiempo), CPI (costo) y cumplimiento de hitos, además de reuniones semanales, informe mensual a la Gerencia de Informática, control de cambios (CCB) y uso de la contingencia como primera respuesta ante desviaciones.

👥 Equipo y contribución
Integrante	Rol	Responsabilidad principal	Contribución
Christian Josué López Rivas	Líder de Proyecto	Coordinación general, comunicación con el docente, plan de despliegue y gestión del cambio, cronograma y control del avance	18 %
Melvin Alexander García Ramos	Analista Funcional	Requerimientos funcionales, definición del problema, casos de uso	17 %
Fernando Miguel Elías Soriano	Arquitecto de Interoperabilidad	Arquitectura FHIR R4, requerimientos técnicos, mapeo de recursos y adaptadores	18 %
Josué Jared De León García	Desarrollador Backend	Diseño del servidor FHIR, adaptadores de integración y base de datos	17 %
Diana Damaris García Medina	Desarrolladora Frontend	Prototipo en Figma y diseño del portal de consulta interinstitucional	15 %
Manuel Armando Vásquez Trujillo	Encargado de Seguridad y Calidad	Requerimientos de seguridad, plan de pruebas, matriz de riesgos y autenticación RBAC	15 %
		Total	100 %
Gráfico de contribución
Christian  ██████████████████  18 %
Fernando   ██████████████████  18 %
Melvin     █████████████████   17 %
Josué      █████████████████   17 %
Diana      ███████████████     15 %
Manuel     ███████████████     15 %
