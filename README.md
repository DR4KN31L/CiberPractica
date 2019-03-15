# CiberPractica
Practica Ciberseguridad 2019

---------------------------------------------------------
# Información del exploit FreeFloat FTP Wbem Freefloat v1.0

este exploit lo ha subido sinn3r y juan vazquez (ambos de @metasploit):

esta vulnerabilidad fue encontrada en el servicio de freefloat 1.0, la cual permite a un usuario malicioso
ingresar al sistema que esté corriendo este servicio.
la forma en que el exploit se ejecuta es la siguiento:

  1. No se necesita credencial para iniciar sesión
  2. la ruta predeterminada del usuario está en C: \, y esto no se puede cambiar.
  3. el usuario puede escribir en cualquier parte del sistema de archivos del servidor. Como resultado de estas implementaciones deficientes,     un usuario malintencionado puede simplemente iniciar sesión y luego cargar archivos, y dejar que WMI ejecute la carga útil cargada

El exploit está cargado en la base de datos de metasploit framework, puede ser usado desde allí.
Finalmente, el exploit fue divulgado el 07/12/2012

WebGrafía:

  https://www.rapid7.com/db/modules/exploit/windows/ftp/freefloatftp_wbem
  
Herramientas usadas para la demo:

  nmap y NSE: https://nmap.org/<br>
  metasploitframework: https://www.metasploit.com/

