---
title: Implementar un proveedor de puerto | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], implementing port suppliers
- port suppliers, implementing
ms.assetid: 6b8579df-58df-4c7f-8112-6015993e8765
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0596809ceccd3d528e3276f2ed310a4835c836eb
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51738757"
---
# <a name="implementing-a-port-supplier"></a>Implementación de un proveedor de puertos
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Un proveedor de puerto proporciona puertos de solicitud para el Administrador de depuración de la sesión (SDM). Un proveedor de puerto debe implementarse al depurar en un equipo que no son de DCOM o cuando un nuevo dispositivo deba ser compatibles. Por ejemplo, para proporcionar la depuración en un teléfono móvil, podría implementar un proveedor de puerto que proporciona los puertos que se conectan al teléfono móvil (quizás por medio de infrarrojos o una conexión de la celda) y enumeran los procesos y los programas que se ejecutan en el teléfono.  
  
 Para la depuración de programas en equipos basados en Windows (incluida la depuración remota), Visual Studio proporciona proveedores de puertos nativos y los procesos de Common Language Runtime (CLR), por lo que no es necesario para implementar su propio proveedor de puerto en esos casos.  
  
## <a name="in-this-section"></a>En esta sección  
 [Implementación y registro de un proveedor de puerto](../../extensibility/debugger/implementing-and-registering-a-port-supplier.md)  
 Describe cómo interactúa el SDM con el proveedor del puerto y sus puertos.  
  
 [Interfaces de proveedor de puerto requeridas](../../extensibility/debugger/required-port-supplier-interfaces.md)  
 Documenta las interfaces que deben implementarse para obtener un proveedor de puerto.  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [Conceptos del depurador](../../extensibility/debugger/debugger-concepts.md)  
 Describe los principales conceptos de arquitectura de depuración.  
  
## <a name="see-also"></a>Vea también  
 [Extensibilidad del depurador de Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)

