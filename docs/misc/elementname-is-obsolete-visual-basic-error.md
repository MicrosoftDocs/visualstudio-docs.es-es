---
title: "&#39;&lt;nombreDeElemento&gt;&#39; est&#225; obsoleto (error de Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc31075"
  - "bc31075"
helpviewer_keywords: 
  - "BC31075"
ms.assetid: 614d36a1-2fba-4d03-963c-1565e88b08a6
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;nombreDeElemento&gt;&#39; est&#225; obsoleto (error de Visual Basic)
Una instrucción intenta obtener acceso a un elemento de programación que se ha marcado con el atributo <xref:System.ObsoleteAttribute> y la directiva para tratarlo como un error.  
  
 Para marcar que cualquier elemento de programación ya no está en uso, aplíquele <xref:System.ObsoleteAttribute>. Si lo hace, puede establecer la propiedad <xref:System.ObsoleteAttribute.IsError%2A> del atributo en `True` o `False`. Si se establece en `True`, el compilador trata como un error los intentos de usar el elemento. Si se establece en `False` o se deja el valor predeterminado `False`, el compilador emite una advertencia si hay un intento de usar el elemento.  
  
 **Identificador de error:** BC31075  
  
### Para corregir este error  
  
-   Asegúrese de que la referencia del código fuente escriba correctamente el nombre del elemento.  
  
## Vea también  
 [NO ESTÁ EN LA COMPILACIÓN: Atributos usados en Visual Basic](http://msdn.microsoft.com/es-es/22231318-8a40-49af-9245-e0aab723563b)   
 [NO ESTÁ EN LA COMPILACIÓN: Aplicación de los atributos](http://msdn.microsoft.com/es-es/2b1703ed-4437-49b3-bc0b-568094324f47)