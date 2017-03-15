---
title: "Depurar aplicaciones de 64 bits | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "depurar [Visual Studio], 64 bits"
  - "depuración en 64 bits"
ms.assetid: db648e5f-6375-4e2d-aa98-eb7261958927
caps.latest.revision: 32
caps.handback.revision: 32
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Depurar aplicaciones de 64 bits
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Puede depurar una aplicación de 64 bits que se esté ejecutando en el equipo local o en un equipo remoto.  
  
 Para depurar una aplicación de 64 bits que se ejecute en un equipo remoto, consulte [Depuración remota](../debugger/remote-debugging.md).  
  
 Para depurar aplicaciones de 64 bits localmente, Visual Studio usa un proceso de trabajo de 64 bits \(msvsmon.exe\) para realizar las operaciones de bajo nivel que no se pueden realizar en el proceso de Visual Studio de 32 bits.  
  
 No se admite la depuración en modo mixto para los procesos de 64 bits que usan .NET Framework 3.5 o versiones anteriores.  
  
## Depurar una aplicación de 64 bits  
 Para intentar depurar una aplicación de 64 bits:  
  
1.  Cree una solución de Visual Studio, por ejemplo una aplicación de consola de C\#.  
  
2.  Establezca la configuración en 64 bits mediante el Administrador de configuración. Para obtener más información, consulta [Cómo: Configurar proyectos para plataformas de destino](../ide/how-to-configure-projects-to-target-platforms.md).  
  
3.  En este momento se inicia la versión de 64 bits del depurador remoto \(msvsmon.exe\). Se ejecuta siempre que se abra la solución con la configuración de 64 bits.  
  
4.  Inicie la depuración. Debe tener la misma experiencia que con una configuración de 32 bits. Si se producen errores, vea la siguiente sección de solución de problemas.  
  
## Solución de problemas de depuración de 64 bits  
 Es posible que se muestre el error: "Una operación de depuración de 64 bits está tardando más de lo previsto." En este caso, Visual Studio envió una solicitud a la versión de 64 bits de msvsmon.exe y el resultado de la solicitud tardó mucho tiempo en volver.  
  
 Existen dos causas probables de este error:  
  
-   Tiene software de seguridad de red instalado en el equipo que provoca que la pila de red no sea confiable y tiene paquetes eliminados transfiriéndose a través de localhost. Intente deshabilitar todo el software de seguridad de red y compruebe si se resuelve el problema. Si es así, notifique a su proveedor de software de seguridad de red que el software está interfiriendo con el tráfico de localhost.  
  
-   Está experimentando un problema de falta de respuesta o de rendimiento con Visual Studio. Si el problema ocurre con frecuencia, puede recopilar volcados de Visual Studio \(devenv.exe\) y el proceso de trabajo \(msvsmon.exe\) y enviarlos a Microsoft. Para obtener información acerca de cómo notificar un problema, consulte [Cómo notificar un problema con Visual Studio](../Topic/How%20to%20Report%20a%20Problem%20with%20Visual%20Studio.md).  
  
## Vea también  
 [Aplicaciones de 64 bits](../Topic/64-bit%20Applications.md)   
 [Configurar programas de 64 bits](/visual-cpp/build/configuring-programs-for-64-bit-visual-cpp)   
 [Compatibilidad de 64 bits del IDE de Visual Studio](../ide/visual-studio-ide-64-bit-support.md)   
 [Usar archivos de volcado de memoria para depurar bloqueos de la aplicación](../debugger/using-dump-files.md)   
 [Depuración remota](../debugger/remote-debugging.md)