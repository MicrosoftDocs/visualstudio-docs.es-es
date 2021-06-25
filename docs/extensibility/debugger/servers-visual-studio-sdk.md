---
title: Servidores (Visual Studio SDK) | Microsoft Docs
description: En este artículo se describe la definición y el rol de un servidor en la arquitectura del depurador en Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- servers, debugging
- debugging [Debugging SDK], servers
ms.assetid: 62236d64-7956-448c-9ac3-5528f3edac1d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 99f6c634053df9191ac419c8ee450dc99cf62c7c
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112902129"
---
# <a name="servers-visual-studio-sdk"></a>Servidores (Visual Studio SDK)
En la arquitectura del depurador, un *servidor*:

- Es un contenedor de puertos y proveedores de puertos y comunica los puertos y proveedores de puertos al administrador de depuración de sesión (SDM) y a los motores de depuración.

- Puede identificarse por nombre y enumerar sus puertos y proveedores de puertos.

- Se representa mediante una [interfaz IDebugCoreServer2,](../../extensibility/debugger/reference/idebugcoreserver2.md) que solo se implementa mediante Visual Studio (una instancia de un servidor para cada instancia de Visual Studio en ejecución).

## <a name="see-also"></a>Consulta también
- [Puertos](../../extensibility/debugger/ports.md)
- [Proveedores de puertos](../../extensibility/debugger/port-suppliers.md)
- [Conceptos del depurador](../../extensibility/debugger/debugger-concepts.md)
- [IDebugCoreServer2](../../extensibility/debugger/reference/idebugcoreserver2.md)
