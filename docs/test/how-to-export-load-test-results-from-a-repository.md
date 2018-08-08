---
title: Exportación de los resultados de pruebas de carga en Visual Studio
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- results, load test
- load tests, exporting results
- Load Test Results Repository
- load test results, exporting
ms.assetid: 716c2af5-8737-4d31-956f-a0273f7c5c0c
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 9e9f3513cb5d7bb03f51be68d1b44b8df161a088
ms.sourcegitcommit: 495bba1d8029646653f99ad20df2f80faad8d58b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/31/2018
ms.locfileid: "39381509"
---
# <a name="how-to-export-load-test-results-from-a-repository"></a>Cómo: Exportar resultados de pruebas de carga de un repositorio

Cuando se ejecutan pruebas de carga, cualquier información recolectada durante una ejecución se almacena en el repositorio de resultados de pruebas de carga. El repositorio de resultados de pruebas de carga contiene datos de los contadores de rendimiento e información acerca de los errores que se hayan producido. Para obtener más información, vea [Administrar resultados de pruebas de carga en el repositorio de resultados de pruebas de carga](../test/manage-load-test-results-in-the-load-test-results-repository.md).

Puede administrar los resultados de pruebas de carga desde el Editor de pruebas de carga con el cuadro de diálogo **Abrir y administrar resultados de pruebas de carga**. Puede abrir, importar, exportar y quitar los resultados de pruebas de carga.

## <a name="to-export-results-from-a-repository"></a>Para exportar resultados de un repositorio

1.  En un proyecto de prueba de carga y rendimiento web, abra una prueba de carga.

2.  En la barra de herramientas insertada, elija **Abrir y administrar resultados**.

     Se muestra el cuadro de diálogo **Abrir y administrar resultados de pruebas de carga**.

3.  En **Escriba un nombre de controlador para buscar resultados de pruebas de carga**, seleccione un controlador. Seleccione **\<Local - Sin controlador>** para acceder a los resultados almacenados en local.

4.  En **Mostrar resultados para la siguiente prueba de carga**, seleccione la prueba de carga cuyos resultados quiere ver. Seleccione **\<Mostrar resultados de todas las pruebas>** para ver todos los resultados de todas las pruebas.

     Si hay resultados de pruebas de carga disponibles, aparecen en la lista **Resultados de pruebas de carga**. Las columnas son **Hora**, **Duración**, **Usuario**, **Resultado**, **Prueba** y **Descripción**. **Prueba** contiene el nombre de la prueba y **Descripción** incluye la descripción opcional que se ha agregado antes de ejecutar la prueba. La columna **Descripción** muestra las descripciones breves que se han escrito en los **Comentarios de análisis** de este resultado de prueba.

5.  En la lista **Resultados de pruebas de carga**, elija un resultado. Puede usar las teclas **Mayús**, **Ctrl** o ambas para seleccionar varios resultados y exportarlos a un único archivo.

6.  Elija **Exportar**.

     Aparecerá el cuadro de diálogo **Exportar resultados de la prueba de carga**.

7.  Escriba un nombre en el cuadro **Nombre de archivo** y, luego, elija **Guardar**.

     Los resultados se exportan a un archivo de almacenamiento.

    > [!NOTE]
    > El cuadro de diálogo **Abrir y administrar resultados de pruebas de carga** permanece abierto después de que aparezcan los resultados.

## <a name="see-also"></a>Vea también

- [Administrar resultados de pruebas de carga en el repositorio de resultados de pruebas de carga](../test/manage-load-test-results-in-the-load-test-results-repository.md)
- [Cómo: Eliminar resultados de pruebas de carga de un repositorio](../test/how-to-delete-load-test-results-from-a-repository.md)
- [Analizar los resultados de pruebas de carga](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Cómo: Importar resultados de pruebas de carga en un repositorio](../test/how-to-import-load-test-results-into-a-repository.md)