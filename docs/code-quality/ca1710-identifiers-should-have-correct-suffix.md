---
title: "CA1710: Los identificadores deberían tener el sufijo correcto | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1710
- IdentifiersShouldHaveCorrectSuffix
helpviewer_keywords:
- IdentifiersShouldHaveCorrectSuffix
- CA1710
ms.assetid: 2b8e6dce-b4e8-4a66-ba9a-6b79be5bfe8c
caps.latest.revision: "20"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 4fd4f23ab77e2b810d5064bd45e9f7d530e9844e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="ca1710-identifiers-should-have-correct-suffix"></a>CA1710: Los identificadores deberían tener el sufijo correcto
|||  
|-|-|  
|TypeName|IdentifiersShouldHaveCorrectSuffix|  
|Identificador de comprobación|CA1710|  
|Categoría|Microsoft.Naming|  
|Cambio problemático|Problemático|  
  
## <a name="cause"></a>Motivo  
 Un identificador no tiene el sufijo correcto.  
  
## <a name="rule-description"></a>Descripción de la regla  
 Por convención, los nombres de tipos que extienden determinados tipos base o que implementan algunas interfaces, o tipos derivados de estos tipos, tienen un sufijo asociado al tipo base o interfaz.  
  
 Las convenciones de nomenclatura proporcionan una apariencia común para las bibliotecas destinadas a Common Language Runtime. Esto reduce la curva de aprendizaje necesaria para las nuevas bibliotecas de software y aumenta la confianza del cliente respecto a que la biblioteca se haya desarrollado por parte de un especialista en desarrollo de código administrado.  
  
 En la tabla siguiente se enumera los tipos base e interfaces que tienen asociados sufijos.  
  
|Tipo base/Interfaz|Sufijo|  
|--------------------------|------------|  
|<xref:System.Attribute?displayProperty=fullName>|Atributo|  
|<xref:System.EventArgs?displayProperty=fullName>|EventArgs|  
|<xref:System.Exception?displayProperty=fullName>|Excepción|  
|<xref:System.Collections.ICollection?displayProperty=fullName>|Collection|  
|<xref:System.Collections.IDictionary?displayProperty=fullName>|Dictionary|  
|<xref:System.Collections.IEnumerable?displayProperty=fullName>|Collection|  
|<xref:System.Collections.Queue?displayProperty=fullName>|Colección o cola|  
|<xref:System.Collections.Stack?displayProperty=fullName>|Colección o pila|  
|<xref:System.Collections.Generic.ICollection%601?displayProperty=fullName>|Collection|  
|<xref:System.Collections.Generic.IDictionary%602?displayProperty=fullName>|Dictionary|  
|<xref:System.Data.DataSet?displayProperty=fullName>|DataSet|  
|<xref:System.Data.DataTable?displayProperty=fullName>|Colección o DataTable|  
|<xref:System.IO.Stream?displayProperty=fullName>|Secuencia|  
|<xref:System.Security.IPermission?displayProperty=fullName>|Permiso|  
|<xref:System.Security.Policy.IMembershipCondition?displayProperty=fullName>|Condición|  
|Un delegado de controlador de eventos.|EventHandler|  
  
 Los tipos que implementan <xref:System.Collections.ICollection> y son un tipo generalizado de estructura de datos, como un diccionario, una pila o una cola, se permiten nombres que proporcione información significativa sobre el uso previsto del tipo.  
  
 Los tipos que implementan <xref:System.Collections.ICollection> y son una colección de elementos específicos tienen nombres que terminan con la palabra "Collection". Por ejemplo, una colección de <xref:System.Collections.Queue> objetos tendría el nombre "QueueCollection". El sufijo "Collection" significa que se pueden enumerar los miembros de la colección utilizando la `foreach` (`For Each` en [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) instrucción.  
  
 Los tipos que implementan <xref:System.Collections.IDictionary> tienen nombres que terminan con la palabra "Dictionary" incluso si el tipo también implementa <xref:System.Collections.IEnumerable> o <xref:System.Collections.ICollection>. Las convenciones de nomenclatura de sufijo "Collection" y "Dictionary" permiten a los usuarios distinguir entre los siguientes dos modelos de enumeración.  
  
 Los tipos con el sufijo "Collection" siguen este patrón de enumeración.  
  
```  
foreach(SomeType x in SomeCollection) { }  
```  
  
 Los tipos con el sufijo "Dictionary" siguen este patrón de enumeración.  
  
```  
foreach(SomeType x in SomeDictionary.Values) { }  
```  
  
 A <xref:System.Data.DataSet> objeto consta de una colección de <xref:System.Data.DataTable> objetos, que consisten en colecciones de <xref:System.Data.DataColumn?displayProperty=fullName> y <xref:System.Data.DataRow?displayProperty=fullName> objetos, entre otros. Estas colecciones implementan <xref:System.Collections.ICollection> a través de la base de <xref:System.Data.InternalDataCollectionBase?displayProperty=fullName> clase.  
  
## <a name="how-to-fix-violations"></a>Cómo corregir infracciones  
 Cambie el nombre del tipo para que se utiliza como sufijo con el término correcto.  
  
## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias  
 Es seguro suprimir una advertencia al utilizar el sufijo "Collection" si el tipo es una estructura de datos generalizada que podría ampliarse o que contendrá un conjunto arbitrario de elementos diversos. En este caso, un nombre que proporcione información significativa sobre la implementación, rendimiento u otras características de la estructura de datos podría tener sentido (por ejemplo, BinaryTree). En casos donde el tipo representa una colección de un tipo específico (por ejemplo, StringCollection), no suprima las advertencias de esta regla porque el sufijo indica que el tipo se puede enumerar mediante el uso de un `foreach` instrucción.  
  
 Para otros sufijos, no suprima las advertencias de esta regla. El sufijo permite el uso previsto sea evidente a partir del nombre de tipo.  
  
## <a name="related-rules"></a>Reglas relacionadas  
 [CA1711: Los identificadores no deberían tener el sufijo incorrecto](../code-quality/ca1711-identifiers-should-not-have-incorrect-suffix.md)  
  
## <a name="see-also"></a>Vea también  
 [Attributes](/dotnet/standard/design-guidelines/attributes)  (Atributos)  
 [Controlar y provocar eventos](/dotnet/standard/events/index)  