---
title: Usar el Diagrama de actividad del usuario virtual de las pruebas de carga en Visual Studio
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, virtual user activity chart
- virtual user activity chart, isolating performance issues
ms.assetid: d1c10fb9-cfeb-4e7f-9991-2d1e1103699e
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: fedc9aebb4d57e258370179bbf820abdc8978940
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
ms.locfileid: "31976437"
---
# <a name="walkthrough-using-the-virtual-user-activity-chart-to-isolate-issues"></a>Tutorial: Usar el Diagrama de actividad del usuario virtual para aislar problemas de rendimiento

En este tutorial obtendrá información sobre cómo usar el Diagrama de actividad del usuario virtual para aislar errores que se produjeron para los usuarios virtuales individuales que ejecutaron la prueba de carga.

 El Diagrama de actividad del usuario virtual permite visualizar la actividad del usuario virtual asociado a la prueba de carga. Cada fila del diagrama representa un usuario virtual individual. El Diagrama de actividad del usuario virtual muestra exactamente qué estaba ejecutando cada usuario virtual durante la prueba. Esto le permite aislar problemas de rendimiento examinando modelos de actividad de usuario y modelos de carga, correlacionar pruebas no superadas o lentas, y ver solicitudes con otra actividad del usuario virtual. El Gráfico de actividad del usuario virtual solo está disponible después de que la carga haya terminado de ejecutarse.

 En este tutorial, se realizarán las siguientes tareas:

-   Obtener información sobre cómo usar las siguientes herramientas asociadas al Diagrama de actividad del usuario virtual:

    -   Usar la herramienta **Ampliar período de tiempo** para especificar un período de tiempo concreto del gráfico que quiera analizar.

    -   Usar los paneles **Leyenda de detalles** y **Resultados del filtro** para aplicar filtrado al gráfico con el fin de ayudar a aislar problemas.

-   Usar el Diagrama de actividad del usuario virtual para analizar un error que se produjo para un usuario virtual concreto y ver los detalles del tipo de error problemático.

 Para obtener más información, vea [Analizar la actividad de usuario virtual en la vista Detalles](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md).

## <a name="prerequisites"></a>Requisitos previos

-   Visual Studio Enterprise

