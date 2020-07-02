---
title: 'CA1812: Evite las clases internas sin instancias | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1812
- AvoidUninstantiatedInternalClasses
helpviewer_keywords:
- AvoidUninstantiatedInternalClasses
- CA1812
ms.assetid: 1bb92a42-322a-44cc-98a8-8858212c1e1f
caps.latest.revision: 28
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 401fbfbccfeeeeec5cbdc0e791b110d1b5f0201b
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/30/2020
ms.locfileid: "85543980"
---
# <a name="ca1812-avoid-uninstantiated-internal-classes"></a>CA1812: Evitar las clases internas sin instancia
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|Valor|
|-|-|
|TypeName|AvoidUninstantiatedInternalClasses|
|Identificador de comprobación|CA1812|
|Categoría|Microsoft. performance|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Causa
 El código del ensamblado no crea una instancia del tipo del nivel de ensamblado.

## <a name="rule-description"></a>Descripción de la regla
 Esta regla intenta localizar una llamada a uno de los constructores del tipo y notifica una infracción si no se encuentra ninguna llamada.

 Esta regla no examina los siguientes tipos:

- Tipos de valor

- Tipos abstractos

- Enumeraciones

- Delegados

- Tipos de matriz emitidos por el compilador

- Tipos de los que no se pueden crear instancias y que `static` `Shared` solo definen métodos (en Visual Basic).

  Si se aplica <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute?displayProperty=fullName> al ensamblado que se está analizando, esta regla no se producirá en los constructores que estén marcados como `internal` porque no se puede saber si un campo está siendo utilizado por otro `friend` ensamblado.

  Aunque no puede solucionar esta limitación en el [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] análisis de código, el FxCop independiente externo se producirá en los constructores internos si cada `friend` ensamblado está presente en el análisis.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, quite el tipo o agregue el código que lo usa. Si el tipo solo contiene métodos estáticos, agregue uno de los siguientes al tipo para evitar que el compilador emita un constructor de instancia público predeterminado:

- Constructor privado para los tipos que tienen como destino [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] las versiones 1,0 y 1,1.

- `static` `Shared` Modificador (en Visual Basic) para los tipos que tienen como destino [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)] .

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Es seguro suprimir una advertencia de esta regla. Se recomienda suprimir esta advertencia en las situaciones siguientes:

- La clase se crea mediante métodos de reflexión enlazados en tiempo de ejecución como <xref:System.Activator.CreateInstance%2A?displayProperty=fullName> .

- La clase la crea automáticamente el motor en tiempo de ejecución o [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] . Por ejemplo, las clases que implementan <xref:System.Configuration.IConfigurationSectionHandler?displayProperty=fullName> o <xref:System.Web.IHttpHandler?displayProperty=fullName> .

- La clase se pasa como un parámetro de tipo genérico que tiene una nueva restricción. Por ejemplo, en el ejemplo siguiente se generará esta regla.

  ```csharp
  internal class MyClass
  {
      public DoSomething()
      {
      }
  }
  public class MyGeneric<T> where T : new()
  {
      public T Create()
      {
          return new T();
      }
  }
  // [...]
  MyGeneric<MyClass> mc = new MyGeneric<MyClass>();
  mc.Create();
  ```

  En estas situaciones, se recomienda suprimir esta advertencia.

## <a name="related-rules"></a>Reglas relacionadas
 [CA1811: Evitar código privado al que no se llama](../code-quality/ca1811-avoid-uncalled-private-code.md)

 [CA1801: Revisar parámetros sin utilizar](../code-quality/ca1801-review-unused-parameters.md)

 [CA1804: Quitar variables locales no utilizadas](../code-quality/ca1804-remove-unused-locals.md)
