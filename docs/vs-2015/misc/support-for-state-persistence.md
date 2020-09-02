---
title: Compatibilidad con la persistencia de estado | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "62434324"
---
# <a name="support-for-state-persistence"></a>Compatibilidad con la persistencia de estado
[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] puede mantener el estado de los objetos comunes. Por ejemplo, las propiedades de solución y proyecto se guardan en y se restauran a partir de archivos de proyecto y de solución. La configuración de usuario se puede exportar e importar desde archivos de configuración.  
  
 Los VSPackages normalmente se basan en el almacenamiento local, ya sea en el registro del sistema o en la carpeta de datos de la aplicación para el usuario o equipo actual. Los valores que requieren una pequeña cantidad de espacio para el almacenamiento, como enteros y cadenas, normalmente se almacenan en el registro del sistema. Los valores que requieren gran cantidad de espacio para el almacenamiento, como los mapas de bits, se guardan en un archivo. La ruta de acceso del archivo se puede guardar en el registro del sistema. El mecanismo de persistencia debe tener permiso de acceso al almacenamiento local.  
  
## <a name="support-for-locating-local-storage"></a>Compatibilidad con la búsqueda de almacenamiento local  
 La <xref:Microsoft.VisualStudio.Shell.Package> clase proporciona compatibilidad para buscar información de estado en el registro del sistema o en la carpeta de datos de la aplicación para el usuario o equipo actual.  
  
 <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>  
 Devuelve la ruta de acceso de la raíz del registro del equipo local para [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , por ejemplo, HKEY_LOCAL_MACHINE \software\microsoft\visualstudio\8.0exp.  
  
 La raíz del registro local se obtiene del <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell> servicio. Si no está disponible, se obtiene del <xref:Microsoft.VisualStudio.Shell.DefaultRegistryRootAttribute> atributo del VSPackage.  
  
 <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A>  
 Devuelve la ruta de acceso de la raíz del registro (por equipo) del usuario actual para [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , por ejemplo, HKEY_CURRENT_USER \software\microsoft\visualstudio\8.0exp.  
  
 La raíz del registro local se obtiene del <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell> servicio. Si no está disponible, se obtiene del atributo DefaultLocalRegistryRoot del VSPackage.  
  
 <xref:Microsoft.VisualStudio.Shell.Package.UserDataPath%2A>  
 Devuelve la ruta de acceso del directorio que sirve de repositorio común para [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] los datos del usuario móvil actual; por ejemplo, C:\Documents and Settings \\ *YourAccountName*\Application Data\Microsoft\VisualStudio\8.0Exp.  
  
 <xref:Microsoft.VisualStudio.Shell.Package.UserLocalDataPath%2A>  
 Devuelve la ruta de acceso del directorio que sirve de repositorio común para [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] los datos del usuario no móvil actual; por ejemplo, C:\Documents and Settings \\ *YourAccountName*\Local Settings\Application Data\Microsoft\VisualStudio\8.0Exp.  
  
## <a name="see-also"></a>Consulte también  
 [Estado de VSPackage](../misc/vspackage-state.md)