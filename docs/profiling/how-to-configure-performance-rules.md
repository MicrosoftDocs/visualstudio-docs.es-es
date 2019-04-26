---
title: Procedimiento Configurar reglas de rendimiento | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.ruleseditor
ms.assetid: a148b468-b849-4858-880a-808a6b47e596
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7387cc54e96aec4deea6a65875f693d704d51859
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62973973"
---
# <a name="how-to-configure-performance-rules"></a>Procedimiento Configurar reglas de rendimiento
Las advertencias de rendimiento de las Herramientas de generación de perfiles de Visual Studio indican problemas en una aplicación para la que se han generado perfiles que pueden ralentizar la ejecución de programas. Las advertencias también pueden indicar que puede ser necesario cambiar los métodos de recolección para recopilar datos más útiles. Las advertencias de rendimiento se generan automáticamente en una sesión de generación de perfiles y aparecen en la ventana **Lista de errores** cuando se abre un archivo de datos de generación de perfiles en [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]. Es posible que determinadas advertencias no se apliquen en los escenarios que le interesan y que otras se produzcan de manera inexacta. Puede configurar las advertencias de rendimiento para mostrar u ocultar advertencias concretas.

### <a name="to-configure-profiler-performance-warnings"></a>Para configurar las advertencias de rendimiento del generador de perfiles

1. En el menú **Herramientas** , haga clic en **Opciones**.

2. Expanda **Herramientas de rendimiento** y después haga clic en **Reglas**.

3. Para habilitar o deshabilitar una advertencia, marque o desmarque la casilla situada junto al **Id.** y el nombre de la advertencia.

4. Para especificar el nivel de advertencia de una regla, haga clic en la celda **Acción** situada junto a la regla y después en el nivel de advertencia.

    - **Deshabilitado**: deshabilita la regla (es igual que desmarcar la casilla situada junto al identificador de la regla).

    - **Advertencia**: la regla se muestra como una advertencia.

    - **Error**: detiene la ejecución de la generación de perfiles y muestra la regla como un error.

    - **Información**: la regla se muestra solo como información.