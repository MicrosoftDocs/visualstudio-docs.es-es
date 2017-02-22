---
title: "CA1058: Los tipos no deben ampliar ciertos tipos base | Microsoft Docs"
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
  - "TypesShouldNotExtendCertainBaseTypes"
  - "CA1058"
helpviewer_keywords: 
  - "CA1058"
  - "TypesShouldNotExtendCertainBaseTypes"
ms.assetid: 8446ee40-beb1-49fa-8733-4d8e813471c0
caps.latest.revision: 24
caps.handback.revision: 24
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1058: Los tipos no deben ampliar ciertos tipos base
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|TypesShouldNotExtendCertainBaseTypes|  
|Identificador de comprobación|CA1058|  
|Categoría|Microsoft.Design|  
|Cambio problemático|Problemático|  
  
## Motivo  
 Un tipo visible externamente extiende algunos tipos base.  En la actualidad, esta regla muestra los tipos que se derivan de los tipos siguientes:  
  
-   <xref:System.ApplicationException?displayProperty=fullName>  
  
-   <xref:System.Xml.XmlDocument?displayProperty=fullName>  
  
-   <xref:System.Collections.CollectionBase?displayProperty=fullName>  
  
-   <xref:System.Collections.DictionaryBase?displayProperty=fullName>  
  
-   <xref:System.Collections.Queue?displayProperty=fullName>  
  
-   <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>  
  
-   <xref:System.Collections.SortedList?displayProperty=fullName>  
  
-   <xref:System.Collections.Stack?displayProperty=fullName>  
  
## Descripción de la regla  
 En [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] versión 1, se recomendaba derivar las nuevas excepciones de <xref:System.ApplicationException>.  La recomendación ha cambiado y las nuevas excepciones deberían derivar de <xref:System.Exception?displayProperty=fullName> o de una de sus subclases en el espacio de nombres <xref:System>.  
  
 No cree una subclase de <xref:System.Xml.XmlDocument> si desea crear una vista de XML de un modelo de objetos u origen de datos subyacente.  
  
### Colecciones no genéricas  
 Utilice y\/o extienda las colecciones genéricas siempre que sea posible.  No extienda las colecciones no genéricas en su código, a menos que previamente lo hubiera distribuido.  
  
 **Ejemplos de uso incorrecto**  
  
```c#  
public class MyCollection : CollectionBase  
{  
}  
  
public class MyReadOnlyCollection : ReadOnlyCollectionBase  
{  
}  
```  
  
 **Ejemplos de uso correcto**  
  
```c#  
public class MyCollection : Collection<T>  
{  
}  
  
public class MyReadOnlyCollection : ReadOnlyCollection<T>  
{  
}  
```  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla, derive el tipo desde un tipo base diferente o desde una colección genérica.  
  
## Cuándo suprimir advertencias  
 No suprima una advertencia de esta regla para las infracciones relativas a <xref:System.ApplicationException>.  Es seguro suprimir una advertencia de esta regla para las infracciones relativas a <xref:System.Xml.XmlDocument>.  Es seguro suprimir una advertencia sobre una colección no genérica si previamente se liberó código.