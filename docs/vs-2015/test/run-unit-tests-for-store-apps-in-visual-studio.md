---
title: Ejecución de pruebas unitarias para aplicaciones de la Tienda en Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5a6f5b32-bfce-4a63-81e9-02d54c592539
caps.latest.revision: 14
author: alexhomer1
ms.author: gewarren
manager: robinr
ms.openlocfilehash: 2a1091231fd934669547348a183de98b15e53dff
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49900493"
---
# <a name="run-unit-tests-for-store-apps-in-visual-studio"></a>Ejecutar pruebas unitarias para aplicaciones de la Tienda en Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En este tema se describe cómo ejecutar pruebas unitarias con el Explorador de pruebas de Microsoft Visual Studio.  
  
> [!NOTE]
>  Los temas de esta sección describen la funcionalidad de Visual Studio Express para Windows 8. Visual Studio Community, Enterprise y Professional proporcionan características adicionales para las pruebas unitarias.  
> 
> - Use cualquier marco de pruebas unitarias de código abierto o de terceros que haya creado un adaptador complementario para el Explorador de pruebas de Microsoft. También puede analizar y mostrar información de cobertura de código para las pruebas.  
>   -   Ejecute las pruebas después de cada compilación. También puede usar Microsoft Fakes, un marco de aislamiento para código administrado para centrar sus pruebas en su propio código sustituyendo el código de prueba para el sistema y la funcionalidad de terceros.  
> 
>   Para obtener más información, vea [Haga una prueba unitaria de su código](../test/unit-test-your-code.md) en la biblioteca de MSDN.  
  
