---
title: "Usar las herramientas de generaci&#243;n de perfiles desde la l&#237;nea de comandos | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "línea de comandos, herramientas de rendimiento"
  - "herramientas de línea de comandos, herramientas de rendimiento"
  - "herramientas de generación de perfiles, línea de comandos"
  - "herramientas, línea de comandos"
  - "línea de comandos, herramientas"
ms.assetid: 6593fa82-181e-4009-a0ed-02aa24c2c063
caps.latest.revision: 35
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 35
---
# Usar las herramientas de generaci&#243;n de perfiles desde la l&#237;nea de comandos
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Puede usar las herramientas de línea de comandos de las herramientas de generación de perfiles de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] para generar perfiles de las aplicaciones en el símbolo del sistema y automatizar la generación de perfiles mediante el uso de archivos por lotes y scripting.  También puede generar los archivos del informe desde el símbolo del sistema.  Puede usar el generador de perfiles independiente y ligero para recopilar los datos de los equipos que no tienen instalado [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
> [!NOTE]
>  Las características de seguridad mejoradas en Windows 8 y Windows Server 2012 requirieron cambios significativos en la forma en que el generador de perfiles de Visual Studio recopila datos en estas plataformas.  Las aplicaciones de la Tienda Windows también requieren nuevas técnicas de recolección.  Vea [Generar perfiles de aplicaciones de Windows 8 y Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
## Tareas comunes  
  
|Tarea|Contenido relacionado|  
|-----------|---------------------------|  
|**Establecer la ubicación de los símbolos:** para mostrar los nombres de las funciones y parámetros, el generador de perfiles debe tener acceso a los archivos de símbolos \(.pdb\) de los archivos binarios perfilados.  Estos archivos deben incluir los archivos de símbolos del sistema operativo de Microsoft y las aplicaciones que desea ver en su análisis.  Puede usar el servidor público de símbolos de Microsoft para asegurarse de que tiene los archivos .pdb correctos para los archivos binarios de Microsoft.|-   [Cómo: Especificar ubicaciones del archivo de símbolos desde la línea de comandos](../profiling/how-to-specify-symbol-file-locations-from-the-command-line.md)|  
|**Generar un perfil de la aplicación:** las herramientas y opciones de línea de comandos que usa para generar el perfil de una aplicación de destino dependen del tipo de la aplicación, del método de generación de perfiles y de si el destino es una aplicación administrada o nativa.|-   [Usar los métodos de generación de perfiles desde la línea de comandos](../profiling/using-profiling-methods-to-collect-performance-data-from-the-command-line.md)<br />-   [Generar perfiles para aplicaciones independientes](../profiling/command-line-profiling-of-stand-alone-applications.md)<br />-   [Generar perfiles de aplicaciones web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)<br />-   [Servicios de generación de perfiles](../profiling/command-line-profiling-of-services.md)|  
|**Crear informes .xml y .csv:** la generación de perfiles desde el símbolo del sistema crea archivos de datos que pueden verse en la interfaz de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  También puede generar archivos de valores separados por comas \(.csv\) o XML mediante la herramienta de línea de comandos VSPerfReport.|-   [Crear informes del generador de perfiles desde la línea de comandos](../profiling/creating-profiler-reports-from-the-command-line.md)<br />-   [VSPerfReport](../profiling/vsperfreport.md)|  
|**Generar perfiles del código en equipos sin Visual Studio:** puede usar el generador de perfiles independiente de las herramientas de generación de perfiles para recopilar los datos de las aplicaciones de los equipos que no tienen instalado [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].|-   [Cómo: Instalar el generador de perfiles independiente](../profiling/how-to-install-the-stand-alone-profiler.md)|  
  
## Reference  
 [Referencia de las herramientas de generación de perfiles de la línea de comandos](../profiling/command-line-profiling-tools-reference.md)  
  
## Vea también  
 [Uso de las herramientas de generación de perfiles](../profiling/performance-explorer.md)