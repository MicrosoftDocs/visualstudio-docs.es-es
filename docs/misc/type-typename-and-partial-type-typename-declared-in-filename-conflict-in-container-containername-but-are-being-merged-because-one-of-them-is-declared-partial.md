---
title: "El tipo &#39;&lt;typename&gt;&#39; y el tipo parcial &#39;&lt;typename&gt;&#39; declarados en &#39;&lt;filename&gt;&#39; est&#225;n en conflicto en el contenedor &#39;&lt;containername&gt;&#39;, pero se combinan porque uno de ellos est&#225; declarado como parcial | Microsoft Docs"
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
  - "vbc40047"
  - "bc40047"
helpviewer_keywords: 
  - "BC40047"
ms.assetid: 05f62dd9-f97d-4893-8904-76ecd2da474c
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# El tipo &#39;&lt;typename&gt;&#39; y el tipo parcial &#39;&lt;typename&gt;&#39; declarados en &#39;&lt;filename&gt;&#39; est&#225;n en conflicto en el contenedor &#39;&lt;containername&gt;&#39;, pero se combinan porque uno de ellos est&#225; declarado como parcial
Una clase o una estructura aparecen en varias definiciones del mismo tipo de contenedor y más de una definición no está marcada como `Partial`.  
  
 Debe utilizar la palabra clave [Partial](/dotnet/visual-basic/language-reference/modifiers/partial) en al menos una de las diversas definiciones de una clase o estructura, pero se recomienda utilizarla en todas las definiciones parciales.  
  
 De forma predeterminada, este mensaje es una advertencia. Para obtener información sobre cómo ocultar las advertencias o cómo tratarlas como errores, vea [Configurar advertencias en Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **Id. de error:** BC40047  
  
### Para corregir este error  
  
-   Utilice la palabra clave [Partial](/dotnet/visual-basic/language-reference/modifiers/partial) en todas las definiciones parciales de la clase o estructura.