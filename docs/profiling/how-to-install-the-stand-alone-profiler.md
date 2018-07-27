---
title: 'Cómo: Instalar el generador de perfiles independiente | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- performance tools, installing stand-alone profiler
- profiling tools, stand-alone profiler
ms.assetid: cae81c95-83cd-4ab6-8a98-84ef977a2f6d
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3898f61987f1767dba57a63bfb3b5b753e8d37aa
ms.sourcegitcommit: 1b9c1e333c2f096d35cfc77e846116f8e5054557
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/06/2018
ms.locfileid: "34815618"
---
# <a name="how-to-install-the-stand-alone-profiler"></a>Cómo: Instalar el generador de perfiles independiente
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] proporciona un generador de perfiles independiente basado en la línea de comandos que se puede ejecutar sin tener que instalar el IDE de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Esta situación se da si un equipo no tiene o no puede tener instalado un entorno de desarrollo. Por ejemplo, no debe instalar un entorno de desarrollo en un servidor web de producción.  
  
> [!NOTE]
>  Al usar el generador de perfiles independiente para recopilar datos de rendimiento para un sitio web de ASP.NET, es preferible usar la herramienta de línea de comandos [VSPerfASPNetCmd](../profiling/vsperfaspnetcmd.md) en vez de la herramienta [VSPerfCmd](../profiling/vsperfcmd.md).  
  
### <a name="to-install-the-stand-alone-profiler"></a>Para instalar el generador de perfiles independiente  
  
1.  Busque el instalador del generador de perfiles independiente (*vs_profiler.exe*) en los medios de instalación de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], en el directorio que incluye la ruta de acceso *\Standalone Profiler* y ejecútelo.  
  
2.  Agregue las rutas de acceso de *vsintr.exe* y *msdis150.dll* a la ruta de acceso del sistema.  
  
    > [!NOTE]
    >  En la instalación predeterminada de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], *vsinstr.exe* y *msdis150.dll* se encuentran en *\Archivos de programa\Visual Studio 10\Team Tools\Performance Tools*.  
  
3.  En el símbolo del sistema, escriba **VSInstr**.  
  
    > [!NOTE]
    >  Si se muestra la información de uso de vsinstr.exe, quiere decir que todo está configurado correctamente. Si ve un error que indica que no se encuentra vsinstr.exe o una de sus dependencias, asegúrese de que las rutas de acceso estén correctamente configuradas como se describe en el paso 2.  
  
4.  Configure el servidor de símbolos estableciendo la variable **_NT_SYMBOL_PATH** en **symsrv\*symsrv.dll\*c:\localcache\*http://msdl.microsoft.com/download/symbols**.  
  
5.  Una vez configurado el servidor de símbolos con las variables de entorno del sistema, ejecute las herramientas del generador de perfiles de línea de comandos en un nuevo símbolo del sistema. De esta forma, las nuevas variables de entorno surtirán efecto. En la ventana del símbolo del sistema, escriba el siguiente comando:  
  
     **start %COMSPEC%**  
  
    > [!NOTE]
    >  Para obtener instrucciones detalladas sobre cómo configurar el paquete del servidor de símbolos, vea [Cómo: Hacer referencia a información de símbolos de Windows](../profiling/how-to-reference-windows-symbol-information.md).  
  
6.  Use la herramienta [VSPerfReport](../profiling/vsperfreport.md) para serializar los símbolos en el archivo de datos de generación de perfiles (.vsp). Use los conmutadores **VSPerfReport /summary:all /packsymbols**. Si no tiene ningún símbolo insertado en el archivo de datos, asegúrese de que tiene establecida la variable de entorno _NT_SYMBOL_PATH.  
  
## <a name="see-also"></a>Vea también  
 [Generación de perfiles desde la línea de comandos](../profiling/using-the-profiling-tools-from-the-command-line.md)   
 [Tutorial: Generación de perfiles de línea de comandos mediante muestreo](../profiling/walkthrough-command-line-profiling-using-sampling.md)   
 [Tutorial: Generar perfiles mediante instrumentación desde la línea de comandos](../profiling/walkthrough-command-line-profiling-using-instrumentation.md)   
 [Cómo: Hacer referencia a información de símbolos de Windows](../profiling/how-to-reference-windows-symbol-information.md)   
 [VSPerfReport](../profiling/vsperfreport.md)