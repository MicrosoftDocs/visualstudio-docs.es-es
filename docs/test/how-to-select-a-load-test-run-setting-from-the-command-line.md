---
title: Establecimiento de parámetros de ejecución de pruebas de carga desde la línea de comandos
description: Una prueba de carga puede incluir parámetros de ejecución, que son propiedades que afectan a la manera en que se ejecuta una prueba de carga. Aprenda a cargar parámetros de ejecución desde la línea de comandos.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- load tests, command line
- load tests, run settings, selecting
ms.assetid: 175d1d58-f09a-4449-b132-a29a394a7c8e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 290f56ba0f0ca9c6a8f6a6a1ee4e30b86bcfacd7
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/23/2020
ms.locfileid: "95440966"
---
# <a name="how-to-select-a-load-test-run-setting-to-use-from-the-command-line"></a>Cómo: Seleccionar los parámetros de ejecución de una prueba de carga que se va a usar desde la línea de comandos

Una prueba de carga puede incluir *parámetros de ejecución*, que son propiedades que afectan a la manera en que se ejecuta una prueba de carga. Los parámetros de ejecución están organizados por categorías en la ventana **Propiedades**. Cuando se ejecuta una prueba de carga, utiliza el parámetro de ejecución que actualmente está definido como activo.

Si su prueba de carga contiene solo uno parámetro de ejecución, siempre es el nodo activo. Si la prueba de carga incluye varios nodos de parámetros de ejecución, puede seleccionar el que vaya a usar al ejecutar una prueba de carga desde la línea de comandos. Vea [Cómo: Agregar más parámetros de ejecución a una prueba de carga](../test/how-to-add-additional-run-settings-to-a-load-test.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-change-the-run-setting-from-the-command-line"></a>Para cambiar el parámetro de ejecución desde la línea de comandos

1. Si quiere usar distintos parámetros de ejecución desde la línea de comandos para aprovechar la estrategia de parámetros de contexto, use el siguiente comando:

    `Set Test.UseRunSetting= CorporateStagingWebServer`

2. Ejecute la prueba de carga usando mstest:

    `mstest /testcontainer:loadtest1.loadtest`

## <a name="see-also"></a>Vea también

- [Configurar los parámetros de ejecución de pruebas de carga](../test/configure-load-test-run-settings.md)
- [Especificar los conjuntos de contadores y las reglas de umbral para equipos en una prueba de carga](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)
- [Cómo: Agregar más parámetros de ejecución a una prueba de carga](../test/how-to-add-additional-run-settings-to-a-load-test.md)
- [Cómo: Seleccionar el parámetro de ejecución activo de una prueba de carga](../test/how-to-select-the-active-run-setting-for-a-load-test.md)
