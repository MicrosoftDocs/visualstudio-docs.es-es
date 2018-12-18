---
title: 'Advertencia de seguridad: Adjuntar a un proceso que pertenezca a un usuario que no sea de confianza puede ser peligroso. Si la información siguiente parece sospechosa o no está seguro, no la adjunte a este proceso | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.attachsecuritywarning
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 52246c1e-a371-40a0-b756-a435cc51876f
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dac3ad5d51e2934bd2cbdf5a8fe9ad30a4a90a8b
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51745587"
---
# <a name="security-warning-attaching-to-a-process-owned-by-an-untrusted-user-can-be-dangerous-if-the-following-information-looks-suspicious-or-you-are-unsure-do-not-attach-to-this-process"></a>Advertencia de seguridad: Adjuntar a un proceso que pertenezca a un usuario que no sea de confianza puede ser peligroso. Si la información siguiente le resulta sospechosa o no está seguro de su procedencia, no la adjunte a este proceso
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Este cuadro de diálogo de advertencia aparece cuando se asocia a un proceso que contiene código de confianza parcial o que pertenece a un usuario que no es de confianza, inmediatamente antes de que ocurra la asociación. Un proceso que no es de confianza y que contiene código malintencionado puede dañar el equipo que lleva a cabo la depuración. Si tiene razones para desconfiar del proceso, debe hacer clic en **cancelar** para evitar la depuración.  
  
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
 [Adjuntar a procesos en ejecución](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Seguridad del depurador](../debugger/debugger-security.md)



