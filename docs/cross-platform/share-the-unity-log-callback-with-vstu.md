---
title: "Uso compartido de la devolución de llamada de registro de Unity con VSTU | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: tgt-pltfrm-cross-plat
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5d71f906-6e50-4399-b59b-d38c6dfef7ee
caps.latest.revision: "2"
author: conceptdev
ms.author: crdun
manager: crdun
ms.openlocfilehash: 7aae3c7bc11cdde209ef4d663793f25fa1e9e67e
ms.sourcegitcommit: 5f5587a1bcf4aae995c80d54a67b4b461f8695f3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/29/2017
---
# <a name="share-the-unity-log-callback-with-vstu"></a>Compartir la devolución de llamada de registro de Unity con VSTU
Visual Studio Tools para Unity registra una devolución de llamada de registro con Unity para poder transmitir su consola a Visual Studio. Si las secuencias de comandos del editor también registran una devolución de llamada de registro con Unity, la devolución de llamada de VSTU puede interferir con la devolución de llamada. Para evitar esta posibilidad, use el evento `VisualStudioIntegration.LogCallback` para cooperar con VSTU.  

## <a name="demonstrates"></a>Demostraciones  
 Cómo compartir la devolución de llamada de registro de Unity creada por Visual Studio Tools para Unity.  

## <a name="example"></a>Ejemplo  

```csharp  
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

## <a name="see-also"></a>Vea también  
 [Ejemplo: Generación de archivo de proyecto](../cross-platform/customize-project-files-created-by-vstu.md)
