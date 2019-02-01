---
title: 'Advertencia de seguridad: Adjuntar a un proceso que pertenezca a un usuario que no sea de confianza puede ser peligroso. Si la información siguiente parece sospechosa o no está seguro, no la adjunte a este proceso | Microsoft Docs'
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
ms.openlocfilehash: 17511c5f89ca40cc002a80da955df10c8773b97c
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54952189"
---
# <a name="security-warning-attaching-to-a-process-owned-by-an-untrusted-user-can-be-dangerous-if-the-following-information-looks-suspicious-or-you-are-unsure-do-not-attach-to-this-process"></a>Advertencia de seguridad: Adjuntar a un proceso que pertenezca a un usuario que no sea de confianza puede ser peligroso. Si la información siguiente le resulta sospechosa o no está seguro de su procedencia, no la adjunte a este proceso
Este cuadro de diálogo de advertencia aparece cuando se asocia a un proceso que contiene código de confianza parcial o que pertenece a un usuario que no es de confianza, inmediatamente antes de que ocurra la asociación. Un proceso que no es de confianza y que contiene código malintencionado puede dañar el equipo que lleva a cabo la depuración. Si existen razones para desconfiar del proceso, debe hacer clic en **Cancelar** para evitar la depuración.  
  
 Para suprimir esta advertencia cuando se depura un escenario legítimo, cierre Visual Studio y establezca el valor de esta clave del registro en 1: `HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\<version>\Debugger\DisableAttachSecurityWarning`y, a continuación, reinicie Visual Studio. Cuando termine de depurar el escenario, restablezca el valor a 0, y reinicie Visual Studio.  
  
 Entre los "usuarios de confianza" se encuentra usted, además de un conjunto de usuarios estándar que normalmente se definen en equipos que tienen instalado .NET Framework, como es el caso de `aspnet`, `localsystem`, `networkservice` y `localservice`.  
  
## <a name="uielement-list"></a>Lista de UIElement  
 nombre  
 Nombre del ensamblado que se solicitó depurar  
  
 Usuario  
 Usuario actual  
  
 Attach  
 Presione este botón para seguir depurando mediante asociación  
  
 No adjuntar  
 No se asocia al proceso  
  
## <a name="see-also"></a>Vea también  
 [Asociar a procesos en ejecución](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Seguridad del depurador](../debugger/debugger-security.md)