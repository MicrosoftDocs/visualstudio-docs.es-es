---
title: Crear vistas personalizadas de objetos administrados | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
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
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 964e3bcee87c6110813862eccdac63765fa5199f
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49273005"
---
# <a name="create-custom-views-of-managed-objects"></a>Crear vistas personalizadas de objetos administrados
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Se puede personalizar la manera en que Visual Studio muestra los tipos de datos en las ventanas de variables del depurador.  
  
## <a name="attributes"></a>Atributos  
 En C# y Visual Basic, se pueden agregar expansiones para los datos personalizados mediante <xref:System.Diagnostics.DebuggerTypeProxyAttribute>, <xref:System.Diagnostics.DebuggerDisplayAttribute> y <xref:System.Diagnostics.DebuggerBrowsableAttribute>.  
  
 En código de [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)], Visual Basic no admite el atributo DebuggerBrowsable. Esta limitación se ha quitado en las versiones más recientes de .NET Framework.  
  
## <a name="visualizers"></a>Visualizadores  
 Se puede escribir un visualizador para mostrar cualquier tipo de datos administrados. Para obtener más información, consulte [Cómo: escribir un visualizador](../debugger/how-to-write-a-visualizer.md).  
  
## <a name="native-code"></a>Código nativo  
 En el caso de código nativo, se pueden agregar expansiones de tipo de datos personalizados al archivo autoexp.dat, ubicado en el directorio Archivos de programa\Microsoft Visual Studio 11.0\Common7\Packages\Debugger. El propio archivo incluye las instrucciones sobre cómo escribir reglas `autoexp`.  
  
> [!CAUTION]
>  La estructura de este archivo y la sintaxis de las reglas autoexp quizá cambien de una versión de Visual Studio a la siguiente.  
  
 Las vistas de tipos nativos también se pueden personalizar escribiendo un complemento de evaluador de expresiones. Para obtener más información, consulte [ejemplo EEAddIn: depuración de expresión del evaluador de expresiones complemento](http://msdn.microsoft.com/en-us/d4f6b068-c812-45bc-9ec0-7e0363c4bb9e).  
  
## <a name="see-also"></a>Vea también  
 [Usar el atributo DebuggerTypeProxy](../debugger/using-debuggertypeproxy-attribute.md)   
 [Usar el atributo DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md)   
 [Inspección e inspección rápida Windows](../debugger/watch-and-quickwatch-windows.md)   
 [Mejorar la depuración con los atributos de visualización del depurador](http://msdn.microsoft.com/library/72bb7aa9-459b-42c4-9163-9312fab4c410)



