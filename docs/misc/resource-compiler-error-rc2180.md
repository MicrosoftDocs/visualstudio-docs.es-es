---
title: "Error del compilador de recursos RC2180 | Microsoft Docs"
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
  - "RC2180"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "RC2180"
ms.assetid: 6d296138-7989-491e-a45b-6c3a4743116a
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# Error del compilador de recursos RC2180
no se puede abrir el archivo temporal  
  
 El compilador de recursos\/Visual C\+\+ no pudo abrir un archivo temporal. La causa más probable es que no tiene permisos de escritura para el directorio o que el directorio no existe. El compilador de recursos\/Visual C\+\+ intenta usar estos archivos en el directorio especificado por la variable de entorno **TMP** o el directorio actual si no se especifica ninguno.