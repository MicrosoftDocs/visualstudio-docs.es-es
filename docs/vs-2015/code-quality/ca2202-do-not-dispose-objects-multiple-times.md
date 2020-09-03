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
ms.openlocfilehash: 31bf7fe33aa59c3a713d2da81ddbd11ed6899723
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85546294"
---
# <a name="ca2202-do-not-dispose-objects-multiple-times"></a>CA2202: No usar Dispose varias veces en objetos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|Value|
|-|-|
|TypeName|DoNotDisposeObjectsMultipleTimes|
|Identificador de comprobación|CA2202|
|Category|Microsoft. Usage|
|Cambio problemático|No trascendental|

## <a name="cause"></a>Causa
 Una implementación de método contiene rutas de acceso de código que podrían provocar varias llamadas a <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> o un equivalente de Dispose, como un método Close () en algunos tipos, en el mismo objeto.

## <a name="rule-description"></a>Descripción de la regla
 Se puede llamar a un método correctamente implementado <xref:System.IDisposable.Dispose%2A> varias veces sin producir una excepción. Sin embargo, esto no se garantiza y, para evitar que se genere, <xref:System.ObjectDisposedException?displayProperty=fullName> no se debe llamar a <xref:System.IDisposable.Dispose%2A> más de una vez en un objeto.

## <a name="related-rules"></a>Reglas relacionadas
 [CA2000: Desechar objetos antes de perder el ámbito](../code-quality/ca2000-dispose-objects-before-losing-scope.md)

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, cambie la implementación para que, independientemente de la ruta de acceso del código, <xref:System.IDisposable.Dispose%2A> se llame solo una vez para el objeto.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima las advertencias de esta regla. Incluso si <xref:System.IDisposable.Dispose%2A> se sabe que para el objeto se puede llamar con seguridad varias veces, la implementación podría cambiar en el futuro.

## <a name="example"></a>Ejemplo
 `using`Las instrucciones anidadas ( `Using` en Visual Basic) pueden producir infracciones de la advertencia CA2202. Si el recurso IDisposable de la instrucción interna anidada `using` contiene el recurso de la `using` instrucción externa, el `Dispose` método del recurso anidado libera el recurso contenido. Cuando se produce esta situación, el `Dispose` método de la `using` instrucción externa intenta desechar su recurso por segunda vez.

 En el ejemplo siguiente, un <xref:System.IO.Stream> objeto que se crea en una instrucción using externa se libera al final de la instrucción using interna en el método Dispose del <xref:System.IO.StreamWriter> objeto que contiene el `stream` objeto. Al final de la instrucción externa `using` , el `stream` objeto se libera una segunda vez. La segunda versión es una infracción de CA2202.

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
 Para resolver este problema, use un `try` / `finally` bloque en lugar de la `using` instrucción externa. En el `finally` bloque, asegúrese de que el `stream` recurso no sea NULL.

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

## <a name="see-also"></a>Consulte también
 <xref:System.IDisposable?displayProperty=fullName> [Patrón de Dispose](https://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)
