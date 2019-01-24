---
title: Generar perfiles de rendimiento de aplicaciones de SharePoint | Microsoft Docs
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 8578a27dc6daceda25667142a3cdccae50a42552
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53905694"
---
# <a name="profile-the-performance-of-sharepoint-applications"></a>Perfilar el rendimiento de las aplicaciones de SharePoint

Si las aplicaciones de SharePoint funcionan despacio o de forma ineficaz, puede usar las características de generación de perfiles en Visual Studio para identificar código problemático y otros elementos. Mediante el uso de la característica de prueba de carga, puede determinar cómo se realiza una aplicación de SharePoint bajo estrés, como cuando muchos usuarios acceden a la aplicación al mismo tiempo. Mediante la ejecución de pruebas de rendimiento web, puede medir el funcionamiento de la aplicación en la web. Mediante el uso de pruebas de IU codificadas, puede comprobar si toda la aplicación de SharePoint, incluida la interfaz de usuario, funciona correctamente. Cuando se usan estas pruebas juntas, puede ayudarle a identificar problemas de rendimiento antes de implementar la aplicación.

## <a name="profile-tools-overview"></a>Introducción a las herramientas de perfil

Generación de perfiles se refiere al proceso de observar y grabar el comportamiento de rendimiento de la aplicación mientras se ejecuta. Mediante la generación de perfiles de la aplicación, puede revelar problemas como los cuellos de botella, código ineficaz y problemas de asignación de memoria, lo que hacer que las aplicaciones ejecutan con lentitud o utilicen demasiada memoria. Por ejemplo, puede usar la generación de perfiles para identificar puntos de conexión en el código, que son segmentos de código que se llaman con frecuencia y pueden ralentizar el rendimiento general de la aplicación. Después de identificar puntos de conexión, a menudo puede optimizar o eliminarlos.

Puede usar varias herramientas de generación de perfiles en el entorno de desarrollo integrado (IDE) para identificar y encontrar estos tipos de problemas de rendimiento. Estas herramientas funcionan del mismo modo para proyectos de SharePoint para otros tipos de proyectos de Visual Studio. El Asistente de rendimiento de las herramientas de generación de perfiles le guía a través de la creación de una sesión de rendimiento que usa las pruebas que especifique. Una sesión de rendimiento es un conjunto de datos de configuración que se usan para recopilar información sobre el rendimiento de una aplicación, junto con los resultados de una o varias ejecuciones de generación de perfiles. Sesiones de rendimiento se almacenan en la carpeta del proyecto y puede verlos en **Explorador de rendimiento**. Para obtener más información, vea [Introducción a los métodos de generación de perfiles](../profiling/understanding-performance-collection-methods.md).

