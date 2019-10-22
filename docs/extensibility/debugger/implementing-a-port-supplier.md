---
title: Implementar un proveedor de puerto | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], implementing port suppliers
- port suppliers, implementing
ms.assetid: 6b8579df-58df-4c7f-8112-6015993e8765
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dd5ba2a96b94cce65dc901a523232b1c3e0a45b9
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66349984"
---
# <a name="implement-a-port-supplier"></a>Implementar un proveedor de puerto
Un proveedor de puerto proporciona puertos de solicitud para el Administrador de depuración de la sesión (SDM). Al depurar en un equipo que no son de DCOM o cuando un nuevo dispositivo requiere soporte técnico, se debe implementar un proveedor de puerto. Por ejemplo, para proporcionar la depuración en un teléfono móvil, puede configurar un proveedor de puerto que proporciona los puertos que se conexión al teléfono móvil (quizás por medio de infrarrojos o una conexión de la celda) y enumeran los procesos y los programas que se ejecutan en el teléfono.

 Para la depuración de programas en equipos basados en Windows (incluida la depuración remota), Visual Studio proporciona proveedores de puertos nativos y los procesos de Common Language Runtime (CLR), por lo que no es necesario para configurar su propio proveedor de puerto en esos casos.

## <a name="in-this-section"></a>En esta sección
 [Implementar y registrar un proveedor de puerto](../../extensibility/debugger/implementing-and-registering-a-port-supplier.md) describe cómo interactúa el SDM con el proveedor del puerto y sus puertos.

 [Interfaces de proveedor de puerto necesarias](../../extensibility/debugger/required-port-supplier-interfaces.md) documenta las interfaces que debe implementar para obtener un proveedor de puerto.

## <a name="related-sections"></a>Secciones relacionadas
 [Conceptos del depurador](../../extensibility/debugger/debugger-concepts.md) describe los principales conceptos de arquitectura de depuración.

## <a name="see-also"></a>Vea también
 [Extensibilidad del depurador de Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)