---
title: Configurar reglas de rendimiento | Microsoft Docs
description: Preste atención a las advertencias de las Herramientas de generación de perfiles de Visual Studio para así usar los mejores métodos de recopilación. Las encontrará en la ventana Lista de errores.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.performance.ruleseditor
ms.assetid: a148b468-b849-4858-880a-808a6b47e596
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 788cc8d8a0988740ae78e5b2b21368eb5658ec7a
ms.sourcegitcommit: 589d96700208bf22c8da9e26a1d2041fbf39b8f9
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/26/2021
ms.locfileid: "98800334"
---
# <a name="how-to-configure-performance-rules"></a>Procedimiento Configurar reglas de rendimiento
Las advertencias de rendimiento de las Herramientas de generación de perfiles de Visual Studio indican problemas en una aplicación para la que se han generado perfiles; dichos problemas pueden ralentizar la ejecución de programas. Las advertencias también pueden indicar que puede ser necesario cambiar los métodos de recolección para recopilar datos más útiles. Las advertencias de rendimiento se generan automáticamente en una sesión de generación de perfiles y aparecen en la ventana **Lista de errores** cuando se abre un archivo de datos de generación de perfiles en [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]. Es posible que determinadas advertencias no se apliquen en los escenarios que le interesan y que otras se produzcan de manera inexacta. Puede configurar las advertencias de rendimiento para mostrar u ocultar advertencias concretas.

### <a name="to-configure-profiler-performance-warnings"></a>Para configurar las advertencias de rendimiento del generador de perfiles

1. En el menú **Herramientas** , haga clic en **Opciones**.

2. Expanda **Herramientas de rendimiento** y después haga clic en **Reglas**.

3. Para habilitar o deshabilitar una advertencia, marque o desmarque la casilla situada junto al **Id.** y el nombre de la advertencia.

4. Para especificar el nivel de advertencia de una regla, haga clic en la celda **Acción** situada junto a la regla y después en el nivel de advertencia.

    - **Deshabilitado**: deshabilita la regla (es igual que desmarcar la casilla situada junto al identificador de la regla).

    - **Advertencia**: la regla se muestra como una advertencia.

    - **Error**: detiene la ejecución de la generación de perfiles y muestra la regla como un error.

    - **Información**: la regla se muestra solo como información.
