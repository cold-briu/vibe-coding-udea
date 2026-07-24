# Bitácora

Registro de sesiones del semillero.

## Sesión 9: 2026-07-22

- **IA Local y Automatización (Presentación de La Alquimia)**
  - **Introducción e Independencia Tecnológica:** La Alquimia (estudiante de Economía de la UdeA) comparte su experiencia en automatización y domótica, destacando las ventajas de ejecutar modelos de IA locales para reducir costos, mejorar la eficiencia y mantener la privacidad de los datos frente a servicios en la nube.
  - **Plataformas de Ejecución Local:** Demostración práctica de Ollama (línea de comandos) y LM Studio (interfaz gráfica que funciona como wrapper de Ollama). Explicación sobre la instalación y carga de modelos (como Gemma 12B), señalando cómo la RAM y el hardware (NPU vs. GPU) condicionan la velocidad (tokens/seg) y la capacidad de razonamiento.
  - **Rendimiento, Benchmarks y Ventana de Contexto:** Generación en vivo de código Python. Discusión sobre el impacto de la ventana de contexto (*context window*) en el uso de RAM al procesar conversaciones extensas o múltiples archivos, y comparativa de costos de hardware (M3, M5, NVIDIA 3060).
  - **Integración del Flujo de Trabajo con OpenCode:** Uso de OpenCode para conectar el editor de código con el modelo local vía API, permitiendo desarrollar proyectos (como páginas web) de forma fluida sin copiar código manualmente.
  - **Agentes Autónomos y Control Remoto con Hermes Agent:** Presentación de Hermes Agent, agente con memoria KV (*Key-Value*) para navegación web, lectura de archivos y ejecución de tareas programadas (reportes). Se mostró su control remoto y envío de notificaciones mediante una pasarela integrada con Telegram.
  - **Infraestructura Híbrida y Economía de Tokens:** Configuración de la capa gratuita de Oracle Cloud (24 GB RAM, 4 vCPU) para modelos livianos (como Bonsai) y estrategia para evitar *rate limits* rotando claves en OpenRouter. La Alquimia destacó que su gasto anual en tokens fue de solo $22 USD.
  - **Siguientes Pasos:** La Alquimia realizará un *pull request* en el repositorio con los enlaces y recursos presentados (Hermes Agent, OpenRouter, Oracle Cloud).

## Sesión 8: 2026-07-15

- Nueva ronda de presentaciones por la llegada de Zurley

- Edison nos cuenta que para el proximo semestre no estará disponible el LIS, nos cuenta que tiene una TITAN nvidia en disposicion para el semillero.

