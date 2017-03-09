---
title: "Error de MSBuild MSB3172 | Microsoft Docs"
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
  - "MSBuild.GenerateManifest.ReadInputManifestFailed"
helpviewer_keywords: 
  - "MSB3172"
ms.assetid: aa7291db-1f36-41e7-a510-90cd4daaa89d
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Error de MSBuild MSB3172
**MSB3172: No se puede leer el manifiesto '\<archivo\>'. '  \<error\>'**  
  
 Se genera este error cuando el proceso de compilación encuentra un problema general al leer un archivo de manifiesto.  El mensaje de error contiene el nombre de archivo seguido de información más detallada sobre el error que se ha producido.  
  
 Puede que haya agregado un ensamblado o un archivo de manifiesto como un archivo de contenido.  Use el comando **Agregar referencia** en lugar de **Agregar archivo** para que el sistema de proyectos haga referencia correctamente al ensamblado dependiente.  Los proyectos más sofisticados con frecuencia marcan .exe.manifest en la carpeta bin como un archivo de proyecto, aunque esta práctica no es recomendable.  El archivo oculto app.manifest se convierte en .exe.manifest y puede modificarse manualmente en escenarios avanzados.  
  
## Vea también  
 [\<PackageFiles\> \(Elemento\)](../deployment/packagefiles-element-bootstrapper.md)