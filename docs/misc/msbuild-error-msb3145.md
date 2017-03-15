---
title: "Error de MSBuild MSB3145 | Microsoft Docs"
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
  - "MSBuild.GenerateBootstrapper.InvalidUrl"
helpviewer_keywords: 
  - "MSB3145"
ms.assetid: 183d4e7e-bdc6-402f-a1b6-531505be605f
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Error de MSBuild MSB3145
**MSB3145: El parámetro de entrada de compilación '\<property\>\=\<value\>' no es una dirección URL web ni un recurso compartido UNC.**  
  
 Este error se produce cuando el valor de la propiedad `SupportUrl`, `ComponentsUrl` o `ApplicationUrl` del proyecto no es válido.  El valor debe ser un identificador URI válido o una ruta de acceso UNC válida.  
  
## Vea también  
 [\<PackageFiles\> \(Elemento\)](../deployment/packagefiles-element-bootstrapper.md)