-   Complete estos procedimientos:

    -   [Registrar y ejecutar una prueba de rendimiento web](http://msdn.microsoft.com/en-us/bd0a82fd-cec0-4861-bc09-e1b0b2d258ef)

    -   [Crear y ejecutar una prueba de carga](http://msdn.microsoft.com/en-us/7041cbcf-9ab1-4579-98ff-8f296aeaded4)

## <a name="open-the-colorwebapp-solution-created-in-the-previous-walkthroughs"></a>Abrir la solución ColorWebApp creada en los tutoriales anteriores

### <a name="open-the-solution"></a>Abra la solución.

1.  Inicie Visual Studio.

2.  Abra la solución ColorWebApp que contiene LoadTest1.loadtest. Esta prueba de carga es el resultado de realizar los pasos de los tres tutoriales que se enumeran al principio de este tema en la sección de requisitos previos.

     En los pasos restantes de este tutorial se da por supuesto que se usan una aplicación web denominada ColorWebApp, una prueba de rendimiento web denominada ColorWebAppTest.webtest y una prueba de carga denominada LoadTest1.loadtest.

## <a name="run-the-load-test"></a>Ejecutar la prueba de carga
 Ejecute la prueba de carga para recopilar datos de actividad del usuario virtual.

### <a name="run-the-load-test-to-collect-virtual-user-activity-data"></a>Ejecutar la prueba de carga para recopilar datos de actividad de usuario virtual

-   En el Editor de pruebas de carga, elija **Ejecutar** en la barra de herramientas. LoadTest1 empezará a ejecutarse.

## <a name="isolate-issues-in-the-virtual-user-activity-chart"></a>Aislar problemas en el Diagrama de actividad del usuario virtual

Después de haber ejecutado la prueba de carga y recopilado los datos de actividad del usuario virtual, puede ver los datos de los resultados de pruebas usando la vista Detalles del Analizador de prueba de carga en el Diagrama de actividad del usuario virtual. También puede usar el Diagrama de actividad del usuario virtual como ayuda para aislar problemas de rendimiento en la prueba de carga.

### <a name="to-use-the-virtual-user-activity-chart-in-your-load-test-results"></a>Para usar el Diagrama de actividad del usuario virtual en los resultados de pruebas de carga

1.  Una vez finalizada la ejecución de la prueba de carga, aparecerá la página Resumen de los resultados de pruebas de carga en el Analizador de prueba de carga. Elija el botón **Gráficos** de la barra de herramientas.

     Se mostrará la vista Gráficos.

2.  En el gráfico **Tiempo de respuesta de la página**, haga clic con el botón derecho cerca de uno de los iconos de infracción del umbral y seleccione **Ir a detalles de usuario**.

    > [!NOTE]
    > También puede usar el botón **Detalles** de la barra de herramientas del Editor de pruebas de carga para abrir el Diagrama de actividad del usuario virtual. Sin embargo, si usa la opción **Ir a detalles de usuario**, el Diagrama de actividad del usuario virtual irá automáticamente a la parte de la prueba en la que hizo clic en el gráfico.

     Se mostrará la vista Detalles con el **Diagrama de actividad del usuario virtual** centrado en el período de tiempo en que se produjeron las infracciones del umbral.

     En el eje y, los trazados horizontales representan a los usuarios virtuales individuales. El eje x muestra la escala de tiempo para la ejecución de la prueba de carga.

3.  En la herramienta **Ampliar período de tiempo** que hay bajo el **Diagrama de detalles del usuario virtual**, ajuste los controles deslizantes izquierdo y derecho hasta que ambos estén cerca del icono de infracción del umbral. Esto cambiará la escala de tiempo en el **Diagrama de actividad del usuario virtual**.

4.  En **Leyenda de detalles**, active la casilla correspondiente a **(Resaltar errores)**. Observe que el usuario virtual que produjo la infracción del umbral aparece resaltado.

5.  En el panel **Resultados del filtro**, desactive las casillas **Mostrar resultados correctos** y **HttpError**, pero deje activada la casilla **ValidationRuleError**.

     El **Diagrama de actividad del usuario virtual** solo mostrará los usuarios virtuales que estuvieron más de 3 segundos en la página Red.aspx tal y como especifica la infracción del umbral configurada en el tutorial anterior.

6.  Deje el puntero del mouse sobre la línea horizontal que representa al usuario virtual que tiene el error de la regla de validación para la infracción del umbral.

7.  Se mostrará una información sobre herramientas con la siguiente información:

    -   **Id. de usuario**

    -   **Escenario**

    -   **Prueba**

    -   **Resultado**

    -   **Network**

    -   **Hora de inicio**

    -   **Duración**

    -   **Agent**

    -   **Registro de prueba**

8.  Observe que **Registro de prueba** es un vínculo. Elija el vínculo **Registro de prueba**.

9. La prueba de rendimiento web ColorWebTest que está asociada al registro se abrirá en el Visor de resultados de pruebas de rendimiento web. Esto le permite aislar dónde se produjeron las infracciones del umbral.

     Puede usar varias configuraciones de los paneles **Leyenda de detalles** y **Resultados del filtro** como ayuda para aislar problemas de rendimiento y errores en las pruebas de carga. Experimente con estos valores y la herramienta **Ampliar período de tiempo** para ver cómo se presentan los datos del usuario virtuales en el **Diagrama de actividad del usuario virtual**.

## <a name="see-also"></a>Vea también

- [Analizar la actividad de usuario virtual en la vista Detalles](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md)
- [Controladores y agentes de prueba](configure-test-agents-and-controllers-for-load-tests.md)
- [Cómo: Crear una configuración de pruebas para una prueba de carga distribuida](../test/how-to-create-a-test-setting-for-a-distributed-load-test.md)
- [Instalar y configurar agentes de prueba](../test/lab-management/install-configure-test-agents.md)
- [Recopilar información de diagnóstico con la configuración de pruebas](../test/collect-diagnostic-information-using-test-settings.md)