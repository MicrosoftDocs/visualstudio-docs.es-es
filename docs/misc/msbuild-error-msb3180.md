---
title: "Error de MSBuild MSB3180 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSBuild.GenerateManifest.DuplicateComDefinition"
helpviewer_keywords: 
  - "MSB3180"
ms.assetid: 98d8cb76-6176-4121-82ee-8a297d9deebc
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Error de MSBuild MSB3180
**MSB3180: El componente COM '\<ensamblado\>' está definido tanto en '\<archivo\>' como en '\<archivo\>', clsid\/tlbid\=\='''\<ensamblado\>'".**  
  
 Este error lo genera el proceso de generación del manifiesto de aplicación cuando se encuentran referencias COM duplicadas \(a clases o bibliotecas de tipos\) en las referencias de archivo o en los manifiestos dependientes.  
  
 Por ejemplo, podría recibir este error si agregó una referencia a un objeto COM con un manifiesto externo y una referencia al mismo objeto COM con un manifiesto interno.  
  
### Para corregir este error  
  
-   Quite una de las referencias COM duplicadas.  
  
## Vea también  
 [\<PackageFiles\> \(Elemento\)](../deployment/packagefiles-element-bootstrapper.md)