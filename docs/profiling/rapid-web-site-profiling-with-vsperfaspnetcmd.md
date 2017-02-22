---
title: "Generaci&#243;n r&#225;pida de perfiles de sitio web con VSPerfASPNETCmd | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "herramientas de generación de perfiles, VSPerfASPNETCmd"
  - "VSPerfASPNETCmd"
ms.assetid: 9a9d62a6-549a-45ac-a948-76eb98586ac5
caps.latest.revision: 16
caps.handback.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Generaci&#243;n r&#225;pida de perfiles de sitio web con VSPerfASPNETCmd
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La herramienta de línea de comandos **VSPerfASPNETCmd** le permite generar perfiles de aplicaciones web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] con facilidad.  En comparación con la herramienta de línea de comandos [VSPerfCmd](../profiling/vsperfcmd.md), tiene menos opciones, no es necesario establecer variables de entorno ni reiniciar el equipo.  **VSPerfASPNETCmd** es el método preferido para generar perfiles con el generador de perfiles independiente.  Para obtener más información, vea [Cómo: Instalar el generador de perfiles independiente](../profiling/how-to-install-the-stand-alone-profiler.md).  
  
> [!NOTE]
>  Las características de seguridad mejoradas en Windows 8 y Windows Server 2012 requirieron cambios significativos en la forma en que el generador de perfiles de Visual Studio recopila datos en estas plataformas.  Las aplicaciones de la Tienda Windows también requieren nuevas técnicas de recolección.  Vea [Generar perfiles de aplicaciones de Windows 8 y Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
 En algunos escenarios, como la recolección de datos de simultaneidad o la detención y reanudación de la generación de perfiles, **VSPerfCmd** es el método de generación de perfiles preferido.  
  
> [!NOTE]
>  Las herramientas de línea de comandos de las Herramientas de generación de perfiles se encuentran en el subdirectorio \\Team Tools\\Performance Tools del directorio de instalación de [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)].  En equipos de 64 bits, utilice la herramienta VSPerfASPNETCmd situada en el directorio \\Team Tools\\Performance Tools de 32 bits.  Para utilizar las herramientas de línea de comandos del generador de perfiles, debe agregar la ruta de acceso de las herramientas a la variable de entorno PATH de la ventana de símbolo del sistema o agregarla al propio comando.  Para obtener más información, vea [Especificar la ruta de acceso a las herramientas de línea de comandos](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
  
## Generar perfiles de una aplicación ASP.NET  
 Para generar perfiles de una aplicación web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], escriba uno de los comandos que se describen en las siguientes secciones.  Se inicia el sitio web y el generador de perfiles empieza a recopilar datos.  Ejecute su aplicación y, a continuación, cierre el explorador.  Para dejar de generar perfiles, presione la tecla Entrar en la ventana de símbolo del sistema.  
  
> [!NOTE]
>  De forma predeterminada, el símbolo del sistema no vuelve después de un comando **vsperfaspnetcmd**.  Puede utilizar la opción **\/nowait** para obligar al símbolo del sistema a volver.  Vea [Utilizar la opción /NoWait](#UsingNoWait).  
  
## Para recopilar estadísticas de una aplicación mediante el método de muestreo  
 El muestreo es el método de generación de perfiles predeterminado de la herramienta **VSPerfASPNETCmd** y no tiene que especificarse en la línea de comandos.  La siguiente línea de comandos recopila estadísticas de aplicación de la aplicación web especificada:  
  
 **vsperfaspnetcmd**  *websiteUrl*  
  
## Para recopilar datos de tiempo detallados mediante el método de instrumentación  
 Utilice la siguiente línea de comandos para recopilar datos de tiempo detallados de una aplicación web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] compilada de forma dinámica:  
  
 **vsperfaspnetcmd \/trace**  *websiteUrl*  
  
 Si desea generar perfiles de archivos .dll compilados de forma estadística de su aplicación web, debe instrumentar los archivos mediante la herramienta de línea de comandos [VSInstr](../profiling/vsinstr.md).  El comando vsperfaspnetcmd \/trace incluirá datos de los archivos instrumentados.  
  
