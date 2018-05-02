---
title: Creación de un editor de datos personalizado para un adaptador de datos de diagnóstico en Visual Studio
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- Diagnostic Data Adapter, creating custom editor
ms.assetid: 24970227-d1ea-4f6d-9839-e911478848ba
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 6141defb2248cf79888b0ed94824a827bd36815f
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-create-a-custom-editor-for-data-for-your-diagnostic-data-adapter"></a>Cómo: Crear un editor personalizado para los datos del adaptador de datos de diagnóstico

Al crear un adaptador de datos de diagnóstico, es posible que quiera permitir que el usuario final configure datos específicos cuando seleccione el adaptador de datos de diagnóstico personalizado para su configuración de pruebas. Por ejemplo, puede seleccionar los datos de configuración que especifican qué claves del Registro se van a extraer, qué nivel de carga de red se debe simular o en que el directorio se deben buscar los archivos temporales o archivos de trabajo para adjuntar.

Debe usar un archivo de configuración para establecer los valores iniciales del adaptador de datos de diagnóstico. Puede proporcionar un editor personalizado para permitir al usuario modificar los datos de configuración.

Para crear su propio editor, tendrá que crear un control de usuario que implemente <xref:Microsoft.VisualStudio.TestTools.Execution.IDataCollectorConfigurationEditor>.

El adaptador de datos de diagnóstico puede utilizar un <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorConfigurationEditorAttribute> para especificar la clase de editor que desea utilizar para editar la configuración de datos de diagnóstico.

También se especifican los datos de configuración predeterminados que desea usar.  Vea [Proyecto de ejemplo para crear un adaptador de datos de diagnóstico](../test/sample-project-for-creating-a-diagnostic-data-adapter.md) para ver una configuración predeterminada de ejemplo.

Use el procedimiento siguiente para crear un editor personalizado para actualizar los datos de la configuración de pruebas cuando se use el adaptador de diagnóstico de datos personalizado.

> [!NOTE]
> Para crear un editor personalizado, primero debe crear un adaptador de datos de diagnóstico con el <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorConfigurationEditorAttribute> aplicado a la clase. Puede utilizar la propiedad opcional <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorConfigurationEditorAttribute.HelpUri*> en ese atributo para especificar el origen de contenido de ayuda para el editor. Para más información sobre cómo crear un adaptador de datos de diagnóstico, vea [Cómo: Crear un adaptador de datos de diagnóstico](../test/how-to-create-a-diagnostic-data-adapter.md).

Para obtener un ejemplo completo de un proyecto de adaptador de datos de diagnóstico, que incluye un editor de configuración personalizado, vea [Proyecto de ejemplo para crear un adaptador de datos de diagnóstico](../test/sample-project-for-creating-a-diagnostic-data-adapter.md).

## <a name="to-create-a-custom-editor-for-your-diagnostic-data-adapter"></a>Para crear un editor personalizado para su adaptador de datos de diagnóstico

1.  En el proyecto, cree un control de usuario para su adaptador de datos de diagnóstico:

    1.  Haga clic con el botón derecho en el proyecto de código que contiene la clase de adaptador de datos de diagnóstico, elija **Agregar** y, después, elija **Control de usuario**.

    2.  Para este ejemplo, agregue una etiqueta con este texto: **Nombre del archivo de datos:** y un cuadro de texto denominado **FileTextBox** que permitirá al usuario escribir los datos necesarios.

    > [!NOTE]
    > Actualmente solo se admiten controles de usuario de Windows Forms.

2.  Agregue estas líneas a la sección de declaración:

    ```csharp
    using System.Xml;
    using Microsoft.VisualStudio.TestTools.Common;
    using Microsoft.VisualStudio.TestTools.Execution;
    ```

3.  Cree este control de usuario en un editor personalizado.

    1.  En el proyecto de código, haga clic con el botón derecho en el control de usuario y elija **Ver código**.

    2.  Establezca la clase para implementar la interfaz del editor <xref:Microsoft.VisualStudio.TestTools.Execution.IDataCollectorConfigurationEditor> de la siguiente manera:

    ```csharp
    public partial class MyDataConfigEditor :
         UserControl, IDataCollectorConfigurationEditor
    ```

    1.  Haga clic con el botón derecho en <xref:Microsoft.VisualStudio.TestTools.Execution.IDataCollectorConfigurationEditor> en el código y seleccione el comando **Implementar interfaz**. Los métodos que necesita implementar en esta interfaz se agregan a la clase.

    2.  Agregue <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorConfigurationEditorAttribute> al control de usuario del editor para identificarlo como un editor de adaptador de datos de diagnóstico y reemplace **Compañía**, **Producto** y **Versión** por la información correspondiente al adaptador de datos de diagnóstico:

        ```csharp
        [DataCollectorConfigurationEditorTypeUri(
            "configurationeditor://MyCompany/MyConfigEditor/1.0")]
        ```

4.  Agregue dos variables privadas como sigue:

    ```csharp
    private DataCollectorSettings collectorSettings;
    private IServiceProvider ServiceProvider { get; set; }
    ```

5.  Agregue el código para inicializar el editor para el adaptador de datos de diagnóstico. Puede agregar valores predeterminados a los campos del control de usuario usando los datos de la variable de configuración. Estos datos son los que están en el elemento `<DefaultConfiguration>` del archivo de configuración XML del adaptador.

    ```csharp
    public void Initialize(
        IServiceProvider svcProvider,
        DataCollectorSettings settings)
    {
        ServiceProvider = svcProvider;
        collectorSettings = settings;

        // Display the default file name as listed in the settings file.
        this.SuspendLayout();
        this.FileTextBox.Text = getText(collectorSettings.Configuration);
        this.ResumeLayout();
    }
    ```

