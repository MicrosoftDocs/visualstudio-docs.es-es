---
title: Implementar un proveedor del puerto | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], implementing port suppliers
- port suppliers, implementing
ms.assetid: 6b8579df-58df-4c7f-8112-6015993e8765
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3bc985bf9fb55b67b5a332f007abe98c6718fbf2
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="implementing-a-port-supplier"></a>Implementar un proveedor de puerto
Un proveedor de puerto proporciona puertos de solicitud para el Administrador de sesión de depuración (SDM). Un proveedor de puerto debe implementarse al depurar en una máquina distinta DCOM o cuando es necesario un dispositivo nuevo que se deben admitir. Por ejemplo, para proporcionar la depuración en un teléfono móvil, podría implementar un proveedor de puerto que proporciona los puertos que se conectan al teléfono móvil (quizás por medio de infrarrojos o una conexión de la celda) y enumeran los procesos y los programas que se ejecutan en el teléfono.  
  
 Para la depuración de programas en equipos basados en Windows (incluida la depuración remota), Visual Studio proporciona proveedores de puertos para nativo y los procesos de Common Language Runtime (CLR), por lo que no es necesario para implementar su propio proveedor de puerto en esos casos.  
  
## <a name="in-this-section"></a>En esta sección  
 [Implementación y registro de un proveedor de puerto](../../extensibility/debugger/implementing-and-registering-a-port-supplier.md)  
 Describe cómo interactúa el SDM con el proveedor del puerto y sus puertos.  
  
 [Interfaces de proveedor de puerto requeridas](../../extensibility/debugger/required-port-supplier-interfaces.md)  
 Documenta las interfaces que deben implementar para obtener un proveedor del puerto.  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [Conceptos del depurador](../../extensibility/debugger/debugger-concepts.md)  
 Describe los principales conceptos de arquitectura de depuración.  
  
## <a name="see-also"></a>Vea también  
 [Extensibilidad del depurador de Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)