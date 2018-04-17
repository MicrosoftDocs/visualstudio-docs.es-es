---
title: Elegir el directorio de instalación para un paquete VSPackage | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, installation directory
ms.assetid: 01fbbb5b-f747-446c-afe0-2a081626a945
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 564a184e8b3907f5a61bccc26cfbafa8d2cf8e67
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="choosing-the-installation-directory-for-a-vspackage"></a>Elegir el directorio de instalación para un paquete VSPackage
Un VSPackage y sus archivos auxiliares deben estar en el sistema de archivos de un usuario. La ubicación depende de si el VSPackage está administrado o no administrado, el esquema de control de versiones en paralelo y la elección del usuario.  
  
## <a name="unmanaged-vspackages"></a>VSPackages administrados  
 Un VSPackage no administrado es un servidor COM que se puede instalar en cualquier ubicación. La información de registro debe refleja con exactitud su ubicación. La interfaz de usuario (UI) de instalador debe proporcionar una ubicación predeterminada como un subdirectorio de la propiedad ProgramFilesFolder Windows Installer. Por ejemplo:  
  
 [ProgramFilesFolder] MyCompany\MyVSPackageProduct\V1.0\  
  
 El usuario debería poder cambiar el directorio predeterminado para dar cabida a los usuarios que tenga una partición de arranque pequeños y prefiere instalar aplicaciones y herramientas de otro volumen.  
  
 Si el esquema de side-by-side utiliza un VSPackage con control de versiones, puede usar subdirectorios para almacenar versiones diferentes. Por ejemplo:  
  
 [ProgramFilesFolder] MyCompany\MyVSPackageProduct\V1.0\2002\  
  
 [ProgramFilesFolder] MyCompany\MyVSPackageProduct\V1.0\2003\  
  
 [ProgramFilesFolder] MyCompany\MyVSPackageProduct\V1.0\2005\  
  
## <a name="managed-vspackages"></a>VSPackages administrado  
 VSPackages administrado también puede instalarse en cualquier ubicación. Sin embargo, debe considerar siempre su instalación en la caché global de ensamblados (GAC) para reducir los tiempos de carga de ensamblado. Dado que los VSPackages administrados siempre son ensamblados con nombre seguro, instalarlos en la GAC significa que toma su comprobación de firma de nombre seguro solo durante la instalación. Ensamblados con nombre seguro instalados en otro lugar del sistema de archivos deben tener sus firmas comprueba cada vez que se cargan. Al instalar VSPackages administrado en la GAC, use la herramienta regpkg **/assembly** conmutador que se va a escribir entradas del registro que señalan a nombre seguro del ensamblado.  
  
 Si instala VSPackages administrado en una ubicación distinta de la GAC, siga las instrucciones anteriores que aparecen para VSPackages no administrados para elegir las jerarquías de directorio. Use la herramienta regpkg **/ codebase** conmutador que se va a escribir entradas del registro que señala a la ruta de acceso del ensamblado de VSPackage.  
  
 Para obtener más información, consulte [registrar y anular el registro de VSPackages](../../extensibility/registering-and-unregistering-vspackages.md).  
  
## <a name="satellite-dlls"></a>Archivos DLL satélite  
 Por convención, VSPackage archivos DLL satélite, que contienen recursos para una configuración regional concreta, se encuentran en los subdirectorios del directorio de VSPackage. Los subdirectorios se corresponden con los valores de Id. (LCID) de configuración regional.  
  
 [Administración de VSPackages](../../extensibility/managing-vspackages.md) indica que las entradas del registro controlan dónde [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] realmente busca un VSPackage satélite DLL. Sin embargo, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] intenta cargar un archivo DLL satélite en un subdirectorio con el nombre de un valor LCID, en el orden siguiente:  
  
1.  LCID (VS LCID por ejemplo \1033 para inglés) predeterminado  
  
2.  LCID predeterminado con el subidioma de forma predeterminada.  
  
3.  LCID predeterminado del sistema.  
  
4.  Valor predeterminado del sistema LCID con el subidioma de forma predeterminada.  
  
5.  EE. UU. Inglés (. \1033 o. \0x409).  
  
 Si la DLL de VSPackage incluye recursos y los puntos de entrada del registro SatelliteDll\DllName, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] intenta cargarlos en el orden especificado anteriormente.  
  
## <a name="see-also"></a>Vea también  
 [Elegir entre VSPackages compartidos y con control de versiones](../../extensibility/choosing-between-shared-and-versioned-vspackages.md)   
 [Administrar paquetes VSPackage](../../extensibility/managing-vspackages.md)   
 [Registro de paquetes administrados](http://msdn.microsoft.com/en-us/f69e0ea3-6a92-4639-8ca9-4c9c210e58a1)