---
title: Pruebas de rendimiento web programadas
ms.date: 10/03/2016
ms.topic: conceptual
helpviewer_keywords:
- Web performance tests, walkthroughs
- Web performance tests, creating
- code, Web performance tests
- Web performance tests, coded
ms.assetid: 169e48f9-52fd-4d0b-83d9-54913bde506b
dev_langs:
- CSharp
- VB
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: f5c1a065d30f3925ba5c567d562d0138de8c5953
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2019
ms.locfileid: "57869281"
---
# <a name="generate-and-run-a-coded-web-performance-test"></a>Generar y ejecutar una prueba de rendimiento web codificada

Las pruebas de rendimiento web se graban al examinar la aplicación web. Las pruebas se incluyen en las pruebas de carga para medir el rendimiento de la aplicación web con la carga de varios usuarios. Una prueba de rendimiento web se puede convertir en un script basado en código que se puede editar y personalizar como cualquier otro código fuente. Por ejemplo, puede agregar construcciones de bucle y bifurcaciones.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="generate-a-coded-web-performance-test"></a>Generar una prueba de rendimiento web codificada

1.  Si no ha creado una prueba de rendimiento web, vea [Grabar una prueba de rendimiento web](/azure/devops/test/load-test/run-performance-tests-app-before-release#create-a-web-performance-and-load-test-project).

2.  Genere la prueba codificada.

     ![Generar una prueba de rendimiento web codificada](../test/media/web_test_coded_generate.png)

3.  Asigne un nombre a la prueba.

     ![Escribir un nombre para la prueba de rendimiento web codificada](../test/media/web_test_coded_generate_nametest.png)

     La nueva prueba codificada se abre en el editor de código.

     Según el rendimiento web y la plantilla de proyecto de prueba de carga que agregó a la solución, el código se generará en Visual Basic o en Visual C#.

     ![La nueva prueba codificada se abre en el editor de código](../test/media/web_test_coded_generate_opencodeeditor.png)

     Puede ver en el código que el método GetRequestEnumerator() de C# o el método Run() de Visual Basic contienen todas las reglas de validación y las solicitudes web que estaban en la prueba recodificada.

4.  Para ver cómo se agrega un código sencillo, desplácese hacia abajo hasta el final del método y, después del código de la última solicitud web, agregue el siguiente código:

    ```c#
    if (DateTime.Today.DayOfWeek == DayOfWeek.Wednesday)
    {
        WebTestRequest customRequest = new WebTestRequest("http://weather.msn.com/");
        yield return customRequest;
    }
    else
    {
        WebTestRequest customRequest = new WebTestRequest("https://msdn.microsoft.com/");
        yield return customRequest;
    }
    ```

    ```vb
    If DateTime.Today.DayOfWeek = DayOfWeek.Wednesday Then
        Dim customRequest As WebTestRequest = New WebTestRequest("http://weather.msn.com/")
        MyBase.Send(customRequest)
    Else
        Dim customRequest As WebTestRequest = New WebTestRequest("https://msdn.microsoft.com/")
        MyBase.Send(customRequest)
    End If
    ```

5.  Compile la solución para comprobar que el código personalizado se compila.

6.  Ejecute la prueba.

     ![Ejecutar la prueba de rendimiento web codificada](../test/media/web_test_coded_generate_run.png)

     Y puesto que el día en que esto se ejecutó resultó ser un miércoles…

     ![Resultados de la prueba de rendimiento web codificada](../test/media/web_test_coded_generate_results.png)

## <a name="qa"></a>Preguntas y respuestas

### <a name="q-can-i-run-more-than-one-test-at-a-time"></a>P: ¿Se pueden ejecutar varias pruebas al mismo tiempo?
 **R:** Sí, use el menú contextual (botón derecho) en el **Explorador de soluciones**.

### <a name="q-should-i-add-a-data-source-before-or-after-i-generate-a-coded-test"></a>P: ¿Debo agregar un origen de datos antes o después de generar una prueba codificada?
 **R:** Es más fácil agregar un [origen de datos](../test/add-a-data-source-to-a-web-performance-test.md) antes de generar la prueba automatizada porque el código se generará de forma automática.

 Cuando ejecuta una prueba codificada con un origen de datos, puede aparecer el siguiente mensaje de error:

 **No se pudo ejecutar la prueba \<nombre de la prueba> en el agente \<nombre_equipo>: Referencia a objeto no establecida como instancia de un objeto.**

 Este error se puede producir porque ha definido DataSourceAttribute para la clase de prueba de rendimiento web sin su correspondiente DataBindingAttribute. Para resolver este error, agregue un atributo DataBindingAttribute adecuado, elimínelo o márquelo como comentario fuera del código.

### <a name="q-should-i-add-validation-and-extraction-rules-before-or-after-i-generate-a-coded-test"></a>P: ¿Debo agregar reglas de validación y de extracción antes o después de generar una prueba codificada?
 **R:** Es más fácil agregar reglas de validación y extracción antes de generar la prueba automatizada; pero se recomienda usar [pruebas automatizadas de IU](../test/use-ui-automation-to-test-your-code.md) para la validación.