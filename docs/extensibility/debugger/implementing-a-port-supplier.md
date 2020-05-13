---
title: Implementación de un proveedor de puertos ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], implementing port suppliers
- port suppliers, implementing
ms.assetid: 6b8579df-58df-4c7f-8112-6015993e8765
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8218e372ad3aece922811bc20cfd7650f33296f3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738556"
---
# <a name="implement-a-port-supplier"></a>Implementar un proveedor portuario
Un proveedor de puertos suministra puertos a petición al administrador de depuración de sesión (SDM). Se debe implementar un proveedor de puertos al depurar en una máquina que no sea DCOM o cuando un nuevo dispositivo requiere soporte técnico. Por ejemplo, para proporcionar depuración a un teléfono celular, puede configurar un proveedor de puertos que proporcione puertos, que se conectan al teléfono celular (quizás mediante IR o una conexión de celda) y enumera los procesos y programas que se ejecutan en el teléfono.

 Para depurar programas en equipos basados en Windows (incluida la depuración remota), Visual Studio proporciona proveedores de puertos para procesos nativos y DeCommon Language Runtime (CLR), por lo que no es necesario configurar su propio proveedor de puertos en esos casos.

## <a name="in-this-section"></a>En esta sección
 [Implementar y registrar un proveedor portuario](../../extensibility/debugger/implementing-and-registering-a-port-supplier.md) Describe cómo el SDM interactúa con el proveedor de puertos y sus puertos.

 [Interfaces de proveedores de puertos requeridas](../../extensibility/debugger/required-port-supplier-interfaces.md) Documenta las interfaces que debe implementar para obtener un proveedor de puertos.

## <a name="related-sections"></a>Secciones relacionadas
 [Conceptos del depurador](../../extensibility/debugger/debugger-concepts.md) Describe los principales conceptos arquitectónicos de depuración.

## <a name="see-also"></a>Vea también
 [Extensibilidad del depurador de Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
