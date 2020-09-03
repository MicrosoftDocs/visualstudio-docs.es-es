---
title: Puertos | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- ports
- debugging [Debugging SDK], ports
ms.assetid: 1d7f3aa7-7eff-4cab-bc53-0a566b1a9363
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7b42e7fa97c12afa07923e99d8b084840ee7ccad
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738308"
---
# <a name="ports"></a>Puertos
En la arquitectura del depurador, un *Puerto*:

- Es un contenedor para un conjunto de procesos que se ejecutan en un servidor. Por ejemplo, un puerto podría representar una conexión a un dispositivo basado en Windows CE mediante un cable serie o una máquina no DCOM en red. Un puerto especial, denominado puerto local, contiene todos los procesos que se ejecutan en el equipo local.

- Puede identificarse por nombre o identificador.

- Puede enumerar todos los procesos que se ejecutan en el puerto e iniciar y finalizar estos procesos.

- Se representa mediante una interfaz [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) , que se crea pasando un argumento [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) a [AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md).

  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] proporciona un puerto predeterminado que controla todos los procesos basados en Windows, tanto nativos como administrados. Se debe configurar un puerto personalizado para las conexiones con dispositivos externos que no estén basados en Windows. Para proporcionar estos puertos personalizados, también debe configurar un proveedor de Puerto personalizado.

## <a name="see-also"></a>Vea también
- [Servidores](../../extensibility/debugger/servers-visual-studio-sdk.md)
- [Procesos](../../extensibility/debugger/processes.md)
- [Conceptos del depurador](../../extensibility/debugger/debugger-concepts.md)
- [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)
- [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md)
- [AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md)
