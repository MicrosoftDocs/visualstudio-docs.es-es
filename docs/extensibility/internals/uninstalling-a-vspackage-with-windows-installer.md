---
title: Desinstalar un paquete VSPackage con Windows Installer | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- packages, uninstalling
- VSPackages, uninstalling
- uninstalling VSPackages
ms.assetid: c4575ac7-82da-4af8-a375-ea756a101fbf
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1a45505a1a423243d54fbb4bb7bfd206dfa0adc2
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/21/2019
ms.locfileid: "56611859"
---
# <a name="uninstalling-a-vspackage-with-windows-installer"></a>Desinstalación de un VSPackage con Windows Installer
En su mayor parte, Windows Installer puede desinstalar el paquete de VS simplemente por "deshacer" lo hice para instalar el paquete de VS. Describen las acciones personalizadas en [comandos que debe ser ejecutar después de instalación](../../extensibility/internals/commands-that-must-be-run-after-installation.md) se debe ejecutar después de una desinstalación también. Dado que las llamadas a devenv.exe se producen justo antes de la acción de InstallFinalize estándar para la instalación y desinstalación, las entradas de tabla CustomAction y InstallExecuteSequence servir ambos casos.

> [!NOTE]
>  Ejecute `devenv /setup` después de desinstalar un paquete MSI.

 Como norma general, si agrega las acciones personalizadas a un paquete de Windows Installer, debe controlar esas acciones durante la reversión y desinstalación. Por ejemplo, si agrega las acciones personalizadas para registrar automáticamente el paquete de VS, debe agregar acciones personalizadas para anular el registro, demasiado.

> [!NOTE]
>  Es posible que un usuario instalar el paquete de VS y, a continuación, desinstale las versiones de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] con el que está integrado. Puede ayudar a asegurarse de que la desinstalación de su VSPackage funciona en ese escenario mediante la eliminación de las acciones personalizadas que se ejecutan código con dependencias en [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

## <a name="handling-launch-conditions-at-uninstall-time"></a>Control de las condiciones de inicio en el momento de la desinstalación
 La acción estándar LaunchConditions lee las filas de la tabla LaunchCondition para mostrar error mensajes si no se cumplen las condiciones. Ya que generalmente se usan las condiciones de inicio para asegurarse de que se cumplen los requisitos del sistema, por lo general, puede omitir las condiciones de inicio durante la desinstalación mediante la adición de la condición, `NOT Installed`, a la fila LaunchConditions de la tabla LaunchCondition.

 Una alternativa consiste en agregar `OR Installed` para iniciar las condiciones que no son importantes durante la desinstalación. Que garantiza que la condición siempre será verdadera durante la desinstalación y, por tanto, no mostrará el mensaje de error de condición de inicio.

> [!NOTE]
>  `Installed` es la propiedad de que Windows Installer se establece cuando detecta que el VSPackage se ha instalado en el sistema.

## <a name="see-also"></a>Vea también
- [Windows Installer](https://msdn.microsoft.com/library/187d8965-c79d-4ecb-8689-10930fa8b3b5)
- [Detección de requisitos del sistema](../../extensibility/internals/detecting-system-requirements.md)