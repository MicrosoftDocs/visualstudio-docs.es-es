---
title: "C&#243;mo: Instalar el generador de perfiles independiente | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "herramientas de rendimiento, instalar el generador de perfiles independiente"
  - "herramientas de generación de perfiles, generador de perfiles independiente"
ms.assetid: cae81c95-83cd-4ab6-8a98-84ef977a2f6d
caps.latest.revision: 24
caps.handback.revision: 24
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# C&#243;mo: Instalar el generador de perfiles independiente
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] proporciona un generador de perfiles independiente basado en la línea de comandos que se puede ejecutar sin instalar el IDE de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Esta situación se produce cuando un equipo no tiene o no puede tener instalado un entorno de desarrollo.  Por ejemplo, no se debe instalar un entorno de desarrollo en un servidor web de producción.  
  
> [!NOTE]
>  Cuando se utiliza el generador de perfiles independiente para recopilar los datos de rendimiento del sitio web ASP.NET, se recomienda la herramienta de línea de comandos [VSPerfASPNetCmd](../profiling/vsperfaspnetcmd.md) frente a la herramienta [VSPerfCmd](../profiling/vsperfcmd.md).  
  
### Para instalar el generador de perfiles independiente  
  
1.  Busque el instalador del generador de perfiles independiente \(vs\_profiler.exe\) en el disco de instalación de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], en el directorio que incluye la ruta de acceso \\Standalone Profiler, y ejecútelo.  
  
2.  Agregue a la ruta de acceso del sistema las rutas de acceso de vsintr.exe y msdis150.dll.  
  
    > [!NOTE]
    >  En la instalación predeterminada de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], vsinstr.exe y msdis150.dll se encuentran en \\Archivos de programa\\Visual Studio 10\\Team Tools\\Performance Tools.  
  
3.  En el símbolo del sistema, escriba **VSInstr**.  
  
    > [!NOTE]
    >  Si se muestra la información de uso de vsinstr.exe, todo está instalado correctamente.  Si observa un error que indica que no se encuentra vsinstr.exe o una de sus dependencias, asegúrese de haber configurado correctamente las rutas de acceso de acuerdo con el paso 2.  
  
4.  Configure el servidor de símbolos estableciendo la variable **\_NT\_SYMBOL\_PATH** en **symsrv\*symsrv.dll\*c:\\localcache\*http:\/\/msdl.microsoft.com\/download\/symbols**  
  
5.  Después de configurar el servidor de símbolos mediante las variables de entorno del sistema, ejecute las herramientas de generador de perfiles de la línea de comandos en un nuevo símbolo del sistema.  De este modo, las nuevas variables de entorno surtirán efecto.  En la ventana del símbolo del sistema, escriba el siguiente comando:  
  
     **start %COMSPEC%**  
  
    > [!NOTE]
    >  Para obtener instrucciones detalladas sobre cómo configurar el paquete del servidor de símbolos, vea [Cómo: Hacer referencia a información de símbolos de Windows](../profiling/how-to-reference-windows-symbol-information.md).  
  
6.  Utilice la herramienta [VSPerfReport](../profiling/vsperfreport.md) para serializar los símbolos en el archivo de datos de generación de perfiles \(.vsp\).  Utilice los modificadores de **VSPerfReport \/summary:all \/packsymbols**.  Si no hay símbolos insertados en el archivo de datos, asegúrese de que tiene configurada la variable de entorno \_NT\_SYMBOL\_PATH.  
  
## Vea también  
 [Generación de perfiles desde la línea de comandos](../profiling/using-the-profiling-tools-from-the-command-line.md)   
 [Tutorial: Generar perfiles utilizando el método de muestreo en la línea de comandos](../Topic/Walkthrough:%20Command-Line%20Profiling%20Using%20Sampling.md)   
 [Tutorial: Generar perfiles utilizando la instrumentación en la línea de comandos](../profiling/walkthrough-command-line-profiling-using-instrumentation.md)   
 [Cómo: Hacer referencia a información de símbolos de Windows](../profiling/how-to-reference-windows-symbol-information.md)   
 [VSPerfReport](../profiling/vsperfreport.md)