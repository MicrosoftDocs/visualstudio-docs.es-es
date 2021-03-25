---
title: Implementación de un proveedor de Puerto | Microsoft Docs
description: Obtenga información acerca de la implementación de un proveedor de puerto, que es necesario para la depuración en una máquina que no es DCOM o cuando un nuevo dispositivo requiere soporte técnico.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], implementing port suppliers
- port suppliers, implementing
ms.assetid: 6b8579df-58df-4c7f-8112-6015993e8765
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 98cc83ac9640241f0f97dc6e4adaacf8f90599b7
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105059917"
---
# <a name="implement-a-port-supplier"></a>Implementación de un proveedor de Puerto
Un proveedor de Puerto proporciona puertos a petición para el administrador de depuración de la sesión (SDM). Se debe implementar un proveedor de puerto durante la depuración en una máquina que no sea DCOM o cuando un nuevo dispositivo requiera compatibilidad. Por ejemplo, para proporcionar depuración a un teléfono móvil, puede configurar un proveedor de puerto que proporcione puertos que se conecten al teléfono móvil (quizás mediante una conexión de INFRARROJOs o de celda) y enumere los procesos y programas que se ejecutan en el teléfono.

 Para depurar programas en equipos basados en Windows (incluida la depuración remota), Visual Studio proporciona proveedores de puertos para los procesos de Common Language Runtime (CLR), por lo que no es necesario configurar su propio proveedor de puertos en esos casos.

## <a name="in-this-section"></a>En esta sección
 [Implementar y registrar un proveedor de Puerto](../../extensibility/debugger/implementing-and-registering-a-port-supplier.md) Describe cómo interactúa el SDM con el proveedor del puerto y sus puertos.

 [Interfaces de proveedor de Puerto requeridas](../../extensibility/debugger/required-port-supplier-interfaces.md) Documenta las interfaces que debe implementar para obtener un proveedor de puerto.

## <a name="related-sections"></a>Secciones relacionadas
 [Conceptos del depurador](../../extensibility/debugger/debugger-concepts.md) Se describen los principales conceptos de la arquitectura de depuración.

## <a name="see-also"></a>Consulte también
 [Extensibilidad del depurador de Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
