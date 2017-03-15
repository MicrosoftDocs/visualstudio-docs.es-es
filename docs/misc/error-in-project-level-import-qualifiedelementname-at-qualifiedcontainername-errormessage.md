---
title: "Error en la importaci&#243;n de nivel de proyecto &#39;&lt;nombreCompletoElemento&gt;&#39; a &#39;&lt;nombreCompletoContenedor&#39;: &lt;mensajeError&gt; | Microsoft Docs"
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
  - "BC30797"
  - "vbc30797"
helpviewer_keywords: 
  - "BC30797"
ms.assetid: 529f354f-f255-4adc-ab21-bd1796e58d69
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Error en la importaci&#243;n de nivel de proyecto &#39;&lt;nombreCompletoElemento&gt;&#39; a &#39;&lt;nombreCompletoContenedor&#39;: &lt;mensajeError&gt;
Una instrucción accede a un elemento de programación que está definido en otro ensamblado, pero no hay ninguna referencia de proyecto para ese ensamblado.  
  
 Por ejemplo, el código podría estar accediendo a una enumeración denominada `desiredEnumeration` con la cadena de calificación `otherNamespace.otherClass.desiredEnumeration`. Si el compilador no puede encontrar `otherNamespace.otherClass` entre las referencias del proyecto, se genera este error.  
  
 **Identificador de error:** BC30797  
  
### Para corregir este error  
  
1.  Asegúrese de que todos los elementos de la cadena de calificación del elemento de programación están escritos correctamente.  
  
2.  Asegúrese de que el proyecto tiene una referencia al ensamblado que define el elemento de programación que quiere.  
  
3.  Consulte el mensaje de error y tome las medidas adecuadas.  
  
## Vea también  
 [NOTINBUILD: Resolver una referencia cuando varias variables tienen el mismo nombre](http://msdn.microsoft.com/es-es/9601e39f-1911-44e1-ace5-3f6e090408b9)   
 [NIB Cómo: Modificar las propiedades y los valores de configuración del proyecto](http://msdn.microsoft.com/es-es/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)   
 [NIB Cómo: Agregar o quitar referencias con el cuadro de diálogo Agregar referencia](http://msdn.microsoft.com/es-es/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)