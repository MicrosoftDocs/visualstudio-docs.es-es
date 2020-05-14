---
title: 'Advertencia de seguridad: Adjuntar a un proceso que pertenezca a un usuario que no sea de confianza puede ser peligroso. Si la información siguiente le resulta sospechosa o no está seguro de su procedencia, no la adjunte a este proceso | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.attachsecuritywarning
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 52246c1e-a371-40a0-b756-a435cc51876f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 05b78ea0ca06a0ba9670e61cc065cf539ea21ebc
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72729774"
---
# <a name="security-warning-attaching-to-a-process-owned-by-an-untrusted-user-can-be-dangerous-if-the-following-information-looks-suspicious-or-you-are-unsure-do-not-attach-to-this-process"></a>Advertencia de seguridad: Adjuntar a un proceso que pertenezca a un usuario que no sea de confianza puede ser peligroso. Si la información siguiente le resulta sospechosa o no está seguro de su procedencia, no la adjunte a este proceso
Este cuadro de diálogo de advertencia aparece cuando se asocia a un proceso que contiene código de confianza parcial o que pertenece a un usuario que no es de confianza, inmediatamente antes de que ocurra la asociación. Un proceso que no es de confianza y que contiene código malintencionado puede dañar el equipo que lleva a cabo la depuración. Si existen razones para desconfiar del proceso, debe hacer clic en **Cancelar** para evitar la depuración.

 Para suprimir esta advertencia al depurar un escenario legítimo, cierre Visual Studio y establezca el valor de esta clave del Registro en 1: `HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\<version>\Debugger\DisableAttachSecurityWarning` y, después, reinicie Visual Studio. Cuando termine de depurar el escenario, restablezca el valor a 0, y reinicie Visual Studio.

 Entre los "usuarios de confianza" se encuentra usted, además de un conjunto de usuarios estándar que normalmente se definen en equipos que tienen instalado .NET Framework, como es el caso de `aspnet`, `localsystem`, `networkservice` y `localservice`.

## <a name="uielement-list"></a>Lista de UIElement
 Nombre: nombre del ensamblado que se solicitó depurar

 Usuario: usuario actual

 Adjuntar: presione este botón para seguir depurando mediante asociación

 No adjuntar: no se asocia al proceso

## <a name="see-also"></a>Vea también
- [Asociar a procesos en ejecución](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)
- [Seguridad del depurador](../debugger/debugger-security.md)