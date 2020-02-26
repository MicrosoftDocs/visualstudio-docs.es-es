---
title: Procedimiento Instalar el generador de perfiles independiente | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- performance tools, installing stand-alone profiler
- profiling tools, stand-alone profiler
ms.assetid: cae81c95-83cd-4ab6-8a98-84ef977a2f6d
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: ec0f211db3d9906d83d9bcf7c7a0ab79ec3e1b7f
ms.sourcegitcommit: bf2e9d4ff38bf5b62b8af3da1e6a183beb899809
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/22/2020
ms.locfileid: "77557834"
---
# <a name="how-to-install-the-stand-alone-profiler"></a>Procedimiento Instalar el generador de perfiles independiente
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] proporciona un generador de perfiles independiente basado en la línea de comandos que se puede ejecutar sin tener que instalar el IDE de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Esta situación se da si un equipo no tiene o no puede tener instalado un entorno de desarrollo. Por ejemplo, no debe instalar un entorno de desarrollo en un servidor web de producción.

> [!NOTE]
> Al usar el generador de perfiles independiente para recopilar datos de rendimiento para un sitio web de ASP.NET, es preferible usar la herramienta de línea de comandos [VSPerfASPNetCmd](../profiling/vsperfaspnetcmd.md) en vez de la herramienta [VSPerfCmd](../profiling/vsperfcmd.md).

### <a name="to-install-the-stand-alone-profiler"></a>Para instalar el generador de perfiles independiente

1. Descargue las [Herramientas de rendimiento para Visual Studio](https://visualstudio.microsoft.com/downloads/?q=performance+tools#performance-tools-for-visual-studio).

1. Busque el instalador de perfiles independiente (*vs_standaloneprofiler.exe*) donde haya descargado las herramientas de rendimiento y ejecútelo.

2. Agregue la ruta de acceso para *vsinstr. exe* a la ruta de acceso del sistema.

   > [!NOTE]
   > Para obtener la ruta de acceso a las herramientas de generación de perfiles, vea [Especificar la ruta de acceso a las herramientas de línea de comandos](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). En equipos de 64 bits, están disponibles las dos versiones de las herramientas, la de 64 bits y la de 32 bits. Para utilizar las herramientas de línea de comandos del generador de perfiles, debe agregar la ruta de acceso de las herramientas a la variable de entorno PATH de la ventana Símbolo del sistema o agregarla al propio comando.

3. En el símbolo del sistema, escriba **VSInstr**.

   > [!NOTE]
   > Si se muestra la información de uso de vsinstr.exe, quiere decir que todo está configurado correctamente. Si ve un error que indica que no se encuentra vsinstr.exe o una de sus dependencias, asegúrese de que las rutas de acceso estén correctamente configuradas como se describe en el paso 2.

4. Configure el servidor de símbolos estableciendo la variable **_NT_SYMBOL_PATH** en **symsrv\*symsrv.dll\*c:\localcache\*https://msdl.microsoft.com/download/symbols** .

5. Una vez configurado el servidor de símbolos con las variables de entorno del sistema, ejecute las herramientas del generador de perfiles de línea de comandos en un nuevo símbolo del sistema. De esta forma, las nuevas variables de entorno surtirán efecto. En la ventana del símbolo del sistema, escriba el siguiente comando:

    **start %COMSPEC%**

   > [!NOTE]
   > Para obtener instrucciones detalladas sobre cómo configurar el paquete del servidor de símbolos, vea [Cómo: Hacer referencia a información de símbolos de Windows](../profiling/how-to-reference-windows-symbol-information.md).

6. Use la herramienta [VSPerfReport](../profiling/vsperfreport.md) para serializar los símbolos en el archivo de datos de generación de perfiles (.vsp). Use los conmutadores **VSPerfReport /summary:all /packsymbols**. Si no tiene ningún símbolo insertado en el archivo de datos, asegúrese de que tiene establecida la variable de entorno _NT_SYMBOL_PATH.

## <a name="see-also"></a>Vea también
- [Generación de perfiles desde la línea de comandos](../profiling/using-the-profiling-tools-from-the-command-line.md)
- [Tutorial: Generar perfiles utilizando la instrumentación en la línea de comandos](command-line-profiling-of-stand-alone-applications.md)
- [Cómo: Hacer referencia a información de símbolos de Windows](../profiling/how-to-reference-windows-symbol-information.md)
- [VSPerfReport](../profiling/vsperfreport.md)
