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
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 911f0423184f22919be016691b9333b2f62d1b61
ms.sourcegitcommit: 12f2851c8c9bd36a6ab00bf90a020c620b364076
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/06/2019
ms.locfileid: "66744800"
---
# <a name="create-custom-views-of-objects-c-visual-basic-c"></a>Crear vistas personalizadas de objetos (C#, Visual Basic, C++)
Se puede personalizar la manera en que Visual Studio muestra los tipos de datos en las ventanas de variables del depurador.

## <a name="native-code"></a>Código nativo

Para C++ código, puede agregar expansiones de tipo de datos personalizados mediante el marco Natvis, como se describe en [crear vistas personalizadas de C++ objetos en el depurador](/visualstudio/debugger/create-custom-views-of-native-objects). Para C++/código de la CLI, también puede usar atributos, que se describen aquí en este artículo.

## <a name="attributes"></a>Atributos

En C#, Visual Basic, y C++ (C++solo código /CLI), se pueden agregar expansiones para los datos personalizados mediante <xref:System.Diagnostics.DebuggerTypeProxyAttribute>, <xref:System.Diagnostics.DebuggerDisplayAttribute>, y <xref:System.Diagnostics.DebuggerBrowsableAttribute>.

En el código de .NET Framework 2.0, Visual Basic no admite el atributo DebuggerBrowsable. Esta limitación se ha quitado en las versiones más recientes de .NET Framework.

## <a name="visualizers"></a>Visualizadores

Se puede escribir un visualizador para mostrar cualquier tipo de datos administrados. Para obtener más información, vea [Cómo: Escritura de un visualizador](/visualstudio/debugger/create-custom-visualizers-of-data).

## <a name="see-also"></a>Vea también

- [Indicar al depurador qué muestra el uso del atributo DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md)
- [Indicar al depurador qué tipo a se muestra el uso del atributo DebuggerTypeProxy](../debugger/using-debuggertypeproxy-attribute.md)
- [Ventanas Inspección e Inspección rápida](../debugger/watch-and-quickwatch-windows.md)
- [Mejorar la depuración con los atributos de visualización del depurador](/dotnet/framework/debug-trace-profile/enhancing-debugging-with-the-debugger-display-attributes)