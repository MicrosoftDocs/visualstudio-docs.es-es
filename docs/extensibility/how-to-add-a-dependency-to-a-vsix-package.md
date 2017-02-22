---
title: "C&#243;mo: agregar una dependencia a un paquete VSIX | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "referencia de paquetes"
  - "ensamblado de paquete"
  - "dll de paquete"
  - "referencia VSIX"
ms.assetid: 8f20177b-dab9-43a3-b959-81a591b451d6
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# C&#243;mo: agregar una dependencia a un paquete VSIX
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Puede configurar la implementación de un paquete VSIX que instala cualquier dependencia que ya no está presente en el equipo de destino. Para ello, incluya las dependencias VSIX en el archivo source.extension.vsixmanifest.  
  
#### Para agregar una dependencia  
  
1.  Abra el archivo source.extension.vsixmanifest en el **diseño** vista. Vaya a la **dependencias** y haga clic en **nuevo**.  
  
2.  Para agregar una extensión instalada: en el **Agregar nueva dependencia** cuadro de diálogo, seleccione **extensión instalada** y, a continuación, para la **nombre**, seleccione una extensión en la lista.  
  
3.  Para agregar otro VSIX que no está instalado:: en el **Agregar nueva dependencia** cuadro de diálogo, seleccione **archivo en el sistema de archivos** y, a continuación, utilice el **Examinar** botón para seleccionar el proyecto VSIX.  
  
## Vea también  
 [Referencia de esquema 1.0 de extensión VSIX](http://msdn.microsoft.com/es-es/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)   
 [Anatomía de un paquete VSIX](../extensibility/anatomy-of-a-vsix-package.md)   
 [Preparar las extensiones para la implementación de Windows Installer](../extensibility/preparing-extensions-for-windows-installer-deployment.md)