---
title: "No se puede usar el tipo &#39;&lt;typename&gt;&#39; en un atributo porque su contenedor &#39;&lt;containername&gt;&#39; no est&#225; declarado como &#39;Public&#39;. | Microsoft Docs"
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
  - "bc31517"
  - "vbc31517"
helpviewer_keywords: 
  - "BC31517"
ms.assetid: 3d1a8f41-8652-4e37-a6bd-40b0ad306c6f
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# No se puede usar el tipo &#39;&lt;typename&gt;&#39; en un atributo porque su contenedor &#39;&lt;containername&gt;&#39; no est&#225; declarado como &#39;Public&#39;.
La clase o módulo donde se define este atributo no está declarado con el modificador `Public`. Las clases y módulos que no especifican un modificador de acceso se declaran como `Friend` de forma predeterminada.  
  
 **Identificador de error:** BC31517  
  
### Para corregir este error  
  
1.  Agregue el modificador `Public` a la clase o módulo donde se define este atributo.  
  
## Vea también  
 [Public](/dotnet/visual-basic/language-reference/modifiers/public)