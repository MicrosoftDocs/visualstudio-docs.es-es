---
title: "El m&#233;todo &#39;&lt;nombreDeProcedimiento&gt;&#39; para el evento &#39;&lt;nombreDeEvento&gt;&#39; no se puede marcar como conforme a CLS porque su tipo contenedor &#39;&lt;nombreDeTipo&gt;&#39; tampoco es conforme a CLS | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc40053"
  - "bc40053"
helpviewer_keywords: 
  - "BC40053"
ms.assetid: 5f7aaf64-b5e6-4f97-9ebd-44cd4c7e8bf5
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# El m&#233;todo &#39;&lt;nombreDeProcedimiento&gt;&#39; para el evento &#39;&lt;nombreDeEvento&gt;&#39; no se puede marcar como conforme a CLS porque su tipo contenedor &#39;&lt;nombreDeTipo&gt;&#39; tampoco es conforme a CLS
Un evento personalizado declara un procedimiento `AddHandler` o `RemoveHandler` y lo marca como `<CLSCompliant(True)>`, pero el evento está definido en un tipo marcado como `<CLSCompliant(False)>` o no está marcado.  
  
 Al aplicar <xref:System.CLSCompliantAttribute> a un elemento de programación, se establece el parámetro `isCompliant` del atributo en `True` o `False` para indicar su conformidad o no conformidad. No hay ningún valor predeterminado para este parámetro, por lo que debe proporcionar uno.  
  
 Si no aplica <xref:System.CLSCompliantAttribute> a un elemento, se considera que no es conforme.  
  
 De forma predeterminada, este mensaje es una advertencia. Para obtener información sobre cómo ocultar las advertencias o cómo tratarlas como errores, vea [Configurar advertencias en Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **Identificador de error:** BC40053  
  
### Para corregir este error  
  
-   Si necesita conformidad con CLS, defina el evento dentro de un tipo que sea conforme a CLS.  
  
-   Si necesita que el evento permanezca dentro de su tipo contenedor, quite <xref:System.CLSCompliantAttribute> de su definición o márquelo como `<CLSCompliant(False)>`.  
  
## Vea también  
 [Cómo: Declarar eventos personalizados para evitar bloqueos](../Topic/How%20to:%20Declare%20Custom%20Events%20To%20Avoid%20Blocking%20\(Visual%20Basic\).md)   
 [Cómo: Declarar eventos personalizados para conservar memoria](../Topic/How%20to:%20Declare%20Custom%20Events%20To%20Conserve%20Memory%20\(Visual%20Basic\).md)   
 [NO ESTÁ EN LA COMPILACIÓN: AddHandler y RemoveHandler](http://msdn.microsoft.com/es-es/a7a24bd2-519a-46fe-8a2c-2b9df2ca28ef)   
 [\<PAVE OVER\> Escribir código conforme a CLS](http://msdn.microsoft.com/es-es/4c705105-69a2-4e5e-b24e-0633bc32c7f3)