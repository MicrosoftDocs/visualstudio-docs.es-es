---
title: Admite los cambios de código (C#) | Documentos de Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Edit and Continue [C#], supported code changes
ms.assetid: c7a48ea9-5a7f-4328-a9d7-f0e76fac399d
caps.latest.revision: 30
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 655d80792bf1a2ab6c1af658bcfb6fb3648f5d10
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47575419"
---
# <a name="supported-code-changes-c"></a>Cambios admitidos en el código (C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [Supported Code Changes (C#)](https://docs.microsoft.com/visualstudio/debugger/supported-code-changes-csharp).  
  
Editar y continuar controla la mayoría de los tipos de cambios de código dentro de los cuerpos de método. Ahora bien, durante la depuración, no es posible efectuar la mayoría de cambios fuera de los cuerpos de método y algunos cambios dentro de estos. Para efectuar dichos cambios no compatibles, es necesario detener la depuración y reiniciar con una versión nueva del código.  
  
 Los siguientes cambios no se pueden aplicar al código de C# durante una sesión de depuración:  
  
-   Cambios en la instrucción actual o en cualquier otra instrucción activa.  
  
     Entre las instrucciones activas se incluye cualquier instrucción, en funciones de la pila de llamadas, que haya sido llamada para llegar a la instrucción actual.  
  
     Un fondo amarillo marca la instrucción actual en la ventana de código fuente. Un fondo sombreado marca otras instrucciones activas; son de solo lectura. Estos colores predeterminados se pueden cambiar en el **opciones** cuadro de diálogo.  
  
-   Cambiar la firma de un tipo.  
  
-   Agregar un método anónimo que captura una variable que no se ha capturado antes.  
  
-   Agregar, quitar o cambiar atributos.  
  
-   Agregar, quitar o cambiar directivas `using`.  
  
-   Agregar una directiva `foreach`, `using` o `lock` en torno a la instrucción activa.  
  
## <a name="unsafe-code"></a>Código no seguro  
 Los cambios efectuados en el código no seguro tienen las mismas limitaciones que los cambios efectuados en el código seguro, con una restricción adicional: Editar y continuar no admite cambios en el código no seguro que esté dentro de un método que contenga el operador `stackalloc`.  
  
## <a name="exceptions"></a>Excepciones  
 Editar y continuar admite cambios en los bloques `catch` y `finally`, pero no se permite agregar un bloque `catch` o `finally` en la instrucción activa.  
  
## <a name="unsupported-scenarios"></a>Escenarios no admitidos  
 La opción Editar y continuar no se encuentra disponible en los siguientes escenarios de depuración:  
  
-   Depurar código LINQ en determinadas circunstancias. Para obtener más información, vea [Depurar LINQ](../debugger/debugging-linq.md).  
  
    -   Capturar una variable que no se ha capturado antes.  
  
    -   Cambiar el tipo de expresión de consulta (por ejemplo, seleccionar un = > seleccionar nuevo {A = a};)  
  
    -   Quitar un `where` que contiene una instrucción activa.  
  
    -   Quitar un `let` que contiene una instrucción activa.  
  
    -   Quitar un `join` que contiene una instrucción activa.  
  
    -   Quitar un `orderby` que contiene una instrucción activa.  
  
-   Depuración en modo mixto (nativa o administrada).  
  
-   Depuración de SQL.  
  
-   Depuración de un volcado de Dr. Volcado de memoria de Watson.  
  
-   Edición de código tras una excepción no controlada, cuando el "**desenredar la pila de llamadas en las excepciones no controladas**" no está seleccionada.  
  
-   Depuración de una aplicación incrustada en tiempo de ejecución.  
  
-   Depurar una aplicación que tiene **adjuntar a** en lugar de ejecutar la aplicación eligiendo **iniciar** desde el **depurar** menú.  
  
-   Depuración de código optimizado.  
  
-   Depurar una versión anterior del código cuando no ha sido posible generar una nueva versión debido a errores de compilación.  
  
## <a name="see-also"></a>Vea también  
 [Editar y continuar (Visual C#)](../debugger/edit-and-continue-visual-csharp.md)   
 [Cómo: Usar Editar y continuar (C#)](../debugger/how-to-use-edit-and-continue-csharp.md)



