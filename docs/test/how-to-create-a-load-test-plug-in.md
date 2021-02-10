---
title: Creación de un complemento de prueba de carga
description: Aprenda a crear un complemento de prueba de carga que ejecute código en distintos momentos mientras se ejecuta dicha prueba de carga y que amplíe o modifique la funcionalidad de esta.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
f1_keywords:
- vs.test.load.loadtestplugin
helpviewer_keywords:
- code, load tests
- plug-ins, load test
- load tests, plug-ins
ms.assetid: 27806972-1b15-4388-833d-6d0632816f1f
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: f8ba810665bce520b82777512b396a693e580a0e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99878011"
---
# <a name="how-to-create-a-load-test-plug-in"></a>Procedimiento Crear un complemento de prueba de carga

Puede crear un complemento de prueba de carga para ejecutar el código en distintos momentos mientras se ejecuta la prueba de carga. Los complementos se crean para expandir o modificar la funcionalidad incorporada de la prueba de carga. Por ejemplo, puede programar un complemento de prueba de carga para establecer o modificar el modelo de prueba de carga mientras se ejecuta la prueba de carga. Para ello, cree una clase que hereda la interfaz <xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin>. Esta clase debe implementar el método <xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin.Initialize*> de esta interfaz. Para obtener más información, vea <xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin>.

