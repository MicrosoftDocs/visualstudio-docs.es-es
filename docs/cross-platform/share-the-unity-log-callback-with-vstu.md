---
title: "Compartir la devoluci&#243;n de llamada de registro de Unity con VSTU | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "tgt-pltfrm-cross-plat"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5d71f906-6e50-4399-b59b-d38c6dfef7ee
caps.latest.revision: 2
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 2
---
# Compartir la devoluci&#243;n de llamada de registro de Unity con VSTU
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Visual Studio Tools para Unity registra una devolución de llamada de registro con Unity para poder transmitir su consola a Visual Studio.  Si las secuencias de comandos del editor también registran una devolución de llamada de registro con Unity, la devolución de llamada de VSTU puede interferir con la devolución de llamada.  Para evitar esta posibilidad, use el evento `VisualStudioIntegration.LogCallback` para cooperar con VSTU.  
  
## Demostraciones  
 Cómo compartir la devolución de llamada de registro de Unity creada por Visual Studio Tools para Unity.  
  
## Ejemplo  
  
```c#  
using System;  
  
using UnityEngine;  
using UnityEditor;  
  
using SyntaxTree.VisualStudio.Unity.Bridge;  
  
[InitializeOnLoad]  
public class LogCallbackHook  
{  
    static LogCallbackHook()  
    {  
        VisualStudioIntegration.LogCallback += (string condition, string trace, LogType type) =>  
        {  
            // place code that implements your log callback here  
        };  
    }  
}  
```  
  
## Vea también  
 [Ejemplo: Generación de archivo de proyecto](../cross-platform/customize-project-files-created-by-vstu.md)