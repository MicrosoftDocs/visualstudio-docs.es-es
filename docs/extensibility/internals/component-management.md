---
title: Administración de componentes | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- installation [Visual Studio SDK], components
- installation [Visual Studio SDK], file management
ms.assetid: 029bffa2-6841-4caa-a41a-442467e1aedc
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 887f71f5aabf7acfdeb822bb4e05c1b0debf63ab
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/21/2019
ms.locfileid: "56602005"
---
# <a name="component-management"></a>Administración de componentes
Unidades de tareas en el instalador de Windows se conocen como componentes de Windows Installer (a veces denominados WICs o simplemente componentes). Un GUID identifica cada WIC, que es la unidad básica de la instalación y el recuento de referencias para las configuraciones que usan a Windows Installer.

 Aunque puede usar varios de los productos para crear el instalador de VSPackage, esta explicación se da por supuesto el uso de Windows Installer (*.msi*) los archivos. Al crear al instalador, debe administrar correctamente implementación del archivo para que el recuento de referencias correcto se produce en todo momento. Por lo tanto, diferentes versiones del producto no interfiera con o interrumpir entre sí en una combinación de la instalación y escenarios de desinstalación.

 En Windows Installer, recuento de referencias se produce en el nivel de componente. Cuidadosamente debe organizar los recursos, archivos, entradas del registro y así sucesivamente, en componentes. Hay otros niveles de organización, como módulos, características y productos, que puede ayudar en escenarios diferentes. Para obtener más información, consulte [conceptos básicos de Windows Installer](../../extensibility/internals/windows-installer-basics.md).

## <a name="guidelines-of-authoring-setup-for-side-by-side-installation"></a>Instrucciones de instalación en paralelo de creación

-   Archivos de autor y las claves del registro que se comparten entre las versiones en sus propios componentes.

     Si lo hace, podrá usarlos fácilmente en la próxima versión. Por ejemplo, las bibliotecas de tipos que se registran de forma global, las extensiones de archivo, otros elementos registrados en **HKEY_CLASSES_ROOT**, y así sucesivamente.

-   Agrupar los componentes compartidos en los módulos de combinación independiente.

     Esta estrategia ayuda a autor correctamente para la instalación en paralelo más adelante.

-   Instalar los archivos compartidos y las claves del registro mediante los mismos componentes de Windows Installer a través de versiones.

     Si usa un componente diferente, se desinstalan los archivos y las entradas del registro cuando se desinstala un paquete VSPackage con control de versiones, pero todavía se instala otro VSPackage.

-   No mezcle los elementos con control de versiones y compartidos en el mismo componente.

     Esto hace imposible instalar los elementos compartidos en una ubicación global y elementos con control de versiones a ubicaciones aisladas.

-   No tiene claves de registro compartido que apuntan a archivos con control de versiones.

     Si lo hace, las claves compartidas se sobrescribirán cuando se instala otro paquete VSPackage con control de versiones. Después de quitar la segunda versión, el archivo a la que señala la clave ha desaparecido.

## <a name="see-also"></a>Vea también
- [Elección entre VSPackages compartidos y con control de versiones](../../extensibility/choosing-between-shared-and-versioned-vspackages.md)
- [Escenarios de instalación de VSPackage](../../extensibility/internals/vspackage-setup-scenarios.md)