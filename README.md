# mini-soc-splunk
Proyecto personal de ciberseguridad - Mini SOC implementado con Splunk para detección y monitoreo de eventos.

# 🛡️ Mini SOC en Splunk

Proyecto personal de ciberseguridad enfocado en la construcción de un entorno **SOC (Security Operations Center)** utilizando **Splunk** como SIEM principal.  
El objetivo fue practicar la **ingesta, análisis y detección de eventos de seguridad** a partir de fuentes simuladas de logs.

---

## 🎯 Objetivos

- Crear un entorno funcional de monitoreo de seguridad con Splunk.
- Ingerir y analizar logs simulados de distintos orígenes (auth.log, apache2, firewall).
- Diseñar dashboards y alertas para identificar comportamientos anómalos.
- Practicar la escritura de búsquedas SPL y la generación de visualizaciones.

---

## ⚙️ Arquitectura

| Componente | Descripción |
|-------------|-------------|
| **Splunk Enterprise (Free)** | Plataforma SIEM utilizada para ingesta, análisis y visualización. |
| **Logs simulados** | Archivos generados manualmente o mediante scripts (auth.log, access.log, etc.) |
| **Dashboards** | Panel principal con métricas de accesos, errores, y detecciones sospechosas. |
| **Alertas** | Condiciones SPL configuradas para notificar intentos de acceso múltiples o tráfico inusual. |

---

## 🧩 Ejemplos de detección

**1️⃣ Detección de accesos fallidos por usuario**
```spl
index=demo source="/var/log/auth.log" action=failure 
| stats count by user, src_ip 
| where count > 5
