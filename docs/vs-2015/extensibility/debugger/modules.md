---
title: Módulos | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- modules
- debugging [Debugging SDK], modules
ms.assetid: c4cf2809-dbdb-4e75-9273-b3d3d77b67d0
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 802a40c248df243adf1319c522278ad94d69eeed
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58988704"
---
# <a name="modules"></a>Módulos
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

En cuanto a la arquitectura de depurador, un **módulo**:  
  
-   Es un contenedor físico de código, como un archivo ejecutable o DLL.  
  
-   Puede volver a cargar sus símbolos y describirse a sí mismos. Descripciones del módulo se muestran en la ventana módulos del IDE.  
  
-   Se representa mediante un [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md) interfaz, creado por un motor de depuración para describir el módulo.  
  
## <a name="see-also"></a>Vea también  
 [Conceptos del depurador](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md)
