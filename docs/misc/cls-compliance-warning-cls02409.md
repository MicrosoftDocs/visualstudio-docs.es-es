---
title: "Advertencia de conformidad con CLS CLS02409 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CLS02409"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS02409"
ms.assetid: 71d566ce-59c2-4d3d-97ff-72f4e9bd21ee
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# Advertencia de conformidad con CLS CLS02409
Los métodos que implementan los métodos de captador y establecedor de una propiedad deben estar marcados con SpecialName en los metadatos  
  
 Los métodos que implementan los métodos de captador y establecedor de una propiedad no se marcaron con **specialname** en los metadatos.  
  
 Para más información sobre la comprobación de conformidad con CLS, vea [Ensamblados conformes con CLS](http://msdn.microsoft.com/es-es/3320b57e-ea55-4697-a17d-f509a36a3c93).  
  
 En la siguiente declaración de función \(mediante el lenguaje de ensamblador MSIL\) se muestran posibles causas de la advertencia CLS02409:  
  
```  
.method public instance int32 get_MyProperty() cil managed  
```  
  
 Puede resolver esta advertencia al agregar la palabra clave **specialname**:  
  
```  
.method public specialname instance int32 get_MyProperty() cil managed  
```