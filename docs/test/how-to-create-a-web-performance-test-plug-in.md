---
title: Creación de un complemento de prueba de rendimiento web
description: Aprenda cómo los complementos de prueba de rendimiento web permiten reutilizar código fuera de las instrucciones declarativas principales de la prueba de rendimiento web.
ms.custom: SEO-VS-2020
ms.date: 10/03/2016
ms.topic: how-to
f1_keywords:
- vs.test.web.webtestplugin
helpviewer_keywords:
- Web performance tests, creating plug-ins
- plug-ins, creating in Web performance tests
ms.assetid: a612f2d2-9806-477d-a126-12842f07da6e
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: 758f57d3b934298ef397984b174fbf2c38d93d1b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99952556"
---
# <a name="how-to-create-a-web-performance-test-plug-in"></a>Procedimiento para crear un complemento de prueba de rendimiento web

Los complementos de pruebas de rendimiento web permiten aislar y reutilizar código fuera de las principales instrucciones declarativas de la prueba de rendimiento web. Un complemento de prueba de rendimiento web personalizado ofrece un modo de llamar a código cuando se ejecuta la prueba de rendimiento web. El complemento de prueba de rendimiento web se ejecuta una vez por cada iteración de la prueba. Además, si invalida los métodos PreRequest o PostRequest en el complemento de pruebas, esos complementos de solicitud se ejecutarán antes o después de cada solicitud, respectivamente.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Para crear un complemento de prueba de rendimiento web personalizado, derive su propia clase de la clase base <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestPlugin>.

Puede usar complementos de prueba de rendimiento web personalizados con las pruebas de rendimiento web que ha grabado, lo que le permitirá escribir una cantidad mínima de código para obtener un mayor nivel de control sobre las pruebas de rendimiento web. Sin embargo, también puede utilizarlos con pruebas de rendimiento web automatizadas. Para obtener más información, consulte [Cómo: Crear una prueba de rendimiento web codificada](../test/generate-and-run-a-coded-web-performance-test.md).

> [!NOTE]
> También puede crear complementos de pruebas de carga. Vea [Cómo: Crear un complemento de prueba de carga](../test/how-to-create-a-load-test-plug-in.md).

## <a name="to-create-a-custom-web-performance-test-plug-in"></a>Para crear un complemento de pruebas de rendimiento web personalizado

1. Abra un proyecto de prueba de carga y rendimiento web que contenga una prueba de rendimiento web.

2. En el **Explorador de soluciones**, haga clic con el botón derecho en la solución, seleccione **Agregar** y luego elija **Nuevo proyecto**.

3. Cree un proyecto de **Biblioteca de clases**.

   El nuevo proyecto de biblioteca de clases se agrega al **Explorador de soluciones** y la nueva clase aparece en el **Editor de código**.

4. En el **Explorador de soluciones**, haga clic con el botón derecho en la carpeta **Referencias** de la nueva biblioteca de clases y seleccione **Agregar referencia**.

   Aparecerá el cuadro de diálogo **Agregar referencia**.

5. Elija la pestaña **.NET**, desplácese hacia abajo y seleccione **Microsoft.VisualStudio.QualityTools.WebTestFramework**.

6. Elija **Aceptar**.

     La referencia a **Microsoft.VisualStudio.QualityTools.WebTestFramework** se agrega a la carpeta **Referencias** del **Explorador de soluciones**.

7. En el **Explorador de soluciones**, haga clic con el botón derecho en el nodo superior del proyecto de prueba de carga y rendimiento web que contiene la prueba de carga a la que quiere agregar el complemento de prueba de rendimiento web y seleccione **Agregar referencia**.

8. Aparecerá el cuadro de diálogo **Agregar referencia**.

9. Elija la pestaña **Proyectos** y seleccione el **proyecto de biblioteca de clases**.

10. Elija **Aceptar**.

11. En el **Editor de código**, escriba el código del complemento. En primer lugar, cree una clase pública derivada de <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestPlugin>.

