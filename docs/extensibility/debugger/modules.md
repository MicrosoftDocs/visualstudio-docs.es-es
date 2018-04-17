---
title: Módulos | Documentos de Microsoft
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
ms.openlocfilehash: f587e015263336436588d14edeeb5c6935872950
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="modules"></a>Módulos
En cuanto a la arquitectura del depurador, una **módulo**:  
  
-   Es un contenedor físico del código, como un archivo ejecutable o un archivo DLL.  
  
-   Puede volver a cargar sus símbolos y autodescriptivos. Descripciones del módulo se muestran en la ventana módulos del IDE.  
  
-   Se representa mediante un [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md) interfaz, creada por un motor de depuración para describir el módulo.  
  
## <a name="see-also"></a>Vea también  
 [Conceptos del depurador](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md)