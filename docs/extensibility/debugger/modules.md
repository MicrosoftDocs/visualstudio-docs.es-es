---
title: Módulos | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- modules
- debugging [Debugging SDK], modules
ms.assetid: c4cf2809-dbdb-4e75-9273-b3d3d77b67d0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: abdf76c7f5f031d2ef7f3bcac2bae8a2c508b783
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738346"
---
# <a name="modules"></a>Módulos
En cuanto a la arquitectura del depurador, un *módulo*:

- Es un contenedor físico de código, como un archivo ejecutable o un archivo DLL.

- Puede volver a cargar sus símbolos y describirse a sí mismo. Las descripciones del módulo se muestran en la ventana módulos del IDE.

- Se representa mediante una interfaz [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md) , creada por un motor de depuración para describir el módulo.

## <a name="see-also"></a>Vea también
- [Conceptos del depurador](../../extensibility/debugger/debugger-concepts.md)
- [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md)
