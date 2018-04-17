---
title: Componente Administración | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- installation [Visual Studio SDK], components
- installation [Visual Studio SDK], file management
ms.assetid: 029bffa2-6841-4caa-a41a-442467e1aedc
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2798d820249f0a1c4310569d22d8510710ca13ee
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="component-management"></a>Administración de componentes
Unidades de tareas de Windows Installer se conocen como componentes de Windows Installer (a veces denominados WICs o simplemente componentes). Un GUID identifica cada WIC, que es la unidad básica de la instalación y el recuento de referencias para configuraciones que usan a Windows Installer.  
  
 Aunque puede usar varios productos para crear al instalador de VSPackage, esta explicación supone el uso de archivos de Windows Installer (.msi). Al crear al instalador, debe administrar correctamente la implementación de archivos para que el recuento de referencias correcto se produce en todo momento. Por lo tanto, distintas versiones del producto no interfieren o rompería entre sí en una combinación de la instalación y escenarios de desinstalación.  
  
 En Windows Installer, recuento de referencias se produce en el nivel de componente. Cuidadosamente debe organizar los recursos, archivos, entradas del registro y así sucesivamente, en componentes. Hay otros niveles de organización, como módulos y características, productos, que pueden ayudar a escenarios diferentes. Para obtener más información, consulte [Fundamentos de Windows Installer](../../extensibility/internals/windows-installer-basics.md).  
  
## <a name="guidelines-of-authoring-setup-for-side-by-side-installation"></a>Instrucciones de instalación para la instalación en paralelo de creación  
  
-   Archivos de autor y claves del registro que se comparten entre las versiones en sus propios componentes.  
  
     Esto le permite consumir fácilmente en la próxima versión. Por ejemplo, las bibliotecas de tipos que están registradas globalmente, extensiones de archivos, otros elementos registrados en HKEY_CLASSES_ROOT y así sucesivamente.  
  
-   Agrupar componentes compartidos en los módulos de combinación independiente.  
  
     Esto ayuda a que se crea correctamente para avanzando side-by-side.  
  
-   Instalar los archivos compartidos y claves del registro con los mismos componentes de Windows Installer a través de versiones.  
  
     Si utiliza un componente diferente, se desinstalarán los archivos y entradas del registro cuando se desinstala un paquete de VS con control de versiones, pero todavía se instala otro VSPackage.  
  
-   No mezcle los elementos con control de versiones y compartidos en el mismo componente.  
  
     Si lo hace, sería imposible instalar elementos compartidos en una ubicación global y elementos con control de versiones a ubicaciones aisladas.  
  
-   No tiene claves del registro compartido que apuntan a archivos con control de versiones.  
  
     Si lo hace, las claves compartidas se sobrescribirá cuando se instala otro VSPackage con control de versiones. Después de quitar la segunda versión, el archivo al que apunta la clave ya no existe.  
  
## <a name="see-also"></a>Vea también  
 [Elegir entre VSPackages compartidos y con control de versiones](../../extensibility/choosing-between-shared-and-versioned-vspackages.md)   
 [Escenarios de instalación de VSPackage](../../extensibility/internals/vspackage-setup-scenarios.md)