---
title: "Registro del paquete de RegPkg de soluci&#243;n de problemas | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "RegPkg"
ms.assetid: f33f822f-697a-4bad-9c10-554b4c8f6246
caps.latest.revision: 15
caps.handback.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
---
# Registro del paquete de RegPkg de soluci&#243;n de problemas
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

> [!NOTE]
>  Es la mejor manera de registrar paquetes en Visual Studio mediante el uso de archivos .pkgdef. Esto permite la implementación de extensión sin necesidad de tener acceso al registro del sistema. Se crean archivos pkgdef mediante el [Utilidad de CreatePkgDef](../../extensibility/internals/createpkgdef-utility.md).  
  
 Para registrar un paquete mediante RegPkg en [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], debe utilizar la versión de RegPkg que sea adecuada para el paquete.  
  
## Versiones de RegPkg relacionados con las versiones de paquete  
 Hay dos versiones de RegPkg. Una versión se incluye en [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Utilice esta versión para registrar paquetes que ha generado mediante uno de los siguientes ensamblados:  
  
1.  Microsoft.VisualStudioShell.9.0.dll  
  
2.  Microsoft.VisualStudioShell.10.0.dll  
  
3.  Microsoft.VisualStudioShell.11.0.dll  
  
 No se puede registrar paquetes que ha generado mediante el ensamblado Microsoft.VisualStudio.Shell.dll anterior.  
  
 La versión anterior de RegPkg puede registrar paquetes que ha generado mediante el ensamblado Microsoft.VisualStudio.Shell.dll. Sin embargo, que no registre paquetes creados mediante versiones posteriores de dicho ensamblado.  
  
## Vea también  
 [Publicar un producto](../../misc/releasing-a-visual-studio-integration-product.md)