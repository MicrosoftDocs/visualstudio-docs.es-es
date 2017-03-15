---
title: "CA2202: No aplicar Dispose a los objetos varias veces | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2202"
  - "Do not dispose objects multiple times"
  - "DoNotDisposeObjectsMultipleTimes"
helpviewer_keywords: 
  - "CA2202"
ms.assetid: fa85349a-cf1e-42c8-a86b-eacae1f8bd96
caps.latest.revision: 20
caps.handback.revision: 20
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2202: No aplicar Dispose a los objetos varias veces
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotDisposeObjectsMultipleTimes|  
|Identificador de comprobación|CA2202|  
|Categoría|Microsoft.Usage|  
|Cambio problemático|No|  
  
## Motivo  
 Una implementación de un método contiene rutas de acceso del código que podrían provocar varias llamadas a <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> o a un equivalente de Dispose, como un método Close\(\) en algunos tipos, en el mismo objeto.  
  
## Descripción de la regla  
 Se puede llamar varias veces a un método <xref:System.IDisposable.Dispose%2A> implementado correctamente sin iniciar una excepción.  Sin embargo, no está garantizado; en consecuencia, para evitar que se genere una excepción <xref:System.ObjectDisposedException?displayProperty=fullName>, no se debe llamar a <xref:System.IDisposable.Dispose%2A> más de una vez en un objeto.  
  
## Reglas relacionadas  
 [CA2000: Eliminar objetos antes de perder el ámbito](../code-quality/ca2000-dispose-objects-before-losing-scope.md)  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla, cambie la implementación de modo que únicamente se llame a <xref:System.IDisposable.Dispose%2A> una vez para el objeto, independientemente de la ruta de acceso del código.  
  
## Cuándo suprimir advertencias  
 No suprima las advertencias de esta regla.  Aunque sepa que <xref:System.IDisposable.Dispose%2A> es invocable varias veces para el objeto con seguridad, la implementación podría cambiar en el futuro.  
  
## Ejemplo  
 Las instrucciones `using` anidadas \(`Using` en Visual Basic\) pueden producir infracciones de la advertencia CA2202.  Si el recurso IDisposable de la instrucción `using` interna anidada contiene el recurso de la instrucción `using` exterior, el método `Dispose` del recurso anidado libera el recurso contenido.  Cuando esta situación se produce, el método `Dispose` de la instrucción `using` exterior intenta disponer de su recurso durante una segunda vez.  
  
 En el ejemplo siguiente, un objeto <xref:System.IO.Stream> que se crea en una instrucción using externa se libera al final de la instrucción using interna en el método Dispose del objeto <xref:System.IO.StreamWriter> que contiene el objeto `stream`.  Al final de la instrucción exterior `using`, el objeto de `stream` se libera una segunda vez.  La segunda versión es una infracción de CA2202.  
  
```  
using (Stream stream = new FileStream("file.txt", FileMode.OpenOrCreate))  
{  
    using (StreamWriter writer = new StreamWriter(stream))  
    {  
        // Use the writer object...  
    }  
}  
  
```  
  
## Ejemplo  
 Para resolver este problema, use el bloque `try`\/`finally` en lugar de la instrucción `using` exterior.  En el bloque `finally`, asegúrese de que el recurso `stream` no es NULL.  
  
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
  
## Vea también  
 <xref:System.IDisposable?displayProperty=fullName>   
 [Patrón de Dispose](../Topic/Dispose%20Pattern.md)