> [!TIP]
> También se pueden crear complementos para pruebas de rendimiento web. Para obtener más información, vea [Cómo: Crear un complemento de prueba de rendimiento web](../test/how-to-create-a-web-performance-test-plug-in.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

<!-- markdownlint-disable MD003 MD020 -->
## <a name="to-create-a-load-test-plug-in-in-c"></a>Para crear un complemento de pruebas de carga de C#
<!-- markdownlint-enable MD003 MD020 -->

1. Abra un proyecto de prueba de carga y rendimiento web que contenga una prueba de rendimiento web.

2. Agregue una prueba de carga al proyecto de prueba y configúrela para la ejecución de una prueba de rendimiento web.

     Para obtener más información, vea [Inicio rápido: Creación de un proyecto de prueba de carga](../test/quickstart-create-a-load-test-project.md).

3. Agregue a la solución un nuevo proyecto **Biblioteca de clases**. (En el **Explorador de soluciones**, haga clic con el botón derecho en la solución, seleccione **Agregar** y luego elija **Nuevo proyecto**).

4. En el **Explorador de soluciones**, haga clic con el botón derecho en la carpeta **Referencias** de la nueva biblioteca de clases y seleccione **Agregar referencia**.

   Aparecerá el cuadro de diálogo **Agregar referencia**.

5. Elija la pestaña **.NET**, desplácese hacia abajo y, luego, seleccione **Microsoft.VisualStudio.QualityTools.LoadTestFramework**.

6. Elija **Aceptar**.

   La referencia a **Microsoft.VisualStudio.QualityTools.LoadTestFramework** se agrega a la carpeta **Referencias** del **Explorador de soluciones**.

7. En el **Explorador de soluciones**, haga clic con el botón derecho en el nodo superior del proyecto de prueba de carga y rendimiento web que contiene la prueba de carga a la que quiere agregar el complemento de prueba de carga y seleccione **Agregar referencia**.

   Aparecerá el cuadro de diálogo **Agregar referencia**.

8. Elija la pestaña **Proyectos** y seleccione el proyecto de biblioteca de clases.

9. Elija **Aceptar**.

10. En el **Editor de código**, agregue una instrucción `using` para el espacio de nombres <xref:Microsoft.VisualStudio.TestTools.LoadTesting>.

11. Implemente la interfaz <xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin> para la clase creada en el proyecto Biblioteca de clases. Vea una implementación del ejemplo en la sección Ejemplo siguiente.

12. Cuando haya terminado de escribir el código, compile el nuevo proyecto.

13. Haga clic con el botón derecho en el nodo superior de la prueba de carga y, luego, elija **Agregar complemento de prueba de carga**.

     Aparecerá el cuadro de diálogo **Agregar complemento de prueba de carga**.

14. En **Seleccionar un complemento**, seleccione la clase del complemento de prueba de carga.

15. En el panel **Propiedades del complemento seleccionado**, establezca los valores iniciales que el complemento va a usar en tiempo de ejecución.

    > [!NOTE]
    > Puede exponer tantas propiedades de los complementos como desee; basta con hacerlas públicas, que se puedan establecer y que tengan un tipo base como Integer, Boolean o String. También puede cambiar las propiedades del complemento de prueba de rendimiento web más tarde en la ventana **Propiedades**.

16. Elija **Aceptar**.

     El complemento se agrega a la carpeta **Complementos de prueba de carga**.

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

El código siguiente muestra un complemento de prueba de carga que ejecuta código personalizado después de que se produzca un evento LoadTestFinished. Si este código se ejecuta en un agente de una máquina remota y el agente de prueba no tienen un servicio SMTP de host local, la prueba de carga permanecerá en el estado "En curso" mientras se abre un cuadro de mensaje.

> [!NOTE]
> El siguiente código requiere que se agregue una referencia a System.Windows.Forms.

```csharp
using System;
using Microsoft.VisualStudio.TestTools.LoadTesting;
using System.Net.Mail;
using System.Windows.Forms;

namespace LoadTestPluginTest
{
    public class MyLoadTestPlugin : ILoadTestPlugin
    {
        LoadTest myLoadTest;

        public void Initialize(LoadTest loadTest)
        {
            myLoadTest = loadTest;
            myLoadTest.LoadTestFinished += new
                EventHandler(myLoadTest_LoadTestFinished);
        }

        void myLoadTest_LoadTestFinished(object sender, EventArgs e)
        {
            try
            {
                // place custom code here
                MailAddress MyAddress = new MailAddress("someone@example.com");
                MailMessage MyMail = new MailMessage(MyAddress, MyAddress);
                MyMail.Subject = "Load Test Finished -- Admin Email";
                MyMail.Body = myLoadTest..Name + " has finished.";

                SmtpClient MySmtpClient = new SmtpClient("localhost");
                MySmtpClient.Send(MyMail);
            }

            catch (SmtpException ex)
            {
                MessageBox.Show(ex.InnerException.Message +
                    ".\r\nMake sure you have a valid SMTP.", "LoadTestPlugin", MessageBoxButtons.OK, MessageBoxIcon.Warning, MessageBoxDefaultButton.Button1);
            }
        }
    }
}
```

Hay ocho eventos asociados a una prueba de carga, que pueden controlarse en el complemento de prueba de carga para que ejecuten código personalizado con la prueba. A continuación se muestra una lista de los eventos que proporcionan acceso a los distintos períodos de la ejecución de la prueba de carga:

- <xref:Microsoft.VisualStudio.TestTools.LoadTesting.LoadTest.LoadTestStarting>

- <xref:Microsoft.VisualStudio.TestTools.LoadTesting.LoadTest.LoadTestFinished>

- <xref:Microsoft.VisualStudio.TestTools.LoadTesting.LoadTest.LoadTestWarmupComplete>

- <xref:Microsoft.VisualStudio.TestTools.LoadTesting.LoadTest.TestStarting>

- <xref:Microsoft.VisualStudio.TestTools.LoadTesting.LoadTest.TestFinished>

- <xref:Microsoft.VisualStudio.TestTools.LoadTesting.LoadTest.ThresholdExceeded>

- <xref:Microsoft.VisualStudio.TestTools.LoadTesting.LoadTest.Heartbeat>

- <xref:Microsoft.VisualStudio.TestTools.LoadTesting.LoadTest.LoadTestAborted>

## <a name="see-also"></a>Vea también

- <xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin>
- [Crear código y complementos personalizados para las pruebas de carga](../test/create-custom-code-and-plug-ins-for-load-tests.md)
- [Cómo: Crear un complemento de prueba de rendimiento web](../test/how-to-create-a-web-performance-test-plug-in.md)
