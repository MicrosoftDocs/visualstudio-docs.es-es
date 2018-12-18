---
title: Creación de código y complementos personalizados para las pruebas de carga en Visual Studio
ms.date: 10/19/2016
ms.topic: conceptual
f1_keywords:
- vs.test.dialog.recorderplugin
helpviewer_keywords:
- Web performance tests, plug-ins
- load tests, plug-ins
ms.assetid: 0c0fcc99-673b-4ea0-a268-0475f66e5cb6
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: ed7b588d597626348b4c148c10dad165649b0468
ms.sourcegitcommit: ae46be4a2b2b63da7e7049e9ed67cd80897c8102
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2018
ms.locfileid: "52895761"
---
# <a name="create-custom-code-and-plug-ins-for-load-tests"></a>Crear código y complementos personalizados para las pruebas de carga

Un complemento personalizado usa código que se escribe y adjunta a una prueba de carga o una prueba de rendimiento web. Puede utilizar la API de prueba de carga y la API de prueba de rendimiento web para crear complementos personalizados para que las pruebas se expandan a la funcionalidad integrada. Puede agregar varios complementos a la prueba de carga.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="tasks"></a>Tareas

|Tareas|Temas relacionados|
|-|-----------------------|
|**Crear un complemento personalizado para la prueba de carga**: puede utilizar la API de prueba de carga para crear un complemento personalizado y agregar mayor funcionalidad a la prueba de carga.|-   [Cómo: Utilizar la API de pruebas de carga](../test/how-to-use-the-load-test-api.md)<br />-   [Cómo: Crear un complemento de pruebas de carga](../test/how-to-create-a-load-test-plug-in.md)|
|**Crear un complemento personalizado para la prueba de rendimiento web:** puede utilizar la API de rendimiento web para crear un complemento personalizado y agregar mayor funcionalidad de prueba a la prueba de rendimiento web, incluso en el nivel de solicitud. También puede crear una prueba de servicio web.<br /><br /> Además, puede crear un complemento de grabadora web que puede modificar una prueba de rendimiento web una vez grabada, pero antes de aparecer en el Visor de resultados de pruebas de rendimiento web.|-   [Cómo: Usar la API de prueba de rendimiento web](../test/how-to-use-the-web-performance-test-api.md)<br />-   [Cómo: Crear un complemento de prueba de rendimiento web](../test/how-to-create-a-web-performance-test-plug-in.md)<br />-   [Cómo: Crear un complemento de nivel de solicitud](../test/how-to-create-a-request-level-plug-in.md)<br />-   [Cómo: Crear una prueba de servicios web](../test/how-to-create-a-web-service-test.md)<br />-   [Cómo: Crear un complemento de grabación](../test/how-to-create-a-recorder-plug-in.md)|
|**Agregar características de UI al Visor de resultados de pruebas de rendimiento web:** puede agregar más características de UI usando un complemento de Visual Studio.|-   [Cómo: Crear un complemento de Visual Studio para el visor de resultados de pruebas de rendimiento web](../test/how-to-create-an-add-in-for-the-web-performance-test-results-viewer.md)|
|**Crear un editor del cuerpo HTTP personalizado:** puede crear un editor personalizado para modificar las respuestas de binarios o de cadenas http XML de un servicio web.|-   [Cómo: Crear un editor de cuerpo HTTP personalizado para el Editor de prueba de rendimiento web](../test/how-to-create-a-custom-http-body-editor-for-the-web-performance-test-editor.md)|

## <a name="reference"></a>Referencia

<xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestPlugin>

<xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequestPlugin>

<xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin>

<xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRecorderPlugin>

<xref:Microsoft.VisualStudio.TestTools.LoadTesting>

## <a name="see-also"></a>Vea también

- [Analizar los resultados de pruebas de carga](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Generar y ejecutar una prueba de rendimiento web codificada](../test/generate-and-run-a-coded-web-performance-test.md)