---
title: "El par&#225;metro de tipo &#39;&lt;typeparametername&gt;&#39; tiene el mismo nombre que el par&#225;metro tipo de un tipo contenedor | Microsoft Docs"
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
  - "vbc40048"
  - "bc40048"
helpviewer_keywords: 
  - "BC40048"
ms.assetid: d5428b36-88d3-42c4-a096-cbc7bb9571f2
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# El par&#225;metro de tipo &#39;&lt;typeparametername&gt;&#39; tiene el mismo nombre que el par&#225;metro tipo de un tipo contenedor
Un parámetro de tipo de un tipo genérico se declara con el mismo nombre que un parámetro de tipo de un tipo genérico contenedor.  
  
 En la lista de parámetros de tipo de un tipo genérico, cada parámetro de tipo debe tener un nombre distinto a todos los nombres siguientes:  
  
-   Cada uno de los demás parámetros de tipo de la misma lista de parámetros de tipo.  
  
-   Cada parámetro de tipo de la lista de parámetros de tipo de cualquier tipo genérico contenedor.  
  
-   Nombre del parámetro de tipo genérico.  
  
 De forma predeterminada, este mensaje es una advertencia. Para obtener información sobre cómo ocultar las advertencias o cómo tratarlas como errores, vea [Configurar advertencias en Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **Identificador de error:** BC40048  
  
### Para corregir este error  
  
-   Cambie el nombre del parámetro de tipo para que sea distinto de los nombres mencionados en la lista de esta página de ayuda.  
  
## Vea también  
 [Tipos genéricos en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Lista de tipos](/dotnet/visual-basic/language-reference/statements/type-list)