---
title: Depuración de los servicios de Azure | Microsoft Docs
description: Puede depurar servicios de Azure con Visual Studio. Use los vínculos de este artículo para obtener información sobre las distintas formas de hacerlo.
ms.custom: SEO-VS-2020
ms.date: 09/14/2018
ms.topic: how-to
helpviewer_keywords:
- debugger
ms.assetid: 3d434de3-ee5f-419d-9a94-ac4ac02d635b
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- azure
ms.openlocfilehash: a77f1291621e84eb2e13075a791e9c6735447137
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99857627"
---
# <a name="debug-azure-services-in-visual-studio"></a>Depuración de los servicios de Azure en Visual Studio

Puede usar Visual Studio para depurar servicios de Azure en distintos escenarios:

Para depurar una aplicación de producción hospedada en:

- Azure App Service, con Visual Studio Enterprise, vea [Depuración de aplicaciones ASP.NET en vivo con Snapshot Debugger](../debugger/debug-live-azure-applications.md).

- Azure App Service o Service Fabric, con Application Insights, vea [Depuración de instantáneas cuando se producen excepciones en aplicaciones de .NET](/azure/application-insights/app-insights-snapshot-debugger).

- Una máquina virtual de Azure o un conjunto de escalado de máquinas virtuales de Azure, vea [Depuración de aplicaciones de ASP.NET en vivo en Azure Virtual Machines y Azure Virtual Machine Scale Sets con Snapshot Debugger](../debugger/debug-live-azure-virtual-machines.md).

- Azure Kubernetes Service, vea [Depuración de Azure Kubernetes Service de ASP.NET en vivo con Snapshot Debugger](../debugger/debug-live-azure-kubernetes.md).

Para depurar de forma remota:

- ASP.NET en IIS (Azure App Service o una máquina virtual de Azure), vea [Depuración remota de ASP.NET en Azure](remote-debugging-azure.md).

- ASP.NET en Azure Service Fabric, vea [Depurar una aplicación de Service Fabric remota](/azure/service-fabric/service-fabric-debugging-your-application#debug-a-remote-service-fabric-application).

## <a name="see-also"></a>Vea también

- [Depurar en Visual Studio](../debugger/index.yml)
