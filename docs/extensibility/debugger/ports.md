---
title: Puertos | Microsoft Docs
description: En este artículo se describe la definición y el rol de un puerto en la arquitectura del depurador en Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- ports
- debugging [Debugging SDK], ports
ms.assetid: 1d7f3aa7-7eff-4cab-bc53-0a566b1a9363
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e53b2b804433f7e9450f34dac5b21e45710cd71c
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900777"
---
# <a name="ports"></a>Puertos
En la arquitectura del depurador, un *puerto*:

- Es un contenedor para un conjunto de procesos que se ejecutan en un servidor. Por ejemplo, un puerto podría representar una conexión a un dispositivo basado en Windows CE mediante un cable serie o a una máquina no DCOM en red. Un puerto especial, denominado puerto local, contiene todos los procesos que se ejecutan en el equipo local.

- Puede identificarse por nombre o identificador.

- Puede enumerar todos los procesos que se ejecutan en el puerto e iniciar y finalizar estos procesos.

- Se representa mediante una [interfaz IDebugPort2,](../../extensibility/debugger/reference/idebugport2.md) que se crea pasando un argumento [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) a [AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md).

  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] proporciona un puerto predeterminado que controla todos los procesos basados en Windows, tanto nativos como administrados. Se debe configurar un puerto personalizado para las conexiones con dispositivos externos que no están basados en Windows. Para proporcionar estos puertos personalizados, también debe configurar un proveedor de puertos personalizado.

## <a name="see-also"></a>Consulta también
- [Servidores](../../extensibility/debugger/servers-visual-studio-sdk.md)
- [Procesos](../../extensibility/debugger/processes.md)
- [Conceptos del depurador](../../extensibility/debugger/debugger-concepts.md)
- [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)
- [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md)
- [AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md)
