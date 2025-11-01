# 🛡️ Mini SOC en Splunk

**Proyecto personal:** Mini SOC implementado con Splunk. Objetivo: practicar ingesta, normalización, detección y visualización de eventos de seguridad.

---

## 🎯 ¿Qué incluye este proyecto?
- Dashboards exportados desde Splunk (folder `dashboards/`)
- Búsquedas SPL y correlaciones (folder `searches/`)
- Logs de ejemplo para reproducir (folder `logs_samples/`)
- Capturas de pantalla del dashboard (folder `assets/`)

---

## 🧩 Componentes principales

- **Plataforma:** Splunk Enterprise / Splunk Free
- **Logs simulados:** `auth.log`
- **Visualizaciones:** Dashboard principal con métricas por usuario, por IP, intentos fallidos, tráfico web sospechoso.
- **Alertas:** Búsquedas SPL que detectan condiciones anómalas.

---

## ⚙️ Ejemplos de búsquedas (SPL)

**Detección de accesos fallidos por usuario:**
```spl
index=main source="/var/log/auth.log" "Failed password"
| rex "from (?<src>\d+\.\d+\.\d+\.\d+)"
| top limit=10 src
