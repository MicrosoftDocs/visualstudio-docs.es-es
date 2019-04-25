---
title: 'Preparación de la depuración: Servicios de Windows | Documentos de Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
- VB
- CSharp
helpviewer_keywords:
- debugging [Visual Studio], Windows services
- Windows Service applications, debugging
ms.assetid: ac0a99f7-ec3d-4a20-b17f-698a817fdcc2
caps.latest.revision: 23
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3d18dcf94c9dd1223446e55025465d1a3b455526
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58996740"
---
# <a name="debugging-preparation-windows-services"></a>Preparación de la depuración: servicios de Windows
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Un servicio de Windows es un programa que se ejecuta en segundo plano en Microsoft Windows. Como ejemplos pueden citarse el servicio Telnet y el servicio de hora de Windows (que actualiza el reloj visible del equipo). Un servicio de Windows no se puede ejecutar desde [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]; debe ejecutarse dentro del contexto del Administrador de control de servicios. Para obtener más información, vea [Crear servicios de Windows](http://msdn.microsoft.com/library/0f5e2cbb-d95d-477c-b2b5-4b990e6b86ff), [Depurar aplicaciones de servicios de Windows](http://msdn.microsoft.com/library/63ab0800-0f05-4f1e-88e6-94c73fd920a2) y [Aplicaciones de servicios de Windows](http://msdn.microsoft.com/library/ba72d648-9553-4849-b829-069ad5ea014b).  
  
## <a name="see-also"></a>Vea también  
 [Depurar código administrado](../debugger/debugging-managed-code.md)   
 [Tipos de proyectos de C#, F# y Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)   
 [Configuración de proyectos para configuraciones de depuración en C#](../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Configuración de proyectos para una configuración de depuración en Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [Cómo: depurar el método OnStart](../debugger/how-to-debug-the-onstart-method.md)
