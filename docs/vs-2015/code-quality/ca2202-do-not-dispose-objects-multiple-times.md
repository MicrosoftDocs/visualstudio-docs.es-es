---
title: 'CA2202: no eliminar objetos varias veces | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2202
- Do not dispose objects multiple times
- DoNotDisposeObjectsMultipleTimes
helpviewer_keywords:
- CA2202
ms.assetid: fa85349a-cf1e-42c8-a86b-eacae1f8bd96
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: e0be715d8aea84fac53ea2a796e71850b961730c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72667398"
---
# <a name="ca2202-do-not-dispose-objects-multiple-times"></a>CA2202: No aplicar Dispose a los objetos varias veces
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotDisposeObjectsMultipleTimes|
|Identificador de comprobación|CA2202|
|Categoría|Microsoft. Usage|
|Cambio problemático|No trascendental|

## <a name="cause"></a>Motivo
 Una implementación de método contiene rutas de acceso de código que pueden hacer que varias llamadas a <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> o un equivalente de Dispose, como un método Close () en algunos tipos, en el mismo objeto.

## <a name="rule-description"></a>Descripción de la regla
 Se puede llamar varias veces a un método <xref:System.IDisposable.Dispose%2A> implementado correctamente sin producir una excepción. Sin embargo, esto no se garantiza y, para evitar que se genere un <xref:System.ObjectDisposedException?displayProperty=fullName> no debe llamar a <xref:System.IDisposable.Dispose%2A> más de una vez en un objeto.

## <a name="related-rules"></a>Reglas relacionadas
 [CA2000: Desechar (Dispose) objetos antes de perder el ámbito](../code-quality/ca2000-dispose-objects-before-losing-scope.md)

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, cambie la implementación para que independientemente de la ruta de acceso del código, <xref:System.IDisposable.Dispose%2A> se llame solo una vez para el objeto.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima las advertencias de esta regla. Incluso si se sabe que <xref:System.IDisposable.Dispose%2A> para el objeto se puede llamar con seguridad varias veces, la implementación podría cambiar en el futuro.

## <a name="example"></a>Ejemplo
 Las instrucciones anidadas `using` (`Using` en Visual Basic) pueden producir infracciones de la advertencia CA2202. Si el recurso IDisposable de la instrucción anidada `using` interna contiene el recurso de la instrucción `using` externa, el método `Dispose` del recurso anidado libera el recurso contenido. Cuando se produce esta situación, el método `Dispose` de la instrucción `using` externa intenta desechar su recurso por segunda vez.

 En el ejemplo siguiente, un objeto <xref:System.IO.Stream> que se crea en una instrucción using externa se libera al final de la instrucción using interna en el método Dispose del objeto <xref:System.IO.StreamWriter> que contiene el objeto `stream`. Al final de la instrucción `using` externa, el objeto `stream` se libera por segunda vez. La segunda versión es una infracción de CA2202.

```
using (Stream stream = new FileStream("file.txt", FileMode.OpenOrCreate))
{
    using (StreamWriter writer = new StreamWriter(stream))
    {
        // Use the writer object...
    }
}
```

## <a name="example"></a>Ejemplo
 Para resolver este problema, use una `try` / bloque `finally` en lugar de la instrucción de `using` externa. En el bloque `finally`, asegúrese de que el recurso `stream` no sea NULL.

```
Stream stream = null;
try
{
    stream = new FileStream("file.txt", FileMode.OpenOrCreate);
    using (StreamWriter writer = new StreamWriter(stream))
    {
        stream = null;
        // Use the writer object...
    }
}
finally
{
    if(stream != null)
        stream.Dispose();
}
```

## <a name="see-also"></a>Vea también
 <xref:System.IDisposable?displayProperty=fullName> [modelo de Dispose](https://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)
