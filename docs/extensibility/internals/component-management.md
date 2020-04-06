---
title: Gestión de componentes (Gestión de componentes Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- installation [Visual Studio SDK], components
- installation [Visual Studio SDK], file management
ms.assetid: 029bffa2-6841-4caa-a41a-442467e1aedc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b5dcac9fb14a83021b852be2c52436fcdca84bf5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709336"
---
# <a name="component-management"></a>Gestión de componentes
Las unidades de tareas en Windows Installer se conocen como componentes de Windows Installer (a veces denominados WIC o simplemente componentes). Un GUID identifica cada WIC, que es la unidad básica de instalación y recuento de referencias para las configuraciones que usan Windows Installer.

 Aunque puede usar varios productos para crear el instalador de VSPackage, esta discusión supone el uso de archivos de Windows Installer (*.msi*). Al crear el instalador, debe administrar correctamente la implementación de archivos para que se haya quedo en todo momento el recuento de referencias correcto. Por lo tanto, diferentes versiones de su producto no interferirán ni se romperán entre sí en una combinación de escenarios de instalación y desinstalación.

 En Windows Installer, el recuento de referencias se produce en el nivel de componente. Debe organizar cuidadosamente los recursos (archivos, entradas del registro, etc.) en componentes. Hay otros niveles de organización, como módulos, características y productos, que pueden ayudar en diferentes escenarios. Para obtener más información, consulte [Conceptos básicos](../../extensibility/internals/windows-installer-basics.md)de Windows Installer .

## <a name="guidelines-of-authoring-setup-for-side-by-side-installation"></a>Directrices de la configuración de creación para la instalación en paralelo

- Cree archivos y claves de registro que se comparten entre versiones en sus propios componentes.

     Esto le permite consumirlos fácilmente en la próxima versión. Por ejemplo, escriba bibliotecas que estén registradas globalmente, extensiones de archivo, otros elementos registrados en HKEY_CLASSES_ROOT , **etc.**

- Agrupe los componentes compartidos en módulos de combinación independientes.

     Esta estrategia le ayuda a crear correctamente para la instalación en paralelo en el futuro.

- Instale los archivos compartidos y las claves del Registro mediante los mismos componentes de Windows Installer en todas las versiones.

     Si usa un componente diferente, los archivos y las entradas del registro se desinstalan cuando se desinstala un VSPackage versionado, pero otro VSPackage sigue instalado.

- No mezcle elementos versionados y compartidos en el mismo componente.

     Al hacerlo, es imposible instalar elementos compartidos en una ubicación global y elementos versionados en ubicaciones aisladas.

- No tiene claves de registro compartidas que apunten a archivos versionados.

     Si lo hace, las claves compartidas se sobrescribirán cuando se instale otro VSPackage versionado. Después de quitar la segunda versión, el archivo al que apunta la clave ha desaparecido.

## <a name="see-also"></a>Vea también
- [Elija entre VSPackages compartidos y versionados](../../extensibility/choosing-between-shared-and-versioned-vspackages.md)
- [Escenarios de configuración de VSPackage](../../extensibility/internals/vspackage-setup-scenarios.md)
