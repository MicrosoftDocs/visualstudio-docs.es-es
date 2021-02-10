---
title: Novedades de la creación de perfil de Visual Studio 2017 | Microsoft Docs
description: Obtenga información sobre cómo las herramientas de diagnóstico incluyen nuevas visualizaciones para ayudarle a identificar problemas que se deben corregir en la aplicación.
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- profiling
- what's new
ms.assetid: d4736cc8-8961-4089-be9e-d5190ce8353c
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
monikerRange: vs-2017
ms.openlocfilehash: 9619daea30960f72b183447839db89adbaee7eb2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99938491"
---
# <a name="whats-new-in-profiling-tools-in-includevs_dev15"></a>Novedades de las herramientas de generación de perfiles en [!include[vs_dev15](../misc/includes/vs_dev15_md.md)]

Las herramientas de diagnóstico incluyen nuevas visualizaciones para ayudarle a identificar problemas en la aplicación que se deben corregir. Las herramientas de diagnóstico ahora incluyen compatibilidad para aplicaciones de ASP.NET.

Para obtener más información, vea las [Notas de la versión para [!include[vs_dev15](../misc/includes/vs_dev15_md.md)]](/visualstudio/releasenotes/vs2017-relnotes).

Se ha agregado una pestaña **Resumen** a las herramientas que le ayudan a centrarse en áreas clave para el análisis de rendimiento. Esta pestaña muestra cuántos eventos se han producido, le permite tomar instantáneas del montón y le permite habilitar rápidamente la recopilación de datos de uso de CPU. Esta vista muestra los eventos de [Application Insights](/azure/azure-monitor/app/visual-studio) o de [Análisis de UI](/visualstudio/releasenotes/vs2017-relnotes). Además, para Visual Studio Enterprise, esta vista también muestra los eventos de IntelliTrace.

![Pestaña de resumen de Herramientas de diagnóstico](../profiling/media/diag-tools-summary-tab-2.png "DiagToolsSummaryTab")

La herramienta de uso de CPU tiene [nuevas visualizaciones](../profiling/Beginners-Guide-to-Performance-Profiling.md) para ayudarle a identificar las funciones que tienen más probabilidades de estar causando problemas de rendimiento. La nueva vista **Llamador y destinatario** que le permite investigar costos de las llamadas de funciones realizadas a y desde una función seleccionada.

![Vista Llamador y destinatario de Herramientas de diagnóstico](../profiling/media/diag-tools-caller-callee-2.png "DiagToolsCallerCallee")

## <a name="see-also"></a>Consulte también

- [Generación de perfiles en Visual Studio](../profiling/index.yml)
- [Primer vistazo a la generación de perfiles](../profiling/profiling-feature-tour.md)