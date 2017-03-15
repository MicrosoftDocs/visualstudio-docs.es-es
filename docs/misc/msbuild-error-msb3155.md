---
title: "Error de MSBuild MSB3155 | Microsoft Docs"
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
  - "MSBuild.GenerateBootstrapper.ProductNotFound"
helpviewer_keywords: 
  - "MSB3155"
ms.assetid: 59bf2293-ef13-4bb1-8f29-5d6966bbe313
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Error de MSBuild MSB3155
**Error de MSBuild MSB3155: El elemento '\<paquete\>' no se pudo encontrar en '\<ruta de acceso\>'**  
  
 Esta advertencia se produce cuando un paquete con el <xref:Microsoft.Build.Tasks.Deployment.Bootstrapper.Product.ProductCode%2A> especificado no se encuentra en la caché de arranque.  
  
> [!NOTE]
>  Microsoft Data Access Components \(MDAC\) ya no se incluye como un paquete de arranque.  Se puede descargar del sitio web de [Microsoft Windows Update](http://go.microsoft.com/fwlink/?LinkId=86676).  
  
### Para corregir este error  
  
-   Quite el paquete de la lista de paquetes para instalar o agregue el paquete a la caché.  Además, asegúrese de que el manifiesto tenga un formato correcto con etiquetas XML válidas.  
  
## Vea también  
 [Referencia de esquemas de productos y paquetes](../deployment/product-and-package-schema-reference.md)   
 [\<PackageFiles\> \(Elemento\)](../deployment/packagefiles-element-bootstrapper.md)   
 [Cuadro de diálogo Requisitos previos](../ide/reference/prerequisites-dialog-box.md)   
 [Crear paquetes de arranque](../deployment/creating-bootstrapper-packages.md)