1. ¿Por qué necesitamos Loki además de Prometheus si ya tenemos /metrics?
Loki se enfoca en el almacenamiento de los logs mientras Prometheus recolecta y almacena metricas no logs

2. ¿Qué ventaja aporta que las fuentes de datos de Grafana estén aprovisionadas como código y no creadas a mano?
Puedes automatizar y desplegar con mayor facilidad en vez de dar clicks a una interfaz 

3. El panel "CPU contenedor" y el panel "CPU host" pueden mostrar valores muy distintos. ¿Por qué? ¿Cuál usarías para alertar sobre una aplicación concreta?
El CPU contenedor mostrara el % que consume el contenedor mientras que CPU host representa el consumo general de todo el servidor. Usaria CPU contenedor pues muestra el consumo especifico de una aplicación

4. ¿Qué diferencia hay entre el evaluation interval y el pending period de una alarma?
La evaluation interval es el intervalo de tiempo en el que se volvera a evaluar la alarma mientras que el pending period es el tiempo que debe cumplirse antes que la alerta cambie de estado a firing
