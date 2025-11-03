# 🛡️ Mini SOC en Splunk

**Proyecto personal**: Implementación de un Mini SOC con Splunk.
Objetivo: Diseñar dashboards para la detección y visualización de intentos de inicio de sesión fallidos, analizando métricas por dirección IP y usuario.

La implementación se realizó sobre un servidor Ubuntu Server 22.04 con Apache, generando eventos reales mediante sesiones SSH simuladas.

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

## 📊 Vista del dashboard en Splunk

![Dashboard del Mini SOC](https://raw.githubusercontent.com/renbor/mini-soc-splunk/refs/heads/main/assets/dashboard_overview.png)

---

## ⚙️ Ejemplos de búsquedas (SPL)

**Detección de accesos fallidos por usuario:**
```spl
index=main source="/var/log/auth.log" "Failed password"
| rex "from (?<src>\d+\.\d+\.\d+\.\d+)"
| top limit=10 src

