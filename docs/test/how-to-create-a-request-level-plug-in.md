---
title: Creación de un complemento de nivel de solicitud (pruebas de rendimiento web)
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- request-level plug-in, creating
- Web performance tests, requests
ms.assetid: d0b5b23c-7e94-4637-be6c-2620a5442d46
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5f136214b787820396fdbcff37f9f3b78574e9c8
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2020
ms.locfileid: "90810277"
---
# <a name="how-to-create-a-request-level-plug-in"></a>Procedimiento para crear un complemento de nivel de solicitud

Las *solicitudes* son las instrucciones declarativas que constituyen las pruebas de rendimiento web. Los complementos de pruebas de rendimiento web permiten aislar y reutilizar código fuera de las principales instrucciones declarativas de la prueba de rendimiento web. Puede crear complementos y agregarlos a una solicitud individual, así como a la prueba de rendimiento web que la contiene. Un *complemento de solicitud* personalizado resulta útil para llamar al código cuando una determinada solicitud se ejecuta en una prueba de rendimiento web.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Cada complemento de solicitud de prueba de rendimiento web tiene un método PreRequest y un método PostRequest. Después de asociar un complemento de solicitud a una solicitud HTTP determinada, se desencadenará el evento PreRequest antes de que se emita la solicitud y se desencadenará PostRequest una vez recibida la respuesta.

Para crear un complemento de solicitud de prueba de rendimiento web personalizado, derive su propia clase de la clase base <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequestPlugin>.

Puede utilizar complementos de solicitud de prueba de rendimiento web personalizados con las pruebas de rendimiento web que haya grabado. Los complementos de solicitud de prueba de rendimiento web personalizados permiten, con una cantidad mínima de código, obtener mayor control sobre las pruebas de rendimiento web. Sin embargo, también puede utilizarlos con pruebas de rendimiento web automatizadas. Vea [Generar y ejecutar una prueba de rendimiento web codificada](../test/generate-and-run-a-coded-web-performance-test.md).

## <a name="to-create-a-request-level-plug-in"></a>Para crear un complemento de nivel de solicitud

1. En el **Explorador de soluciones**, haga clic con el botón derecho en la solución, seleccione **Agregar** y luego elija **Nuevo proyecto**.

2. Cree un proyecto de **Biblioteca de clases**.

3. En el **Explorador de soluciones**, haga clic con el botón derecho en la carpeta **Referencias** de la nueva biblioteca de clases y seleccione **Agregar referencia**.

     Aparecerá el cuadro de diálogo **Agregar referencia**.

4. Elija la pestaña **.NET**, desplácese hacia abajo, seleccione **Microsoft.VisualStudio.QualityTools.WebTestFramework** y, luego, elija **Aceptar**.

     La referencia a **Microsoft.VisualStudio.QualityTools.WebTestFramework** se agrega a la carpeta **Referencias** del **Explorador de soluciones**.

5. En el **Explorador de soluciones**, haga clic con el botón derecho en el nodo superior del proyecto de prueba de carga y rendimiento web que contiene la prueba de carga a la que quiere agregar el complemento de prueba de solicitud de prueba de rendimiento web. Seleccione **Agregar referencia**.

     Aparecerá el cuadro de diálogo **Agregar referencia**.

6. Elija la pestaña **Proyectos**, seleccione el **proyecto de biblioteca de clases** y luego haga clic en **Aceptar**.

7. En el **Editor de código**, escriba el código del complemento. En primer lugar, cree una clase pública derivada de <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequestPlugin>.

8. Implemente el código dentro de uno de los controladores de eventos <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequestPlugin.PreRequest*> y <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequestPlugin.PostRequest*> o en ambos. Vea una implementación del ejemplo en la sección Ejemplo siguiente.

9. Cuando haya terminado de escribir el código, compile el nuevo proyecto.

10. Abra la prueba de rendimiento web a la que desea agregar el complemento de solicitud.

11. Haga clic con el botón derecho en la solicitud a la que quiere agregar el complemento de solicitud y, luego, seleccione **Agregar complemento de solicitud**.

     Se muestra el cuadro de diálogo **Agregar complemento de solicitudes de prueba web**.

12. En **Seleccionar un complemento**, seleccione el nuevo complemento.

13. En el panel **Propiedades del complemento seleccionado**, establezca los valores iniciales que el complemento va a usar en tiempo de ejecución.

    > [!NOTE]
    > Puede exponer tantas propiedades de los complementos como desee; basta con hacerlas públicas, que se puedan establecer y que tengan un tipo base como Integer, Boolean o String. También puede cambiar las propiedades del complemento de prueba de rendimiento web más tarde en la ventana Propiedades.

14. Elija **Aceptar**.

     El complemento se agrega a la carpeta **Complementos de solicitud**, que es una carpeta secundaria de la solicitud HTTP.

    > [!WARNING]
    > Puede obtener un error similar al siguiente al ejecutar una prueba de rendimiento web o una prueba de carga que use su complemento:
    >
    > **Error en la solicitud: Excepción en el evento \<plug-in>: no se pudo cargar el archivo o el ensamblado "\<"Plug-in name".dll file>, Version=\<n.n.n.n>, Culture=neutral, PublicKeyToken=null" o una de sus dependencias. El sistema no puede encontrar el archivo especificado.**
    >
    > Esto ocurre si realiza cambios en el código de cualquier complemento y crea una nueva versión de DLL **(Version=0.0.0.0)** , pero el complemento sigue haciendo referencia a la versión original del complemento. Para corregir este problema, siga estos pasos:
    >
    > 1. En el proyecto de prueba de carga y rendimiento web, aparecerá una advertencia en las referencias. Quite y vuelva a agregar la referencia al archivo DLL del complemento.
    > 2. Quite el complemento de la prueba o de la ubicación apropiada y, a continuación, agréguelo de nuevo.

## <a name="example"></a>Ejemplo

Puede usar el código siguiente para crear un complemento personalizado de prueba de rendimiento web que muestre dos cuadros de diálogo. Un cuadro de diálogo muestra la dirección URL asociada a la solicitud a la que adjunta el complemento de solicitud. El segundo cuadro de diálogo muestra el nombre de equipo para el agente.

> [!NOTE]
> El siguiente código requiere que se agregue una referencia a System.Windows.Forms.

```csharp
using System;
using System.Collections.Generic;
using System.Windows.Forms;
using Microsoft.VisualStudio.TestTools.WebTesting;

namespace RequestPluginNamespace
{
    public class MyWebRequestPlugin : WebTestRequestPlugin
    {
        public override void PostRequest(object sender, PostRequestEventArgs e)
        {
            MessageBox.Show(e.WebTest.Context.AgentName);
        }
        public override void PreRequest(object sender, PreRequestEventArgs e)
        {
            MessageBox.Show(e.Request.Url);
        }
    }
}
```

## <a name="see-also"></a>Vea también

- <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequestPlugin>
- [Crear código y complementos personalizados para las pruebas de carga](../test/create-custom-code-and-plug-ins-for-load-tests.md)
- [Codificación de una regla de extracción personalizada para una prueba de rendimiento web](../test/code-a-custom-extraction-rule-for-a-web-performance-test.md)
- [Codificación de una regla de validación personalizada para una prueba de rendimiento web](../test/code-a-custom-validation-rule-for-a-web-performance-test.md)
- [Cómo: Crear un complemento de prueba de carga](../test/how-to-create-a-load-test-plug-in.md)
- [Generar y ejecutar una prueba de rendimiento web codificada](../test/generate-and-run-a-coded-web-performance-test.md)
