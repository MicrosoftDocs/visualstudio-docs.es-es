---
title: Mostrar tipo personalizado con DebuggerTypeProxy | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- attributes [C#], debugger
- DebuggerTypeProxyAttribute class
- DebuggerTypeProxy attribute
ms.assetid: 943f3bb1-993e-4800-a47e-0af78b063014
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c379fbeb9d17f92dcc7067424ea06bb1a2805ed1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62929635"
---
# <a name="tell-the-debugger-what-type-to-show-using-debuggertypeproxy-attribute-c-visual-basic-ccli"></a>Indicar al depurador qué tipo a se muestra el uso del atributo DebuggerTypeProxy (C#, Visual Basic, C++/CLI)

<xref:System.Diagnostics.DebuggerTypeProxyAttribute> especifica un proxy, o suplente, para un tipo y cambia la forma en que se muestra el tipo en las ventanas del depurador. Cuando se ve una variable que tiene un proxy, el proxy reemplaza al tipo original en la **presentación**. En la ventana de las variables del depurador se muestran sólo los miembros públicos del tipo de servidor proxy. No se muestran los miembros privados.

Este atributo se puede aplicar a:

- Estructuras
- Clases
- Ensamblados

> [!NOTE]
> Para código nativo, este atributo solo se admite en C++código /CLI.

Una clase de proxy de tipo debe tener un constructor que tome un argumento del tipo que el proxy reemplazará. El depurador crea una nueva instancia de la clase de proxy de tipo cada vez que necesita mostrar una variable del tipo de destino. Esto puede afectar al rendimiento. Por tanto, en el constructor no debe realizarse más trabajo del estrictamente necesario.

Para minimizar la reducción de rendimiento, el evaluador de expresiones no examina los atributos en el proxy de presentación del tipo, a menos que el usuario expanda el tipo haciendo clic en el símbolo + en la ventana del depurador o mediante <xref:System.Diagnostics.DebuggerBrowsableAttribute>. Por consiguiente, no se deben colocar atributos en el propio tipo de presentación. Los atributos pueden y deben utilizarse en el cuerpo del tipo de presentación.

Se recomienda que el proxy de tipo sea una clase anidada privada dentro de la clase que el atributo tiene como destino. De este modo, puede obtener acceso fácilmente a los miembros internos.

<xref:System.Diagnostics.DebuggerTypeProxyAttribute> se puede heredar, por lo que si se especifica un proxy de tipo en una clase base se aplicará a todas las clases derivadas, a menos que las clases derivadas especifican a su propio proxy de tipo.

Si se utiliza <xref:System.Diagnostics.DebuggerTypeProxyAttribute> en el nivel de ensamblado, el parámetro `Target` especifica el tipo que reemplazará el proxy.

Para obtener un ejemplo de cómo utilizar este atributo junto con <xref:System.Diagnostics.DebuggerDisplayAttribute> y <xref:System.Diagnostics.DebuggerTypeProxyAttribute>, consulte[utilizando el atributo DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md).

## <a name="using-generics-with-debuggertypeproxy"></a>Utilizar genéricos con DebuggerTypeProxy

La compatibilidad con los genéricos es limitada. En C#, `DebuggerTypeProxy` solo acepta tipos abiertos. Un tipo abierto, también denominado tipo no construido, es un tipo genérico de cuyos parámetros de tipo no se han creado instancias con argumentos. No se admiten los tipos cerrados, también denominados tipos construidos.

La sintaxis de un tipo abierto tiene el siguiente aspecto:

`Namespace.TypeName<,>`

Si utiliza un tipo genérico como destino en `DebuggerTypeProxy`, debe utilizar esta sintaxis. El mecanismo `DebuggerTypeProxy` deduce los parámetros de tipo automáticamente.

Para obtener más información sobre los tipos abiertos y cerrados en C#, vea el [especificación del lenguaje C#](/dotnet/csharp/language-reference/language-specification), abra la sección 20.5.2 tipos y cerrados.

Visual Basic no tiene sintaxis de tipos abiertos, por lo que no se puede hacer lo mismo en Visual Basic. En su lugar, debe utilizar una representación de cadena del nombre del tipo abierto.

`"Namespace.TypeName'2"`

## <a name="see-also"></a>Vea también

- [Usar el atributo DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md)
- [Crear vistas personalizadas de objetos administrados](../debugger/create-custom-views-of-dot-managed-objects.md)
- [Mejorar la depuración con los atributos de visualización del depurador](/dotnet/framework/debug-trace-profile/enhancing-debugging-with-the-debugger-display-attributes)
