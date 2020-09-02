---
title: Configurar Firewall para depuración remota (cuadro de diálogo) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.firewallconfiguration
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
helpviewer_keywords:
- Configure Firewall for Remote Debugging dialog box
- remote debugging, configuring firewalls
- firewalls, configuring for remote debugging
ms.assetid: 5dff3393-fdeb-4129-a2f6-31f653107a82
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 26e2b1300feb8d2a15e63089ee9bddde5f2d1ef4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "65702285"
---
# <a name="configure-firewall-for-remote-debugging-dialog-box"></a>Configurar Firewall para depuración remota (cuadro de diálogo)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Este cuadro de diálogo aparece cuando el Firewall de Windows bloquea el depurador y le impide recibir información a través de la red. Para continuar con la depuración remota, debe abrir un "agujero" en el firewall para que el depurador pueda recibir información.  
  
> [!CAUTION]
> Al abrir un "agujero" en el Firewall, puede exponer su equipo a amenazas de seguridad que el Firewall está diseñado para bloquear. Al abrir un "agujero" para la depuración remota se desbloquean los puertos 4020 y 4021 de Visual Studio 2015. En otras versiones de Visual Studio, se usan otros números de puerto. Para más información, vea [Asignaciones de puerto de depurador remoto](../debugger/remote-debugger-port-assignments.md). Además, permite al depurador abrir puertos adicionales. Para más información, vea [Configuración del Firewall de Windows para la depuración remota](../debugger/configure-the-windows-firewall-for-remote-debugging.md).  
  
## <a name="uielement-list"></a>Lista de UIElement  
 **Cancelar depuración remota**  
 Cancela el intento de depuración remota. La configuración de seguridad del equipo permanece intacta.  
  
 **Desbloquear la depuración remota de los equipos de la red local (subred)**  
 Permite la depuración remota de los equipos de la subred local. Esto puede abrir puntos vulnerables en los equipos de la subred local, pero el firewall continúa bloqueando la información procedente del exterior de la subred.  
  
 **Desbloquear la depuración remota desde cualquier equipo**  
 Permite la depuración remota de cualquier equipo de la red. Esta configuración es la menos segura.  
  
## <a name="see-also"></a>Consulte también  
 [Seguridad del depurador](../debugger/debugger-security.md)   
 [Configuración del Herramientas remotas en el dispositivo](https://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c)   
 [Depurar la referencia de la interfaz de usuario](../debugger/debugging-user-interface-reference.md)
