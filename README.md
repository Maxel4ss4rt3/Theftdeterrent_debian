# Theft Deterrent
## Debian Linux (incluye Mint, Ubuntu, Kali, Huayra, etc.)
1. Descargar los 4 archivos que terminan en .deb que están disponibles en este repositorio.
2. En una terminal, van al directorio donde hayan guardado los archivos (generalmente es /home/usuario/Descargas).
3. Instalar la librería con el comando
   ```sudo dpkg -i theftdeterrentclient-lib_6.0.0.11.huayra10_amd64.deb```
5. Instalar el daemon con el comando
   ```sudo dpkg -i theftdeterrentdaemon_6.0.0.11.huayra10_amd64.deb```
7. Instalar guardian con el comando
   ```sudo dpkg -i theftdeterrentguardian_6.0.0.11.huayra10_amd64.deb```
9. Instalar el agente con
    ```sudo dpkg -i theftdeterrentclient_6.0.0.11.huayra10_amd64.deb```
11. Reiniciar (recomendado, opcional)
12. Ejecutar en la terminal el comando ```theftdeterrentclient``` para verificar que se instaló.
13. Ir a la configuración del programa (dentro del mismo) y fijar el servidor a `citd.dgp.educ.ar`.

## Solucion de error de dependencia '(>= python 2.6)'
1. Lo que hice fue extraer el "theftdeterrentguardian_6.0.0.11.huayra10_amd64.deb" con el comando 
```dpkg-deb -R ./theftdeterrentguardian_6.0.0.11.huayra10_amd64.deb guardian``` , dentro de 
./guardian modificar el archivo "control" ubicado en la carpeta 'DEBIAN' (./guardian/DEBIAN/control),
con leafpad o cualquier editor de texto abrir 'control'. 
Nos ubicamos en la linea ```Pre-Depends: python (>= 2.6)```, y modificamos ```python``` por ```python3```
en la condicion ```(>= 2.6)``` a ```(>= 3)``` en mi caso mi version es 3.11.2, y guardar cambios y salir.
2. Nos ubicamos en la carpeta /Descargas y debemos empaquetar ``guardian```, borre el anterior paquete ```theftdeterrentguardian_6.0.0.11.huayra10_amd64.deb```:
	```dpkg-deb -b guardian theftdeterrentguardian_6.0.0.11.huayra10_amd64.deb```
3. Ahora puede instalarlo con el comando del paso 7. Se creara un shorcut en el menu y 
desde ahi podra ejecutarlo 'Theft Deterrent Client', finalmente siga el paso 13.

## Error no se conecta al servidor
1.Si da error servidor, mate los procesos con el comando 
```htop``` referidos a theft (F3.search -> "theft" -> F9 Kill -> 9. SIGKILL). Reinstale el deamon (paso 5),
debe aparecer en la terminal '' server start'' y en ultima linea que inicio un PID.
2. inicie el programa nuevamente, siga el paso 13.

