---
title: API de prueba de rendimiento web
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- Web performance tests, using the API
- APIs, Web performance tests
ms.assetid: 93a6a1dd-663b-4ab5-8760-7d6b081561d3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e869bc46997ffb6ebecae2aa3e49c3cb6b2582fa
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/18/2020
ms.locfileid: "75594349"
---
# <a name="how-to-use-the-web-performance-test-api"></a>Cómo: Usar la API de pruebas de rendimiento web

Puede escribir código para sus pruebas de rendimiento web. La API de prueba de rendimiento web se utiliza para crear pruebas de rendimiento web automatizadas, complementos de prueba de rendimiento web, complementos de solicitud, solicitudes, reglas de extracción y reglas de validación. Las clases que constituyen estos tipos son las clases principales de esta API. Los otros tipos contenidos en esta API se utilizan para permitir la creación de objetos <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTest>, <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestPlugin>, <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequestPlugin>, <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequest>, <xref:Microsoft.VisualStudio.TestTools.WebTesting.ExtractionRule> y <xref:Microsoft.VisualStudio.TestTools.WebTesting.ValidationRule>. El espacio de nombres <xref:Microsoft.VisualStudio.TestTools.WebTesting> sirve para crear pruebas de rendimiento web personalizadas.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

También puede utilizar la API de prueba de rendimiento web para crear y guardar pruebas de rendimiento web declarativas mediante programación. Para ello, utilice las clases <xref:Microsoft.VisualStudio.TestTools.WebTesting.DeclarativeWebTest> y <xref:Microsoft.VisualStudio.TestTools.WebTesting.DeclarativeWebTestSerializer>.

> [!TIP]
> El Examinador de objetos se usa para examinar el espacio de nombres <xref:Microsoft.VisualStudio.TestTools.WebTesting>. Los editores de Visual C# y de Visual Basic ofrecen compatibilidad con IntelliSense para codificar con las clases del espacio de nombres.

También se pueden crear complementos para pruebas de carga. Para obtener más información, vea [Cómo: Usar la API de pruebas de carga](../test/how-to-use-the-load-test-api.md) y [Cómo: Crear un complemento de pruebas de carga](../test/how-to-create-a-load-test-plug-in.md).

## <a name="to-use-the-webtesting-namespace"></a>Para usar el espacio de nombres WebTesting

1. Abra un proyecto de prueba de carga y rendimiento web que contenga una prueba de rendimiento web.

2. Agregue un proyecto de biblioteca de clases de Visual C# o Visual Basic a la solución de prueba.

3. Agregue una referencia en el proyecto de prueba de carga y rendimiento web para el proyecto de biblioteca de clases.

4. Agregue una referencia al archivo DLL Microsoft.VisualStudio.QualityTools.WebTestFramework en el proyecto de biblioteca de clases.

5. En el archivo de clase ubicado en el proyecto de biblioteca de clases, agregue una instrucción `using` para el espacio de nombres <xref:Microsoft.VisualStudio.TestTools.WebTesting>.

6. Cree una clase que implemente la interfaz <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestPlugin>.

7. Compile el proyecto.

8. Agregue el nuevo complemento de prueba de rendimiento web usando el Editor de pruebas de rendimiento web:

    1. Elija **Agregar complemento de prueba web** en la barra de herramientas.

         Aparecerá el cuadro de diálogo **Agregar complemento de prueba web**.

    2. En **Seleccionar un complemento**, seleccione la clase de complemento de prueba de rendimiento web.

    3. En el panel **Propiedades del complemento seleccionado**, establezca los valores iniciales que el complemento va a usar en tiempo de ejecución.

        > [!NOTE]
        > Puede exponer tantas propiedades de los complementos como desee; basta con hacerlas públicas, que se puedan establecer y que tengan un tipo base como Integer, Boolean o String. También puede editar las propiedades del complemento de prueba de rendimiento web más tarde en la ventana Propiedades.

    4. Elija **Aceptar**.

9. Ejecute su prueba de rendimiento web.

     Para obtener una implementación de ejemplo de <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestPlugin>, vea [Cómo: Crear un complemento de pruebas de rendimiento web](../test/how-to-create-a-web-performance-test-plug-in.md).

## <a name="see-also"></a>Vea también

- <xref:Microsoft.VisualStudio.TestTools.WebTesting>
- [Crear código y complementos personalizados para las pruebas de carga](../test/create-custom-code-and-plug-ins-for-load-tests.md)
- [Cómo: Usar la API de pruebas de carga](../test/how-to-use-the-load-test-api.md)
- [Cómo: Crear un complemento de pruebas de rendimiento web](../test/how-to-create-a-web-performance-test-plug-in.md)
