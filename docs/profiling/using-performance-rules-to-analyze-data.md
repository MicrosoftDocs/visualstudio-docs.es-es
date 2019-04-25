---
title: Usar reglas de rendimiento para analizar datos | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 1deed23e-b31b-4714-982f-08ceebfc3096
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e0e69de397f9c8f4160d81047f086a6db60741e8
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/21/2019
ms.locfileid: "56641655"
---
# <a name="use-performance-rules-to-analyze-data"></a>Usar reglas de rendimiento para el análisis de datos
Las advertencias de rendimiento de las herramientas de generación de perfiles de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] indican problemas en una aplicación para la que se han generado perfiles que pueden ralentizar la ejecución de programas. Las advertencias también pueden indicar que puede ser necesario cambiar los métodos de recolección para recopilar datos más útiles. Las advertencias de rendimiento se generan automáticamente en una sesión de generación de perfiles. Las advertencias aparecen en la ventana **Lista de errores** cuando un archivo de datos de generación de perfiles se abre en Visual Studio. En la ventana **Lista de errores**, puede buscar el código fuente del problema y puede mostrar información detallada sobre el error, como información sobre la forma de resolver el problema. También puede deshabilitar advertencias en las que no está interesado.

> [!NOTE]
>  Las advertencias de rendimiento del generador de perfiles son generadas por el análisis dinámico de ejecución de programas y son independientes de las advertencias del análisis de código. El análisis de código también puede generar advertencias de rendimiento para código administrado en función del análisis estático del código fuente. Para obtener más información, vea [Analizar la calidad del código administrado](/visualstudio/code-quality/code-analysis-for-managed-code-overview) y [Advertencias de rendimiento](../code-quality/performance-warnings.md).

## <a name="in-this-section"></a>En esta sección
- [Cómo: Ver advertencias de rendimiento](../profiling/how-to-view-performance-warnings.md)

 Proporciona información sobre cómo abrir la ventana **Lista de errores** para ver las advertencias de rendimiento del generador de perfiles.

- [Cómo: Configurar las reglas de rendimiento](../profiling/how-to-configure-performance-rules.md)

 Proporciona información sobre cómo activar o desactivar las advertencias de rendimiento individuales.

- [Referencia de reglas de rendimiento](../profiling/performance-rules-reference.md)

 Proporciona información detallada sobre las advertencias de rendimiento del generador de perfiles.