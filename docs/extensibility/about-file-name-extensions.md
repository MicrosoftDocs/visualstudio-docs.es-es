---
title: "Acerca de las extensiones de nombre de archivo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "extensiones de archivo"
  - "extensiones de nombre de archivo"
ms.assetid: 99f4f9ff-fb84-4258-9787-6890f308a57f
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# Acerca de las extensiones de nombre de archivo
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Cuando se registra una extensión de archivo de un Paquete, se asocia a una versión de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  esto es importante si más de una versión de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] está instalada en un equipo.  
  
 Las extensiones de archivo para VSPackages se registran en la clave de HKEY\_CLASSES\_ROOT con un valor predeterminado que señala al identificador de programación asociado \(ProgID\).  
  
 A continuación se muestra un ejemplo de la información de registro de la extensión de archivo .vcproj:  
  
```  
HKEY_CLASSES_ROOT\  
   .vcproj\  
      (default)=" VisualStudio.vcproj.8.0"   
```  
  
 Los archivos asociados con [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] deben tener ProgID versiones, como `VisualStudio.vcproj.8.0`, permitir que en paralelo instalaciones del producto mantener las asociaciones de extensiones de archivo entre versiones del producto.  ProgID específico también permite utilizar verbos estándar, como abierto, edición, etc., sin preocuparse de sobrescribir o que se sobrescriba con otras aplicaciones o versiones de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
 En algunos casos, ProgID asociado a una extensión de archivo no debe cambiar.  Por ejemplo, ProgID para la extensión de archivo .htm \(progid \= htmlfile\) es codificada duro en varios lugares en el sistema operativo, y ampliamente se conoce y se utiliza en asociación con archivos .htm y .html.  
  
## Vea también  
 [Registrar extensiones de nombre de archivo para las implementaciones en paralelo](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)   
 [Especificar los controladores de archivo para las extensiones de nombre de archivo](../extensibility/specifying-file-handlers-for-file-name-extensions.md)