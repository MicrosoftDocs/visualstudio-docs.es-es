---
title: Crear vistas personalizadas de objetos administrados | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.data.elements
dev_langs:
- CSharp
- VB
- FSharp
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 389deb0b6504ca5c7a3716399429f176e5dc7870
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53861441"
---
# <a name="create-custom-views-of-managed-objects"></a>Crear vistas personalizadas de objetos administrados
Se puede personalizar la manera en que Visual Studio muestra los tipos de datos en las ventanas de variables del depurador.  
  
## <a name="attributes"></a>Atributos  
 En C# y Visual Basic, se pueden agregar expansiones para los datos personalizados mediante <xref:System.Diagnostics.DebuggerTypeProxyAttribute>, <xref:System.Diagnostics.DebuggerDisplayAttribute> y <xref:System.Diagnostics.DebuggerBrowsableAttribute>.  
  
 En código de [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)], Visual Basic no admite el atributo DebuggerBrowsable. Esta limitación se ha quitado en las versiones más recientes de .NET Framework.  
  
## <a name="visualizers"></a>Visualizadores  
 Se puede escribir un visualizador para mostrar cualquier tipo de datos administrados. Para obtener más información, vea [Cómo: Escritura de un visualizador](/visualstudio/debugger/create-custom-visualizers-of-data).  
  
## <a name="native-code"></a>Código nativo  
 En el caso de código nativo, se pueden agregar expansiones de tipo de datos personalizados al archivo autoexp.dat, ubicado en el directorio Archivos de programa\Microsoft Visual Studio 11.0\Common7\Packages\Debugger. El propio archivo incluye las instrucciones sobre cómo escribir reglas `autoexp`.  
  
> [!CAUTION]
>  La estructura de este archivo y la sintaxis de las reglas autoexp quizá cambien de una versión de Visual Studio a la siguiente.  
  
 Las vistas de tipos nativos también se pueden personalizar escribiendo un complemento de evaluador de expresiones. Para obtener más información, consulte [ejemplo EEAddIn: Depuración de la expresión del evaluador de expresiones complemento](https://msdn.microsoft.com/library/d4f6b068-c812-45bc-9ec0-7e0363c4bb9e).  
  
## <a name="see-also"></a>Vea también  
 [Uso del atributo DebuggerTypeProxy](../debugger/using-debuggertypeproxy-attribute.md)   
 [Uso del atributo DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md)   
 [Ventanas Inspección e Inspección rápida](../debugger/watch-and-quickwatch-windows.md)   
 [Mejorar la depuración con los atributos de visualización del depurador](/dotnet/framework/debug-trace-profile/enhancing-debugging-with-the-debugger-display-attributes)