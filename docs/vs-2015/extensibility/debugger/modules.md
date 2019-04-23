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
ms.openlocfilehash: 7a2b2f04e1088b9b06cb05015a6b0b4da5d60927
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2019
ms.locfileid: "60076411"
---
# <a name="modules"></a>Módulos
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

En cuanto a la arquitectura de depurador, un **módulo**:  
  
- Es un contenedor físico de código, como un archivo ejecutable o DLL.  
  
- Puede volver a cargar sus símbolos y describirse a sí mismos. Descripciones del módulo se muestran en la ventana módulos del IDE.  
  
- Se representa mediante un [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md) interfaz, creado por un motor de depuración para describir el módulo.  
  
## <a name="see-also"></a>Vea también  
 [Conceptos del depurador](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md)
