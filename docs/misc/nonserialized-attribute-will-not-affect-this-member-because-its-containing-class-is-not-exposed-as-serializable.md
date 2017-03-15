---
title: "El atributo &#39;NonSerialized&#39; no tendr&#225; ning&#250;n efecto en este miembro porque su clase contenedora no est&#225; expuesta como &#39;Serializable&#39;. | Microsoft Docs"
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
  - "vbc30772"
  - "bc30772"
helpviewer_keywords: 
  - "BC30772"
ms.assetid: 1014e944-40c1-4078-8a38-139736ef89da
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# El atributo &#39;NonSerialized&#39; no tendr&#225; ning&#250;n efecto en este miembro porque su clase contenedora no est&#225; expuesta como &#39;Serializable&#39;.
De forma predeterminada, las clases y sus miembros son no serializables. El atributo <xref:System.NonSerializedAttribute> solo es necesario si un miembro de una clase serializable no se debe serializar.  
  
 **Identificador de error:** BC30772  
  
### Para corregir este error  
  
-   Agregue el atributo <xref:System.SerializableAttribute> a la clase.  
  
     \-O bien\-  
  
-   Quite el atributo <xref:System.NonSerializedAttribute> del miembro.  
  
## Vea también  
 <xref:System.NonSerializedAttribute>   
 <xref:System.SerializableAttribute>   
 [NO ESTÁ EN LA COMPILACIÓN: Atributos en Visual Basic](http://msdn.microsoft.com/es-es/620bfc0e-4582-4c8b-8432-ebc5c3dccc22)