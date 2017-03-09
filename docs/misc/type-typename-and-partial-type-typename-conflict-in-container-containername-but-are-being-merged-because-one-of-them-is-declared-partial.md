---
title: "El tipo &#39;&lt;nombreDeTipo&gt;&#39; y el tipo parcial &#39;&lt;nombreDeTipo&gt;&#39; est&#225;n en conflicto en el contenedor &#39;&lt;nombreDeContenedor&gt;&#39;, pero se est&#225;n combinando porque uno de ellos est&#225; declarado como parcial | Microsoft Docs"
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
  - "bc40046"
  - "vbc40046"
helpviewer_keywords: 
  - "BC40046"
ms.assetid: c243e70b-ecd5-49ef-a260-a7bb12a4a3b1
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# El tipo &#39;&lt;nombreDeTipo&gt;&#39; y el tipo parcial &#39;&lt;nombreDeTipo&gt;&#39; est&#225;n en conflicto en el contenedor &#39;&lt;nombreDeContenedor&gt;&#39;, pero se est&#225;n combinando porque uno de ellos est&#225; declarado como parcial
Una clase o una estructura aparecen en varias definiciones del mismo tipo de contenedor y más de una definición no está marcada como `Partial`.  
  
 Debe usar la palabra clave [Partial](/dotnet/visual-basic/language-reference/modifiers/partial) en al menos una de las diversas definiciones de una clase o estructura, pero se recomienda usarla en todas las definiciones parciales.  
  
 De forma predeterminada, este mensaje es una advertencia. Para obtener información sobre cómo ocultar las advertencias o cómo tratarlas como errores, vea [Configurar advertencias en Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **Identificador de error:** BC40046  
  
### Para corregir este error  
  
-   Use la palabra clave [Partial](/dotnet/visual-basic/language-reference/modifiers/partial) en todas las definiciones parciales de la clase o estructura.  
  
## Vea también  
 [Partial](/dotnet/visual-basic/language-reference/modifiers/partial)