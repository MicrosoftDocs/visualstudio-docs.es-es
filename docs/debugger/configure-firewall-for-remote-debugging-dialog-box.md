---
title: Configurar Firewall para depuración remota (cuadro de diálogo) | Microsoft Docs
description: Obtenga información sobre el cuadro de diálogo Configurar Firewall para depuración remota, que aparece cuando el Firewall de Windows impide que el depurador reciba datos a través de la red.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.debug.firewallconfiguration
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 86a0cac2e42e1271e689f2b1880eef8ca6d14644
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2020
ms.locfileid: "97728968"
---
# <a name="configure-firewall-for-remote-debugging-dialog-box"></a>Configurar Firewall para depuración remota (cuadro de diálogo)
Este cuadro de diálogo aparece cuando el Firewall de Windows bloquea el depurador y le impide recibir información a través de la red. Para continuar con la depuración remota, debe abrir un "agujero" en el firewall para que el depurador pueda recibir información.

> [!CAUTION]
> Al abrir un "agujero" en el Firewall, puede exponer su equipo a amenazas de seguridad que el Firewall está diseñado para bloquear. Al abrir un "agujero" para la depuración remota se desbloquean los puertos 4020 y 4021 de Visual Studio 2015. En otras versiones de Visual Studio, se usan otros números de puerto. Para más información, vea [Asignaciones de puerto de depurador remoto](../debugger/remote-debugger-port-assignments.md). Además, permite al depurador abrir puertos adicionales. Para más información, vea [Configuración del Firewall de Windows para la depuración remota](../debugger/configure-the-windows-firewall-for-remote-debugging.md).

## <a name="uielement-list"></a>Lista de UIElement
 **Cancelar depuración remota** Cancela el intento de depuración remota. La configuración de seguridad del equipo permanece intacta.

 **Desbloquear la depuración remota de los equipos de la red local (subred)** Habilita la depuración remota de máquinas en la subred local. Esto puede abrir puntos vulnerables en los equipos de la subred local, pero el firewall continúa bloqueando la información procedente del exterior de la subred.

 **Desbloquear la depuración remota desde cualquier equipo** Habilita la depuración remota de máquinas en cualquier parte de la red. Esta configuración es la menos segura.

## <a name="see-also"></a>Vea también

- [Seguridad del depurador](../debugger/debugger-security.md)
- [Remote Debugging](../debugger/remote-debugging.md)
- [Depurar la referencia de la interfaz de usuario](../debugger/debugging-user-interface-reference.md)