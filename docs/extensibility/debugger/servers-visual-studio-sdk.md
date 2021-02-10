---
title: Servidores (SDK de Visual Studio) | Microsoft Docs
description: En este artículo se describe la definición y el rol de un servidor en la arquitectura del depurador de Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- servers, debugging
- debugging [Debugging SDK], servers
ms.assetid: 62236d64-7956-448c-9ac3-5528f3edac1d
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d60c214fce57f5958d8b30ca231c3e8a2bc05194
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99960811"
---
# <a name="servers-visual-studio-sdk"></a>Servidores (Visual Studio SDK)
En la arquitectura del depurador, un *servidor*:

- Es un contenedor de puertos y proveedores de puertos y comunica puertos y proveedores de puertos con el administrador de depuración de sesión (SDM) y los motores de depuración.

- Puede identificarse por nombre y enumerar los puertos y los proveedores de puertos.

- Se representa mediante una interfaz [IDebugCoreServer2](../../extensibility/debugger/reference/idebugcoreserver2.md) , que solo implementa Visual Studio (una instancia de un servidor para cada instancia de Visual Studio en ejecución).

## <a name="see-also"></a>Vea también
- [Puertos](../../extensibility/debugger/ports.md)
- [Proveedores de puertos](../../extensibility/debugger/port-suppliers.md)
- [Conceptos del depurador](../../extensibility/debugger/debugger-concepts.md)
- [IDebugCoreServer2](../../extensibility/debugger/reference/idebugcoreserver2.md)