## Para recopilar datos de memoria de .NET  
 La opción **\/Memory** recopila datos acerca de la asignación de objetos en la memoria de .NET y puede recopilar datos sobre la duración de esos objetos.  La recolección de datos de asignación es el modo predeterminado de la opción de datos **\/Memory** y no tiene que especificarse en la línea de comandos.  
  
 **vsperfaspnetcmd \/memory** *websiteUrl*  
  
 Utilice el parámetro **Lifetime** para recopilar datos de la duración de los objetos además de los datos de asignación:  
  
 **vsperfaspnetcmd \/memory:lifetime** *websiteUrl*  
  
 También puede utilizar la opción **\/Trace** para incluir información de tiempo detallada con los datos de memoria de .NET:  
  
 **vsperfaspnetcmd \/memory**\[**:lifetime**\] **\/trace** `websiteUrl`  
  
## Para recopilar datos de interacción de capas  
  
> [!WARNING]
>  La generación de perfiles de interacción de capas los datos de \(TIP\) se puede obtener utilizando [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], o [!INCLUDE[vs_pro_current_short](../profiling/includes/vs_pro_current_short_md.md)].  Sin embargo, los datos de generación de perfiles de interacción de capas solo se pueden ver en [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)] y [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)].  
>   
>  Para recopilar datos de TIP en Windows 8 o Windows Server 2012, debe utilizar la opción de instrumentación \(**\/trace**\).  
  
 Para recopilar datos de interacción de capas con datos de muestreo:  
  
 **vsperfaspnetcmd \/tip** `websiteUrl`  
  
 Para recopilar datos de interacción de capas con datos de instrumentación:  
  
 **vsperfaspnetcmd \/trace \/tip** *websiteUrl*  
  
 Para recopilar datos de interacción de capas con datos de memoria de .NET:  
  
 **vsperfaspnetcmd \/memory**\[**:lifetime**\] **\/tip** *websiteUrl*  
  
##  <a name="UsingNoWait"></a> Utilizar la opción \/NoWait  
 De forma predeterminada, el símbolo del sistema no vuelve después de un comando **vsperfaspnetcmd**.  Puede utilizar la siguiente opción de sintaxis para obligar al símbolo del sistema a volver.  A continuación, puede realizar otras operaciones en la ventana de símbolo del sistema.  Para terminar la generación de perfiles, utilice la opción **\/shutdown** en un comando **vsperfaspnetcmd** independiente.  
  
 Para comenzar la generación de perfiles:  
  
 **vsperfaspnetcmd** \[*\/Options*\] **\/nowait** *websiteUrl*  
  
 Para finalizar la generación de perfiles:  
  
 **vsperfaspnetcmd \/shutdown** *websiteUrl*  
  
## Opciones adicionales  
 Puede agregar cualquiera de las siguientes opciones a los comandos enumerados anteriormente en esta sección, excepto el comando **vsperfaspnetcmd \/shutdown**.  
  
|Opción|Descripción|  
|------------|-----------------|  
|**\/Output:** `VspFile`|De forma predeterminada, el archivo de datos de generación de perfiles \(.vsp\) se crea en el directorio actual con el nombre de archivo **PerformanceReport.vsp**.  Utilice la opción \/output para especificar una ubicación o un nombre de archivo diferentes o ambos a la vez.|  
|**\/PackSymbols:Off**|De forma predeterminada, VSPerfASPNETCmd incrusta símbolos \(nombres de funciones y parámetros, etc.\) en el archivo .vsp.  Al incrustar los símbolos, el archivo de datos de generación de perfiles puede hacerse muy grande.  Si va a tener acceso a los archivos .pdb que contienen los símbolos al analizar los datos, utilice la opción \/packsymbols:off para deshabilitar la incrustación de los símbolos.|