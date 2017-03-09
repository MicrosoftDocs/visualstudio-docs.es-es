---
title: "Compatibilidad con la persistencia de estado | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "persistencia de estado, compatibilidad de marco de trabajo de paquetes administrados"
  - "marco de trabajo de paquetes administrados, compatibilidad de persistencia de estado"
  - "estado, persistencia"
ms.assetid: d25866f2-8d1f-477f-8aa5-3af3fbbf6e97
caps.latest.revision: 15
caps.handback.revision: 15
manager: "douge"
---
# Compatibilidad con la persistencia de estado
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] puede mantener el estado de objetos comunes.  Por ejemplo, la solución y las propiedades del proyecto se guarda a y se restauran de la solución y archivos de proyecto.  La configuración del usuario se pueden exportar a e importar de los archivos de configuración.  
  
 VSPackages depende normalmente en almacenamiento local, en el registro del sistema o en la carpeta de datos de aplicación para el usuario actual o el equipo.  Los valores que requieren una pequeña cantidad de espacio para el almacenamiento, como enteros y cadenas, se almacenan normalmente en el sistema.  Los valores que requieren mucho espacio para el almacenamiento, como mapas de bits, se guardan en un archivo.  La ruta de acceso del archivo se sí mismo puede guardar en el sistema.  El mecanismo de persistencia debe tener permiso de acceso al almacenamiento local.  
  
## Compatibilidad para buscar almacenamiento local  
 La clase de <xref:Microsoft.VisualStudio.Shell.Package> proporciona compatibilidad para buscar información de estado en la carpeta de registro del sistema o de datos de aplicación para el usuario o el equipo actual.  
  
 <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>  
 Devuelve la ruta de acceso raíz para [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], por ejemplo, HKEY\_LOCAL\_MACHINE \\Software\\Microsoft\\VisualStudio\\8.0Exp del registro del equipo local.  
  
 La raíz local del registro se obtiene del servicio de <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell> .  Si esto no está disponible, se obtiene del atributo de <xref:Microsoft.VisualStudio.Shell.DefaultRegistryRootAttribute> de VSPackage.  
  
 <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A>  
 Devuelve la ruta de acceso raíz actual para [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], por ejemplo, HKEY\_CURRENT\_USER \\Software\\Microsoft\\VisualStudio\\8.0Exp de registro de usuario \(por equipo\).  
  
 La raíz local del registro se obtiene del servicio de <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell> .  Si esto no está disponible, se obtiene del atributo de DefaultLocalRegistryRoot de VSPackage.  
  
 <xref:Microsoft.VisualStudio.Shell.Package.UserDataPath%2A>  
 Devuelve la ruta de acceso que actúa como repositorio común de datos para el usuario móvil actual, por ejemplo, C de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] : \\Documents and Settings \\*TheAccountName*\\Application Data\\Microsoft\\VisualStudio\\8.0Exp.  
  
 <xref:Microsoft.VisualStudio.Shell.Package.UserLocalDataPath%2A>  
 Devuelve la ruta de acceso que actúa como repositorio común de datos para el usuario de no\-itinerancia actual, por ejemplo, C de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] : \\Documents and Settings \\*TheAccountName*\\Local Settings\\Application Data\\Microsoft\\VisualStudio\\8.0Exp.  
  
## Vea también  
 [Estado de VSPackage](../misc/vspackage-state.md)