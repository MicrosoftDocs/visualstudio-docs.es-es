---
title: "El tipo &#39;&lt;nombreDeTipo1&gt;&#39; no se puede marcar como conforme a CLS porque el tipo contenedor &#39;&lt;nombreDeTipo2&gt;&#39; no es conforme a CLS | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc40030"
  - "bc40030"
helpviewer_keywords: 
  - "BC40030"
ms.assetid: f1cfcf04-2a99-46ef-ac87-34cc2099125c
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# El tipo &#39;&lt;nombreDeTipo1&gt;&#39; no se puede marcar como conforme a CLS porque el tipo contenedor &#39;&lt;nombreDeTipo2&gt;&#39; no es conforme a CLS
Una clase o interfaz se marca como `<CLSCompliant(True)>` cuando está anidada en un tipo marcado como `<CLSCompliant(False)>` o sin marcar.  
  
 Para que una clase o interfaz sea conforme a [Independencia del lenguaje y componentes independientes del lenguaje](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md) \(CLS\), toda su jerarquía de contención debe ser conforme. Esto significa que cada tipo en el que está anidada debe ser conforme.  
  
 Al aplicar <xref:System.CLSCompliantAttribute> a un elemento de programación, establezca el parámetro `isCompliant` del atributo en `True` o `False` para indicar conformidad o disconformidad. No hay ningún valor predeterminado para este parámetro y debe proporcionar un valor.  
  
 Si no se aplica <xref:System.CLSCompliantAttribute> a un elemento, se considera que no es conforme.  
  
 De forma predeterminada, este mensaje es una advertencia. Para obtener más información sobre cómo ocultar las advertencias o cómo tratarlas como errores, vea [Configurar advertencias en Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **Identificador de error:** BC40030  
  
### Para corregir este error  
  
-   Si necesita conformidad con CLS, defina este tipo dentro de una jerarquía de contención diferente.  
  
-   Si necesita que este tipo permanezca en la jerarquía de contención actual, quite el <xref:System.CLSCompliantAttribute> de su definición o márquelo como `<CLSCompliant(False)>`.  
  
## Vea también  
 [\<PAVE OVER\> Escribir código conforme a CLS](http://msdn.microsoft.com/es-es/4c705105-69a2-4e5e-b24e-0633bc32c7f3)