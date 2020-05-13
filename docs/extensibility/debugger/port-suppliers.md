---
title: Proveedores de puertos ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- port suppliers
- debugging [Debugging SDK], port suppliers
ms.assetid: a8f3db96-1a13-4e93-9ef6-0861880369e0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6313a7afce9ed272177a26d8da1a9d1516c8022e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738299"
---
# <a name="port-suppliers"></a>Proveedores portuarios
En la arquitectura del depurador, un proveedor de *puertos:*

- Está contenido por un servidor y proporciona puertos a petición a ese servidor.

- Puede agregar y quitar puertos del servidor contenedor.

- Puede enumerar todos los puertos que ha proporcionado al servidor.

- Se representa mediante un [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md) interfaz, que se registra con Visual Studio a través del registro. Esta interfaz se puede obtener llamando a [GetPortSupplier](../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md).

  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]proporciona un proveedor de puertopredeterminado y un puerto predeterminado. Si es necesario implementar un puerto personalizado, también es necesario implementar un proveedor de puertos personalizado para proporcionar esos puertos personalizados.

## <a name="see-also"></a>Vea también
- [Servidores](../../extensibility/debugger/servers-visual-studio-sdk.md)
- [Puertos](../../extensibility/debugger/ports.md)
- [Conceptos del depurador](../../extensibility/debugger/debugger-concepts.md)
- [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)
- [GetPortSupplier](../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)
