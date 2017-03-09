---
title: "Error de MSBuild MSB3150 | Microsoft Docs"
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
  - "MSBuild.GenerateBootstrapper.NoStringsForCulture"
helpviewer_keywords: 
  - "MSB3150"
ms.assetid: 90d86aef-f4df-4070-8ecc-173eb40668aa
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Error de MSBuild MSB3150
**MSB3150: Ninguna cadena disponible para compilar la referencia cultural '{0}' de un arranque.**  
  
 Este error se produce cuando se encuentra setup.xml, pero este archivo no contiene el nodo de cadenas.  Es probable que el archivo XML esté dañado.  
  
### Para corregir este error  
  
-   Vaya al **Panel de control**, seleccione **Agregar o quitar programas** y repare el SDK de Visual Studio, o bien, copie los archivos en el directorio apropiado \(\<ruta de instalación del SDK\>\\bootstrapper\\engine\\\<referencia cultural\>\\setup.xml\).