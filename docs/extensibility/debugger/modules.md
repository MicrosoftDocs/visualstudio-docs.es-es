---
title: Módulos | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- modules
- debugging [Debugging SDK], modules
ms.assetid: c4cf2809-dbdb-4e75-9273-b3d3d77b67d0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8750c1f6676966be8564fbf4a175a66fa180a401
ms.sourcegitcommit: 25a62c2db771f938e3baa658df8b1ae54a960e4f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2018
ms.locfileid: "39233170"
---
# <a name="modules"></a>Módulos
En cuanto a la arquitectura de depurador, un *módulo*:  
  
-   Es un contenedor físico de código, como un archivo ejecutable o DLL.  
  
-   Puede volver a cargar sus símbolos y describirse a sí mismos. Descripciones del módulo se muestran en la ventana módulos del IDE.  
  
-   Se representa mediante un [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md) interfaz, creado por un motor de depuración para describir el módulo.  
  
## <a name="see-also"></a>Vea también  
 [Conceptos del depurador](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md)