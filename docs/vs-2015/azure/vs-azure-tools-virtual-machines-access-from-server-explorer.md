---
title: Obtener acceso a máquinas virtuales de Azure desde el Explorador de servidores | Microsoft Docs
description: Obtenga una visión general de cómo ver, crear y administrar máquinas virtuales (VM) en el Explorador de servidores en Visual Studio.
author: ghogen
manager: douge
assetId: eb3afde6-ba90-4308-9ac1-3cc29da4ede0
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 8/31/2017
ms.author: ghogen
ms.openlocfilehash: e1410b3dc60ec9689b6582e794aaf10cd13092aa
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/05/2018
ms.locfileid: "51002355"
---
# <a name="accessing-azure-virtual-machines-from-server-explorer"></a>Acceso a Azure Virtual Machines desde el Explorador de servidores

Si tiene máquinas virtuales hospedadas por Azure, puede tener acceso a ellos en el Explorador de servidores. Primero debe iniciar sesión su suscripción de Azure para ver los servicios móviles. Para iniciar sesión, abra el menú contextual del nodo de Azure en el Explorador de servidores y elija **conectar a Microsoft Azure**.

1. En Cloud Explorer, elija una máquina virtual y, a continuación, elija la tecla F4 para mostrar su ventana de propiedades.

    La siguiente tabla muestra qué propiedades están disponibles, pero son todas de solo lectura. Para cambiarlas, utilice el [portal Azure](http://go.microsoft.com/fwlink/p/?LinkID=525040).

   | Property | Descripción |
   | --- | --- |
   | Nombre DNS |La dirección URL con la dirección de Internet de la máquina virtual. |
   | Entorno |Para una máquina virtual, el valor de esta propiedad es siempre de producción. |
   | nombre |El nombre de la máquina virtual. |
   | Tamaño |El tamaño de la máquina virtual, que refleja la cantidad de memoria y espacio en disco que está disponible. Para obtener más información, consulte [tamaños de máquina Virtual](https://docs.microsoft.com/azure/cloud-services/cloud-services-sizes-specs). |
   | Estado |Los valores incluyen iniciando, iniciado, deteniéndose, detenido y recuperando estado. Si aparece recuperando estado, el estado actual es desconocido. Los valores para esta propiedad son distintos de los valores que se usan en el [portal Azure](http://go.microsoft.com/fwlink/p/?LinkID=525040). |
   | SubscriptionID |El identificador de suscripción para su cuenta de Azure. Esta información se puede mostrar en el [portal Azure](http://go.microsoft.com/fwlink/p/?LinkID=525040) viendo las propiedades de una suscripción. |
2. Elija un nodo de extremo y, a continuación, ver el **propiedades** ventana.
3. En la tabla siguiente se describe las propiedades disponibles de los puntos de conexión, pero son de solo lectura. Para agregar o editar los puntos de conexión para una máquina virtual, use el [portal Azure](http://go.microsoft.com/fwlink/p/?LinkID=525040). 

   | Property | Descripción |
   | --- | --- |
   | nombre |Un identificador para el punto de conexión. |
   | Puerto privado |El puerto de acceso a la red interna a la aplicación. |
   | Protocolo |El protocolo que usa la capa de transporte para este extremo, TCP o UDP. |
   | Puerto público |El puerto que se usa para el acceso público a la aplicación. |
