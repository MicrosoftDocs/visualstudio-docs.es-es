---
title: Depurar aplicaciones de 64 bits | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], 64-bit
- 64-bit debugging
ms.assetid: db648e5f-6375-4e2d-aa98-eb7261958927
caps.latest.revision: 38
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2f67acff26d346b915f6b457fc0887f1d5f2ec3b
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "65695912"
---
# <a name="debug-64-bit-applications"></a>Depurar aplicaciones de 64 bits
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [aplicaciones de depuración de 64 bits](https://docs.microsoft.com/visualstudio/debugger/debug-64-bit-applications) .  
  
Puede depurar una aplicación de 64 bits que se esté ejecutando en el equipo local o en un equipo remoto.  
  
 Para depurar una aplicación de 64 bits que se ejecute en un equipo remoto, consulte [Remote Debugging](../debugger/remote-debugging.md).  
  
 Para depurar aplicaciones de 64 bits localmente, Visual Studio usa un proceso de trabajo de 64 bits (msvsmon.exe) para realizar las operaciones de bajo nivel que no se pueden realizar en el proceso de Visual Studio de 32 bits.  
  
 No se admite la depuración en modo mixto para los procesos de 64 bits que usan .NET Framework 3.5 o versiones anteriores.  
  
## <a name="debug-a-64-bit-application"></a>Depurar una aplicación de 64 bits  
 Para intentar depurar una aplicación de 64 bits:  
  
1. Cree una solución de Visual Studio, por ejemplo una aplicación de consola de C#.  
  
2. Establezca la configuración en 64 bits mediante el Administrador de configuración. Para obtener más información, vea [Cómo: Configurar proyectos para plataformas de destino](../ide/how-to-configure-projects-to-target-platforms.md).  
  
3. En este momento se inicia la versión de 64 bits del depurador remoto (msvsmon.exe). Se ejecuta siempre que se abra la solución con la configuración de 64 bits.  
  
4. Inicie la depuración. Debe tener la misma experiencia que con una configuración de 32 bits. Si se producen errores, vea la siguiente sección de solución de problemas.  
  
## <a name="troubleshooting-64-bit-debugging"></a>Solución de problemas de depuración de 64 bits  
 Es posible que vea un error: "Una operación de depuración de 64 bits está tardando más de lo esperado." En este caso, Visual Studio envió una solicitud a la versión de 64 bits de msvsmon.exe y el resultado de la solicitud tardó mucho tiempo en volver.  
  
 Existen dos causas probables de este error:  
  
- Tiene software de seguridad de red instalado en el equipo que provoca que la pila de red no sea confiable y tiene paquetes eliminados transfiriéndose a través de localhost. Intente deshabilitar todo el software de seguridad de red y compruebe si se resuelve el problema. Si es así, notifique a su proveedor de software de seguridad de red que el software está interfiriendo con el tráfico de localhost.  
  
- Está experimentando un problema de falta de respuesta o de rendimiento con Visual Studio. Si el problema ocurre con frecuencia, puede recopilar volcados de Visual Studio (devenv.exe) y el proceso de trabajo (msvsmon.exe) y enviarlos a Microsoft. 
  
## <a name="see-also"></a>Vea también  
 [Aplicaciones de 64 bits](https://msdn.microsoft.com/library/fd4026bc-2c3d-4b27-86dc-ec5e96018181)   
 [Configurar programas de 64 bits](https://msdn.microsoft.com/library/cb99f72b-8c74-48f4-846a-8921b37b97e9)   
 [Compatibilidad de 64 bits del IDE de Visual Studio](../ide/visual-studio-ide-64-bit-support.md)   
 [Usar archivos de volcado de memoria](../debugger/using-dump-files.md)   
 [Remote Debugging](../debugger/remote-debugging.md)
