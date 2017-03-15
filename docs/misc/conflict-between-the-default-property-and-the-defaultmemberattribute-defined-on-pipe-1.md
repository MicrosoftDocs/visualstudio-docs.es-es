---
title: "Hay un conflicto entre la propiedad predeterminada y el atributo &#39;DefaultMemberAttribute&#39; definido en &#39;|1&#39;. | Microsoft Docs"
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
  - "vbc32304"
  - "bc32304"
helpviewer_keywords: 
  - "BC32304"
ms.assetid: 42803d13-ff1d-40ed-a4a8-269e2fb4aa01
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Hay un conflicto entre la propiedad predeterminada y el atributo &#39;DefaultMemberAttribute&#39; definido en &#39;|1&#39;.
Una clase, estructura o interfaz declara una propiedad predeterminada con la palabra clave [Default](/dotnet/visual-basic/language-reference/modifiers/default), pero también aplica <xref:System.Reflection.DefaultMemberAttribute> para designar un miembro distinto como miembro predeterminado.  
  
 Un tipo puede tener a lo sumo un miembro predeterminado. Cuando se declara una propiedad predeterminada, Visual Basic aplica automáticamente <xref:System.Reflection.DefaultMemberAttribute> a la clase, estructura o interfaz que designan esa propiedad.  
  
 **Identificador de error:** BC32304  
  
### Para corregir este error  
  
1.  Decida qué miembro debe ser el miembro predeterminado de la clase, estructura o interfaz.  
  
2.  Elimine la declaración en conflicto \(ya sea la palabra clave `Default` o <xref:System.Reflection.DefaultMemberAttribute>\).  
  
## Vea también  
 <xref:System.Reflection.DefaultMemberAttribute>   
 [Default](/dotnet/visual-basic/language-reference/modifiers/default)   
 [NO ESTÁ EN LA COMPILACIÓN: Propiedades predeterminadas](http://msdn.microsoft.com/es-es/a70f2a27-8176-4858-935e-f25afdd43ab5)   
 [Cómo: Declarar y llamar a una propiedad predeterminada en Visual Basic](../Topic/How%20to:%20Declare%20and%20Call%20a%20Default%20Property%20in%20Visual%20Basic.md)