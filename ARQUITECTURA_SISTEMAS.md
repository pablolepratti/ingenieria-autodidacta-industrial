# Arquitectura de sistemas del proyecto

## 1. Sistemas vivos
- **CMMS Fábrica** (Streamlit + MongoDB Atlas)
  - Colecciones: `activos_tecnicos`, `calibraciones`, `tareas_tecnicas`, `observaciones`, `historial`
  - Alineación: ISO 55001, ISO 14224
- **MIA / MIA Lite**
  - Sensores: ESP32 + ADS1115 + ZMPT101B + SCT-013
  - Envío: HTTP/MQTT → MongoDB / InfluxDB
  - Visualización: Grafana / Streamlit

## 2. Relación con los módulos
- **Módulo 0** define el marco y el método autodidacta.
- **Módulo 1** documenta y mantiene activos → escribe en `activos_tecnicos`
- **Módulo 2** calibra y registra → escribe en `calibraciones` y `historial`
- **Módulo 3** prueba hardware / mecatrónica → genera bitácoras en `/Plantillas/03_BITACORA_SENSOR.md`
- **Módulo 4** conecta datos → scripts Python / Streamlit / Mongo
- **Módulo 5** consume esos datos → IA / dashboards
- **Módulo 6** verifica que todo quede documentado → ISO / DIN
- **Módulo 7** integra todo en un sistema funcional

## 3. Flujo de datos
Sensor → ESP32 → HTTP/MQTT → DB (Mongo/Influx) → App (Streamlit) → Registro en `historial` → Informe técnico
