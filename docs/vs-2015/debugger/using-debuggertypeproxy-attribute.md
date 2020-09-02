---
title: Usar el atributo DebuggerTypeProxy | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- attributes [C#], debugger
- DebuggerTypeProxyAttribute class
- DebuggerTypeProxy attribute
ms.assetid: 943f3bb1-993e-4800-a47e-0af78b063014
caps.latest.revision: 27
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f6e349dd5bea4e0d89c31864960a5438d1e2b13f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "65684074"
---
# <a name="using-debuggertypeproxy-attribute"></a>Utilizar el atributo DebuggerTypeProxy
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Compatible DebuggerTypeProxyAttribute] (AssetID:///T: System. Diagnostics. compatible DebuggerTypeProxyAttribute? qualifyHint = false&AutoUpgrade = true) especifica un proxy, o está en reposo, para un tipo y cambia la forma en que se muestra el tipo en las ventanas del depurador. Cuando se ve una variable que tiene un proxy, el proxy reemplaza al tipo original en la **presentación**. En la ventana de las variables del depurador se muestran sólo los miembros públicos del tipo de servidor proxy. No se muestran los miembros privados.  
  
 Este atributo se puede aplicar a:  
  
- Estructuras  
  
- Clases  
  
- Ensamblados  
  
  Una clase de proxy de tipo debe tener un constructor que tome un argumento del tipo que el proxy reemplazará. El depurador crea una nueva instancia de la clase de proxy de tipo cada vez que necesita mostrar una variable del tipo de destino. Esto puede afectar al rendimiento. Por tanto, en el constructor no debe realizarse más trabajo del estrictamente necesario.  
  
  Para minimizar la reducción de rendimiento, el evaluador de expresiones no examina los atributos en el proxy de presentación del tipo, a menos que el usuario expanda el tipo haciendo clic en el símbolo + en la ventana del depurador o mediante <xref:System.Diagnostics.DebuggerBrowsableAttribute>. Por consiguiente, no se deben colocar atributos en el propio tipo de presentación. Los atributos pueden y deben utilizarse en el cuerpo del tipo de presentación.  
  
  Se recomienda que el proxy de tipo sea una clase anidada privada dentro de la clase que el atributo tiene como destino. De este modo, puede obtener acceso fácilmente a los miembros internos.  
  
  Si se utiliza <xref:System.Diagnostics.DebuggerTypeProxyAttribute> en el nivel de ensamblado, el parámetro `Target` especifica el tipo que reemplazará el proxy.  
  
  Para obtener un ejemplo de cómo utilizar este atributo junto con los atributos <xref:System.Diagnostics.DebuggerDisplayAttribute> y <xref:System.Diagnostics.DebuggerTypeProxyAttribute>, vea [Usar el atributo DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md).  
  
## <a name="using-generics-with-debuggertypeproxy"></a>Utilizar genéricos con DebuggerTypeProxy  
 La compatibilidad con los genéricos es limitada. En C#, `DebuggerTypeProxy` solo acepta tipos abiertos. Un tipo abierto, también denominado tipo no construido, es un tipo genérico de cuyos parámetros de tipo no se han creado instancias con argumentos. No se admiten los tipos cerrados, también denominados tipos construidos.  
  
 La sintaxis de un tipo abierto tiene el siguiente aspecto:  
  
 `Namespace.TypeName<,>`  
  
 Si utiliza un tipo genérico como destino en `DebuggerTypeProxy`, debe utilizar esta sintaxis. El mecanismo `DebuggerTypeProxy` deduce los parámetros de tipo automáticamente.  
  
 Para obtener más información sobre los tipos abiertos y cerrados en C#, vea [Especificación del lenguaje C#](https://msdn.microsoft.com/library/e5d5a5cc-636b-4bff-b9c8-a8edc6207c22), sección 20.5.2 Tipos abiertos y cerrados.  
  
 Visual Basic no tiene sintaxis de tipos abiertos, por lo que no se puede hacer lo mismo en Visual Basic. En su lugar, debe utilizar una representación de cadena del nombre del tipo abierto.  
  
 `"Namespace.TypeName'2"`  
  
## <a name="see-also"></a>Consulte también  
 [Usar el atributo DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md)   
  [Mejorar la depuración con los atributos de visualización del depurador](https://msdn.microsoft.com/library/72bb7aa9-459b-42c4-9163-9312fab4c410)
