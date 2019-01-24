---
title: Crear vistas personalizadas de objetos | Microsoft Docs
ms.date: 01/08/2019
ms.topic: conceptual
f1_keywords:
- vs.debug.data.elements
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- data types, custom
- custom data types
- managed code, custom data types
- autoexp.dat file
- mcee_cs.dat file
- debugger, expanding data types
- mcee_mc.dat file
ms.assetid: 9969e9b2-9008-4729-8a14-0d6deaa61576
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: c2e4b2d34df1a1e870247112892d4cd00ff887f3
ms.sourcegitcommit: 01185dadd2fa1f9a040d2a366869f1a5e1d18e0f
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/11/2019
ms.locfileid: "54227647"
---
# <a name="create-custom-views-of-objects-c-visual-basic-c"></a>Crear vistas personalizadas de objetos (C#, Visual Basic, C++)
Se puede personalizar la manera en que Visual Studio muestra los tipos de datos en las ventanas de variables del depurador.  

## <a name="native-code"></a>Código nativo

Para el código de C++, puede agregar expansiones de tipo de datos personalizados mediante el marco Natvis, como se describe en [crear vistas personalizadas de objeto nativo en el depurador](/visualstudio/debugger/create-custom-views-of-native-objects). Para C / c++ / CLI código, también puede utilizar atributos, que se describen aquí en este artículo.

## <a name="attributes"></a>Atributos

En C#, Visual Basic y C++ (C++ / c++ / sólo código CLI), se pueden agregar expansiones para los datos personalizados mediante <xref:System.Diagnostics.DebuggerTypeProxyAttribute>, <xref:System.Diagnostics.DebuggerDisplayAttribute>, y <xref:System.Diagnostics.DebuggerBrowsableAttribute>.  
  
En código de [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)], Visual Basic no admite el atributo DebuggerBrowsable. Esta limitación se ha quitado en las versiones más recientes de .NET Framework.    

## <a name="visualizers"></a>Visualizadores

Se puede escribir un visualizador para mostrar cualquier tipo de datos administrados. Para obtener más información, vea [Cómo: Escritura de un visualizador](/visualstudio/debugger/create-custom-visualizers-of-data).
  
## <a name="see-also"></a>Vea también  
 [Uso del atributo DebuggerTypeProxy](../debugger/using-debuggertypeproxy-attribute.md)   
 [Uso del atributo DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md)   
 [Ventanas Inspección e Inspección rápida](../debugger/watch-and-quickwatch-windows.md)   
 [Mejorar la depuración con los atributos de visualización del depurador](/dotnet/framework/debug-trace-profile/enhancing-debugging-with-the-debugger-display-attributes)