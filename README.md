## 🎙️ Módulo de Síntesis de Voz y Diseño Sonoro (Comercio Itinerante)

###**Descripción General**
Este flujo de trabajo implementa un motor de Text-to-Speech (TTS) hiperrealista utilizando la API de **ElevenLabs** integrada directamente en **ComfyUI**. El objetivo principal es generar activos de audio dinámicos para casos de uso comercial (ej. perifoneo para venta de chatarra o helados), operando ComfyUI como un servidor backend que procesa solicitudes mediante formato JSON.

### ⚙️ Arquitectura del Flujo (Nodos Principales)
Para lograr un resultado comercial de alta fidelidad, el circuito se compone de los siguientes módulos lógicos:

1. **Generación Base (`ElevenLabs Texto a Voz`):** * Actúa como el motor principal. Recibe el *prompt* de texto estructurado con signos de puntuación específicos para forzar pausas e inflexiones naturales en el locutor.
   * **Modelo utilizado:** `eleven_multilingual_v2` (Garantiza una pronunciación perfecta en español).
2. **Carga de Ambiente (`Load Audio`):** * Inyecta archivos de audio en formato MP3 que contienen el "Sound Design" o ruido de fondo (ej. sonido de calle, motores o campanas musicales) para dotar de contexto espacial a la voz.
3. **Consola de Mezcla (`Audio Mix / Merge`):** * Nodo matemático que superpone la pista de voz generada por la IA sobre la pista de ambiente, permitiendo ajustar los niveles de volumen para que la locución principal no se pierda.
4. **Exportación (`Save Audio`):** * Compila y guarda el resultado final en un archivo `.mp3` listo para ser reproducido en altavoces externos o perifoneo móvil.

### 🎛️ Parámetros
A diferencia de los TTS convencionales que suenan robóticos o formales, este flujo utiliza "Parámetros" para emular la euforia y el tono de un vendedor real en la calle. Los ajustes clave aplicados son:
* **Estabilidad (Stability) ajustada al `0.25`:** Al reducir este valor, se le otorga libertad al modelo matemático para variar el tono y la emoción, sonando más humano y menos predecible.
* **Exageración de Estilo (Style) ajustado al `0.50`:** Fuerza a la IA a "actuar" el guion en lugar de solo leerlo, ideal para textos con signos de exclamación.

### **Uso y Reproducibilidad**
Para ejecutar este flujo, el usuario debe contar con su propia `API Key` de ElevenLabs configurada en el nodo principal. Al presionar "Ejecutar", el flujo renderiza la mezcla completa en aproximadamente 5 a 10 segundos, demostrando su viabilidad como una solución SaaS de bajo costo computacional local.
