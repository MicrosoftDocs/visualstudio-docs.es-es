---
title: "&#39;Microsoft.VisualBasic.ComClassAttribute&#39; se ha especificado para la clase &#39;&lt;classname&gt;&#39; pero no tiene miembros p&#250;blicos que se puedan exponer a COM; por tanto, no se ha generado ninguna interfaz COM. | Microsoft Docs"
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
  - "bc40011"
  - "vbc40011"
helpviewer_keywords: 
  - "BC40011"
ms.assetid: 39aed273-bf27-4667-8116-022c4dd8f3c5
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Microsoft.VisualBasic.ComClassAttribute&#39; se ha especificado para la clase &#39;&lt;classname&gt;&#39; pero no tiene miembros p&#250;blicos que se puedan exponer a COM; por tanto, no se ha generado ninguna interfaz COM.
Una clase con un bloque de atributos `COMClassAttribute` no define métodos ni propiedades `Public`. Si una clase debe estar expuesta como un objeto COM, sus propiedades y métodos deben declararse con acceso `Public`.  
  
 De forma predeterminada, el mensaje es una advertencia. Para más información sobre cómo ocultar las advertencias o cómo tratarlas como errores, vea [Configurar advertencias en Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **Identificador de error:** BC40011  
  
### Para corregir este error  
  
-   Agregue la palabra clave `Public` a uno o varios métodos o propiedades de la clase o quite el bloque de atributos `COMClassAttribute`.  
  
## Vea también  
 [NO ESTÁ EN LA COMPILACIÓN: Atributos usados en Visual Basic](http://msdn.microsoft.com/es-es/22231318-8a40-49af-9245-e0aab723563b)   
 [NO ESTÁ EN LA COMPILACIÓN: Aplicación de atributos](http://msdn.microsoft.com/es-es/2b1703ed-4437-49b3-bc0b-568094324f47)   
 [Public](/dotnet/visual-basic/language-reference/modifiers/public)   
 [Clase ComClassAttribute](http://msdn.microsoft.com/es-es/5c2f0835-9210-47dc-bc59-5c1769953574)