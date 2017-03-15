---
title: "Registrar VSPackages | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "VSPackages administrado, registrar"
  - "registro, VSPackages administrado"
ms.assetid: 79b9424e-7e9b-4fc8-9b9f-00212674573c
caps.latest.revision: 20
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 20
---
# Registrar VSPackages
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] utiliza los archivos .pkgdef para describir buscar un VSPackage.  Un archivo .pkgdef contiene toda la información que se agregue de otra manera de registro del sistema.  VSPackages administrado es registrado agregar atributos al código fuente y después ejecuta [Utilidad de CreatePkgDef](../../extensibility/internals/createpkgdef-utility.md) en el ensamblado resultante para generar un archivo .pkgdef.  
  
## En esta sección  
 [Especificar la ubicación del archivo de VSPackage del Shell de VS](../../extensibility/internals/specifying-vspackage-file-location-to-the-vs-shell.md)  
 Describe la ruta de acceso de carga para VSPackages.  
  
 [Registrar y anular el registro VSPackages](../../extensibility/registering-and-unregistering-vspackages.md)  
 explica cómo registrar un VSPackage.  
  
 [Usar un atributo de registro personalizado para registrar una extensión](../../misc/using-a-custom-registration-attribute-to-register-an-extension.md)  
 Describe cómo crear un registro de manifiesto que se puede usar para implementar un VSPackage administrado.