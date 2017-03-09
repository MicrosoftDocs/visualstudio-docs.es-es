---
title: "&#39;&lt;procedimiento1&gt;&#39; y &#39;&lt;procedimiento2&gt;&#39; no se pueden sobrecargar el uno al otro porque solo se diferencian en par&#225;metros declarados como &#39;ByRef&#39; o &#39;ByVal&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc42003"
  - "bc42003"
helpviewer_keywords: 
  - "BC42003"
ms.assetid: f058f1e0-64d2-4497-85fc-a58e16b0d805
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;procedimiento1&gt;&#39; y &#39;&lt;procedimiento2&gt;&#39; no se pueden sobrecargar el uno al otro porque solo se diferencian en par&#225;metros declarados como &#39;ByRef&#39; o &#39;ByVal&#39;
'\<procedimiento1\>' y '\<procedimiento2\>' no se pueden sobrecargar el uno al otro porque solo se diferencian en parámetros declarados como ByRef o ByVal. Se supone Shadows.  
  
 Dos declaraciones de procedimiento especifican el mismo nombre y la misma lista de argumentos. La única diferencia se encuentra en la especificación de `ByRef` o `ByVal` de uno o varios de los argumentos. Las versiones sobrecargadas de un procedimiento deben distinguirse entre sí por el número, el orden o los tipos de datos de los argumentos.  
  
 Este mensaje es una advertencia. Se supone `Shadows` de forma predeterminada. Para obtener más información sobre cómo ocultar las advertencias o cómo tratarlas como errores, vea [Configurar advertencias en Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **Identificador de error:** BC42003  
  
### Para corregir este error  
  
-   Si tiene previsto crear un conjunto de versiones sobrecargadas de un procedimiento, distinga el número, el orden o los tipos de datos de los argumentos de cada versión. Asimismo, agregue la palabra clave `Overloads` a cada declaración.  
  
-   Si no tiene previsto sobrecargar un procedimiento, cambie el nombre del procedimiento en una de las declaraciones.  
  
## Vea también  
 [Sobrecarga de procedimientos](/dotnet/visual-basic/programming-guide/language-features/procedures/procedure-overloading)