##  <a name="BKMK_In_this_topic"></a> En este tema  
 [Marcos de pruebas unitarias y proyectos de prueba](#BKMK_Unit_test_frameworks_and_test_projects)  
  
 [Ejecutar pruebas en el Explorador de pruebas](#BKMK_Running_tests_in_Test_Explorer)  
  
- [Ejecutar pruebas](#BKMK_Running_tests)  
  
  [Ver los resultados de la prueba](#BKMK_Viewing_test_results)  
  
- [Ver los detalles de la prueba](#BKMK_Viewing_test_details)  
  
- [Ver el código fuente de un método de prueba](#BKMK_Viewing_the_source_code_of_a_test_method)  
  
  [Organizar la lista de pruebas](#BKMK_Organizing_the_test_list)  
  
- [Agrupar las pruebas](#BKMK_Grouping_tests)  
  
- [Buscar y filtrar la lista de pruebas](#BKMK_Searching_and_filtering_the_test_list)  
  
  [Depurar las pruebas unitarias](#BKMK_Debugging_unit_tests)  
  
##  <a name="BKMK_Unit_test_frameworks_and_test_projects"></a> Marcos de pruebas unitarias y proyectos de prueba  
 Visual Studio Express para las aplicaciones de la Tienda Windows incluye los marcos de pruebas unitarias de Microsoft para código en C++ administrado y nativo. El Explorador de pruebas puede ejecutar pruebas de varios proyectos de prueba en una solución y desde las clases de prueba que forman parte de los proyectos de código de producción. Proyectos de prueba pueden ser cualquier combinación de los marcos de pruebas unitarias de Visual C++, Visual C# y Visual Basic. Cuando se escribe el código sometido a prueba para .NET Framework, el proyecto de prueba se puede escribir en cualquier lenguaje de .NET Framework, independientemente del lenguaje del código de destino. Los proyectos de código de C/C ++ nativos deben probarse con el marco de pruebas unitarias de C++.  
  
##  <a name="BKMK_Running_tests_in_Test_Explorer"></a> Ejecutar pruebas en el Explorador de pruebas  
 Al compilar el proyecto de prueba, las pruebas aparecen en el Explorador de pruebas. Si el Explorador de pruebas no está visible, elija **Prueba** en el menú de Visual Studio, elija **Ventanas**y, después, **Explorador de pruebas**.  
  
 ![Explorador de pruebas unitarias](../ide/media/ute-failedpassednotrunsummary.png "UTE_FailedPassedNotRunSummary")  
  
 Al ejecutar, escribir y volver a ejecutar las pruebas, el Explorador de pruebas muestra los resultados en los grupos predeterminados de **Pruebas no superadas**, **Pruebas superadas**, **Pruebas omitidas** y **Pruebas no ejecutadas**. Puede cambiar la manera en que el Explorador de pruebas agrupa las pruebas.  
  
 Desde la barra de herramientas del Explorador de pruebas puede realizar gran parte del trabajo de búsqueda, organización y ejecución de las pruebas.  
  
 ![Ejecutar pruebas desde la barra de herramientas del Explorador de pruebas](../test/media/ute-toolbar.png "UTE_ToolBar")  
  
###  <a name="BKMK_Running_tests"></a> Ejecutar pruebas  
 Puede ejecutar todas las pruebas de la solución, todas las pruebas de un grupo o un conjunto de pruebas seleccionado. Realice una de las siguientes acciones:  
  
- Para ejecutar todas las pruebas de una solución, elija **Ejecutar todas**.  
  
- Para ejecutar todas las pruebas de un grupo predeterminado, elija **Ejecutar...** y el grupo en el menú.  
  
- Seleccione las pruebas individuales que quiere ejecutar, abra el menú contextual de una prueba seleccionada y elija **Ejecutar pruebas seleccionadas**.  
  
  Según se vayan ejecutando las pruebas, se animará la barra de superado o no superado en la parte superior de la ventana del Explorador de pruebas. Al finalizar la ejecución de las pruebas, la barra de superado o no superado se pondrá verde si se superan todas las pruebas. En caso contrario, se pondrá roja.  
  
##  <a name="BKMK_Viewing_test_results"></a> Ver los resultados de la prueba  
 Al ejecutar, escribir y volver a ejecutar las pruebas, el Explorador de pruebas muestra los resultados en los grupos de **Pruebas no superadas**, **Pruebas superadas**, **Pruebas omitidas** y **Pruebas no ejecutadas**. El panel de detalles de la parte inferior del Explorador de pruebas muestra un resumen de la ejecución de la prueba.  
  
###  <a name="BKMK_Viewing_test_details"></a> Ver los detalles de la prueba  
 Para ver los detalles de una prueba individual, selecciónela.  
  
 El panel de detalles de la prueba muestra la información siguiente:  
  
- El nombre de archivo de origen y el número de línea del método de prueba.  
  
- Estado de la prueba.  
  
- El tiempo que ha tardado en ejecutarse el método de prueba.  
  
  Si la prueba no se supera, en el panel de detalles se mostrará también:  
  
- El mensaje que ha devuelto el marco de pruebas unitarias para la prueba.  
  
- El seguimiento de la pila en el momento en que la prueba generó el error.  
  
###  <a name="BKMK_Viewing_the_source_code_of_a_test_method"></a> Ver el código fuente de un método de prueba  
 Para mostrar el código fuente de un método de prueba en el Editor de Visual Studio, seleccione la prueba y elija **Abrir prueba** en el menú contextual (teclado: F12).  
  
##  <a name="BKMK_Organizing_the_test_list"></a> Organizar la lista de pruebas  
  
###  <a name="BKMK_Grouping_tests"></a> Agrupar las pruebas  
 De forma predeterminada, el Explorador de pruebas muestra las pruebas como nodos secundarios de **Pruebas no superadas**, **Pruebas superadas**, **Pruebas omitidas** y **Pruebas no ejecutadas**.  
  
|||  
|-|-|  
|![Botón de grupo Explorador de pruebas](../test/media/ute-groupby-btn.png "UTE_GroupBy_btn")|Para agrupar las pruebas por el tiempo necesario para ejecutarlas, abra la lista **Agrupar por** y elija **Duración**. Elija **Resultado de la prueba** para volver a la agrupación original.|  
  
###  <a name="BKMK_Searching_and_filtering_the_test_list"></a> Buscar y filtrar la lista de pruebas  
 Si tiene muchas pruebas, puede escribir en el cuadro de búsqueda del Explorador de pruebas para filtrar la lista por la cadena especificada. Puede restringir el filtro a tipos específicos de cadenas seleccionando uno en la lista de filtros antes de introducir la cadena de búsqueda.  
  
 ![Categorías de filtro de búsqueda](../test/media/ute-searchfilter.png "UTE_SearchFilter")  
  
##  <a name="BKMK_Debugging_unit_tests"></a> Depurar las pruebas unitarias  
 Se puede usar el Explorador de pruebas para iniciar una sesión de depuración para las pruebas. La ejecución paso a paso del código con el depurador de Visual Studio permite avanzar y retroceder sin problemas entre las pruebas unitarias y el proyecto objeto de prueba. Para iniciar la depuración:  
  
1. En el editor de Visual Studio, establezca un punto de interrupción en uno o varios métodos de prueba que desee depurar.  
  
   > [!NOTE]
   >  Dado que los métodos de prueba se pueden ejecutar en cualquier orden, establezca puntos de interrupción en todos los métodos de prueba que desee depurar.  
  
2. En el Explorador de pruebas, seleccione los métodos de prueba y elija **Depurar pruebas seleccionadas** en el menú contextual.  
  
   Para obtener más información sobre el depurador, vea [Debugging in Visual Studio](../debugger/debugging-in-visual-studio.md).



