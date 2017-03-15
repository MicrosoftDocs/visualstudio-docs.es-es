---
title: "La clase base &#39;&lt;nombreDeClaseBase&gt;&#39; ya ha implementado &#39;&lt;nombreDeInterfazBase&gt;.&lt;nombreDeMiembro&gt;&#39; de &#39;implements &lt;nombreDeInterfazDerivada&gt;&#39;. Se supone que &lt;tipo&gt; se implementa de nuevo | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc42014"
  - "vbc42014"
helpviewer_keywords: 
  - "BC42014"
ms.assetid: 95fff622-5d54-4ec8-90f0-477de1d58687
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# La clase base &#39;&lt;nombreDeClaseBase&gt;&#39; ya ha implementado &#39;&lt;nombreDeInterfazBase&gt;.&lt;nombreDeMiembro&gt;&#39; de &#39;implements &lt;nombreDeInterfazDerivada&gt;&#39;. Se supone que &lt;tipo&gt; se implementa de nuevo
Una propiedad, un procedimiento o un evento en una clase derivada usa una cláusula `Implements` que especifica un miembro de interfaz derivado ya implementado en la interfaz base de la clase base.  
  
 El miembro que se implementa se define mediante la interfaz base y se hereda de la interfaz derivada. La clase base implementa directamente la interfaz base. La clase derivada implementa la interfaz derivada y puede obviar con facilidad el hecho de que la clase base ya ha implementado el miembro.  
  
 Una clase derivada puede volver a implementar un miembro de interfaz implementado por su clase base. Esto no es el mismo que reemplazar la implementación de la clase base. Para obtener más información, consulte [Implements](/dotnet/visual-basic/language-reference/statements/implements-clause).  
  
 De forma predeterminada, este mensaje es una advertencia. Para obtener información sobre cómo ocultar las advertencias o cómo tratarlas como errores, vea [Configurar advertencias en Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **Identificador de error:** BC42014  
  
### Para corregir este error  
  
-   Si piensa volver a implementar el miembro de interfaz, no es necesario realizar ninguna acción. El código de la clase derivada tiene acceso al miembro nuevamente implementado a menos que se use la palabra clave [MyBase \- delete](http://msdn.microsoft.com/es-es/52491d06-6451-4f6f-9aa6-8fab59bbc2b9) para acceder a la implementación de la clase base.  
  
-   Si no tiene pensado volver a implementar el miembro de interfaz, quite la cláusula `Implements` de la declaración de propiedad, procedimiento o evento.  
  
## Vea también  
 [Interfaces](/dotnet/visual-basic/programming-guide/language-features/interfaces/index)   
 [NO ESTÁ EN LA COMPILACIÓN: Palabra clave Implements e instrucción Implements](http://msdn.microsoft.com/es-es/b96560f7-6413-480f-a1e2-f80253bab5be)