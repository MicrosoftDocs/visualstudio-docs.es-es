---
title: Mejorar el rendimiento si Visual Studio es lento
titleSuffix: ''
ms.date: 04/11/2018
ms.topic: conceptual
helpviewer_keywords:
- performance [Visual Studio]
author: gewarren
ms.author: gewarren
manager: douge
f1_keywords:
- vs.performancecenter
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: f5fe9324360a01700024e14e6c70755d61aa3e60
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/07/2018
ms.locfileid: "53065780"
---
# <a name="optimize-visual-studio-performance"></a>Optimización del rendimiento de Visual Studio

Este artículo proporciona algunas sugerencias que se pueden probar en el caso de que Visual Studio se ejecute lentamente. También puede echar un vistazo a [Sugerencias y trucos de rendimiento de Visual Studio](../ide/visual-studio-performance-tips-and-tricks.md) para obtener más sugerencias para mejorar el rendimiento.

## <a name="upgrade-to-visual-studio-2017-version-156-or-later"></a>Actualización a Visual Studio 2017, versión 15.6 o posterior

Si actualmente usa Visual Studio 2015, descargue [Visual Studio 2017](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) de forma gratuita para comprobar su mejora del rendimiento. Las soluciones se cargan dos o tres veces más rápido en Visual Studio 2017, con mejoras de rendimiento también en otras áreas. Visual Studio 2017 es compatible en paralelo con Visual Studio 2015, por lo que no pierde nada por probarlo.

Si ya usa Visual Studio 2017, asegúrese de que está ejecutando la versión 15.6 o una posterior. Los datos demuestran que las soluciones se cargan dos o tres veces más rápido en la versión 15.6. Descárguela [aquí](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017).

## <a name="extensions-and-tool-windows"></a>Extensiones y ventanas de herramientas

Puede que tenga instaladas extensiones que ralenticen Visual Studio. Para obtener ayuda para administrar las extensiones a fin de mejorar el rendimiento, vea [Cambiar la configuración de extensión para mejorar el inicio, la carga de solución y el rendimiento de la escritura](../ide/optimize-visual-studio-startup-time.md#extensions).

Del mismo modo, puede que tenga instaladas ventanas de herramientas que ralenticen Visual Studio. Para obtener ayuda para administrar las ventanas de herramientas, vea [Cambiar la configuración de la ventana de herramientas para mejorar el tiempo de inicio](../ide/optimize-visual-studio-startup-time.md#tool-windows).

## <a name="hardware"></a>Hardware

Si está pensando en actualizar el hardware, una unidad de estado sólido (SSD) tiene más impacto en el rendimiento que algo más de RAM o una CPU más rápida.

Si agrega una SSD, para conseguir un rendimiento óptimo, instale Windows en esa unidad en lugar de en una unidad de disco duro (HDD). No parece que la ubicación de la unidad de las soluciones de Visual Studio tenga tanta importancia.

Además, no ejecute la solución desde una unidad USB. Cópiela en la unidad de disco duro o la SSD.

## <a name="help-us-improve"></a>Ayúdenos a mejorar

Sus comentarios nos ayudan a mejorar. Use la característica **Notificar un problema** para "registrar" un seguimiento y enviárnoslo. Seleccione el icono de comentarios situado junto a **Inicio rápido** o seleccione **Ayuda** > **Enviar comentarios** > **Notificar un problema** en la barra de menús. Para obtener más información, vea [Cómo notificar un problema con Visual Studio 2017](../ide/how-to-report-a-problem-with-visual-studio-2017.md).

## <a name="see-also"></a>Vea también

- [Sugerencias y trucos de rendimiento](../ide/visual-studio-performance-tips-and-tricks.md)
- [Visual Studio blog - Load solutions faster with Visual Studio 2017 version 15.6](https://blogs.msdn.microsoft.com/visualstudio/2018/04/04/load-solutions-faster-with-visual-studio-2017-version-15-6/) (Blog de Visual Studio: Cargar soluciones más rápido con Visual Studio 2017 versión 15.6)