---
title: "&#39;Microsoft.VisualBasic.ComClassAttribute&#39; no se puede aplicar a &#39;&lt;nombreClase1&gt;&#39; porque su contenedor &#39;&lt;nombreClase2&gt;&#39; no est&#225; declarado como &#39;Public&#39;. | Microsoft Docs"
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
  - "vbc32504"
  - "bc32504"
helpviewer_keywords: 
  - "BC32504"
ms.assetid: 4138b639-88d6-4b51-afcd-c92a1be36f1c
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Microsoft.VisualBasic.ComClassAttribute&#39; no se puede aplicar a &#39;&lt;nombreClase1&gt;&#39; porque su contenedor &#39;&lt;nombreClase2&gt;&#39; no est&#225; declarado como &#39;Public&#39;.
Una clase que usa un bloque de atributos `COMClassAttribute` se declara dentro de una clase que no es `Public`. Si una clase debe exponerse como un objeto COM, toda su jerarquía de contención debe declararse con acceso `Public`.  
  
 **Identificador de error:** BC32504  
  
### Para corregir este error  
  
-   Declare todas las clases contenedoras `Public`, o quite el bloque de atributos `COMClassAttribute`.  
  
## Vea también  
 [NO ESTÁ EN LA COMPILACIÓN: Atributos usados en Visual Basic](http://msdn.microsoft.com/es-es/22231318-8a40-49af-9245-e0aab723563b)   
 [NO ESTÁ EN LA COMPILACIÓN: Aplicación de atributos](http://msdn.microsoft.com/es-es/2b1703ed-4437-49b3-bc0b-568094324f47)   
 [Clase ComClassAttribute](http://msdn.microsoft.com/es-es/5c2f0835-9210-47dc-bc59-5c1769953574)   
 [Public](/dotnet/visual-basic/language-reference/modifiers/public)