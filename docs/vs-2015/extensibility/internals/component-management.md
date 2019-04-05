---
title: Administración de componentes | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- installation [Visual Studio SDK], components
- installation [Visual Studio SDK], file management
ms.assetid: 029bffa2-6841-4caa-a41a-442467e1aedc
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c4667bd26db80c005605214eeca9e852a7705bdf
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58988908"
---
# <a name="component-management"></a>Administración de componentes
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Unidades de tareas en el instalador de Windows se conocen como componentes de Windows Installer (a veces denominados WICs o simplemente componentes). Un GUID identifica cada WIC, que es la unidad básica de la instalación y el recuento de referencias para las configuraciones que usan a Windows Installer.  
  
 Aunque puede usar varios de los productos para crear al instalador de VSPackage, esta explicación se da por supuesto el uso de archivos de Windows Installer (.msi). Al crear al instalador, debe administrar correctamente implementación del archivo para que el recuento de referencias correcto se produce en todo momento. Por lo tanto, diferentes versiones del producto no interfiera con o interrumpir entre sí en una combinación de la instalación y escenarios de desinstalación.  
  
 En Windows Installer, recuento de referencias se produce en el nivel de componente. Cuidadosamente debe organizar los recursos, archivos, entradas del registro y así sucesivamente, en componentes. Hay otros niveles de organización, como módulos, características y productos, que puede ayudar en escenarios diferentes. Para obtener más información, consulte [conceptos básicos de Windows Installer](../../extensibility/internals/windows-installer-basics.md).  
  
## <a name="guidelines-of-authoring-setup-for-side-by-side-installation"></a>Instrucciones de instalación en paralelo de creación  
  
-   Archivos de autor y las claves del registro que se comparten entre las versiones en sus propios componentes.  
  
     Esto le permite consumirlos fácilmente en la próxima versión. Por ejemplo, las bibliotecas de tipos que están registradas globalmente, extensiones de archivos, otros elementos registrados en HKEY_CLASSES_ROOT y así sucesivamente.  
  
-   Agrupar los componentes compartidos en los módulos de combinación independiente.  
  
     Esto ayuda a crear correctamente para side-by-side más adelante.  
  
-   Instalar los archivos compartidos y las claves del registro mediante los mismos componentes de Windows Installer a través de versiones.  
  
     Si usa un componente diferente, se desinstalan los archivos y las entradas del registro cuando se desinstala un paquete VSPackage con control de versiones, pero todavía se instala otro VSPackage.  
  
-   No mezcle los elementos con control de versiones y compartidos en el mismo componente.  
  
     Esto hace imposible instalar los elementos compartidos en una ubicación global y elementos con control de versiones a ubicaciones aisladas.  
  
-   No tiene claves de registro compartido que apuntan a archivos con control de versiones.  
  
     Si lo hace, las claves compartidas se sobrescribirán cuando se instala otro paquete VSPackage con control de versiones. Después de quitar la segunda versión, el archivo a la que señala la clave ha desaparecido.  
  
## <a name="see-also"></a>Vea también  
 [Elección entre VSPackages compartidos y con control de versiones](../../extensibility/choosing-between-shared-and-versioned-vspackages.md)   
 [Escenarios de instalación de VSPackage](../../extensibility/internals/vspackage-setup-scenarios.md)
