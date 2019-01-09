---
title: Creación de un complemento de grabación para pruebas de rendimiento web
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- Web performance tests, recorder plug-in
ms.assetid: 6fe13be1-aeb5-4927-9bff-35950e194da9
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.openlocfilehash: d047298a263e707c2f4e09475d2f6510a586a4f2
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53945826"
---
# <a name="how-to-create-a-recorder-plug-in"></a>Procedimiento Crear un complemento de grabadora

<xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRecorderPlugin> permite modificar una prueba de rendimiento web grabada. La modificación se produce después de hacer clic en **Detener** en la barra de herramientas de la **grabadora de pruebas de rendimiento web**, pero antes de que la prueba se guarde y se presente en el Editor de pruebas de rendimiento web.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Un complemento de grabación permite realizar una correlación personalizada sobre parámetros dinámicos. Con la funcionalidad de correlación integrada, las pruebas de rendimiento web detectan los parámetros dinámicos de la grabación web al finalizar o cuando se usa **Promover parámetros dinámicos a parámetros de pruebas web** en la barra de herramientas del **Editor de pruebas de rendimiento web**. Sin embargo, la funcionalidad de detección integrada no encuentra siempre todos los parámetros dinámicos. Por ejemplo, no encuentra un id. de sesión, que normalmente obtiene su valor cambiado entre 5 y 30 minutos. Por tanto, tiene que realizar el proceso de correlación manualmente.

<xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRecorderPlugin> le permite escribir código para su propio complemento personalizado. Este complemento puede realizar la correlación o modificar la prueba de rendimiento web de muchas maneras antes de que se guarde y presente en el Editor de pruebas de rendimiento web. Por tanto, si determina que hay que correlacionar una variable dinámica concreta para muchas de sus grabaciones, puede automatizar el proceso.

Un complemento de grabadora también se puede usar para muchos otros fines, como agregar reglas de extracción y validación, agregar parámetros de contexto o convertir comentarios en transacciones en una prueba de rendimiento web.

En los procedimientos siguientes se describe cómo crear el código rudimentario para un complemento de grabadora, implementar el complemento y ejecutarlo. En el código de ejemplo que sigue a los procedimientos se muestra cómo usar Visual C# con el fin de crear un complemento de grabadora para la correlación personalizada de parámetros dinámicos.

## <a name="create-a-recorder-plug-in"></a>Crear un complemento de grabadora

### <a name="to-create-a-recorder-plug-in"></a>Para crear un complemento de grabadora

1.  Abra una solución que contenga el proyecto de prueba de carga y rendimiento web con la prueba de rendimiento web para la que desee crear un complemento de grabadora.

2.  En el **Explorador de soluciones**, haga clic con el botón derecho en la solución, seleccione **Agregar** y luego elija **Nuevo proyecto**.

     Aparecerá el cuadro de diálogo **Agregar nuevo proyecto**.

3.  En **Plantillas instaladas**, seleccione **Visual C#**.

4.  En la lista de plantillas, seleccione **Biblioteca de clases**.

5.  En el cuadro de texto **Nombre**, escriba un nombre para el complemento de grabación.

     La biblioteca de clases se agrega al **Explorador de soluciones** y la nueva clase se abre en el **Editor de código**.

6.  En el **Explorador de soluciones**, en la carpeta de proyecto de la nueva biblioteca de clases, haga clic con el botón derecho en la carpeta **Referencias** y seleccione **Agregar referencia**.

    > [!TIP]
    > Un ejemplo de carpeta de proyecto de nueva biblioteca de clases es **RecorderPlugins**.

     Aparecerá el cuadro de diálogo **Agregar referencia**.

7.  Seleccione la pestaña **.NET**.

8.  Desplácese hacia abajo, seleccione **Microsoft.VisualStudio.QualityTools.WebTestFramework** y, luego, elija **Aceptar**.

     **Microsoft.VisualStudio.QualityTools.WebTestFramework** se agrega a la carpeta **Referencias** del **Explorador de soluciones**.

9. Escriba el código del complemento de grabadora. En primer lugar, cree una clase pública derivada de <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRecorderPlugin>.

10. Invalide el método <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRecorderPlugin.PostWebTestRecording*> .

    ```csharp
    public class Class1 : WebTestRecorderPlugin
        {
            public override void PostWebTestRecording(object sender, PostWebTestRecordingEventArgs e)
            {
                base.PostWebTestRecording(sender, e);
            }
        }
    ```

     Los argumentos de evento le darán dos objetos con los que trabajar: el resultado grabado y la prueba de rendimiento web grabada. Esto le permitirá recorrer en iteración el resultado en busca de ciertos valores y, a continuación, ir a la misma solicitud en la prueba de rendimiento web para realizar modificaciones. También puede modificar simplemente la prueba de rendimiento web si desea agregar un parámetro de contexto o parametrizar partes de la dirección URL.

    > [!NOTE]
    > Si modifica la prueba de rendimiento web, también necesitará establecer la propiedad <xref:Microsoft.VisualStudio.TestTools.WebTesting.PostWebTestRecordingEventArgs.RecordedWebTestModified*> en true: `e.RecordedWebTestModified = true;`

