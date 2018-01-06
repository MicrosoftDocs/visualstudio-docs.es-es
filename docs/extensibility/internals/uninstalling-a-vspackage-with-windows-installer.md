---
title: Desinstalar un paquete VSPackage con Windows Installer | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- packages, uninstalling
- VSPackages, uninstalling
- uninstalling VSPackages
ms.assetid: c4575ac7-82da-4af8-a375-ea756a101fbf
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: ee8ad89e02dfa8aebbb39a9d7ebe523ad01bb7e9
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="uninstalling-a-vspackage-with-windows-installer"></a>Desinstalar un paquete VSPackage con Windows Installer
En su mayor parte, Windows Installer puede desinstalar el paquete de VS justo por "deshacer" lo que hizo para instalar el paquete de VS. Las acciones personalizadas se describen en [comandos que debe ser ejecutar después de instalación](../../extensibility/internals/commands-that-must-be-run-after-installation.md) se debe ejecutar después de la desinstalación también. Como las llamadas a devenv.exe se producen justo antes de la acción de InstallFinalize estándar para la instalación y desinstalación, las entradas de tabla CustomAction y InstallExecuteSequence sirven ambos casos.  
  
> [!NOTE]
>  Ejecute `devenv /setup` después de desinstalar un paquete MSI.  
  
 Como norma general, si agrega acciones personalizadas a un paquete de Windows Installer, debe controlar dichas acciones durante la desinstalación y reversión. Por ejemplo, si agrega las acciones personalizadas para registrarse ellos mismos el VSPackage, debe agregar acciones personalizadas para anular el registro, demasiado.  
  
> [!NOTE]
>  Es posible que un usuario instalar el paquete de VS y, a continuación, desinstale las versiones de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] con que está integrado. Puede ayudar a asegurarse de que la desinstalación de su VSPackage funciona en ese escenario mediante la eliminación de las acciones personalizadas que se ejecutan código con dependencias en [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## <a name="handling-launch-conditions-at-uninstall-time"></a>Control de las condiciones de inicio en el momento de la desinstalación  
 La acción estándar LaunchConditions lee las filas de la tabla LaunchCondition para mostrar error mensajes si no se cumplen las condiciones. Como las condiciones de inicio se utilizan normalmente para asegurarse de que se cumplen los requisitos de sistema, por lo general, puede omitir las condiciones de inicio durante la desinstalación mediante la adición de la condición, `NOT Installed`, a la fila LaunchConditions de la tabla LaunchCondition.  
  
 Una alternativa consiste en agregar `OR Installed` para iniciar las condiciones que no son importantes durante la desinstalación. Esto asegura que la condición siempre será verdadera durante la desinstalación y, por tanto, no mostrará el mensaje de error de condición de inicio.  
  
> [!NOTE]
>  `Installed`es la propiedad de que Windows Installer se establece cuando detecta que el paquete de VS ya se instaló en el sistema.  
  
## <a name="see-also"></a>Vea también  
 [Instalador de Windows](http://msdn.microsoft.com/en-us/187d8965-c79d-4ecb-8689-10930fa8b3b5)   
 [Detección de requisitos del sistema](../../extensibility/internals/detecting-system-requirements.md)