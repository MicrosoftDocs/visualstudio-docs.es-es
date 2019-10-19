---
title: Crear vistas personalizadas de objetos administrados | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.data.elements
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- data types [C#], custom
- custom data types
- managed code, custom data types
- autoexp.dat file
- mcee_cs.dat file
- debugger, expanding data types
- mcee_mc.dat file
ms.assetid: 9969e9b2-9008-4729-8a14-0d6deaa61576
caps.latest.revision: 37
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: cb5b56404c7ddc99b7999b47cf3c2a899f915efd
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72578030"
---
# <a name="create-custom-views-of-managed-objects"></a>Creación de vistas personalizadas de objetos administrados
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Se puede personalizar la manera en que Visual Studio muestra los tipos de datos en las ventanas de variables del depurador.  
  
## <a name="attributes"></a>Atributos  
 En C# y Visual Basic, se pueden agregar expansiones para los datos personalizados mediante <xref:System.Diagnostics.DebuggerTypeProxyAttribute>, <xref:System.Diagnostics.DebuggerDisplayAttribute> y <xref:System.Diagnostics.DebuggerBrowsableAttribute>.  
  
 En código de [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)], Visual Basic no admite el atributo DebuggerBrowsable. Esta limitación se ha quitado en las versiones más recientes de .NET Framework.  
  
## <a name="visualizers"></a>Visualizadores  
 Se puede escribir un visualizador para mostrar cualquier tipo de datos administrados. Para obtener más información, vea [Cómo: escribir un visualizador](../debugger/how-to-write-a-visualizer.md).  
  
## <a name="native-code"></a>Código nativo  
 En el caso de código nativo, se pueden agregar expansiones de tipo de datos personalizados al archivo autoexp.dat, ubicado en el directorio Archivos de programa\Microsoft Visual Studio 11.0\Common7\Packages\Debugger. El propio archivo incluye las instrucciones sobre cómo escribir reglas `autoexp`.  
  
> [!CAUTION]
> La estructura de este archivo y la sintaxis de las reglas autoexp quizá cambien de una versión de Visual Studio a la siguiente.  
  
 Las vistas de tipos nativos también se pueden personalizar escribiendo un complemento de evaluador de expresiones. Para obtener más información, vea [ejemplo de EEAddIn: complemento del evaluador de expresiones de depuración](https://msdn.microsoft.com/d4f6b068-c812-45bc-9ec0-7e0363c4bb9e).  
  
## <a name="see-also"></a>Vea también  
 [Uso del atributo DebuggerTypeProxy](../debugger/using-debuggertypeproxy-attribute.md)   
 [Uso del atributo DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md)   
 [Ventanas Inspección e Inspección rápida](../debugger/watch-and-quickwatch-windows.md)   
 [Mejorar la depuración con los atributos de visualización del depurador](https://msdn.microsoft.com/library/72bb7aa9-459b-42c4-9163-9312fab4c410)
