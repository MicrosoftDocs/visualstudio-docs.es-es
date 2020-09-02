---
title: Implementación de un proveedor de Puerto | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], implementing port suppliers
- port suppliers, implementing
ms.assetid: 6b8579df-58df-4c7f-8112-6015993e8765
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ffa6daa20c08bd236657c88e762b2f453554cb74
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68152679"
---
# <a name="implementing-a-port-supplier"></a>Implementación de un proveedor de puertos
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Un proveedor de Puerto proporciona puertos a petición para el administrador de depuración de la sesión (SDM). Un proveedor de puerto debe implementarse al depurar en una máquina que no sea DCOM o cuando sea necesario admitir un nuevo dispositivo. Por ejemplo, para proporcionar depuración a un teléfono móvil, puede implementar un proveedor de puerto que proporcione puertos que se conecten al teléfono móvil (quizás por medio de IR o una conexión de celda) y enumere los procesos y programas que se ejecutan en el teléfono.  
  
 Para depurar programas en equipos basados en Windows (incluida la depuración remota), Visual Studio proporciona proveedores de puertos para los procesos de Common Language Runtime (CLR), por lo que no hay necesidad de implementar su propio proveedor de puertos en esos casos.  
  
## <a name="in-this-section"></a>En esta sección  
 [Implementación y registro de un proveedor de puerto](../../extensibility/debugger/implementing-and-registering-a-port-supplier.md)  
 Describe cómo interactúa el SDM con el proveedor del puerto y sus puertos.  
  
 [Interfaces de proveedor de puerto requeridas](../../extensibility/debugger/required-port-supplier-interfaces.md)  
 Documenta las interfaces que se deben implementar para obtener un proveedor de puerto.  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [Conceptos del depurador](../../extensibility/debugger/debugger-concepts.md)  
 Describe los conceptos principales de la arquitectura de depuración.  
  
## <a name="see-also"></a>Consulte también  
 [Extensibilidad del depurador de Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
