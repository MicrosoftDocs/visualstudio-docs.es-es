---
title: Preparar la depuración de servicios de Windows | Microsoft Docs
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], Windows services
- Windows Service applications, debugging
ms.assetid: ac0a99f7-ec3d-4a20-b17f-698a817fdcc2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 39928a89dae0f58201ec5f86fa0584095809fe48
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "55018402"
---
# <a name="debugging-preparation-windows-services"></a>Preparación de la depuración: servicios de Windows
Un servicio de Windows es un programa que se ejecuta en segundo plano en Microsoft Windows. Como ejemplos pueden citarse el servicio Telnet y el servicio de hora de Windows (que actualiza el reloj visible del equipo). Un servicio de Windows no se puede ejecutar desde [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]; debe ejecutarse dentro del contexto del Administrador de control de servicios. Para obtener más información, vea [Crear servicios de Windows](/dotnet/framework/windows-services/how-to-create-windows-services), [Depurar aplicaciones de servicios de Windows](/dotnet/framework/windows-services/how-to-debug-windows-service-applications) y [Aplicaciones de servicios de Windows](/dotnet/framework/windows-services/index).  
  
## <a name="see-also"></a>Vea también  
 [Depurar código administrado](../debugger/debugging-managed-code.md)   
 [Tipos de proyectos de C#, F# y Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)   
 [Configuración de proyectos para configuraciones de depuración en C#](../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Configuración de proyectos para una configuración de depuración en Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [Cómo: depurar el método OnStart](../debugger/how-to-debug-the-onstart-method.md)