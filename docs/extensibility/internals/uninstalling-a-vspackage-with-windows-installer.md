---
title: Desinstalación de un VSPackage con Windows Installer | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- packages, uninstalling
- VSPackages, uninstalling
- uninstalling VSPackages
ms.assetid: c4575ac7-82da-4af8-a375-ea756a101fbf
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a8e92937e848d124c18dc91b9bdfa0f020f27f20
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72722127"
---
# <a name="uninstalling-a-vspackage-with-windows-installer"></a>Desinstalación de un VSPackage con Windows Installer
En su mayor parte, Windows Installer puede desinstalar el VSPackage simplemente "deshaciendo" lo que hizo para instalar el VSPackage. Las acciones personalizadas descritas en los [comandos que se deben ejecutar después](../../extensibility/internals/commands-that-must-be-run-after-installation.md) de la instalación deben ejecutarse después de una desinstalación. Dado que las llamadas a devenv. exe se producen justo antes de la acción estándar InstallFinalize para la instalación y desinstalación, las entradas de la tabla CustomAction y InstallExecuteSequence sirven en ambos casos.

> [!NOTE]
> Ejecute `devenv /setup` después de desinstalar un paquete MSI.

 Como norma general, si agrega acciones personalizadas a un paquete de Windows Installer, debe controlar esas acciones durante la desinstalación y la reversión. Si agrega acciones personalizadas para registrar automáticamente el VSPackage, por ejemplo, debe agregar acciones personalizadas para anular su registro.

> [!NOTE]
> Un usuario puede instalar el VSPackage y, a continuación, desinstalar las versiones de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] con las que está integrado. Puede ayudar a garantizar que la desinstalación del VSPackage funcione en ese escenario mediante la eliminación de acciones personalizadas que ejecutan código con dependencias en [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

## <a name="handling-launch-conditions-at-uninstall-time"></a>Administrar condiciones de inicio en el momento de la desinstalación
 La acción estándar LaunchConditions Lee las filas de la tabla LaunchCondition para mostrar los mensajes de error si no se cumplen las condiciones. Como las condiciones de inicio se utilizan generalmente para garantizar que se cumplen los requisitos del sistema, normalmente puede omitir las condiciones de inicio durante la desinstalación agregando la condición, `NOT Installed`, a la fila LaunchConditions de la tabla LaunchCondition.

 Una alternativa consiste en agregar `OR Installed` a las condiciones de inicio que no son importantes durante la desinstalación. Esto garantiza que la condición siempre será verdadera durante la desinstalación y, por lo tanto, no mostrará el mensaje de error de la condición de inicio.

> [!NOTE]
> `Installed` es la propiedad Windows Installer establece cuando detecta que el VSPackage ya está instalado en el sistema.

## <a name="see-also"></a>Vea también
- [Windows Installer](https://msdn.microsoft.com/library/187d8965-c79d-4ecb-8689-10930fa8b3b5)
- [Detección de requisitos del sistema](../../extensibility/internals/detecting-system-requirements.md)