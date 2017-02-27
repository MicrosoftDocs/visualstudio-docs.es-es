---
title: "Solucionar problemas de las herramientas de generaci&#243;n de perfiles | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0b61cdf7-75b7-4abd-aff2-7bd997717626
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# Solucionar problemas de las herramientas de generaci&#243;n de perfiles
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Al trabajar con las herramientas de generación de perfiles, puede experimentar uno de los siguientes problemas:  
  
-   [Las herramientas de generación de perfiles no recopilan datos](#NoDataCollected)  
  
-   [En las vistas de rendimiento y los informes aparecen números para los nombres de función](#NoSymbols)  
  
##  <a name="NoDataCollected"></a> Las herramientas de generación de perfiles no recopilan datos  
 Después de crear el perfil de una aplicación, no se crea ningún archivo de datos de generación de perfiles \(.vsp\) y aparece la siguiente advertencia en la Ventana de salida o en la ventana Comandos:  
  
 PRF0025: No se recopiló ningún dato.  
  
 Este problema puede deberse a diversos motivos:  
  
-   Un proceso cuyo perfil se generó usando el muestreo o el método de memoria .NET inicia un proceso secundario que resulta ser el proceso que realiza el trabajo de la aplicación.  Por ejemplo, algunas aplicaciones leen la línea de comandos para determinar si se han iniciado como una aplicación Windows o como una aplicación de línea de comandos.  Si se solicitó una aplicación Windows, el proceso original inicia un nuevo proceso configurado como una aplicación Windows y el proceso original termina.  Como las herramientas de generación de perfiles no recopilan automáticamente datos de los procesos secundarios, no se recopila ningún dato.  
  
     Para recopilar los datos de generación de perfiles en este escenario, asocie el generador de perfiles al proceso secundario en lugar de iniciar la aplicación con el generador de perfiles.  Para obtener más información vea [Cómo: Asociar y desasociar el generador de perfiles de los procesos en ejecución](../profiling/how-to-attach-and-detach-performance-tools-to-running-processes.md) y [Attach \(VSPerfCmd\)](../profiling/attach.md)  
  
##  <a name="NoSymbols"></a> En las vistas de rendimiento y los informes aparecen números para los nombres de función  
 Después de crear el perfil de una aplicación, aparecen números en lugar de nombres de función en los informes y las vistas.  
  
 Este problema se debe a que el motor de análisis de herramientas de generación de perfiles no puede encontrar los archivos .pdb que contienen la información de símbolos que se asigna a la información del código fuente, como los nombres de función y los números de línea del archivo compilado.  De forma predeterminada, el compilador crea el archivo .pdb cuando se compila el archivo de la aplicación.  En la aplicación compilada se almacena una referencia al directorio local del archivo .pdb.  El motor de análisis busca el archivo .pdb en el directorio al que se hace referencia y, a continuación, en el archivo que actualmente contiene el archivo de la aplicación.  Si no se encuentra el archivo .pdb, el motor de análisis usa los desplazamientos de las funciones en lugar de los nombres de función.  
  
 Puede corregir el problema siguiendo uno de estos mecanismos:  
  
-   Buscando los archivos .pdb y situándolos en el mismo directorio que los archivos de la aplicación.  
  
-   Insertando la información de símbolos en el archivo de datos de generación de perfiles \(.vsp\).  Para obtener más información, vea [Guardar información de símbolos con archivos de datos de generación de perfiles](../profiling/saving-symbol-information-with-performance-data-files.md).  
  
> [!NOTE]
>  El motor de análisis necesita que el archivo .pdb tenga la misma versión que el archivo de la aplicación compilado.  Un archivo .pdb de una compilación anterior o posterior del archivo de la aplicación no funcionará.