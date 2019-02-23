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
ms.openlocfilehash: 1f31e3760a0697be8c9fc80eb811c99df79d32b1
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/22/2019
ms.locfileid: "56718916"
---
# <a name="modules"></a>Módulos
En cuanto a la arquitectura de depurador, un *módulo*:

-   Es un contenedor físico de código, como un archivo ejecutable o DLL.

-   Puede volver a cargar sus símbolos y describirse a sí mismos. Descripciones del módulo se muestran en la ventana módulos del IDE.

-   Se representa mediante un [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md) interfaz, creado por un motor de depuración para describir el módulo.

## <a name="see-also"></a>Vea también
- [Conceptos del depurador](../../extensibility/debugger/debugger-concepts.md)
- [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md)