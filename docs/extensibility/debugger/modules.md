---
title: Módulos | Microsoft Docs
description: En este artículo se describe la definición y el rol de un módulo en la arquitectura del depurador de Visual Studio.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 57202231c1bbfc7712d322b8cc7a30e3f64c87af
ms.sourcegitcommit: 42981ace63c0f2b087de5703ca76b8dcdd93a719
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/04/2020
ms.locfileid: "96606650"
---
# <a name="modules"></a>Módulos
En cuanto a la arquitectura del depurador, un *módulo*:

- Es un contenedor físico de código, como un archivo ejecutable o un archivo DLL.

- Puede volver a cargar sus símbolos y describirse a sí mismo. Las descripciones del módulo se muestran en la ventana módulos del IDE.

- Se representa mediante una interfaz [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md) , creada por un motor de depuración para describir el módulo.

## <a name="see-also"></a>Consulte también
- [Conceptos del depurador](../../extensibility/debugger/debugger-concepts.md)
- [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md)
