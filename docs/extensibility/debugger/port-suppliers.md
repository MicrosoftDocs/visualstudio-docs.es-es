---
title: Proveedores de puertos | Microsoft Docs
description: En este artículo se describe la definición y el rol de un proveedor de puertos en la arquitectura del depurador Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- port suppliers
- debugging [Debugging SDK], port suppliers
ms.assetid: a8f3db96-1a13-4e93-9ef6-0861880369e0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 0526135f706a42c622617a069e501297570e3b49
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899126"
---
# <a name="port-suppliers"></a>Proveedores de puertos
En la arquitectura del depurador, un proveedor *de puertos*:

- Está contenido por un servidor y proporciona puertos a petición a ese servidor.

- Puede agregar y quitar puertos del servidor que lo contiene.

- Puede enumerar todos los puertos que ha proporcionado al servidor.

- Se representa mediante una [interfaz IDebugPortSupplier2,](../../extensibility/debugger/reference/idebugportsupplier2.md) que se registra con Visual Studio a través del Registro. Esta interfaz se puede obtener llamando a [GetPortSupplier.](../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)

  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] proporciona un proveedor de puertos predeterminado y un puerto predeterminado. Si es necesario implementar un puerto personalizado, también debe implementarse un proveedor de puertos personalizado para proporcionar esos puertos personalizados.

## <a name="see-also"></a>Consulta también
- [Servidores](../../extensibility/debugger/servers-visual-studio-sdk.md)
- [Puertos](../../extensibility/debugger/ports.md)
- [Conceptos del depurador](../../extensibility/debugger/debugger-concepts.md)
- [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)
- [GetPortSupplier](../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)
