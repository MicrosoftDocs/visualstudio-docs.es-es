---
title: "Configurar Firewall para el cuadro de diálogo de depuración remota | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: vs.debug.firewallconfiguration
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- Configure Firewall for Remote Debugging dialog box
- remote debugging, configuring firewalls
- firewalls, configuring for remote debugging
ms.assetid: 5dff3393-fdeb-4129-a2f6-31f653107a82
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: d945926a08a59fb37e5467591957ee3dcf661b9b
ms.sourcegitcommit: 9e6ff74da1afd8bd2f0e69387ce81f2a74619182
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/04/2018
---
# <a name="configure-firewall-for-remote-debugging-dialog-box"></a>Configurar Firewall para depuración remota (cuadro de diálogo)
Este cuadro de diálogo aparece cuando el Firewall de Windows bloquea el depurador y le impide recibir información a través de la red. Para continuar con la depuración remota, debe abrir un "agujero" en el firewall para que el depurador pueda recibir información.  
  
> [!CAUTION]
>  Al abrir un "agujero" en el Firewall, puede exponer su equipo a amenazas de seguridad que el Firewall está diseñado para bloquear. Al abrir un "agujero" para la depuración remota se desbloquean los puertos 4020 y 4021 de Visual Studio 2015. En otras versiones de Visual Studio, se usan otros números de puerto. Para obtener más información, consulte [asignaciones de puerto de depurador remoto](../debugger/remote-debugger-port-assignments.md). Además, permite al depurador abrir puertos adicionales. Para obtener más información, consulte [configurar Firewall de Windows para la depuración remota](../debugger/configure-the-windows-firewall-for-remote-debugging.md).  
  
## <a name="uielement-list"></a>Lista de UIElement  
 **Cancelar depuración remota**  
 Cancela el intento de depuración remota. La configuración de seguridad del equipo permanece intacta.  
  
 **Desbloquear la depuración remota desde equipos de la red local (subred)**  
 Permite la depuración remota de los equipos de la subred local. Esto puede abrir puntos vulnerables en los equipos de la subred local, pero el firewall continúa bloqueando la información procedente del exterior de la subred.  
  
 **Desbloquear la depuración remota desde cualquier equipo**  
 Permite la depuración remota de cualquier equipo de la red. Esta configuración es la menos segura.  
  
## <a name="see-also"></a>Vea también  
 [Seguridad del depurador](../debugger/debugger-security.md)   
 [Depuración remota](../debugger/remote-debugging.md)  
 [Depurar la referencia de la interfaz de usuario](../debugger/debugging-user-interface-reference.md)