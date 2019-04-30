---
title: Módulos | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- modules
- debugging [Debugging SDK], modules
ms.assetid: c4cf2809-dbdb-4e75-9273-b3d3d77b67d0
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 611d067030cd935f6957a976c8a3aa2b7d4f8ae3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62925407"
---
# <a name="modules"></a>Módulos
En cuanto a la arquitectura de depurador, un *módulo*:

- Es un contenedor físico de código, como un archivo ejecutable o DLL.

- Puede volver a cargar sus símbolos y describirse a sí mismos. Descripciones del módulo se muestran en la ventana módulos del IDE.

- Se representa mediante un [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md) interfaz, creado por un motor de depuración para describir el módulo.

## <a name="see-also"></a>Vea también
- [Conceptos del depurador](../../extensibility/debugger/debugger-concepts.md)
- [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md)