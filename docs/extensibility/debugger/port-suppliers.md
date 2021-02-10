---
title: Proveedores de puertos | Microsoft Docs
description: En este artículo se describe la definición y el rol de un proveedor de puerto en la arquitectura del depurador de Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- port suppliers
- debugging [Debugging SDK], port suppliers
ms.assetid: a8f3db96-1a13-4e93-9ef6-0861880369e0
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b543770e5fcc920b05e5d19a15e312174ddad3dd
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99934395"
---
# <a name="port-suppliers"></a>Proveedores de puertos
En la arquitectura del depurador, un *proveedor de Puerto*:

- Está contenido en un servidor y proporciona puertos a petición para ese servidor.

- Puede Agregar y quitar puertos del servidor que lo contiene.

- Puede enumerar todos los puertos proporcionados al servidor.

- Se representa mediante una interfaz [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md) , que se registra con Visual Studio a través del registro. Esta interfaz se puede obtener llamando a [GetPortSupplier](../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md).

  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] proporciona un proveedor de puerto predeterminado y un puerto predeterminado. Si es necesario implementar un puerto personalizado, también debe implementarse un proveedor de Puerto personalizado para proporcionar esos puertos personalizados.

## <a name="see-also"></a>Vea también
- [Servidores](../../extensibility/debugger/servers-visual-studio-sdk.md)
- [Puertos](../../extensibility/debugger/ports.md)
- [Conceptos del depurador](../../extensibility/debugger/debugger-concepts.md)
- [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)
- [GetPortSupplier](../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)
