---
title: Comprobar y depurar código de SharePoint | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- unit testing [SharePoint development in Visual Studio]
- IntelliTrace [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, IntelliTrace
- SharePoint development in Visual Studio, unit testing
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 327e7be43fc60142fc50634ec61f6fd9499461e2
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/29/2018
ms.locfileid: "37119830"
---
# <a name="verify-and-debug-sharepoint-code"></a>Comprobar y depurar el código de SharePoint
Con IntelliTrace y las pruebas unitarias, puede depurar las soluciones de SharePoint más fácilmente y asegurarse de que cada método en ellas funciona correctamente. Puede usar estas características para los proyectos de SharePoint en Visual Studio siguiendo los mismos procedimientos que en otros tipos de proyectos.

## <a name="intellitrace"></a>IntelliTrace
Mediante IntelliTrace, puede determinar el estado actual de la solución de SharePoint, así como los eventos que se produjeron en el pasado y el contexto en el que se produjeron. Puede navegar hacia delante y hacia atrás a varios puntos de la solución de SharePoint donde se grabaron eventos de interés y revisar los estados y valores de las variables en cada punto. Mediante esta navegación dinámica, puede depurar de forma más rápida y fácil las soluciones de SharePoint sin tener que establecer numerosos puntos de interrupción. También puede guardar la sesión de depuración en un registro de IntelliTrace (*.iTrace*) de archivo, abrirlo posteriormente en Visual Studio Enterprise y realizar una depuración posterior a un bloqueo. El *.iTrace* archivo incluye información detallada sobre cuándo y dónde se produjeron los errores específicos de SharePoint, por lo que más fácilmente puede averiguar qué está causando los errores. La información de la *.iTrace* archivo es un subconjunto del registro de errores completo que crea el registro unificado del sistema (ULS) en SharePoint. Esta información incluye eventos que son específicos de SharePoint, como cuando un perfil de usuario se abre o se cierra y cuando las propiedades de un proyecto de SharePoint se cargan, se leen o se cambian. Puede configurar los eventos que registra IntelliTrace. Para obtener más información, consulte [mediante datos de IntelliTrace guardado](/visualstudio/debugger/using-saved-intellitrace-data).

Cuando se produce un error en SharePoint, el cuadro de diálogo de error muestra un identificador "identificador de correlación" para ese error concreto. También puede obtener los identificadores de correlación de eventos que se muestran en el *.iTrace* archivo. Para mostrar una lista de todos los eventos que se produjeron con un identificador de correlación dado, puede escribir el identificador en el **Analysis** sección de la página de resumen de IntelliTrace. En esa sección, puede elegir si se muestran solo los nombres de los eventos que se produjeron o los nombres de los eventos junto con su información de llamadas, como el nombre de función, los puntos de salida y de entrada, los parámetros y los valores devueltos.

Puede obtener eventos de Visual Studio en IntelliTrace eligiendo la **F5** clave. Sin embargo, para obtener los eventos que son específicos de SharePoint, debe reunir los datos de IntelliTrace en las soluciones de SharePoint mediante Microsoft Monitoring Agent. Esta herramienta recopila datos de IntelliTrace y crea *.iTrace* archivos para las aplicaciones implementadas fuera de Visual Studio. Para obtener más información, consulte [las características de IntelliTrace](/visualstudio/debugger/intellitrace-features) y [mediante el recolector independiente IntelliTrace](/visualstudio/debugger/using-the-intellitrace-stand-alone-collector).

## <a name="unit-test"></a>Prueba unitaria
Puede encontrar más fácilmente los errores en el código si realiza pruebas unitarias, en las que el código de prueba se escribe y ejecuta en los métodos de prueba. Estos métodos contienen variables vacías y una instrucción Assert que puede usar para comprobar la lógica y funcionalidad del proyecto basándose en el modelo de objetos de SharePoint. Para obtener más información, vea [Haga una prueba unitaria de su código](/visualstudio/test/unit-test-your-code).

### <a name="support-for-microsoft-fakes-framework"></a>Compatibilidad con el marco Microsoft Fakes
Los proyectos de SharePoint admiten Microsoft Fakes, un marco de aislamiento en el que se pueden crear códigos auxiliares basados en el delegado y en correcciones de compatibilidad (shim) en las aplicaciones basadas en .NET Framework. Utilizando el marco Fakes, puede crear, mantener e insertar implementaciones ficticias en las pruebas unitarias. Estos códigos auxiliares y shims aíslan las pruebas unitarias del entorno. Puede crear códigos auxiliares para probar código que utiliza interfaces o clases no selladas con métodos reemplazables. Puede crear shims para redirigir llamadas codificadas para clases selladas con métodos estáticos o que no se pueden reemplazar a una implementación alternativa de shim. También puede usar delegados con tipos de código auxiliar y tipos de shim para personalizar dinámicamente el comportamiento de los miembros individuales del código auxiliar. Para obtener más información, consulte [aislar el código probado con Microsoft Fakes](/visualstudio/test/isolating-code-under-test-with-microsoft-fakes).

## <a name="related-articles"></a>Artículos relacionados

|Title|Descripción|
|-----------|-----------------|
|[IntelliTrace](/visualstudio/debugger/intellitrace)|Describe cómo depurar soluciones de Visual Studio más fácilmente mediante IntelliTrace.|
|[Tutorial: Depurar una aplicación de SharePoint mediante IntelliTrace](../sharepoint/walkthrough-debugging-a-sharepoint-application-by-using-intellitrace.md)|Muestra cómo buscar los errores de codificación en un proyecto de SharePoint mediante IntelliTrace.|
|[Haga una prueba unitaria de su código](/visualstudio/test/unit-test-your-code)|Describe cómo buscar errores lógicos en el código mediante pruebas unitarias.|

## <a name="see-also"></a>Vea también
[Mejorar la calidad del código](/visualstudio/test/improve-code-quality)
