---
title: Soporte técnico de persistencia de estado | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- state persistence, managed package framework support
- managed package framework, state persistence support
- state, persistence
ms.assetid: d25866f2-8d1f-477f-8aa5-3af3fbbf6e97
caps.latest.revision: 15
manager: jillfra
ms.openlocfilehash: 6dc542d2e410b79a21e436a1881c06bd3cc4eef8
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62434324"
---
# <a name="support-for-state-persistence"></a>Compatibilidad con la persistencia de estado
[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] puede mantener el estado de objetos comunes. Por ejemplo, las propiedades de solución y proyecto se guarda en y restauradas a partir de archivos de solución y proyecto. Configuración de usuario puede exportarse a e importar desde archivos de configuración.  
  
 Los VSPackages normalmente se basan en el almacenamiento local, en el registro del sistema o en la carpeta de datos de aplicación para el usuario actual o el equipo. Los valores que requieren una pequeña cantidad de espacio de almacenamiento, como enteros y cadenas, normalmente se almacenan en el registro del sistema. Los valores que requieren una gran cantidad de espacio de almacenamiento, como mapas de bits, se guardan en un archivo. La ruta de acceso del archivo sí se puede guardar en el registro del sistema. El mecanismo de persistencia debe tener permiso para tener acceso al almacenamiento local.  
  
## <a name="support-for-locating-local-storage"></a>Soporte técnico para la localización de almacenamiento Local  
 El <xref:Microsoft.VisualStudio.Shell.Package> proporciona compatibilidad para buscar información de estado en la carpeta de datos del sistema del registro o una aplicación para el usuario actual o el equipo.  
  
 <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>  
 Devuelve la ruta de acceso del registro raíz del equipo local para [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], por ejemplo, HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\8.0Exp.  
  
 Se obtiene la raíz del registro local de la <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell> service. Si no está disponible, se obtiene de la <xref:Microsoft.VisualStudio.Shell.DefaultRegistryRootAttribute> atributo del VSPackage.  
  
 <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A>  
 Devuelve la ruta de acceso del usuario actual (por equipo) raíz del registro para [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], por ejemplo, HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0Exp.  
  
 Se obtiene la raíz del registro local de la <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell> service. Si no está disponible, se obtiene desde el atributo DefaultLocalRegistryRoot del VSPackage.  
  
 <xref:Microsoft.VisualStudio.Shell.Package.UserDataPath%2A>  
 Devuelve la ruta de acceso del directorio que sirve de repositorio común para [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] datos para el actual usuario móvil, por ejemplo, C:\Documents and Settings\\*YourAccountName*\Application VisualStudio\8.0Exp.  
  
 <xref:Microsoft.VisualStudio.Shell.Package.UserLocalDataPath%2A>  
 Devuelve la ruta de acceso del directorio que sirve de repositorio común para [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] datos para el que no son móviles usuario actual, por ejemplo, C:\Documents and Settings\\*YourAccountName*\Local Data\Microsoft\VisualStudio\8.0Exp.  
  
## <a name="see-also"></a>Vea también  
 [Estado de VSPackage](../misc/vspackage-state.md)