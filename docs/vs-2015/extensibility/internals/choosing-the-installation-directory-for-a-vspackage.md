---
title: Elegir el directorio de instalación de un paquete VSPackage | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- VSPackages, installation directory
ms.assetid: 01fbbb5b-f747-446c-afe0-2a081626a945
caps.latest.revision: 18
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d3ed255d5b8a876ff29e5230c4517ab0b5e04398
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49843410"
---
# <a name="choosing-the-installation-directory-for-a-vspackage"></a>Selección del directorio de instalación de un VSPackage
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Un VSPackage y sus archivos auxiliares deben estar en el sistema de archivos de un usuario. La ubicación depende de si VSPackage está administrado o no administrados, el esquema de versiones en paralelo y la elección del usuario.  
  
## <a name="unmanaged-vspackages"></a>VSPackages no administrados  
 Un VSPackage no administrado es un servidor COM que se puede instalar en cualquier ubicación. La información de registro debe refleja con exactitud su ubicación. La interfaz de usuario (UI) de installer debe proporcionar una ubicación predeterminada como un subdirectorio de la propiedad ProgramFilesFolder Windows Installer. Por ejemplo:  
  
 [ProgramFilesFolder] MyCompany\MyVSPackageProduct\V1.0\  
  
 El usuario debería poder cambiar el directorio predeterminado para dar cabida a los usuarios que tenga una partición de arranque pequeño y prefiera instalar aplicaciones y herramientas en otro volumen.  
  
 Si el esquema de side-by-side usa un VSPackage con control de versiones, puede usar los subdirectorios para almacenar versiones diferentes. Por ejemplo:  
  
 [ProgramFilesFolder] MyCompany\MyVSPackageProduct\V1.0\2002\  
  
 [ProgramFilesFolder] MyCompany\MyVSPackageProduct\V1.0\2003\  
  
 [ProgramFilesFolder] MyCompany\MyVSPackageProduct\V1.0\2005\  
  
## <a name="managed-vspackages"></a>VSPackages administrado  
 VSPackages administrado también puede instalarse en cualquier ubicación. Sin embargo, debe considerar siempre su instalación en la caché global de ensamblados (GAC) para reducir los tiempos de carga de ensamblado. Dado que los paquetes VSPackage administrados siempre son ensamblados con nombre seguro, su instalación en la GAC significa que toma su comprobación de firma de nombre seguro solo durante la instalación. Ensamblados con nombre seguro instalados en otro lugar en el sistema de archivos deben tener sus firmas comprueba cada vez que se cargan. Al instalar los paquetes VSPackage administrados en la GAC, use la herramienta regpkg **/assembly** conmutador para escribir entradas del registro que apunte al nombre seguro del ensamblado.  
  
 Si instala los paquetes VSPackage administrados en una ubicación distinta de la GAC, siga los consejos anteriores dado para los VSPackages no administrados para elegir las jerarquías de directorio. Use la herramienta regpkg **/ codebase** conmutador para escribir entradas del registro que apunte a la ruta de acceso del ensamblado de VSPackage.  
  
 Para obtener más información, consulte [registrar y anular el registro de VSPackages](../../extensibility/registering-and-unregistering-vspackages.md).  
  
## <a name="satellite-dlls"></a>Archivos DLL satélite  
 Por convención, VSPackage archivos DLL satélite, que contiene los recursos de una configuración regional concreta, se encuentran en subdirectorios del directorio de VSPackage. Los subdirectorios se corresponden con los valores de configuración regional (LCID) de identificador.  
  
 [Administración de VSPackages](../../extensibility/managing-vspackages.md) indica que las entradas del registro controlan dónde [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] realmente busca un VSPackage satélite DLL. Sin embargo, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] intenta cargar un archivo DLL satélite en un subdirectorio con nombre para un valor LCID, en el orden siguiente:  
  
1. LCID (por ejemplo \1033 para inglés de LCID de VS) predeterminado  
  
2. LCID predeterminado con el subidioma de forma predeterminada.  
  
3. LCID predeterminado del sistema.  
  
4. Sistema LCID predeterminado con el subidioma de forma predeterminada.  
  
5. EE. UU. Inglés (. \1033 o. \0x409).  
  
   Si la DLL de VSPackage incluye los recursos y los puntos de entrada del registro SatelliteDll\DllName, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] intenta cargarlos en el orden anterior.  
  
## <a name="see-also"></a>Vea también  
 [Elección entre VSPackages compartidos y con control de versiones](../../extensibility/choosing-between-shared-and-versioned-vspackages.md)   
 [Administración de VSPackages](../../extensibility/managing-vspackages.md)   
 [Registro de paquetes administrados](http://msdn.microsoft.com/en-us/f69e0ea3-6a92-4639-8ca9-4c9c210e58a1)

