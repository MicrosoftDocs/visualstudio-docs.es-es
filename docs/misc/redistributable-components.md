---
title: "Componentes redistribuibles | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "componentes redistribuibles"
  - "instalación [SDK de Visual Studio], componentes redistribuibles"
ms.assetid: 5072281f-3cb3-4985-bd93-c7981233bf92
caps.latest.revision: 20
caps.handback.revision: 20
manager: "douge"
---
# Componentes redistribuibles
[!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] incluye código que puede distribuir a los usuarios según los términos del contrato de licencia de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] SDK.  Tales componentes redistribuibles incluye los paquetes de Windows Installer y módulos de combinación se convierten en parte del proceso de instalación del producto, y el código fuente que se compila en el VSPackages.  
  
 La tabla siguiente se describen los componentes redistribuibles que se incluyen en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] SDK.  Los componentes pueden encontrarse en  *ruta de instalación de Visual Studio SDK*\\VisualStudioIntegration\\Redistributables \\.  
  
|Nombre de archivo|Descripción|  
|-----------------------|-----------------|  
|VSSDKTestHost.exe|Puede instalar esta aplicación ejecutable como parte de la instalación.|  
  
## Instalar paquetes redistribuibles  
 Proporcionan los componentes redistribuibles que instalan código ejecutable como paquetes de Windows Installer \(archivos .msi\) para que Microsoft puede proporcionar actualizaciones si es necesario dirigir vulnerabilidades de seguridad u otros errores críticos.  
  
 Porque Windows Installer permite que sólo un paquete instalar al mismo tiempo, instalar un paquete redistribuible requiere que utiliza un programa ejecutable independiente que instalar varios paquetes secuencialmente.  Un programa se suele denominar *un encadenador* o *un*arranque.  
  
> [!IMPORTANT]
>  *La instalación anidadas* \(también conocida como *instalación simultánea*\) se desaconsejan los en Windows Installer porque un producto “anidados” no se puede aplicar revisiones independientemente.  Puede aplicar revisiones sólo el producto que lo instaló.  Dado que los paquetes redistribuibles de [!INCLUDE[vssdk_current_long](../misc/includes/vssdk_current_long_md.md)] instalan archivos en los directorios compartidos y deben admitir la aplicación de revisión independiente, no deben instalarse mediante una instalación anidados.  
  
## Vea también  
 [Publicar un producto](../misc/releasing-a-visual-studio-integration-product.md)