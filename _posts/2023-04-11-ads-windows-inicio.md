---
layout: single
title: Alternate Data Stream (ADS) - inicio 01
excerpt: "Datos ocultos para el bien o para mal, parte 1"
date: 2023-04-11
classes: wide
header:
  teaser: /assets/images/windows/ads-windows-logo.png
  teaser_home_page: true
categories:
  - Investigación
  - infosec
tags:
  - windows
---

![](/assets/images/windows/ads-windows-logo.png)

# **Alternate Data Streams (ADS): conocimientos básicos**

En esta ocasión aprenderemos los fundamentos básicos de un ADS o en español Secuencia de Datos Alternativa. Los ADS son una característica de los sistemas de archivos NTFS (Sistema de Archivos de Nueva Tecnología) de Microsoft Windows. Una secuencia de datos es un flujo de bytes que se asocia con un archivo en un sistema de archivos. Las ADS permiten a los usuarios adjuntar una o más secuencias de datos adicionales a un archivo existente, sin cambiar el tamaño del archivo original.

Lo que debemos de saber antes de leer por completo este post:
> 1. Aprenderemos los conceptos básicos de un ADS. 
> 2. Mostraré un ejemplo básico.
> 3. La segunda parte de este post será ejecutar alguna aplicación a partir de un ADS.
<br><br>

## **1-Utilidades del ADS - para qué son buenos?**
1. **Almacenamiento de metadatos:** Las ADS se pueden usar para almacenar información de metadatos adicionales sobre un archivo, como información de autor, fecha de creación, descripción, etc. Esta información puede ser útil para organizar y buscar archivos.
2. **Almacenamiento de datos relacionados:** Las ADS se pueden usar para almacenar datos relacionados con un archivo, como una hoja de cálculo de Excel que contiene datos adicionales para un informe de proyecto.
3. **Creación de archivos de datos compartidos:** Las ADS se pueden usar para crear archivos de datos compartidos que contengan múltiples archivos relacionados en un solo archivo. Esto puede hacer que sea más fácil compartir y administrar archivos relacionados.
<br>

## **2-Ejemplo - Manos a la obra**
Para crear un ADS legitimo sigamos los siguientes pasos:
> 1. Abrir el CMD (command prompt) o línea de comandos de Windows.
En la línea de comando del CMD debemos crear una carpeta llamada “ejemplo”, para esto utilicemos el comando `mkdir ejemplo`. Nos movemos a dentro de la carpeta con el comando `cd ejemplo`.
>2. Creamos un archivo llamado nota.txt con el texto “texto para el documento txt” y ADS llamado “holaADS”, haciendo uso del CMD de la siguiente manera `echo "texto para el documento txt" > nota.txt:holaADS`
>3. Fin, con esto tenemos un ADS según la utilidad “1. almacenamiento de metadatos” de la lista anterior.

![](/assets/images/windows/ads-windows-001.png)
<br>

## **3-Visualización del ADS**
Intentemos visualizar el ADS con el comando `dir`. Al parecer no nos muestra nada en particular ni sospechoso.
![](/assets/images/windows/ads-windows-002.png)

En cambio, si utilizamos el comando `dir /r` nos muestra que el ADS tiene 32 bytes, sin embargo, el archivo nota.txt tiene 0 byte, ya que en este no hemos escrito nada.
> El comando "dir /r" en Windows muestra una lista de archivos y directorios en la ubicación actual, incluyendo la información de la secuencia de datos alternativos (ADS) asociada con cada archivo. El modificador "/r" significa "mostrar secuencias de datos alternativos" y es útil para identificar y ver información adicional asociada con los archivos.

![](/assets/images/windows/ads-windows-003.png)

En esta fase aún no vemos la cadena de texto introducida en el ADS, para esto utilizaremos powershell con la función `get-item` y `get-content`.<br>
>1. La función "Get-Item" es un cmdlet de PowerShell que se utiliza para recuperar información sobre un elemento específico en un sistema de archivos. La función se utiliza comúnmente para recuperar información de un archivo, un directorio, una clave de registro, un valor de registro, etc.
>2. En PowerShell, "Get-Content" es un cmdlet que se utiliza para leer el contenido de un archivo de texto y devolver su contenido como una serie de objetos de cadena. Es uno de los cmdlets más utilizados en PowerShell para trabajar con archivos de texto y puede ser utilizado para leer y procesar archivos de cualquier tamaño.
![](/assets/images/windows/ads-windows-004.png)
<br>

## **4-Eliminar un ADS**
Podemos hacer uso de dos (2) comandos:
>1. `Clear-Content nota.txt -Stream holaAD`, este comando elimina los datos **asociados** con el ADS.
>2. `Remove-Item nota.txt -Stream holaADS`, eliminar la secuencia **por completo** usando este comando. 
![](/assets/images/windows/ads-windows-005.png)

<br>

> Existen varias medidas que puedes tomar para protegerte del uso malicioso de secuencias de datos alternativas (ADS). Algunas de ellas son:
>1. **(Recomendado)** Mantén actualizado tu software de seguridad: Asegúrate de que tu software de seguridad, como tu antivirus y cortafuegos, estén actualizados y funcionando correctamente para detectar y bloquear archivos maliciosos que utilicen ADS.
>2. (Ser cuidadoso) Deshabilita las ADS en tu sistema de archivos NTFS: Si No necesitas utilizar ADS, puedes deshabilitarlas en tu sistema de archivos NTFS. 
>2. Ejecuta programas de solo fuentes confiables: Descarga y ejecuta programas y archivos solo de fuentes confiables y legítimas. Esto te ayudará a evitar archivos maliciosos que utilicen ADS para ocultarse.

<br>Siguiendo estas medidas, podrás reducir el riesgo de que tu sistema sea comprometido por el uso malicioso de secuencias de datos alternativas (ADS).

<br><br>

**¡Saludos!**

#### Rubén González