Después de crear y ejecutar un análisis de perfiles en la aplicación, un informe proporciona detalles sobre el rendimiento. Este informe puede incluir elementos como un gráfico de uso de CPU en el tiempo, una pila de llamadas de función jerárquica o un árbol de llamadas. El contenido exacto del informe puede variar, dependiendo del tipo de prueba que se ejecuta, como el muestreo o instrumentación. Para obtener más información, consulte [Introducción a informes de las herramientas de generación de perfiles](http://go.microsoft.com/fwlink/?LinkId=224689).

## <a name="performance-session-process"></a>Proceso de la sesión de rendimiento

Para generar perfiles de una aplicación, primero debe usar al Asistente de rendimiento de las herramientas de generación de perfiles para crear una sesión de rendimiento. En la barra de menús, elija **analizar**, **iniciar Asistente de rendimiento**. Como se complete el asistente, escriba la información necesaria para la sesión de rendimiento, como el método de perfil que desea y la aplicación que desea generar perfiles. Para obtener más información, vea [Cómo: Generar perfiles de un sitio Web o aplicación Web mediante el Asistente de rendimiento](http://go.microsoft.com/fwlink/?LinkId=224692). Como alternativa, puede usar las opciones de línea de comandos para configurar y ejecutar una sesión de rendimiento. Para obtener más información, consulte [mediante la generación de perfiles de herramientas de la línea de comandos](http://go.microsoft.com/fwlink/?LinkId=224703). Si desea configurar todos los aspectos de una sesión de rendimiento manualmente, vea [Cómo: Crear manualmente sesiones de rendimiento con las herramientas de generación de perfiles](http://go.microsoft.com/fwlink/?LinkId=224691). También puede crear una sesión de rendimiento de una prueba unitaria si, en el **resultados de pruebas** ventana, abra el menú contextual para la prueba unitaria y, a continuación, eligiendo **crear sesión de rendimiento**.

Después de establecer una sesión de rendimiento, se guarda la configuración de sesión, el servidor está configurado para proporcionar datos de generación de perfiles y se ejecuta la aplicación. Si usa la aplicación, datos de rendimiento se escriben en un archivo de registro. Sesiones de rendimiento se muestran en **Explorador de rendimiento** bajo el **destinos** carpeta. Al finalizar una sesión de rendimiento, el informe aparece en la **informes** carpeta **Explorador de rendimiento**. Para mostrar el informe, ábralo en **Explorador de rendimiento**. Para ver o configurar las propiedades de una sesión de rendimiento, abra el menú contextual en **Explorador de rendimiento**y, a continuación, elija **propiedades**. Para obtener más información acerca de las propiedades específicas de una sesión de rendimiento, consulte [configurar sesiones de rendimiento para las herramientas de generación de perfiles](http://go.microsoft.com/fwlink/?LinkId=224694). Para obtener información acerca de cómo interpretar los resultados de una sesión de rendimiento, consulte [analizar datos de las herramientas de generación de perfiles](http://go.microsoft.com/fwlink/?LinkId=224704).

## <a name="stress-test"></a>Prueba de esfuerzo

Puede analizar el rendimiento de esfuerzo de las aplicaciones mediante la creación de pruebas de carga y pruebas de rendimiento web en Visual Studio. Cuando se crea una prueba de carga en Visual Studio, especifique una combinación de factores, denominada escenario, para probar la aplicación en. Estos factores incluyen el modelo de carga, el modelo de combinación de pruebas, combinación de pruebas, combinación de redes y combinación de exploradores web. Escenarios de prueba de carga pueden incluir pruebas unitarias y pruebas de rendimiento web.

Figura 1: Ejemplo de resultados de pruebas de carga

![Vista de gráficos de ejecución de prueba](../sharepoint/media/load-webgraphs.png "vista de gráficos de prueba de carga")

Pruebas de rendimiento web simulan cómo un usuario final puede interactuar con una aplicación de SharePoint. Puede crear pruebas de rendimiento web grabando las solicitudes HTTP en una sesión del explorador o mediante el uso de la **grabadora de prueba de rendimiento Web**. Las solicitudes web aparecen en la **Editor de prueba de rendimiento Web** una vez finalizada la sesión del explorador. A continuación, puede depurar los resultados en el **Visor de resultados de pruebas de rendimiento Web**. Puede crear pruebas de rendimiento web manualmente mediante el uso de la **Editor de prueba de rendimiento Web**.

## <a name="test-user-interfaces"></a>Interfaces de usuario de prueba

Pruebas de IU codificadas controlan automáticamente la aplicación de SharePoint a través de su interfaz de usuario (UI). Estas pruebas cubren los controles de interfaz de usuario, como botones y menús, para comprobar que funcionan correctamente. Esta clase de prueba es especialmente útil si la validación u otra lógica se realiza en la interfaz de usuario, como en una página web. También puede usar pruebas de IU codificadas para automatizar las pruebas manuales. Puede crear pruebas de IU codificadas para las aplicaciones de SharePoint de la misma manera como crear pruebas para otros tipos de aplicaciones. Para obtener más información, consulte [probar aplicaciones de SharePoint 2010 con pruebas de IU codificadas](../test/testing-sharepoint-2010-applications-with-coded-ui-tests.md).

## <a name="related-topics"></a>Temas relacionados

|Título|Descripción|
|-----------|-----------------|
|[Tutorial: Generar perfiles de una aplicación de SharePoint](../sharepoint/walkthrough-profiling-a-sharepoint-application.md)|Muestra cómo realizar un análisis de perfiles de muestreo en una aplicación de SharePoint.|
|[Ejecutar pruebas de rendimiento en la aplicación antes del lanzamiento](/azure/devops/test/load-test/run-performance-tests-app-before-release?view=vsts)|Describe cómo crear pruebas de carga, que le ayudarán a las aplicaciones de SharePoint de prueba de esfuerzo.|
|[Haga una prueba unitaria de su código](../test/unit-test-your-code.md)|Describe cómo buscar errores lógicos en el código mediante pruebas unitarias.|
|[Probar aplicaciones de SharePoint 2010 con pruebas de IU codificadas](../test/testing-sharepoint-2010-applications-with-coded-ui-tests.md)|Describe cómo probar la interfaz de usuario de las aplicaciones de SharePoint.|

## <a name="see-also"></a>Vea también

- [Build and debug SharePoint solutions](../sharepoint/building-and-debugging-sharepoint-solutions.md) (Compilar y depurar las soluciones de SharePoint)
- [Mejorar la calidad del código](../test/improve-code-quality.md)