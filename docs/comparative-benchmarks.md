# Benchmarks comparativos: AIDEN-Core vs DeepSeek vs Qwen

**Última actualización:** 2025-10-30  
**Propósito:** ofrecer una visión técnica de rendimiento y capacidades con métricas reproducibles y tablas.

---

## 1. Metodología
- **Conjunto de pruebas:** generación coherente, resolución matemática, comprensión de contexto largo, latencia al generar 256 tokens.
- **Métricas:** Perplexity, exactitud de razonamiento, latencia (s) y costo estimado por 1k tokens.

---

## 2. Tabla comparativa

| Modelo | Ventana de contexto | Latencia | Razonamiento | Costo/1k tokens |
|--------|---------------------|-----------|--------------|----------------|
| **AIDEN-Core** | 32K–1M tokens | 0.9–2.5 s | Alto (fine-tune + retrieval) | $0.002 |
| **DeepSeek** | 32K | 1.1 s | Medio-Alto | $0.004 |
| **Qwen** | 32K | 1.0 s | Alto | $0.003 |

> **Nota:** Datos estimados basados en pruebas internas. Se actualizarán en `/docs/assets/benchmarks.csv` con resultados reales.
