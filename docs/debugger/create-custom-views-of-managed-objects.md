---
title: Creación de vistas personalizadas de objetos administrados | Microsoft Docs
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
ms.openlocfilehash: f5247a56667f5715d9f155c662eb333967878d71
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2019
ms.locfileid: "73188647"
---
# <a name="create-custom-views-of-managed-objects-c-visual-basic-f-ccli"></a>Creación de vistas personalizadas de objetos administrados (C#, Visual Basic, F# y C++/CLI)
Se puede personalizar la manera en que Visual Studio muestra los tipos de datos en las ventanas de variables del depurador.

## <a name="attributes"></a>Atributos

En C#, Visual Basic, F# y C++ (solo código de C++/CLI), se pueden agregar expansiones para los datos personalizados mediante <xref:System.Diagnostics.DebuggerTypeProxyAttribute>, <xref:System.Diagnostics.DebuggerDisplayAttribute> y <xref:System.Diagnostics.DebuggerBrowsableAttribute>.

En código de .NET Framework 2.0, Visual Basic no admite el atributo DebuggerBrowsable. Esta limitación se ha quitado en las últimas versiones de .NET.

## <a name="visualizers"></a>Visualizadores

Se puede escribir un visualizador para mostrar cualquier tipo de datos administrados. Para obtener más información, vea [Cómo: Escritura de un visualizador](create-custom-visualizers-of-data.md).

> [!NOTE]
> En el código de C++, puede agregar expansiones de tipos de datos personalizados mediante el marco Natvis, tal como se describe en [Crear vistas personalizadas de objetos C++ en el depurador mediante el marco Natvis](create-custom-views-of-native-objects.md).

## <a name="see-also"></a>Vea también

- [Indicar al depurador qué se va a mostrar mediante el atributo DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md)
- [Indicar al depurador qué tipo se va a mostrar mediante el atributo DebuggerTypeProxy](../debugger/using-debuggertypeproxy-attribute.md)
- [Ventanas Inspección e Inspección rápida](../debugger/watch-and-quickwatch-windows.md)
- [Mejorar la depuración con los atributos de visualización del depurador](/dotnet/framework/debug-trace-profile/enhancing-debugging-with-the-debugger-display-attributes)
