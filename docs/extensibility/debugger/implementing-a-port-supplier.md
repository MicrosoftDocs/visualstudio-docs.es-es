---
title: Implementar un proveedor del puerto | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], implementing port suppliers
- port suppliers, implementing
ms.assetid: 6b8579df-58df-4c7f-8112-6015993e8765
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b0743f307dc579f6197880b0b89acaf2db0dda08
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31098997"
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