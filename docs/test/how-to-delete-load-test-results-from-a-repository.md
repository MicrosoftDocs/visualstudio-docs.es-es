---
title: 'Cómo: Eliminar los resultados de pruebas de carga de un repositorio en Visual Studio'
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- results, load test
- load tests, deleting results
- load test results, removing
- Load Test Results Repository
- load tests, removing results
- load test results, deleting
ms.assetid: c2afe36b-d061-4f0e-9580-c18569ec08f9
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: da6f56175cc1292762107566ab1ebba81c140581
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
ms.locfileid: "31972024"
---
# <a name="how-to-delete-load-test-results-from-a-repository"></a>Cómo: Eliminar los resultados de pruebas de carga de un repositorio

Cuando se ejecutan pruebas de carga, cualquier información recolectada durante una ejecución se almacena en el repositorio de resultados de pruebas de carga. El repositorio de resultados de pruebas de carga contiene datos de los contadores de rendimiento e información acerca de los errores que se hayan producido. Para obtener más información, vea [Administrar los resultados de pruebas de carga en el repositorio de resultados de pruebas de carga](../test/manage-load-test-results-in-the-load-test-results-repository.md).

 Puede administrar los resultados de pruebas de carga desde el Editor de pruebas de carga con el cuadro de diálogo **Abrir y administrar resultados de pruebas de carga**. Puede abrir, importar, exportar y quitar los resultados de pruebas de carga.

## <a name="to-delete-results-from-a-repository"></a>Para eliminar resultados de un repositorio

1.  En un proyecto de prueba de carga y rendimiento web, abra una prueba de carga.

2.  En la barra de herramientas insertada, elija **Abrir y administrar resultados**.

     Se muestra el cuadro de diálogo **Abrir y administrar resultados de pruebas de carga**.

3.  En **Escriba un nombre de controlador para buscar resultados de pruebas de carga**, seleccione un controlador. Seleccione **\<Local - Sin controlador>** para acceder a los resultados almacenados en local.

4.  En **Mostrar resultados para la siguiente prueba de carga**, seleccione la prueba de carga cuyos resultados quiere ver. Seleccione **\<Mostrar resultados de todas las pruebas>** para ver todos los resultados de todas las pruebas.

     Si hay resultados de pruebas de carga disponibles, aparecen en la lista **Resultados de pruebas de carga**. Las columnas son **Hora**, **Duración**, **Usuario**, **Resultado**, **Prueba** y **Descripción**. **Prueba** contiene el nombre de la prueba y **Descripción** incluye la descripción opcional que se ha agregado antes de ejecutar la prueba. La columna **Descripción** muestra las descripciones breves que se han escrito en los **Comentarios de análisis** de este resultado de prueba.

5.  En la lista **Resultados de pruebas de carga**, elija un resultado. Puede utilizar las teclas Mayús, Ctrl, o ambas, para seleccionar más de un resultado.

6.  Elija **Quitar**.

     Los resultados se quitan del repositorio.

    > [!NOTE]
    > El cuadro de diálogo **Abrir y administrar resultados de pruebas de carga** permanece abierto después de quitar los resultados.

## <a name="see-also"></a>Vea también

- [Cómo: Exportar los resultados de pruebas de carga de un repositorio](../test/how-to-export-load-test-results-from-a-repository.md)
- [Administrar los resultados de pruebas de carga en el repositorio de resultados pruebas de carga](../test/manage-load-test-results-in-the-load-test-results-repository.md)
- [Analizar resultados de pruebas de carga](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Cómo: Importar los resultados de pruebas de carga a un repositorio](../test/how-to-import-load-test-results-into-a-repository.md)