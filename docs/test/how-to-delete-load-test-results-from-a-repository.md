---
title: Procedimiento para eliminar los resultados de pruebas de carga de un repositorio
description: Aprenda a quitar información del repositorio Resultados de la prueba de carga mediante el cuadro de diálogo Abrir y administrar resultados de prueba de carga.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- results, load test
- load tests, deleting results
- load test results, removing
- Load Test Results Repository
- load tests, removing results
- load test results, deleting
ms.assetid: c2afe36b-d061-4f0e-9580-c18569ec08f9
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: 4976d8487b66d06384321874d56b82084ab42dd5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99961539"
---
# <a name="how-to-delete-load-test-results-from-a-repository"></a>Procedimiento para eliminar los resultados de pruebas de carga de un repositorio

Cuando se ejecutan pruebas de carga, cualquier información recolectada durante una ejecución se almacena en el repositorio de resultados de pruebas de carga. El repositorio de resultados de pruebas de carga contiene datos de los contadores de rendimiento e información acerca de los errores que se hayan producido. Para obtener más información, vea [Administrar resultados de pruebas de carga en el repositorio de resultados de pruebas de carga](../test/manage-load-test-results-in-the-load-test-results-repository.md).

Puede administrar los resultados de pruebas de carga desde el Editor de pruebas de carga con el cuadro de diálogo **Abrir y administrar resultados de pruebas de carga**. Puede abrir, importar, exportar y quitar los resultados de pruebas de carga.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-delete-results-from-a-repository"></a>Para eliminar resultados de un repositorio

1. En un proyecto de prueba de carga y rendimiento web, abra una prueba de carga.

2. En la barra de herramientas insertada, elija **Abrir y administrar resultados**.

     Se muestra el cuadro de diálogo **Abrir y administrar resultados de pruebas de carga**.

3. En **Escriba un nombre de controlador para buscar resultados de pruebas de carga**, seleccione un controlador. Seleccione **\<Local - No controller>** para tener acceso a los resultados almacenados localmente.

4. En **Mostrar resultados para la siguiente prueba de carga**, seleccione la prueba de carga cuyos resultados quiere ver. Seleccione **\<Show results for all tests>** para ver todos los resultados de todas las pruebas.

     Si hay resultados de pruebas de carga disponibles, aparecen en la lista **Resultados de pruebas de carga**. Las columnas son **Hora**, **Duración**, **Usuario**, **Resultado**, **Prueba** y **Descripción**. **Prueba** contiene el nombre de la prueba y **Descripción** incluye la descripción opcional que se ha agregado antes de ejecutar la prueba. La columna **Descripción** muestra las descripciones breves que se han escrito en los **Comentarios de análisis** de este resultado de prueba.

5. En la lista **Resultados de pruebas de carga**, elija un resultado. Puede usar las teclas **Mayús**, **Ctrl** o ambas para seleccionar más de un resultado.

6. Elija **Quitar**.

     Los resultados se quitan del repositorio.

    > [!NOTE]
    > El cuadro de diálogo **Abrir y administrar resultados de pruebas de carga** permanece abierto después de quitar los resultados.

## <a name="see-also"></a>Vea también

- [Cómo: Exportar resultados de pruebas de carga desde un repositorio](../test/how-to-export-load-test-results-from-a-repository.md)
- [Administrar resultados de pruebas de carga en el repositorio de resultados de pruebas de carga](../test/manage-load-test-results-in-the-load-test-results-repository.md)
- [Analizar los resultados de pruebas de carga](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Cómo: Importar los resultados de pruebas de carga en un repositorio](../test/how-to-import-load-test-results-into-a-repository.md)
