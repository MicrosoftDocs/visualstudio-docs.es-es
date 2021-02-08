---
title: Opciones de depuración de servicios en la nube de Azure | Microsoft Docs
description: Depuración de servicios en la nube de Azure
author: mikejo5000
manager: jmartens
ms.topic: conceptual
ms.workload: azure-vs
ms.date: 03/18/2017
ms.author: mikejo
ms.technology: vs-ide-debug
ms.openlocfilehash: 2471b79c7401d63b9655586fc4745d3977d37275
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99844234"
---
# <a name="learn-the-various-ways-to-debug-an-azure-cloud-service"></a>Aprendizaje de las diversas maneras de depurar un servicio en la nube de Azure
Este artículo contiene vínculos a las diversas maneras de depurar un servicio en la nube de Azure.

## <a name="debugging-an-azure-cloud-service-in-visual-studio"></a>Depuración de un servicio en la nube de Azure en Visual Studio
Puede ahorrar tiempo y dinero si utiliza el emulador de proceso de Azure para depurar su servicio en la nube en un equipo local. La depuración de un servicio localmente antes de su implementación puede mejorar la fiabilidad y el rendimiento sin pagar por tiempo de proceso. No obstante, podrían producirse algunos errores solo al ejecutar un servicio en la nube en Azure. Los errores que se producen solo al ejecutar un servicio en la nube de Azure pueden depurarse habilitando la depuración remota cuando se publique el servicio. Luego, se debe asociar el depurador a una instancia de rol. Para obtener más información, consulte [Depuración del servicio en la nube en el equipo local](vs-azure-tools-debug-cloud-services-virtual-machines.md#debug-your-cloud-service-on-your-local-computer).

## <a name="using-intellitrace"></a>Uso de IntelliTrace
Si usa Visual Studio Enterprise para escribir roles destinados a .NET Framework 4.5, puede habilitar IntelliTrace en el momento de implementar un servicio en la nube de Azure desde Visual Studio. IntelliTrace proporciona un registro que se puede usar con Visual Studio para depurar la aplicación como si se estuviera ejecutando en Azure. Para obtener más información, vea [Depurar con IntelliTrace y Visual Studio un servicio en la nube](vs-azure-tools-intellitrace-debug-published-cloud-services.md).

## <a name="remote-debugging"></a>Depuración remota
Puede habilitar la depuración remota en los servicios en la nube cuando implementa el servicio en la nube desde Visual Studio. Si elige habilitar la depuración remota para una implementación, los servicios de depuración remota se instalan en las máquinas virtuales que ejecutan cada instancia de rol. Estos servicios, como `msvsmon.exe`, no afectan al rendimiento ni al resultado en cuanto a costos adicionales. Para obtener más información, consulte [Depuración de un servicio en la nube en Azure](vs-azure-tools-debug-cloud-services-virtual-machines.md#debug-a-cloud-service-in-azure).

## <a name="next-steps"></a>Pasos siguientes
- [Depurar una máquina virtual o un servicio en la nube de Azure en Visual Studio](./vs-azure-tools-debug-cloud-services-virtual-machines.md): Obtenga información sobre cómo depurar los servicios en la nube de Azure.