12. Implemente el código dentro de uno o más controladores de eventos. Vea una implementación del ejemplo en la sección Ejemplo siguiente.

    - <xref:Microsoft.VisualStudio.TestTools.WebTesting.PostWebTestRecordingEventArgs>

    - <xref:Microsoft.VisualStudio.TestTools.WebTesting.PostWebTestEventArgs>

    - <xref:Microsoft.VisualStudio.TestTools.WebTesting.PreRequestEventArgs>

    - <xref:Microsoft.VisualStudio.TestTools.WebTesting.PostRequestEventArgs>

    - <xref:Microsoft.VisualStudio.TestTools.WebTesting.PrePageEventArgs>

    - <xref:Microsoft.VisualStudio.TestTools.WebTesting.PostPageEventArgs>

    - <xref:Microsoft.VisualStudio.TestTools.WebTesting.PreTransactionEventArgs>

    - <xref:Microsoft.VisualStudio.TestTools.WebTesting.PostTransactionEventArgs>

13. Cuando haya terminado de escribir el código, compile el nuevo proyecto.

14. Abra una prueba de rendimiento web.

15. Para agregar el complemento de prueba de rendimiento web, elija **Agregar complemento de prueba web** en la barra de herramientas.

     Aparecerá el cuadro de diálogo **Agregar complemento de prueba web**.

16. En **Seleccionar un complemento**, seleccione la clase de complemento de prueba de rendimiento web.

17. En el panel **Propiedades del complemento seleccionado**, establezca los valores iniciales que el complemento va a usar en tiempo de ejecución.

    > [!NOTE]
    > Puede exponer tantas propiedades de los complementos como desee; basta con hacerlas públicas, que se puedan establecer y que tengan un tipo base como Integer, Boolean o String. También puede cambiar las propiedades del complemento de prueba de rendimiento web más tarde en la ventana Propiedades.

18. Elija **Aceptar**.

     El complemento se agrega a la carpeta **Complementos de prueba web**.

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

El código siguiente crea un complemento de prueba de rendimiento web personalizado que agrega un elemento al objeto <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestContext> que representa la iteración de la prueba.

Después de ejecutar la prueba de rendimiento web, con este complemento puede ver el elemento agregado llamado **TestIteratnionNumber** en la pestaña **Contexto** del **Visor de resultados de rendimiento web**.

```csharp
using System;
using System.Collections.Generic;
using System.Text;
using System.ComponentModel;
using Microsoft.VisualStudio.TestTools.WebTesting;

namespace SampleRules
{
    [Description("This plugin can be used to set the ParseDependentsRequests property for each request")]
    public class SampleWebTestPlugin : WebTestPlugin
    {
        private bool m_parseDependents = true;

        public override void PreWebTest(object sender, PreWebTestEventArgs e)
        {
            // TODO: Add code to execute before the test.
        }

        public override void PostWebTest(object sender, PostWebTestEventArgs e)
        {
            // TODO: Add code to execute after the test.
        }

        public override void PreRequest(object sender, PreRequestEventArgs e)
        {
            // Code to execute before each request.
            // Set the ParseDependentsRequests value on the request
            e.Request.ParseDependentRequests = m_parseDependents;
        }

        // Properties for the plugin.
        [DefaultValue(true)]
        [Description("All requests will have their ParseDependentsRequests property set to this value")]
        public bool ParseDependents
        {
            get
            {
                return m_parseDependents;
            }
            set
            {
                m_parseDependents = value;
            }
        }
    }
}
```

## <a name="see-also"></a>Vea también

- <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequestPlugin>
- [Crear código y complementos personalizados para las pruebas de carga](../test/create-custom-code-and-plug-ins-for-load-tests.md)
- [Cómo: Crear un complemento de nivel de solicitud](../test/how-to-create-a-request-level-plug-in.md)
- [Codificación de una regla de extracción personalizada para una prueba de rendimiento web](../test/code-a-custom-extraction-rule-for-a-web-performance-test.md)
- [Codificación de una regla de validación personalizada para una prueba de rendimiento web](../test/code-a-custom-validation-rule-for-a-web-performance-test.md)
- [Cómo: Crear un complemento de prueba de carga](../test/how-to-create-a-load-test-plug-in.md)
- [Generar y ejecutar una prueba de rendimiento web codificada](../test/generate-and-run-a-coded-web-performance-test.md)
