# Validación de Observabilidad y Alertas

Esta guía describe los pasos necesarios para validar que el entorno de monitoreo local (Métricas, Logs y Alertas) está funcionando correctamente de extremo a extremo.

## 1. Validar las Métricas de Contenedores en Prometheus
1. Ingresa a **Grafana** (`http://localhost:3000`).
2. Dirígete a la pestaña de **Explore** (Explorar).
3. Selecciona la fuente de datos (Data Source) de **Prometheus**.
4. Ejecuta la siguiente consulta PromQL:
   ```promql
   container_cpu_usage_seconds_total{name="lab-backend"}
   ```


## 2. Validar el Monitoreo de Logs Centralizados en Loki
1. Mantente en la pestaña **Explore** de Grafana.
2. Selecciona la fuente de datos de **Loki**.
3. Ejecuta la siguiente consulta LogQL para ver los registros del backend:
   ```logql
   {tier="application"}
   ```
   *(También puedes utilizar `{container="lab-backend"}`)*


## 3. Validar la Configuración de Alertas y Notificaciones (Webhooks)
1. En el menú de Grafana, dirígete a la sección **Alerting** > **Contact points**.
2. Verifica que existe un Contact Point configurado que apunte al webhook del backend (URL: `http://backend:3001/alerts`).
3. Haz clic en el botón **Test** dentro del Contact Point para enviar una alerta simulada.
4. Abre la consola / terminal en tu servidor (o equipo local) y revisa los logs del contenedor backend ejecutando:
   ```bash
   docker logs lab-backend | grep grafana_alert_received
   ```