11. Agregue más código según lo que desee que el complemento de grabadora ejecute después de que se produzca la grabación web. Por ejemplo, puede agregar código para administrar la correlación personalizada como se muestra en el ejemplo siguiente. También puede crear un complemento de grabadora para tareas como convertir comentarios en transacciones o agregar reglas de validación a la prueba de rendimiento web.

12. En el menú **Compilar**, elija **Compilar \<nombre de proyecto de biblioteca de clases>**.

13. Después, debe implementar el complemento de grabadora para que se registre con Visual Studio.

### <a name="deploy-the-recorder-plug-in"></a>Implementar el complemento de grabadora

Después de compilar el complemento de grabadora, coloque el archivo DLL resultante en una de estas dos ubicaciones:

- *%ProgramFiles(x86)%\Microsoft Visual Studio\\[versión]\\[edición]\Common7\IDE\PrivateAssemblies\WebTestPlugins*

- *%USERPROFILE%\Documents\Visual Studio [versión]\WebTestPlugins*

> [!WARNING]
> Después de copiar el complemento de grabadora a una de las dos ubicaciones, debe reiniciar Visual Studio para que el complemento de grabadora se registre.

### <a name="to-execute-the-recorder-plug-in"></a>Para ejecutar el complemento de grabadora

1.  Cree una nueva prueba de rendimiento web.

     Aparecerá el cuadro de diálogo **Habilitar WebTestRecordPlugins**.

2.  Active la casilla correspondiente al complemento de grabadora y haga clic en **Aceptar**.

     Una vez que la prueba de rendimiento web complete la grabación, se ejecutará el nuevo complemento de grabadora.

    > [!WARNING]
    > Puede obtener un error similar al siguiente al ejecutar una prueba de rendimiento web o una prueba de carga que use su complemento:
    >
    > **Error en la solicitud: Excepción en el evento \<complemento>: no se pudo cargar el archivo o ensamblado "\<archivo "nombre_de_complemento".dll>, Version=\<n.n.n.n>, Culture=neutral, PublicKeyToken=null" o una de sus dependencias. El sistema no puede encontrar el archivo especificado.**
    >
    > Esto ocurre si realiza cambios en el código de cualquier complemento y crea una nueva versión de DLL **(Version=0.0.0.0)**, pero el complemento sigue haciendo referencia a la versión original del complemento. Para corregir este problema, siga estos pasos:
    >
    > 1. En el proyecto de prueba de carga y rendimiento web, aparecerá una advertencia en las referencias. Quite y vuelva a agregar la referencia al archivo DLL del complemento.
    > 2. Quite el complemento de la prueba o de la ubicación apropiada y, a continuación, agréguelo de nuevo.

## <a name="example"></a>Ejemplo

En este ejemplo se muestra cómo crear un complemento de grabadora personalizado de prueba de rendimiento web para realizar una correlación personalizada de parámetros dinámicos.

> [!NOTE]
> Al final de este tema se muestra una lista completa del código de ejemplo.

**Revisión del código de ejemplo**

## <a name="iterate-through-the-result-to-find-first-page-with-reportsession"></a>Recorrer en iteración el resultado para encontrar la primera página con ReportSession

En esta parte del ejemplo de código se recorre en iteración cada objeto grabado y se busca el cuerpo de la respuesta para ReportSession.

```csharp
foreach (WebTestResultUnit unit in e.RecordedWebTestResult.Children)
 {
     WebTestResultPage page = unit as WebTestResultPage;
     if (page != null)
     {
         if (!foundId)
         {
             int indexOfReportSession = page.RequestResult.Response.BodyString.IndexOf("ReportSession");
             if (indexOfReportSession > -1)
             {
```

## <a name="add-an-extraction-rule"></a>Agregar una regla de extracción

Ahora que se ha encontrado una respuesta, necesita agregar una regla de extracción. En esta parte del ejemplo de código se crea la regla de extracción mediante la clase <xref:Microsoft.VisualStudio.TestTools.WebTesting.ExtractionRuleReference> y, a continuación, se busca la solicitud correcta de la prueba de rendimiento web a la que se va a agregar la regla de extracción. A cada objeto de resultado se le ha agregado una nueva propiedad denominada DeclarativeWebTestItemId que se usa en el código para obtener la solicitud correcta de la prueba de rendimiento web.

