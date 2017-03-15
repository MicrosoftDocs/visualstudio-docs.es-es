---
title: "CA1710: Los identificadores deber&#237;an tener el sufijo correcto | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1710"
  - "IdentifiersShouldHaveCorrectSuffix"
helpviewer_keywords: 
  - "IdentifiersShouldHaveCorrectSuffix"
  - "CA1710"
ms.assetid: 2b8e6dce-b4e8-4a66-ba9a-6b79be5bfe8c
caps.latest.revision: 20
caps.handback.revision: 20
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1710: Los identificadores deber&#237;an tener el sufijo correcto
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|IdentifiersShouldHaveCorrectSuffix|  
|Identificador de comprobación|CA1710|  
|Categoría|Microsoft.Naming|  
|Cambio problemático|Problemático|  
  
## Motivo  
 Un identificador no tiene el sufijo correcto.  
  
## Descripción de la regla  
 Por convención, los nombres de tipos que extienden determinados tipos base o que implementan algunas interfaces, o tipos derivados de estos tipos, tienen un sufijo asociado al tipo base o a la interfaz.  
  
 Las convenciones de nomenclatura proporcionan una apariencia común para las bibliotecas destinadas a Common Language Runtime.  Esto reduce la curva de aprendizaje necesaria para las nuevas bibliotecas de software y aumenta la confianza del cliente respecto a que la biblioteca se haya desarrollado por parte de un especialista en desarrollo de código administrado.  
  
 La tabla siguiente muestra los tipos base e interfaces con sufijos asociados.  
  
|Tipo base\/Interfaz|Sufijo|  
|-------------------------|------------|  
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
|<xref:System.IO.Stream?displayProperty=fullName>|Stream|  
|<xref:System.Security.IPermission?displayProperty=fullName>|Permiso|  
|<xref:System.Security.Policy.IMembershipCondition?displayProperty=fullName>|Condition|  
|Un delegado de controlador de eventos.|EventHandler|  
  
 Los tipos que implementan <xref:System.Collections.ICollection> y que son un tipo de estructura de datos generalizada, como un diccionario, un pila o cola, son nombres permitidos que proporcionan información significativa sobre el uso que se le va a dar al tipo.  
  
 Los tipos que implementan <xref:System.Collections.ICollection> y que forman parte de la colección de elementos específicos tienen nombres que terminan con la palabra "Collection".  Por ejemplo, una colección de objetos <xref:System.Collections.Queue> tendría el nombre "QueueCollection".  El sufijo "Collection" significa que los miembros de la colección se pueden enumerar mediante la instrucción `foreach` \(`For Each` en [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\).  
  
 Los tipos que implementan <xref:System.Collections.IDictionary> tienen nombres que finalizan con la palabra "Dictionary" incluso si el tipo también implementa <xref:System.Collections.IEnumerable> o <xref:System.Collections.ICollection>.  Las convenciones de nomenclatura de uso de los sufijos "Collection" y "Dictionary" permiten a los usuarios distinguir entre los dos modelos de enumeración siguientes.  
  
 Los tipos con el sufijo "Collection" siguen este modelo de enumeración.  
  
```  
foreach(SomeType x in SomeCollection) { }  
```  
  
 Los tipos con el sufijo "Dictionary" siguen este modelo de enumeración.  
  
```  
foreach(SomeType x in SomeDictionary.Values) { }  
```  
  
 Un objeto <xref:System.Data.DataSet> está compuesto de una colección de objetos <xref:System.Data.DataTable>, compuestos de colecciones de <xref:System.Data.DataColumn?displayProperty=fullName> y objetos <xref:System.Data.DataRow?displayProperty=fullName>, entre otros.  Estas colecciones implementan <xref:System.Collections.ICollection> mediante de la clase base <xref:System.Data.InternalDataCollectionBase?displayProperty=fullName>.  
  
## Cómo corregir infracciones  
 Cambie el nombre del tipo para aplicar el sufijo con el término correcto.  
  
## Cuándo suprimir advertencias  
 Es seguro suprimir una advertencia al utilizar el sufijo "Collection" si el tipo tiene una estructura de datos generalizada que podría extenderse o contener una conjunto arbitrario de elementos diversos.  En ese caso, podría tener sentido un nombre que proporciona información significativa sobre la implementación, rendimiento u otras características de la estructura de datos \(por ejemplo, BinaryTree\).  En los casos en que un tipo representa una colección de un tipo específico \(por ejemplo, StringCollection\), no suprima ninguna advertencia de esta regla porque el sufijo indica que el tipo puede enumerarse mediante una instrucción `foreach`.  
  
 En caso de otros sufijos, no suprima ninguna advertencia de esta regla.  El sufijo permite el uso que se le pretende dar resulte evidente por el nombre de tipo.  
  
## Reglas relacionadas  
 [CA1711: Los identificadores no deberían tener el sufijo incorrecto](../code-quality/ca1711-identifiers-should-not-have-incorrect-suffix.md)  
  
## Vea también  
 [Atributos](../Topic/Attributes1.md)   
 [Eventos y delegados](http://msdn.microsoft.com/es-es/d98fd58b-fa4f-4598-8378-addf4355a115)