6.  Agregue el código para guardar los datos de los controles en el editor de nuevo con el formato XML requerido por la API del adaptador de datos de diagnóstico, de la siguiente manera:

    ```csharp
    public DataCollectorSettings SaveData()
    {
        collectorSettings.Configuration.InnerXml =
            String.Format(
    @"<MyCollectorName
        xmlns=""http://MyCompany/schemas/MyDiagnosticDataCollector/1.0"">
      <File FullPath=""{0}"" />
    </MyCollectorName>",
        FileTextBox.Text);
        return collectorSettings;
    }
    ```

7.  Si es importante para usted, agregue código para comprobar que los datos son correctos en el método `VerifyData`, o puede hacer que el método devuelva `true`.

    ```csharp
    public bool VerifyData()
    {
        // Not currently verifying data
        return true;
    }
    ```

8.  (Opcional) Puede agregar código para restablecer los datos a la configuración inicial que se proporciona en el archivo de configuración XML en el método `ResetToAgentDefaults()` que usa el método `getText()` privado.

    ```csharp
    // Reset to default value from XML configuration
    // using a custom getText() method
    public void ResetToAgentDefaults()
    {
        this.FileTextBox.Text = getText(collectorSettings.DefaultConfiguration);
    }

    // Local method to read the configuration settings
    private string getText(XmlElement element)
    {
        // Setup namespace manager with our namespace
        XmlNamespaceManager nsmgr =
            new XmlNamespaceManager(
                element.OwnerDocument.NameTable);

        // Find all the "File" elements under our configuration
        XmlNodeList files = element.SelectNodes("//ns:MyCollectorName/ns:File", nsmgr);

        string result = String.Empty;
        if (files.Count > 0)
        {
            XmlAttribute pathAttribute = files[0].Attributes["FullPath"];
            if (pathAttribute != null &&
                !String.IsNullOrEmpty(pathAttribute.Value))
            {
                result = pathAttribute.Value;
            }
        }

        return result;
    }
    ```

9. Compile la solución. Copie el ensamblado del adaptador de datos de diagnóstico y el archivo de configuración XML (`<diagnostic data adapter name>.dll.config`) en la siguiente ubicación, según su directorio de instalación: *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\PrivateAssemblies\DataCollectors*.

    > [!NOTE]
    > Aunque el editor de configuración se puede encontrar en un proyecto y un ensamblado diferentes del adaptador de datos de diagnóstico, también pueden estar en el mismo ensamblado.

10. Para usar el adaptador de datos de diagnóstico en las pruebas, debe seleccionarlo en la lista de configuraciones de pruebas existentes o crear uno nuevo con Microsoft Test Manager o Visual Studio y, seguidamente, seleccionarlo.

     El adaptador se muestra en la pestaña **Datos y diagnósticos** de la configuración de pruebas con el nombre descriptivo que se ha asignado a la clase.

11. Para configurar el adaptador de datos de diagnóstico para la configuración de pruebas, elija **Configurar** al lado del nombre del adaptador.

     Se muestra el editor personalizado.

12. Modifique los campos necesarios en el editor personalizado y, luego, elija **Guardar**.

13. Si va a ejecutar las pruebas en Microsoft Test Manager, antes de ello puede asignar esta configuración de pruebas al plan de pruebas o usar el comando **Ejecutar con opciones** para asignar e invalidar la configuración de pruebas. Para obtener más información sobre la configuración de pruebas, vea [Recopilar información de diagnóstico con la configuración de pruebas](../test/collect-diagnostic-information-using-test-settings.md).

14. Para poder utilizar el nuevo editor de configuración con un adaptador de datos de diagnóstico, debe aplicar <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorConfigurationEditorAttribute> a cada clase del adaptador de datos de diagnóstico con la que desee utilizar el editor, y volver a compilarla e instalarla en el equipo cliente. Para más información sobre cómo instalar adaptadores de datos de diagnóstico y editores de configuración, vea [Cómo: Instalar un adaptador de datos de diagnóstico personalizado](../test/how-to-install-a-custom-diagnostic-data-adapter.md).

15. Ejecute las pruebas usando la configuración de pruebas y con el adaptador de datos de diagnóstico seleccionado.

     El archivo de datos que especificó en el editor se adjunta a los resultados de pruebas.

 Para obtener más información sobre cómo establecer la configuración de pruebas para usar un entorno al ejecutar las pruebas, vea [Recopilar datos de diagnóstico durante las pruebas (VSTS)](/vsts/manual-test/collect-diagnostic-data) o [Recopilar datos de diagnóstico en pruebas manuales (VSTS)](/vsts/manual-test/mtm/collect-more-diagnostic-data-in-manual-tests).

## <a name="see-also"></a>Vea también

- <xref:Microsoft.VisualStudio.TestTools.Execution.IDataCollectorConfigurationEditor>
- <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorConfigurationEditorAttribute>
- <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorConfigurationEditorAttribute>
- [Crear un adaptador de datos de diagnóstico para recopilar datos personalizados o afectar a un equipo de prueba](../test/create-a-diagnostic-data-adapter-to-collect-custom-data-or-affect-a-test-machine.md)
- [Recopilar información de diagnóstico con la configuración de pruebas](../test/collect-diagnostic-information-using-test-settings.md)
- [Proyecto de ejemplo para crear un adaptador de datos de diagnóstico](../test/sample-project-for-creating-a-diagnostic-data-adapter.md)