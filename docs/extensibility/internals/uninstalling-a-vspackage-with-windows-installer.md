---
title: Desinstalación de un VSPackage con Windows Installer ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- packages, uninstalling
- VSPackages, uninstalling
- uninstalling VSPackages
ms.assetid: c4575ac7-82da-4af8-a375-ea756a101fbf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fee88e895d40d42114eaf53422503524594b485f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704271"
---
# <a name="uninstalling-a-vspackage-with-windows-installer"></a>Desinstalación de un VSPackage con Windows Installer
En su mayor parte, Windows Installer puede desinstalar el VSPackage simplemente "deshacer" lo que hizo para instalar el VSPackage. Las acciones personalizadas descritas en [Comandos que deben ejecutarse después](../../extensibility/internals/commands-that-must-be-run-after-installation.md) de la instalación también deben ejecutarse después de una desinstalación. Dado que las llamadas a devenv.exe se producen justo antes de la acción estándar InstallFinalize para la instalación y la desinstalación, las entradas de tabla CustomAction e InstallExecuteSequence sirven en ambos casos.

> [!NOTE]
> Ejecutar `devenv /setup` después de desinstalar un paquete MSI.

 Como regla general, si agrega acciones personalizadas a un paquete de Windows Installer, debe controlar esas acciones durante la desinstalación y la reversión. Si agrega acciones personalizadas para registrar automáticamente el VSPackage, por ejemplo, también debe agregar acciones personalizadas para anular el registro.

> [!NOTE]
> Es posible que un usuario instale el VSPackage [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] y, a continuación, desinstale las versiones con las que está integrado. Puede ayudar a asegurarse de que la desinstalación de VSPackage funciona en [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]ese escenario eliminando las acciones personalizadas que ejecutan código con dependencias en .

## <a name="handling-launch-conditions-at-uninstall-time"></a>Manejo de las condiciones de lanzamiento en el momento de la desinstalación
 La acción estándar LaunchConditions lee las filas de la tabla LaunchCondition para mostrar mensajes de error si no se cumplen las condiciones. Como las condiciones de lanzamiento se usan generalmente para garantizar que se cumplen los `NOT Installed`requisitos del sistema, generalmente puede omitir las condiciones de lanzamiento durante la desinstalación agregando la condición, , a la fila LaunchConditions de la tabla LaunchCondition.

 Una alternativa es `OR Installed` agregar a las condiciones de lanzamiento que no son importantes durante la desinstalación. Esto garantiza que la condición siempre será verdadera durante la desinstalación y, por lo tanto, no mostrará el mensaje de error de condición de inicio.

> [!NOTE]
> `Installed`es la propiedad que Windows Installer establece cuando detecta que el VSPackage ya se ha instalado en el sistema.

## <a name="see-also"></a>Vea también
- [Windows Installer](https://msdn.microsoft.com/library/187d8965-c79d-4ecb-8689-10930fa8b3b5)
- [Detección de requisitos del sistema](../../extensibility/internals/detecting-system-requirements.md)
