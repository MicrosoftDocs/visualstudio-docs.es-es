---
title: "El descriptor de acceso &#39;&lt;palabraClave&gt;&#39; de &#39;&lt;nombreDePropiedad&gt;&#39; est&#225; obsoleto (advertencia de Visual Basic) | Microsoft Docs"
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
  - "vbc40020"
  - "bc40020"
helpviewer_keywords: 
  - "BC40020"
ms.assetid: 005440f4-6e82-421c-b2ce-9c5139325bac
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# El descriptor de acceso &#39;&lt;palabraClave&gt;&#39; de &#39;&lt;nombreDePropiedad&gt;&#39; est&#225; obsoleto (advertencia de Visual Basic)
Una instrucción intenta leer o escribir una propiedad para la que se ha marcado el procedimiento correspondiente con el atributo <xref:System.ObsoleteAttribute> y la directiva para tratarlo como una advertencia.  
  
 Para marcar que cualquier elemento de programación ya no está en uso, aplíquele <xref:System.ObsoleteAttribute>. Si lo hace, puede establecer la propiedad <xref:System.ObsoleteAttribute.IsError%2A> del atributo en `True` o `False`. Si se establece en `True`, el compilador trata como un error los intentos de usar el elemento. Si se establece en `False` o se deja el valor predeterminado `False`, el compilador emite una advertencia si hay un intento de usar el elemento.  
  
 De forma predeterminada, este mensaje es una advertencia, ya que la propiedad <xref:System.ObsoleteAttribute.IsError%2A> de <xref:System.ObsoleteAttribute> es `False`. Para obtener más información sobre cómo ocultar las advertencias o cómo tratarlas como errores, vea [Configurar advertencias en Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **Identificador de error:** BC40020  
  
### Para corregir este error  
  
1.  Asegúrese de que en la referencia de código fuente está escrito correctamente el nombre de la propiedad.  
  
2.  Evite acceder a la propiedad de la manera \(lectura o escritura\) que generó este mensaje.  
  
## Vea también  
 [NO ESTÁ EN LA COMPILACIÓN: Atributos usados en Visual Basic](http://msdn.microsoft.com/es-es/22231318-8a40-49af-9245-e0aab723563b)   
 [NO ESTÁ EN LA COMPILACIÓN: Aplicación de los atributos](http://msdn.microsoft.com/es-es/2b1703ed-4437-49b3-bc0b-568094324f47)   
 [Procedimientos de propiedad](/dotnet/visual-basic/programming-guide/language-features/procedures/property-procedures)