```csharp
ExtractionRuleReference ruleReference = new ExtractionRuleReference();
     ruleReference.Type = typeof(ExtractText);
     ruleReference.ContextParameterName = "SessionId";
     ruleReference.Properties.Add(new PluginOrRuleProperty("EndsWith", "&ControlID="));
     ruleReference.Properties.Add(new PluginOrRuleProperty("HtmlDecode", "True"));
     ruleReference.Properties.Add(new PluginOrRuleProperty("IgnoreCase", "True"));
     ruleReference.Properties.Add(new PluginOrRuleProperty("Index", "0"));
     ruleReference.Properties.Add(new PluginOrRuleProperty("Required", "True"));
     ruleReference.Properties.Add(new PluginOrRuleProperty("StartsWith", "ReportSession="));
     ruleReference.Properties.Add(new PluginOrRuleProperty("UseRegularExpression", "False"));

     WebTestRequest requestInWebTest = e.RecordedWebTest.GetItem(page.DeclarativeWebTestItemId) as WebTestRequest;
     if (requestInWebTest != null)
     {
         requestInWebTest.ExtractionRuleReferences.Add(ruleReference);
         e.RecordedWebTestModified = true;
     }
```

## <a name="replace-query-string-parameters"></a>Reemplazar parámetros de la cadena de consulta

Ahora el código busca todos los parámetros de cadena de consulta que tienen ReportSession como nombre y cambia el valor a {{SessionId}} como se muestra en esta parte del ejemplo de código:

```csharp
WebTestRequest requestInWebTest = e.RecordedWebTest.GetItem(page.DeclarativeWebTestItemId) as WebTestRequest;
if (requestInWebTest != null)
{
    foreach (QueryStringParameter param in requestInWebTest.QueryStringParameters)
    {
         if (param.Name.Equals("ReportSession"))
         {
             param.Value = "{{SessionId}}";
         }
     }
 }
```

```csharp
using System.ComponentModel;
using Microsoft.VisualStudio.TestTools.WebTesting;
using Microsoft.VisualStudio.TestTools.WebTesting.Rules;

namespace RecorderPlugin
{
    [DisplayName("Correlate ReportSession")]
    [Description("Adds extraction rule for Report Session and binds this to querystring parameters that use ReportSession")]
    public class CorrelateSessionId : WebTestRecorderPlugin
    {
        public override void PostWebTestRecording(object sender, PostWebTestRecordingEventArgs e)
        {
            //first find the session id
            bool foundId = false;
            foreach (WebTestResultUnit unit in e.RecordedWebTestResult.Children)
            {
                WebTestResultPage page = unit as WebTestResultPage;
                if (page != null)
                {
                    if (!foundId)
                    {
                        int indexOfReportSession = page.RequestResult.Response.BodyString.IndexOf("ReportSession");
                        if (indexOfReportSession > -1)
                        {
                            //add an extraction rule to this request
                            // Get the corresponding request in the Declarative Web performance test
                            ExtractionRuleReference ruleReference = new ExtractionRuleReference();

                            ruleReference.Type = typeof(ExtractText);
                            ruleReference.ContextParameterName = "SessionId";
                            ruleReference.Properties.Add(new PluginOrRuleProperty("EndsWith", "&ControlID="));
                            ruleReference.Properties.Add(new PluginOrRuleProperty("HtmlDecode", "True"));
                            ruleReference.Properties.Add(new PluginOrRuleProperty("IgnoreCase", "True"));
                            ruleReference.Properties.Add(new PluginOrRuleProperty("Index", "0"));
                            ruleReference.Properties.Add(new PluginOrRuleProperty("Required", "True"));
                            ruleReference.Properties.Add(new PluginOrRuleProperty("StartsWith", "ReportSession="));
                            ruleReference.Properties.Add(new PluginOrRuleProperty("UseRegularExpression", "False"));

                            WebTestRequest requestInWebTest = e.RecordedWebTest.GetItem(page.DeclarativeWebTestItemId) as WebTestRequest;
                            if (requestInWebTest != null)
                            {
                                requestInWebTest.ExtractionRuleReferences.Add(ruleReference);
                                e.RecordedWebTestModified = true;
                            }
                            foundId = true;

                        }
                    }
                    else
                    {
                        //now update query string parameters
                        WebTestRequest requestInWebTest = e.RecordedWebTest.GetItem(page.DeclarativeWebTestItemId) as WebTestRequest;
                        if (requestInWebTest != null)
                        {
                            foreach (QueryStringParameter param in requestInWebTest.QueryStringParameters)
                            {
                                if (param.Name.Equals("ReportSession"))
                                {
                                    param.Value = "{{SessionId}}";
                                }
                            }
                        }
                    }
                }
            }
        }
    }
}
```

## <a name="see-also"></a>Vea también

- <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequestPlugin>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRecorderPlugin.PostWebTestRecording*>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.ExtractionRuleReference>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRecorderPlugin.PostWebTestRecording*>
- [Crear código y complementos personalizados para las pruebas de carga](../test/create-custom-code-and-plug-ins-for-load-tests.md)
- [Generar y ejecutar una prueba de rendimiento web codificada](../test/generate-and-run-a-coded-web-performance-test.md)