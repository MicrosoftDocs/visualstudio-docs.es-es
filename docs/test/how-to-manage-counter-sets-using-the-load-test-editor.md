---
title: Carga de conjuntos de contadores de pruebas en Visual Studio
ms.date: 10/19/2016
ms.topic: conceptual
f1_keywords:
- vs.test.load.dialog.countersetmapping
helpviewer_keywords:
- counters, counter sets
- performance counters
- counter sets
- load tests, counter sets
ms.assetid: 64315c2f-a0b2-4378-be16-0774b99beef5
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 022e105261c5d1e7f079a29915363ed02812d3bc
ms.sourcegitcommit: ae46be4a2b2b63da7e7049e9ed67cd80897c8102
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2018
ms.locfileid: "52894357"
---
# <a name="how-to-manage-counter-sets-using-the-load-test-editor"></a>Cómo: Administrar conjuntos de contadores mediante el Editor de pruebas de carga

Cuando se crea una prueba de carga con el **Asistente para prueba de carga nueva**, se agrega un conjunto de contadores inicial. Este conjunto inicial de contadores ofrece una serie de conjuntos de contadores predefinidos para la prueba de carga.

> [!NOTE]
> Si las pruebas de carga se distribuyen entre varios equipos remotos, los contadores de controlador y de agente se asignan automáticamente a los conjuntos de contadores de controlador y de agente. Para obtener más información sobre cómo usar máquinas remotas en la prueba de carga, vea [Controladores y agentes de prueba](configure-test-agents-and-controllers-for-load-tests.md).

La administración de conjuntos de contadores implica la elección del conjunto de equipos del que desea recopilar datos de rendimiento, así como la asignación de un grupo de conjuntos de contadores para recopilar datos de cada equipo individual. Los contadores se administran en el **Editor de pruebas de carga**.

![Administrar conjuntos de contadores](../test/media/loadtestmanagecountersets.png)

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-manage-counter-sets"></a>Para administrar conjuntos de contadores

1.  Abra una prueba de carga.

2.  Elija el botón **Administrar conjuntos de contadores**.

     -O bien-

     Haga clic con el botón derecho en la carpeta **Conjuntos de contadores** del árbol de la prueba de carga y elija **Administrar conjuntos de contadores**.

     Se muestra el cuadro de diálogo **Administrar conjuntos de contadores**.

3.  (Opcional) En el cuadro de lista **Los conjuntos de contadores y equipos seleccionados se agregarán debajo de los siguientes parámetros de ejecución**, seleccione otro parámetro de ejecución.

    > [!NOTE]
    > Esto último sólo se aplica si se tiene más de un parámetro de ejecución en la prueba de carga.

4.  (Opcional) Elija **Agregar equipo** para agregar un nuevo equipo con el fin de supervisarlo. Se le solicitará un nombre. Escriba el nombre de un equipo y verá los nodos que puede seleccionar bajo la nueva entrada. Por ejemplo, **ASP.NET**, **IIS**, **SQL** y otros. Active las casillas situadas delante de los nodos que desee seleccionar. Los nuevos contadores aparecen en el panel **Vista previa de las selecciones**.

5.  (Opcional) En el cuadro de texto **Etiquetas de equipo**, escriba una etiqueta para asociarla al equipo. Por ejemplo, "MáquinaPruebas12 en lab3."

     Las etiquetas de equipo permiten identificar un equipo con un nombre fácil de reconocer.

     Las etiquetas se muestran en el nodo **Asignaciones de conjuntos de contadores** del árbol en el Editor de pruebas de carga. Lo que es más importante, las etiquetas se muestran en los informes de Excel, que sirve de ayuda a las partes interesadas para identificar el rol que desempeña el equipo en la prueba de carga. Por ejemplo, "Servidor1 web en lab2" o "SQL Server2 en oficina Phoenix". Para obtener más información, vea [Informar de los resultados de las pruebas de carga para las comparaciones de pruebas o los análisis de tendencias](../test/compare-load-test-results.md).

6.  Elija **Aceptar**.

## <a name="see-also"></a>Vea también

- [Controladores y agentes de prueba](configure-test-agents-and-controllers-for-load-tests.md)
- [Especificar los conjuntos de contadores y las reglas de umbral para equipos en una prueba de carga](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)
- [Configurar los parámetros de ejecución de pruebas de carga](../test/configure-load-test-run-settings.md)