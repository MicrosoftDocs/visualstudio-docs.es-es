---
title: Opciones para depurar Azure cloud services | Microsoft Docs
description: Depuración de Azure cloud services
author: mikejo5000
manager: douge
ms.assetid: 80755da7-8350-4f5c-97ce-2962beabb36d
ms.topic: conceptual
ms.workload: azure-vs
ms.date: 03/18/2017
ms.author: mikejo
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.openlocfilehash: bd2608371871b7adc925fc11927fe061b00a1ec6
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/05/2018
ms.locfileid: "51002885"
---
# <a name="learn-the-various-ways-to-debug-an-azure-cloud-service"></a>Aprendizaje de las diversas maneras de depurar un servicio en la nube de Azure
En este artículo se proporciona vínculos a las diversas maneras de depurar un servicio de nube de Azure. 

## <a name="debugging-an-azure-cloud-service-in-visual-studio"></a>Depurar un servicio de nube de Azure en Visual Studio
Puede ahorrar tiempo y dinero mediante el uso de Azure compute emulator para depurar el servicio en la nube en un equipo local. Al depurar un servicio localmente antes de implementarlo, puede mejorar la confiabilidad y rendimiento sin pagar por tiempo de proceso. Sin embargo, podrían producirse algunos errores solo al ejecutar un servicio en la nube en Azure. Errores que se producen cuando se ejecuta un servicio en la nube en Azure pueden depurarse habilitando la depuración remota al publicar su servicio y, a continuación, asociar al depurador a una instancia de rol. Para obtener más información, consulte [depurar su servicio en la nube en el equipo local](vs-azure-tools-debug-cloud-services-virtual-machines.md#debug-your-cloud-service-on-your-local-computer).

## <a name="using-intellitrace"></a>Uso de IntelliTrace 
Si usas Visual Studio Enterprise para escribir roles destinados a .NET Framework 4.5, puede habilitar IntelliTrace en el momento de implementar un servicio de nube de Azure desde Visual Studio. IntelliTrace proporciona un registro que puede usar con Visual Studio para depurar la aplicación como si se estuviera ejecutando en Azure. Para obtener más información, consulte [depurar un servicio en la nube publicado con IntelliTrace y Visual Studio](http://go.microsoft.com/fwlink/p/?LinkId=623016).

## <a name="remote-debugging"></a>Depuración remota 
Puede habilitar la depuración remota en los servicios en la nube en el momento cuando se implementa el servicio en la nube desde Visual Studio. Si decide habilitar la depuración remota para una implementación, servicios de depuración remota se instalan en las máquinas virtuales que se ejecutan cada instancia de rol. Estos servicios, como `msvsmon.exe` : no afectan al rendimiento o dar lugar a costos adicionales. Para obtener más información, consulte [depurar un servicio en la nube en Azure](vs-azure-tools-debug-cloud-services-virtual-machines.md#debug-a-cloud-service-in-azure).

## <a name="next-steps"></a>Pasos siguientes
- [Depuración de una máquina virtual en Visual Studio o un servicio de nube de Azure](./vs-azure-tools-debug-cloud-services-virtual-machines.md) -Obtenga información sobre los detalles de cómo depurar los servicios de nube de Azure.