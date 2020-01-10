---
title: Mejorar el rendimiento si Visual Studio es lento
titleSuffix: ''
ms.date: 04/11/2018
ms.topic: conceptual
helpviewer_keywords:
- performance [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jillfra
f1_keywords:
- vs.performancecenter
ms.workload:
- multiple
ms.openlocfilehash: 6495e8506e12c0c5e5f878a23c609fe53a401bde
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/01/2020
ms.locfileid: "75597001"
---
# <a name="optimize-visual-studio-performance"></a>Optimización del rendimiento de Visual Studio

Este artículo proporciona algunas sugerencias que se pueden probar en el caso de que Visual Studio se ejecute lentamente. También puede echar un vistazo a [Sugerencias y trucos de rendimiento de Visual Studio](../ide/visual-studio-performance-tips-and-tricks.md) para obtener más sugerencias para mejorar el rendimiento.

## <a name="upgrade-visual-studio"></a>Actualizar Visual Studio

Si actualmente usa Visual Studio 2015, descargue [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) o [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) de forma gratuita para comprobar su mejora de rendimiento. Las soluciones se cargan dos o tres veces más rápido que en Visual Studio 2015, con mejoras de rendimiento también en otras áreas. Visual Studio 2017 y Visual Studio 2019 son compatibles en paralelo con Visual Studio 2015, por lo que no se pierde nada por probarlo.

::: moniker range="vs-2017"

Si ya usa Visual Studio 2017, asegúrese de que está ejecutando la versión 15.6 o posterior. Los datos demuestran que las soluciones se cargan dos o tres veces más rápido en la versión 15.6. Descárguela [aquí](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download).

::: moniker-end

## <a name="extensions-and-tool-windows"></a>Extensiones y ventanas de herramientas

Puede que tenga instaladas extensiones que ralenticen Visual Studio. Para obtener ayuda para administrar las extensiones a fin de mejorar el rendimiento, vea [Cambiar la configuración de extensión para mejorar el inicio, la carga de solución y el rendimiento de la escritura](../ide/optimize-visual-studio-startup-time.md#extensions).

Del mismo modo, puede que tenga instaladas ventanas de herramientas que ralenticen Visual Studio. Para obtener ayuda para administrar las ventanas de herramientas, vea [Cambiar la configuración de la ventana de herramientas para mejorar el tiempo de inicio](../ide/optimize-visual-studio-startup-time.md#tool-windows).

## <a name="hardware"></a>Hardware

Si está pensando en actualizar el hardware, una unidad de estado sólido (SSD) tiene más impacto en el rendimiento que algo más de RAM o una CPU más rápida.

Si agrega una SSD, para conseguir un rendimiento óptimo, instale Windows en esa unidad en lugar de en una unidad de disco duro (HDD). No parece que la ubicación de la unidad de las soluciones de Visual Studio tenga tanta importancia.

Además, no ejecute la solución desde una unidad USB. Cópiela en la unidad de disco duro o la SSD.

## <a name="help-us-improve"></a>Ayúdenos a mejorar

Sus comentarios nos ayudan a mejorar. Use la característica **Notificar un problema** para "registrar" un seguimiento y enviárnoslo. Seleccione el icono de comentarios situado junto a **Inicio rápido** o seleccione **Ayuda** > **Enviar comentarios** > **Notificar un problema** en la barra de menús. Para más información, vea [Cómo notificar un problema con Visual Studio](../ide/how-to-report-a-problem-with-visual-studio.md).

## <a name="see-also"></a>Vea también

- [Sugerencias y trucos de rendimiento](../ide/visual-studio-performance-tips-and-tricks.md)
- [Visual Studio blog - Load solutions faster with Visual Studio 2017 version 15.6](https://devblogs.microsoft.com/visualstudio/load-solutions-faster-with-visual-studio-2017-version-15-6/) (Blog de Visual Studio: Cargar soluciones más rápido con Visual Studio 2017 versión 15.6)
