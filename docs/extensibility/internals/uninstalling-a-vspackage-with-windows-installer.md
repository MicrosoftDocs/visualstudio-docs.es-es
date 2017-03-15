---
title: "Desinstalaci&#243;n de un paquete VSPackage con Windows Installer | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "paquetes, desinstalar"
  - "VSPackages, desinstalar"
  - "desinstalación de VSPackages"
ms.assetid: c4575ac7-82da-4af8-a375-ea756a101fbf
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# Desinstalaci&#243;n de un paquete VSPackage con Windows Installer
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

En su mayor parte, Windows Installer puede desinstalar el VSPackage simplemente por "deshacer" lo hice para instalar el paquete VSPackage. Las acciones personalizadas que se tratan en [Comandos que se deben ejecutar después de la instalación](../../extensibility/internals/commands-that-must-be-run-after-installation.md) se debe ejecutar después de una desinstalación también. Como las llamadas a devenv.exe se producen justo antes de la acción de InstallFinalize estándar para la instalación y desinstalación, las entradas de tabla CustomAction y InstallExecuteSequence sirven ambos casos.  
  
> [!NOTE]
>  Ejecute `devenv /setup` después de desinstalar un paquete MSI.  
  
 Como regla general, si agregar acciones personalizadas a un paquete de Windows Installer, debe controlar esas acciones durante la reversión y desinstalación. Por ejemplo, si agrega las acciones personalizadas para registrar automáticamente el VSPackage, debe agregar acciones personalizadas para anular su registro, demasiado.  
  
> [!NOTE]
>  Es posible que un usuario instalar el paquete VSPackage y, a continuación, desinstale las versiones de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] con que está integrado. Puede ayudar a asegurarse de que la desinstalación de su VSPackage funciona en ese escenario eliminando acciones personalizadas que se ejecutan código con dependencias en [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## Control de las condiciones de inicio en la desinstalación  
 La acción estándar de LaunchConditions lee las filas de la tabla LaunchCondition para mostrar error mensajes si no se cumplen las condiciones. Como las condiciones de inicio se utilizan normalmente para asegurarse de que se cumplen los requisitos del sistema, por lo general, puede omitir las condiciones de inicio durante la desinstalación agregando la condición, `NOT Installed`, a la fila LaunchConditions de la tabla LaunchCondition.  
  
 Una alternativa es agregar `OR Installed` a condiciones que no sean importantes durante la desinstalación de inicio. Esto asegura que la condición siempre será verdadera durante la desinstalación y, por tanto, no mostrará el mensaje de error de la condición de inicio.  
  
> [!NOTE]
>  `Installed` es la propiedad de que Windows Installer se establece cuando detecta que el VSPackage ya se ha instalado en el sistema.  
  
## Vea también  
 [Windows Installer](http://msdn.microsoft.com/es-es/187d8965-c79d-4ecb-8689-10930fa8b3b5)   
 [Detectar los requisitos del sistema](../../extensibility/internals/detecting-system-requirements.md)