---
title: Selección de un parámetro de ejecución para una prueba de carga
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, run settings, active
ms.assetid: ed6ff546-acfa-4dd8-b3a2-6e7455930ca4
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 12582aa4c1aa41aa0a38f652cf4841ba1f9953e1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62949950"
---
# <a name="how-to-select-the-active-run-setting-for-a-load-test"></a>Procedimiento para seleccionar el parámetro de ejecución activo de una prueba de carga

Después de crear la prueba de carga con el **Asistente para prueba de carga nueva**, puede usar el **Editor de pruebas de carga** para cambiar las propiedades de los escenarios de modo que satisfagan las necesidades y los objetivos de la prueba.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Una prueba de carga puede contener uno o más *parámetros de ejecución* que son un conjunto de propiedades que afectan a la manera en que se ejecuta una prueba de carga. Los parámetros de ejecución están organizados por categorías en la ventana **Propiedades**. Cuando se ejecuta una prueba de carga, utiliza el parámetro de ejecución que actualmente está definido como activo.

> [!NOTE]
> Para obtener una lista completa de los parámetros de ejecución y sus descripciones, vea [Propiedades de los parámetros de ejecución de las pruebas de carga](../test/load-test-run-settings-properties.md).

Si la prueba de carga solo incluye un nodo de parámetros de ejecución en la carpeta **Parámetros de ejecución**, ese nodo siempre será el nodo activo. Si la prueba de carga incluye varios nodos de parámetros de ejecución, puede seleccionar uno para que se utilice al ejecutar una prueba de carga. Vea [Cómo: Agregar más parámetros de ejecución a una prueba de carga](../test/how-to-add-additional-run-settings-to-a-load-test.md).

En el **Editor de pruebas de carga**, el parámetro de ejecución activo se identifica por el sufijo "[Active]".

## <a name="select-the-active-run-setting"></a>Seleccionar el parámetro de ejecución activo

1. Abra una prueba de carga.

2. Expanda la carpeta **Parámetros de ejecución**.

3. Haga clic con el botón derecho en el nodo de configuración de ejecución que desee activar y, a continuación, elija **Establecer como activa**.

     En el **Editor de pruebas de carga**, el nodo de parámetro de ejecución afectado se actualiza con el sufijo "[Active]".

     El parámetro de ejecución seleccionado se activará y permanecerá en ese estado hasta que se active otro parámetro de ejecución.

> [!NOTE]
> Puede reemplazar el parámetro de ejecución activo estableciendo una variable de entorno denominada `Test.UseRunSetting=<run setting name>`. Esto resulta muy útil cuando se ejecuta una prueba de carga desde la línea de comandos o desde un archivo por lotes. Esto le permite elegir diferentes parámetros de ejecución sin tener que abrir la prueba de carga.

## <a name="specify-the-run-setting-to-use-from-the-command-line"></a>Especificar el parámetro de ejecución que se va a usar desde la línea de comandos

Puede invalidar los parámetros de ejecución predeterminados en la prueba de carga estableciendo una variable de entorno de la línea de comandos:

**Establecer Test.UseRunSetting=PreProdEnvironment**

Y para ejecutar la prueba:

**mstest /testcontainer:loadtest1.loadtest**

## <a name="see-also"></a>Vea también

- [Configurar los parámetros de ejecución de pruebas de carga](../test/configure-load-test-run-settings.md)
- [Especificar los conjuntos de contadores y las reglas de umbral para equipos en una prueba de carga](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)
- [Cómo: Agregar más parámetros de ejecución a una prueba de carga](../test/how-to-add-additional-run-settings-to-a-load-test.md)