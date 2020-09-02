---
title: Generar perfiles del rendimiento de las aplicaciones de SharePoint | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.Profiling.SilverlightWebPartOnly
- VS.SharePointTools.Profiling.DotNetTrustLevel
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, profiling
- performance testing [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, performance testing
- profiling [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 72739cd1063298a2dafc71976fd45360bc2d6ec2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "73189202"
---
# <a name="profile-the-performance-of-sharepoint-applications"></a>Generar perfiles del rendimiento de las aplicaciones de SharePoint

Si las aplicaciones de SharePoint funcionan lentamente o de manera ineficaz, puede usar las características de generación de perfiles de Visual Studio para identificar código problemático y otros elementos. Mediante el uso de la característica de pruebas de carga, puede determinar el rendimiento de una aplicación de SharePoint en situaciones de estrés, como cuando muchos usuarios acceden a la aplicación simultáneamente. Mediante la ejecución de pruebas de rendimiento web, puede medir cómo funciona la aplicación en la Web. Mediante el uso de pruebas de IU codificadas, puede comprobar si toda la aplicación de SharePoint, incluida su interfaz de usuario, funciona correctamente. Al utilizar estas pruebas juntas, pueden ayudarle a identificar los problemas de rendimiento antes de implementar la aplicación.

## <a name="profile-tools-overview"></a>Información general de las herramientas de perfil

La generación de perfiles hace referencia al proceso de observación y grabación del comportamiento de rendimiento de la aplicación mientras se ejecuta. Al generar perfiles de la aplicación, puede descubrir problemas como cuellos de botella, código ineficaz y problemas de asignación de memoria, lo que hace que las aplicaciones se ejecuten lentamente o utilicen demasiada memoria. Por ejemplo, puede usar la generación de perfiles para identificar zonas activas en el código, que son segmentos de código a los que se llama con frecuencia y que pueden ralentizar el rendimiento general de la aplicación. Después de identificar las zonas activas, a menudo se pueden optimizar o eliminar.

Puede usar varias herramientas de generación de perfiles en el entorno de desarrollo integrado (IDE) para identificar y localizar estos tipos de problemas de rendimiento. Estas herramientas funcionan de la misma manera para los proyectos de SharePoint que para otros tipos de proyectos de Visual Studio. El Asistente de Herramientas de generación de perfiles rendimiento le guía por la creación de una sesión de rendimiento que usa las pruebas que especifique. Una sesión de rendimiento es un conjunto de datos de configuración que se usa para recopilar información de rendimiento de una aplicación, junto con los resultados de una o varias ejecuciones de generación de perfiles. Las sesiones de rendimiento se almacenan en la carpeta del proyecto y puede verlas en **Explorador de rendimiento**. Para obtener más información, vea [Introducción a los métodos de generación de perfiles](../profiling/understanding-performance-collection-methods.md).

Después de crear y ejecutar un análisis de perfil en la aplicación, un informe proporciona detalles sobre su rendimiento. Este informe puede incluir elementos como un gráfico de uso de CPU a lo largo del tiempo, una pila de llamadas de función jerárquica o un árbol de llamadas. El contenido exacto del informe puede variar en función del tipo de prueba que se ejecute, como el muestreo o la instrumentación. Para obtener más información, vea [información general sobre informes de herramientas de generación de perfiles](../profiling/performance-report-overview.md).

## <a name="performance-session-process"></a>Proceso de sesión de rendimiento

Para generar perfiles de una aplicación, empiece usando el Asistente de Herramientas de generación de perfiles rendimiento para crear una sesión de rendimiento. En la barra de menús, elija **analizar**, **iniciar Asistente de rendimiento**. Cuando complete el asistente, escriba la información necesaria para la sesión de rendimiento, como el método de perfil que desee y la aplicación de la que desea generar perfiles. Para obtener más información, consulte [Cómo: generar perfiles de un sitio web o una aplicación Web mediante el Asistente de rendimiento](../profiling/how-to-collect-performance-data-for-a-web-site.md). Como alternativa, puede usar las opciones de línea de comandos para configurar y ejecutar una sesión de rendimiento. Para obtener más información, vea [usar el herramientas de generación de perfiles desde la línea de comandos](../profiling/using-the-profiling-tools-from-the-command-line.md). Si desea configurar manualmente cada aspecto de una sesión de rendimiento, consulte [Cómo: crear manualmente sesiones de rendimiento con el herramientas de generación de perfiles](../profiling/how-to-manually-create-performance-sessions.md). También puede crear una sesión de rendimiento a partir de una prueba unitaria de; en la ventana de **resultados de pruebas** , abra el menú contextual de la prueba unitaria y, a continuación, elija **crear sesión de rendimiento**.

Después de configurar una sesión de rendimiento, se guarda la configuración de sesión, el servidor se configura para proporcionar datos de generación de perfiles y la aplicación se ejecuta. A medida que se utiliza la aplicación, los datos de rendimiento se escriben en un archivo de registro. Las sesiones de rendimiento se muestran en **Explorador de rendimiento** en la carpeta **destinos** . Una vez finalizada la sesión de rendimiento, el informe aparece en la carpeta **informes** de **Explorador de rendimiento**. Para mostrar el informe, ábralo en **Explorador de rendimiento**. Para ver o configurar las propiedades de una sesión de rendimiento, abra el menú contextual en **Explorador de rendimiento**y, a continuación, elija **propiedades**. Para obtener más información acerca de las propiedades específicas de una sesión de rendimiento, consulte [configuración de sesiones de rendimiento para herramientas de generación de perfiles](../profiling/configuring-performance-sessions.md). Para obtener información sobre cómo interpretar los resultados de una sesión de rendimiento, consulte [analizar datos de herramientas de generación de perfiles](../profiling/analyzing-performance-tools-data.md).

## <a name="stress-test"></a>Prueba de esfuerzo

Puede analizar el rendimiento de esfuerzo de las aplicaciones mediante la creación de pruebas de carga y pruebas de rendimiento web en Visual Studio. Cuando se crea una prueba de carga en Visual Studio, se especifica una combinación de factores, denominada escenario, para probar la aplicación. Estos factores incluyen el patrón de carga, el modelo de combinación de pruebas, la combinación de pruebas, la combinación de redes y la combinación de exploradores Web. Los escenarios de prueba de carga pueden incluir pruebas unitarias y pruebas de rendimiento web.

Figura 1: ejemplo de resultados de pruebas de carga

![Vista de gráficos de prueba de carga en ejecución](../sharepoint/media/load-webgraphs.png "Vista de gráficos de prueba de carga en ejecución")

Las pruebas de rendimiento web simulan el modo en que un usuario final puede interactuar con una aplicación de SharePoint. Puede crear pruebas de rendimiento web grabando solicitudes HTTP en una sesión del explorador o mediante la **grabadora de pruebas de rendimiento web**. Las solicitudes web aparecen en el **Editor de pruebas de rendimiento web** una vez finalizada la sesión del explorador. A continuación, puede depurar los resultados en el **visor de resultados de pruebas de rendimiento web**. También puede generar manualmente las pruebas de rendimiento web mediante el **Editor de pruebas de rendimiento web**.

## <a name="test-user-interfaces"></a>Probar interfaces de usuario

Las pruebas de IU codificadas controlan automáticamente la aplicación de SharePoint a través de su interfaz de usuario (IU). Estas pruebas cubren los controles de interfaz de usuario, como botones y menús, para comprobar que funcionan correctamente. Este tipo de pruebas es especialmente útil si la validación u otra lógica se realiza en la interfaz de usuario, como en una página web. También puede usar pruebas de IU codificadas para automatizar las pruebas manuales. Cree pruebas de IU codificadas para las aplicaciones de SharePoint del mismo modo que crea pruebas para otros tipos de aplicaciones. Para obtener más información, vea [probar aplicaciones de SharePoint 2010 con pruebas de IU codificadas](/visualstudio/test/testing-sharepoint-2010-applications-with-coded-ui-tests?view=vs-2015).

## <a name="related-topics"></a>Temas relacionados

|Title|Descripción|
|-----------|-----------------|
|[Tutorial: generar perfiles de una aplicación de SharePoint](../sharepoint/walkthrough-profiling-a-sharepoint-application.md)|Muestra cómo realizar un análisis de Perfil de muestreo en una aplicación de SharePoint.|
|[Ejecutar pruebas de rendimiento en la aplicación antes del lanzamiento](/azure/devops/test/load-test/run-performance-tests-app-before-release?view=vsts)|Describe cómo crear pruebas de carga, que le ayudarán a realizar pruebas de esfuerzo de las aplicaciones de SharePoint.|
|[Prueba unitaria del código](../test/unit-test-your-code.md)|Describe cómo buscar errores lógicos en el código mediante pruebas unitarias.|
|[Probar aplicaciones de SharePoint 2010 con pruebas automatizadas de IU](/visualstudio/test/testing-sharepoint-2010-applications-with-coded-ui-tests?view=vs-2015)|Describe cómo probar la interfaz de usuario de las aplicaciones de SharePoint.|

## <a name="see-also"></a>Vea también

- [Build and debug SharePoint solutions](../sharepoint/building-and-debugging-sharepoint-solutions.md) (Compilar y depurar las soluciones de SharePoint)
- [Mejorar la calidad del código](../test/improve-code-quality.md)