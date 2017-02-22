---
title: "CA1822: Marcar el miembro como est&#225;tico | Microsoft Docs"
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
  - "MarkMembersAsStatic"
  - "CA1822"
helpviewer_keywords: 
  - "MarkMethodsAsStatic"
  - "CA1822"
ms.assetid: 743f0af7-41d1-4852-8d97-af0688b31118
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1822: Marcar el miembro como est&#225;tico
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|MarkMembersAsStatic|  
|Identificador de comprobación|CA1822|  
|Categoría|Microsoft.Performance|  
|Cambio problemático|Poco problemático: si el miembro no se puede ver fuera del ensamblado, independientemente del cambio realizado.  Poco importante: si solo cambia el miembro por un miembro de instancia con la palabra clave `this`.<br /><br /> Problemático: si cambia el miembro de un miembro de instancia por un miembro estático y se puede ver fuera del ensamblado.|  
  
## Motivo  
 Un miembro que no tiene acceso a los datos de instancia no se marca como static \(Shared en [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\).  
  
## Descripción de la regla  
 Los miembros que no tienen acceso a datos de instancia o que llaman a métodos de instancia se pueden marcar como static \(Shared en [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\).  Después de marcar los métodos como static, el compilador emite los sitios de llamada no virtuales para estos miembros.  Al emitir los sitios de llamada no virtuales, se evita tener que comprobar para cada llamada en tiempo de ejecución que el puntero de objeto actual no es null.  Esto puede proporcionar una mejora apreciable del rendimiento del código en el que el rendimiento es fundamental.  En algunos casos, la imposibilidad de tener acceso a la instancia del objeto actual representa un problema de corrección.  
  
## Cómo corregir infracciones  
 Marque el miembro como static \(o Shared en [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\) o utilice 'this'\/'Me' en el cuerpo del método, si es apropiado.  
  
## Cuándo suprimir advertencias  
 Es seguro suprimir una advertencia de esta regla para el código previamente distribuido para el que la corrección supondría un cambio importante.  
  
## Reglas relacionadas  
 [CA1811: Evitar código privado al que no se llama](../code-quality/ca1811-avoid-uncalled-private-code.md)  
  
 [CA1812: Evitar las clases internas sin instancia](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)  
  
 [CA1804: Quitar variables locales no utilizadas](../code-quality/ca1804-remove-unused-locals.md)