---
title: Acceso a Azure Virtual Machines desde el Explorador de servidores | Microsoft Docs
description: Obtenga una visión general de cómo ver, crear y administrar Azure los máquinas virtuales (VM) en el Explorador de servidores de Visual Studio.
author: ghogen
manager: jillfra
assetId: eb3afde6-ba90-4308-9ac1-3cc29da4ede0
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 8/31/2017
ms.author: ghogen
ms.openlocfilehash: a9ca956400956ae337d8d1e0f5a881f1dc4c6377
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/05/2020
ms.locfileid: "93398558"
---
# <a name="accessing-azure-virtual-machines-from-server-explorer"></a>Tener acceso a Azure Virtual Machines desde el Explorador de servidores

Si tiene máquinas virtuales hospedadas por Azure, puede acceder a ellas en el Explorador de servidores. Primero debe iniciar una sesión en su suscripción de Azure para ver los servicios móviles. Para iniciar sesión, abra el menú contextual del nodo de Azure en el Explorador de servidores y elija **Conectar a Microsoft Azure**.

1. En Cloud Explorer, elija una máquina virtual y, a continuación, presione la tecla F4 para mostrar su ventana de propiedades.

    La siguiente tabla muestra las propiedades que están disponibles, pero son todas de solo lectura. Utilice el [Azure Portal](https://portal.azure.com) para cambiarlas.

   | Propiedad. | Descripción |
   | --- | --- |
   | Nombre DNS |La dirección URL con la dirección de Internet de la máquina virtual. |
   | Entorno |En el caso de una máquina virtual, el valor de esta propiedad siempre es Production. |
   | Nombre |El nombre de la máquina virtual. |
   | Size |El tamaño de la máquina virtual, que refleja la cantidad de memoria y espacio en disco disponibles. Para obtener más información, consulte [tamaños de máquina virtual](/azure/cloud-services/cloud-services-sizes-specs). |
   | Estado |Los valores incluyen: Iniciando, Iniciado, Deteniéndose, Detenido y Recuperando estado. Si aparece Recuperando estado, el estado actual es desconocido. Los valores para esta propiedad son distintos de los que se usan en [Azure Portal](https://portal.azure.com). |
   | SubscriptionID |El Id. de suscripción de la cuenta de Azure. Esta información se puede mostrar en [Azure Portal](https://portal.azure.com) mediante la visualización de las propiedades de una suscripción. |
2. Elija un nodo de extremo y, a continuación, vea la ventana **Propiedades**.
3. La tabla siguiente describe las propiedades disponibles de los extremos, pero son de solo lectura. Para agregar o editar los puntos de conexión de una máquina virtual, use [Azure Portal](https://portal.azure.com).

   | Propiedad. | Descripción |
   | --- | --- |
   | Nombre |Un identificador para el extremo. |
   | Private Port |El puerto del acceso de red interno de la aplicación. |
   | Protocolo |El protocolo que usa la capa de transporte para este extremo, TCP o UDP. |
   | Public Port |El puerto que se usa para el acceso público a la aplicación. |
