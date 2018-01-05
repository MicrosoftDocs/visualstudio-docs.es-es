---
title: 'CA1058: Los tipos no deben ampliar ciertos tipos base | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- TypesShouldNotExtendCertainBaseTypes
- CA1058
helpviewer_keywords:
- CA1058
- TypesShouldNotExtendCertainBaseTypes
ms.assetid: 8446ee40-beb1-49fa-8733-4d8e813471c0
caps.latest.revision: "24"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: c042c854e535f764fe4e0eac01a0e66aa5b49f20
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="ca1058-types-should-not-extend-certain-base-types"></a>CA1058: Los tipos no deben ampliar ciertos tipos base
|||  
|-|-|  
|TypeName|TypesShouldNotExtendCertainBaseTypes|  
|Identificador de comprobación|CA1058|  
|Categoría|Microsoft.Design|  
|Cambio problemático|Problemático|  
  
## <a name="cause"></a>Motivo  
 Un tipo visible externamente extiende algunos tipos base. Actualmente, esta regla notifica tipos que derivan de los tipos siguientes:  
  
-   <xref:System.ApplicationException?displayProperty=fullName>  
  
-   <xref:System.Xml.XmlDocument?displayProperty=fullName>  
  
-   <xref:System.Collections.CollectionBase?displayProperty=fullName>  
  
-   <xref:System.Collections.DictionaryBase?displayProperty=fullName>  
  
-   <xref:System.Collections.Queue?displayProperty=fullName>  
  
-   <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>  
  
-   <xref:System.Collections.SortedList?displayProperty=fullName>  
  
-   <xref:System.Collections.Stack?displayProperty=fullName>  
  
## <a name="rule-description"></a>Descripción de la regla  
 Para [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] versión 1, se recomendaba derivar las nuevas excepciones de <xref:System.ApplicationException>. Ha cambiado la recomendación y nuevas excepciones deben derivarse de <xref:System.Exception?displayProperty=fullName> o una de sus subclases en el <xref:System> espacio de nombres.  
  
 No cree una subclase de <xref:System.Xml.XmlDocument> si desea crear una vista XML de un origen de datos o el modelo de objeto subyacente.  
  
### <a name="non-generic-collections"></a>Colecciones no genéricas  
 Utilice o extienda las colecciones genéricas siempre que sea posible. No se extienden colecciones no genéricas en el código, a menos que envió previamente.  
  
 **Ejemplos de uso incorrecto**  
  
```csharp  
public class MyCollection : CollectionBase  
{  
}  
  
public class MyReadOnlyCollection : ReadOnlyCollectionBase  
{  
}  
```  
  
 **Ejemplos de uso correcto**  
  
```csharp  
public class MyCollection : Collection<T>  
{  
}  
  
public class MyReadOnlyCollection : ReadOnlyCollection<T>  
{  
}  
```  
  
## <a name="how-to-fix-violations"></a>Cómo corregir infracciones  
 Para corregir una infracción de esta regla, derive el tipo de un tipo base diferente o una colección genérica.  
  
## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias  
 No suprima las advertencias de esta regla para las infracciones sobre <xref:System.ApplicationException>. Es seguro suprimir una advertencia de esta regla si hay infracciones de sobre <xref:System.Xml.XmlDocument>. Es seguro suprimir una advertencia sobre una colección no genérica si previamente se liberó el código.