- Juanda presenta [Medebooks](https://medebooks.vercel.app/). La hizo en 36 horas contando con el limnite de Tokens. Claude pudo tomar al data de ArcGis usando sus propias capacidades. [Repositorio](https://github.com/juandaveth/medebooks) 

    - Juanda habla sobre el SaasPocalypse.

    - Presenta diapositivas [De producto a Metodo](https://canva.link/lga7tb1yiiecnp2)

    - Presenta el problema "como replicar el flujo de trabajo en diferentes modelos cuando se acaban los tokens.

    - La Alquimia introduce el concepto de Agent As a Service

    - Flujo de trabajo:

        1. Pedirle a claude que lo entreviste. 
        2. Perfilar mejor al usuario real.
        3. Gratis primero. "No voy a gastar en un dominio sin que esto genere antes. El [blog](https://medebooks.vercel.app/blog/como-construi-medebooks-con-claude-code) documenta con mas detalle.
        4. Pedirle a claude explicaciones exahustivas para entender mejor lo que se está creando.


    - Juan hace énfasis en el modelo de negocio de las empresas de IA y como su modelo de suscripción está subsidiado y no es sostenible.

    - Recomendado, fluid voice para interactuar por voz con claude.

    - Invita a cosntruir en publico y documentar en codigo abierto.

- Se sostiene conversacion sobre los retos para tener codigo de AI que sea legible.

- Jackie menciona claude cowork y como usa su gestor de tareas para optimizar los promps que ingresa a claude code a traves de vs code.

- La Alquimia comparte un link de referido para google ai pro de 4 meses gratis.

## Sesión 7: 2026-06-10

- Juan David presenta las diferencias conceptuales entre MCP, Skills y Roles.

- Edison destaca la importancia de pensar en cómo reproducir los resultados obtenidos con IA. Queda pendiente para Juan David revisar y documentar cómo Claude generó la presentación.

- Santiago comenta cómo el vibecoding se está democratizando al punto de hacerse desde el celular.

- Yuri comparte su experiencia desarrollando en una empresa: construyó una aplicación en Flutter en 5 días, un proceso que antes tomaba meses. La lanzaron rápidamente a un grupo de WhatsApp de 400 gestores turísticos. Las 45 primeras descargas sobrecargaron el backend desplegado en un Droplet — un buen problema para tener al inicio. La IA ayudó a solucionar el problema de escala directamente en el servidor.

- Yuri también presenta [RASA](https://legacy-docs-oss.rasa.com/docs/rasa/), el framework de NLP con el que trabajó su equipo. Explicó su arquitectura:

  - **Intents**: definen la intención del usuario (ej. "balance"). RASA permite visualizar la distancia lingüística entre ejemplos de un mismo intent — mostraron el caso con vocabulario del sector turístico (RNT - Registro Nacional de Turismo).
  - **stories.yml**: reglas que rigen el flujo de conversación a partir de los intents.
  - **responses.yml**: respuestas asociadas a cada flujo.
  - **actions.yml**: conecta el chatbot con el backend, donde vive la lógica de negocio. La comunicación con las bases de datos se hace a través de sockets.
  - El equipo analiza las preguntas reales de los gestores turísticos para refinar y clasificar los intents.
  - Demo de los comandos `rasa train` y `rasa shell` para entrenar el modelo y probarlo en consola.

- Edison propone la posibilidad de participar en el [Gemini X Prize](https://www.geminixprize.com) y lanza la pregunta al grupo.

## Sesión 6: 2026-05-27

- **Introducción a RAG y Predicción de Tokens**
  - Explicación de la arquitectura RAG (Retrieval-Augmented Generation) como método para inyectar contexto externo a los modelos de lenguaje.
  - Análisis por parte de Andrés sobre la mecánica fundamental de los LLMs: cómo los modelos calculan probabilidades para predecir el token más cercano/probable en una secuencia de texto.
- **Orquestación Visual con FlowiseAI**
  - Revisión de [FlowiseAI](https://flowiseai.com/) como herramienta de código abierto y ejecución local para coordinar múltiples agentes en una sola interfaz.
  - Exploración de las herramientas clave dentro del ecosistema de Flowise:
    - **Chatflows:** Diseños secuenciales para flujos de conversación e interacciones guiadas.
    - **Agentflows:** Configuración avanzada de agentes autónomos con toma de decisiones complejas.
    - **Marketplaces:** Uso de plantillas (*templates*) preconfiguradas y públicas de la comunidad para acelerar el desarrollo.
  - Discusión sobre el cambio de paradigma: pasar de trabajar saltando entre múltiples ventanas simultáneas a centralizar tareas mediante flujos de agentes automatizados.
  - Invitación abierta al semillero para experimentar con la construcción y ensamble visual de pipelines de RAG dentro de FlowiseAI https://github.com/flowiseai/flowise
- **Modelos Open Source y Contenido Multimedia**
  - Debate sobre los casos de uso actuales para la producción audiovisual utilizando modelos alojados en Hugging Face (considerado el "GitHub de los modelos de IA").
- **Casos de Éxito y Aplicaciones de Negocio (Presentación de Santiago)**
  - **Oportunidad de Mercado:** Análisis de la creación e implementación de RAGs personalizados como un modelo de negocio de alto valor para empresas que necesitan consultar de forma privada sus propios datos históricos y operativos.
  - **RAG + LMS:** Demostración práctica de un sistema RAG desarrollado por Santiago para un cliente real, integrado con un proyecto de *Learning Management System* (LMS) orientado a optimizar la capacitación y procesos en empresas.
  - **Sintaxis y CLI:** Muestra de cómo estructurar información mediante archivos YAML para mantenerla en un formato legible por humanos y procesable por máquinas. Santiago mostró el desarrollo de una interfaz de línea de comandos (CLI) que permite interactuar con toda esta documentación de procesos directamente desde la terminal, conviviendo con los formatos tradicionales de Google Docs.
  - **Monitoreo de Costos:** Santiago mostró la extensión de [AI Usage](https://chromewebstore.google.com/detail/cciheeifdkaaocckeeefebhhhkaecpmm?utm_source=item-share-cb) para auditar y visualizar en tiempo real el consumo de tokens gastados en la ejecución de los modelos.
- **Línea de Investigación: Lenguajes Sintéticos y Optimización de Tokens**
  - Origen del debate: Ejercicio práctico donde Andrés instruyó al modelo usando *"Caveman English"* (inglés de cavernícola), evidenciando cómo la reducción de complejidad gramatical optimiza drásticamente el consumo de tokens.
  - Formulación de pregunta de investigación por parte del Profe Edison: *¿Cómo pueden los agentes de IA diseñar y adoptar sus propios lenguajes o protocolos de comunicación sintéticos para maximizar la compresión semántica y minimizar los costos de tokens en entornos multi-agente?*
- **Proyección Estratégica (Próximo Semestre)**
  - Propuesta del Profe Edison para introducir el uso básico de [n8n](https://n8n.io/) en el siguiente ciclo. Esto permitirá a los asistentes dominar la lógica de automatización tradicional y comprender mejor las ventajas y la potencia de herramientas nativas de IA como FlowiseAI.

## Sesión 5: 2026-05-20

- **Visión Estratégica (Próximo Semestre)**
  - Propuesta del Profe Edison para estructurar el Semillero como un grupo exclusivo por invitación.
  - Debate sobre la gestión del tiempo y la viabilidad de extender la duración de las sesiones más allá de una hora (planteado por Santiago).
  - Enfoque en rutas en aprendizaje a través de los cursos oficiales de Claude.
- **Discusión Técnica y Referencias**
  - Análisis del consumo de tokens y el futuro de la infraestructura de IA basado en el ensayo [Situational Awareness](https://situational-awareness.ai/).
  - Introducción a la metodología *Spec-Driven Development* (SDD) mediante el repositorio curado [Awesome Spec-Driven Development](https://github.com/Engineering4AI/awesome-spec-driven-development).
  - Exploración de [agents.md](https://agents.md/) como una fuente de referencia clave para consultar otros ejemplos prácticos de flujos de trabajo (*workflows*) de agentes estructurados en Markdown.
  - Revisión del framework [BMAD Method](https://github.com/bmad-code-org/BMAD-METHOD?tab=readme-ov-file#readme), enfocado en la orquestación de agentes para la creación de agencias de desarrollo autónomas.
  - Estudio de caso práctico del repositorio de **Gotalab**, analizando el flujo de trabajo para desglosar features (*Break down a large initiative*) en su guía de documentación técnica [spec-driven.md](https://github.com/gotalab/cc-sdd/blob/main/docs/guides/spec-driven.md).
- **Líneas de Investigación Propuestas**
  - **Optimización Sintáctica:** Análisis comparativo de eficiencia en consumo de tokens y precisión estructural entre formatos YAML y Markdown (`.md`).
  - **Agentes de Validación:** Estudiar la necesidad de "Agentes Supervisores" en circuitos cerrados de retroalimentación para auditar la precisión del código en SDD. Podemos vernos en casos donde un agente complique el trabajo, antes de hacerlo bien.
  - **Taxonomía de Agentes (Vibecoding Core):** Delimitación conceptual y operativa entre un *skill*, un *MCP (Model Context Protocol)* y un *Role*.
- **Filosofía y Cultura**
  - Reflexión sobre [The Way of Code](https://wayofcode.com/) (inspirado en Rick Rubin), adoptando el rol del programador actual como un productor creativo y editor de contexto. Esta discusión siembra la semilla para el futuro **Manifiesto de Vibecoding UdeA**.
- **Tareas y Siguientes Pasos**
  [ ] Definir criterios de selección para el formato por invitación.
  [ ] Evaluar el nuevo horario para las sesiones prácticas.
  [ ] Diseñar el entorno de pruebas para experimentar con las líneas de investigación planteadas.

## Sesión 4: 2026-05-13

- Hablamos sobre google dev exper talk, agentic flutter y angular. Aula 21 - 326 ingeniera 20 junio 10 am a 2 pm

> Enviar logo universidad para que ellos compartan comunicaciones y mandar correo oficial a facultades. 

- Sandusky expone su flujo de trabajo creando el curso de programacion creativa : artilugiotaller.com

## Sesión 3: 2026-05-06

- Merge del PR de Dani donde explica el flujo de trabajo para la creación de material de estudio.

- Santiago presenta su flujo de trabajo para creacion de prototipos

- Primer caso, Lorenz AI en clude design, articulando Google Stich, Gemini y Claude Design

- Caso: Sistema de control de redes contra incendios, articulando Figma, Gemini y Claude Design.

- Idea: Taller sobre economia de tokens

- Se presenta Erix y GDC Colombia, vistazo a como funciona GDC

- Nos presenta las proximas actividades de GDC Colombia.

- Hablamos sobre las posibilidades para realizar un evento de "Build with AI" en la universidad.

- Quedamos pendientes de coordinar fecha y logística para el evento de "Expert talks" en la universidad para no cruzar con examenes finales.

- Erix nos habla sobre como se usa la IA en Mercado Libre desde su experiencia persona: Usan SDD; Skills, MCP, todo con Claude Code exclusivamente. La IA es requisito dentro de la compañía. Orquestan equipos de agentes para desarrollar segun responsabilidades.

- Meli usa diferentes plantilla de SDD.

    - La primera desarrolla planes donde el agente hace preguntas al product owner.
    - La segunda plantilla detalla las espeficaciones de tecnologia.
    - La tercera plantilla incluye los detalles de la especificacion para cada feature. 
    - Para aceptar el codigo, usan skills en claude para diferentes plataformas, para android por ejemplo un skill que presenta los criterios de aceptacion adaptados a android. Asegurando buenas practicas, uso del framework, seguridad, etc.

- Pendiente: Coordinar taller de google dev experts sobre creacion de agentes con gemini.

## Sesión 2: 2026-04-29

- Andrés Presenta brevemente el programa de google dev community : https://developers.google.com/community/build-with-ai y sugire la posibildiad de organizar una meetup en la universidad.

- Daniel nos muestra su flujo de trabajo creando clases: Numeros transfinitios con Latex y ondas gravitatorias con Jupyter + python. Importante: documentar sus prompts en la carpeta de repo. Uso de copilot desde github directamente en el navegador. Otras herramientas usadas Prism. Importante: La universidad ofrece copilot junto a github education.

- Edison comenta la idea de un orquestador de modelos que separe labores entre diferentes modelos.

- Daniel dice que le gustarpia crear flujos de trabajo mas elaborados y que no sea simplemente enviar prompts.

## Sesión 1: 2026-04-22

- Introducción al programa.
- Presentación de asistentes.
- Acuerdo de flujo de trabajo: Trunk-based en GitHub con PR's.
- Propuesta de trabajo: Estructura de carpetas individuales en `proyectos/`.
