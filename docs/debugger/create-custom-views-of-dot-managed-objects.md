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
ms.openlocfilehash: 36e875bc8101bc8a1b0eb1bec6671c76e3b0c9b2
ms.sourcegitcommit: 8a3545329a58e446672181cfed2083f850e1ad14
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/02/2019
ms.locfileid: "71814295"
---
# <a name="create-custom-views-of-objects-c-visual-basic-f-ccli"></a>Crear vistas personalizadas de objetos (C#, Visual Basic, F#, C++/CLI)
Se puede personalizar la manera en que Visual Studio muestra los tipos de datos en las ventanas de variables del depurador.

## <a name="attributes"></a>Atributos

En C#, Visual Basic, F#y C++ (C++solo en el código/CLI), puede Agregar expansiones para los datos personalizados mediante <xref:System.Diagnostics.DebuggerTypeProxyAttribute>, <xref:System.Diagnostics.DebuggerDisplayAttribute> y <xref:System.Diagnostics.DebuggerBrowsableAttribute>.

En .NET Framework código 2,0, Visual Basic no admite el atributo DebuggerBrowsable. Esta limitación se ha quitado en las versiones más recientes de .NET Framework.

## <a name="visualizers"></a>Visualizadores

Se puede escribir un visualizador para mostrar cualquier tipo de datos administrados. Para obtener más información, vea [Cómo: Escritura de un visualizador](/visualstudio/debugger/create-custom-visualizers-of-data).

> [!NOTE]
> En C++ el código, puede Agregar expansiones de tipos de datos personalizados mediante el marco Natvis, tal como se describe en [crear vistas personalizadas de C++ objetos en el depurador](/visualstudio/debugger/create-custom-views-of-native-objects).

## <a name="see-also"></a>Vea también

- [Indicar al depurador qué Mostrar mediante el atributo DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md)
- [Indicar al depurador qué tipo debe mostrar mediante el atributo DebuggerTypeProxy](../debugger/using-debuggertypeproxy-attribute.md)
- [Ventanas Inspección e Inspección rápida](../debugger/watch-and-quickwatch-windows.md)
- [Mejorar la depuración con los atributos de visualización del depurador](/dotnet/framework/debug-trace-profile/enhancing-debugging-with-the-debugger-display-attributes)