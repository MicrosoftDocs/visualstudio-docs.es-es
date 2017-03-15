---
title: "Error de MSBuild MSB3152 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSBuild.GenerateBootstrapper.PackageFileNotFound"
helpviewer_keywords: 
  - "MSB3152"
ms.assetid: 5a3859d4-4107-4e46-bb42-04de92b551de
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Error de MSBuild MSB3152
**MSB3152: La ubicación de instalación de los requisitos previos no se estableció como 'sitio Web del proveedor de componentes' y el archivo '\<archivo\>' del elemento '\<paquete\>' no se encuentra en el disco.  Vea la Ayuda para obtener más información.**  
  
 Este error se produce cuando falta un archivo que es necesario para el instalador de requisitos previos.  Los archivos del instalador se copian en una carpeta especial que Visual Studio tiene reservada para los paquetes redistribuibles.  La carpeta varía según la versión de Visual Studio que se use para el desarrollo.  Para obtener más información sobre la ubicación específica de la carpeta, vea [Crear paquetes de arranque](../deployment/creating-bootstrapper-packages.md).  
  
### Para corregir este error  
  
-   Determine si el archivo existe en el disco.  
  
-   Utilice HomeSite para intentar resolver el problema del paquete.  
  
-   Establezca el valor de `CopyComponents` en `false` en el archivo de proyecto.  
  
-   No utilice el paquete de arranque roto.  
  
## Vea también  
 [Crear paquetes de arranque](../deployment/creating-bootstrapper-packages.md)