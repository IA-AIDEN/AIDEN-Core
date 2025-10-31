# Arquitectura conceptual — AIDEN Core

**Resumen:**  
Este documento describe la arquitectura lógica y de componentes del modelo central *AIDEN-Core* y su ecosistema (AIDEN One, AIVA, AIDEN Azul Deep, AIDEN API Azul Dark). Diseñada para priorizar interacción por voz, memoria contextual y escalabilidad empresarial.

---

## 1. Visión general del sistema
- **Frontend (Interfaz de Contexto):** Web / Móvil / Widgets embebidos. Entrada principal: voz (STT) + texto. Salida: texto + TTS.
- **Controlador de diálogo y orquestador (Runtime):** Maneja turnos conversacionales, contexto, managers y mixer.
- **Modelos LLM (AIDEN-Core):** Núcleo de generación y razonamiento (tokens, contexto).
- **Subsistemas especializados:**
  - **NLP + Razonamiento** (razonamiento extendido, chain-of-thought control)
  - **Memoria / Vector DB** (store/retrieve de contexto, embeddings)
  - **Módulo de Personalización** (per-user profiles, tonos, preferencias)
  - **Módulo de Voz** (STT ↔ TTS, prosodia y control emocional)
  - **API / Integraciones** (endpoints para Managers, Mixer y clientes empresariales)
- **Infra & Orquestación:** Autoscaling, autenticación, metrica y auditoría.

---

## 2. Diagrama lógico (placeholder)
> **Insertar aquí:** `/docs/assets/architecture-diagram.png`  
(Áreas: Frontend → Orquestador → LLM + Memory → TTS/STT → API)

---

## 3. Componentes clave y responsabilidades

### 3.1 Orquestador de diálogo
- Enruta entrada (voz/texto).
- Normaliza prompts, aplica system prompts y safety filters.
- Envía a LLM o a módulos especializados.
- Controla contexto y ventana de contexto (cache por sesión).

### 3.2 Motor LLM (AIDEN-Core)
- Generación autoregresiva con control de temperatura, top-k/top-p y penalizaciones de repetición.
- Soporta largos context windows (configurable por modelo).
- Interfaces: sync/async y streaming.

### 3.3 Memoria vectorial
- Embeddings para recuperación semántica.
- Estrategias: recency-weighted, topic-clustering, persona anchoring.

### 3.4 Managers & Mixer (orquestación de habilidades)
- **Managers:** agentes configurables (p. ej. redacción académica).
- **Mixer:** pipeline compositor de múltiples módulos (diseño + código + contenido).

### 3.5 Módulo voz
- STT de baja latencia; pipeline de pos-procesado (punctuation, intent extraction).
- TTS multi-voice, control de prosodia, parámetros emocionales.

---

## 4. Consideraciones de despliegue
- Multi-GPU / offload + offload_folder para shards grandes.
- Monitorización (latencias, errores, costos por token).
- Sistemas de fallback (servicios ligeros) para degradar funcionalidad en picos.

---

## 5. Placeholder: Requisitos no funcionales
- Latencia objetivo: < 1.2s (interacción por voz básica).
- SLA Enterprise: 99.9%
- Seguridad: cifrado en reposo y en tránsito, control por rol.

---

## 6. Próximos pasos (pendientes de documentación técnica)
- Diagrama detallado de componentes con puertos y API.
- Especificación OpenAPI para endpoints del AIDEN API.
- Tests de integración End-to-End.
