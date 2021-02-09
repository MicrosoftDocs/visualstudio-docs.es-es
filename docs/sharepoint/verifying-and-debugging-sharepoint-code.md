---
title: Comprobar y depurar código de SharePoint | Microsoft Docs
description: Comprobar y depurar código de SharePoint. Use IntelliTrace para examinar los eventos pasados y el estado actual de la solución. Use pruebas unitarias para asegurarse de que los métodos funcionan correctamente.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- unit testing [SharePoint development in Visual Studio]
- IntelliTrace [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, IntelliTrace
- SharePoint development in Visual Studio, unit testing
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: d406afbc0a8506262f1bdc17310802b7f41a931a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99892143"
---
# <a name="verify-and-debug-sharepoint-code"></a>Comprobar y depurar código de SharePoint
Con IntelliTrace y las pruebas unitarias, puede depurar las soluciones de SharePoint más fácilmente y asegurarse de que cada método en ellas funciona correctamente. Puede usar estas características para los proyectos de SharePoint en Visual Studio siguiendo los mismos procedimientos que para otros tipos de proyectos.

## <a name="intellitrace"></a>Solamente
Mediante IntelliTrace, puede determinar el estado actual de la solución de SharePoint, así como los eventos que se produjeron en el pasado y el contexto en el que se produjeron. Puede navegar hacia delante y hacia atrás a varios puntos de la solución de SharePoint donde se grabaron eventos de interés y revisar los estados y valores de las variables en cada punto. Mediante esta navegación dinámica, puede depurar de forma más rápida y fácil las soluciones de SharePoint sin tener que establecer numerosos puntos de interrupción. También puede guardar la sesión de depuración en un archivo de registro de IntelliTrace (*. iTrace*), abrirlo más adelante en Visual Studio Enterprise y realizar la depuración después de un bloqueo. El archivo *. iTrace* incluye información detallada sobre cuándo y dónde se produjeron los errores específicos de SharePoint, de modo que pueda averiguar más fácilmente lo que está causando los errores. La información del archivo *. iTrace* es un subconjunto del registro de errores completo que crea el sistema de Registro Unificado (ULS) de SharePoint. Esta información incluye eventos que son específicos de SharePoint, como cuando un perfil de usuario se abre o se cierra y cuando las propiedades de un proyecto de SharePoint se cargan, se leen o se cambian. Puede configurar los eventos que registra IntelliTrace. Para obtener más información, vea el tema sobre el [uso de datos guardados de IntelliTrace](../debugger/using-saved-intellitrace-data.md).

Cuando se produce un error en SharePoint, el cuadro de diálogo de error muestra un identificador "identificador de correlación" para ese error concreto. También puede obtener los identificadores de correlación de los eventos que se enumeran en el archivo *. iTrace* . Para mostrar una lista de todos los eventos que se produjeron con un identificador de correlación determinado, puede escribir el identificador en la sección de **análisis** de la página de Resumen de IntelliTrace. En esa sección, puede elegir si se muestran solo los nombres de los eventos que se produjeron o los nombres de los eventos junto con su información de llamadas, como el nombre de función, los puntos de salida y de entrada, los parámetros y los valores devueltos.

Puede obtener eventos de Visual Studio en IntelliTrace eligiendo la tecla **F5** . Sin embargo, para obtener los eventos que son específicos de SharePoint, debe reunir los datos de IntelliTrace en las soluciones de SharePoint mediante Microsoft Monitoring Agent. Esta herramienta recopila datos de IntelliTrace y crea archivos *. iTrace* para las aplicaciones que se implementan fuera de Visual Studio. Para obtener más información, consulte [características de IntelliTrace](../debugger/intellitrace-features.md) y [uso del recopilador](../debugger/using-the-intellitrace-stand-alone-collector.md)independiente de IntelliTrace.

## <a name="unit-test"></a>Prueba unitaria
Puede encontrar más fácilmente los errores en el código si realiza pruebas unitarias, en las que el código de prueba se escribe y ejecuta en los métodos de prueba. Estos métodos contienen variables vacías y una instrucción Assert que puede usar para comprobar la lógica y funcionalidad del proyecto basándose en el modelo de objetos de SharePoint. Para obtener más información, vea [Haga una prueba unitaria de su código](../test/unit-test-your-code.md).

### <a name="support-for-microsoft-fakes-framework"></a>Compatibilidad con Microsoft Falsification Framework
Los proyectos de SharePoint admiten Microsoft Fakes, un marco de aislamiento en el que se pueden crear códigos auxiliares basados en el delegado y en correcciones de compatibilidad (shim) en las aplicaciones basadas en .NET Framework. Utilizando el marco Fakes, puede crear, mantener e insertar implementaciones ficticias en las pruebas unitarias. Estos códigos auxiliares y shims aíslan las pruebas unitarias del entorno. Puede crear códigos auxiliares para probar código que utiliza interfaces o clases no selladas con métodos reemplazables. Puede crear shims para redirigir llamadas codificadas para clases selladas con métodos estáticos o que no se pueden reemplazar a una implementación alternativa de shim. También puede usar delegados con tipos de código auxiliar y tipos de shim para personalizar dinámicamente el comportamiento de los miembros individuales del código auxiliar. Para obtener más información, vea [aislar el código sometido a prueba con](../test/isolating-code-under-test-with-microsoft-fakes.md)las emulaciones de Microsoft.

## <a name="related-articles"></a>Artículos relacionados

|Title|Descripción|
|-----------|-----------------|
|[IntelliTrace](../debugger/intellitrace.md)|Describe cómo depurar soluciones de Visual Studio más fácilmente mediante IntelliTrace.|
|[Tutorial: depurar una aplicación de SharePoint mediante IntelliTrace](../sharepoint/walkthrough-debugging-a-sharepoint-application-by-using-intellitrace.md)|Muestra cómo buscar los errores de codificación en un proyecto de SharePoint mediante IntelliTrace.|
|[Prueba unitaria del código](../test/unit-test-your-code.md)|Describe cómo buscar errores lógicos en el código mediante pruebas unitarias.|

## <a name="see-also"></a>Vea también

- [Mejorar la calidad del código](../test/improve-code-quality.md)