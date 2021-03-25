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
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f40cb7d0c65822fcb6ba4d4ca0132147f62d9286
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105054769"
---
# <a name="modules"></a>Módulos
En cuanto a la arquitectura del depurador, un *módulo*:

- Es un contenedor físico de código, como un archivo ejecutable o un archivo DLL.

- Puede volver a cargar sus símbolos y describirse a sí mismo. Las descripciones del módulo se muestran en la ventana módulos del IDE.

- Se representa mediante una interfaz [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md) , creada por un motor de depuración para describir el módulo.

## <a name="see-also"></a>Consulte también
- [Conceptos del depurador](../../extensibility/debugger/debugger-concepts.md)
- [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md)
