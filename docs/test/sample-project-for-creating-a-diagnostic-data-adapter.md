---
title: Proyecto de ejemplo para crear un adaptador de datos de diagnóstico en Visual Studio
ms.date: 10/19/2016
ms.topic: sample
helpviewer_keywords:
- Diagnostic Data Adapter [Visual Studio ALM]
- samples. Diagnostic Data Adapter [Visual Studio ALM]
- Diagnostic Data Adapter, sample
ms.assetid: 548bdc5e-338f-4be7-a555-e6a2efb1df6b
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 1de27441ea5d0a6af320c031e43affd2c2e14be0
ms.sourcegitcommit: 495bba1d8029646653f99ad20df2f80faad8d58b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/31/2018
ms.locfileid: "39380775"
---
# <a name="sample-project-for-creating-a-diagnostic-data-adapter"></a>Proyecto de ejemplo para crear un adaptador de datos de diagnóstico

"MyDiagnosticDataAdapter" es un adaptador de datos de diagnóstico simple que puede adjuntar un archivo de registro a los resultados de pruebas cuando se hagan las pruebas.

 Necesitará permisos administrativos en cualquier máquina en la que se instale el recopilador de datos de diagnóstico o editor de configuración.

## <a name="example-data-adapter"></a>Adaptador de datos de ejemplo

En este ejemplo se muestra cómo realizar las tareas siguientes:

-   Aplicar atributos para que Microsoft Test Manager reconozca una clase como un adaptador de datos de diagnóstico.

-   Aplicar atributos para que Microsoft Test Manager reconozca una clase de control de usuario como un editor y la use para cambiar la configuración de un adaptador de datos de diagnóstico.

-   Obtener acceso a los datos de configuración predeterminados.

-   Registrar eventos de recolección de datos de diagnóstico específicos.

-   Adjuntar el archivo de registro enviándolo a <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionSink>.

```csharp
// My Data Collector Class
using Microsoft.VisualStudio.TestTools.Common;
using Microsoft.VisualStudio.TestTools.Execution;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Xml;
using System;

namespace MyCompany.MyDiagnosticDataAdapters
{
    // Provide a URI and friendly name for your diagnostic data adapter
    [DataCollectorTypeUri("datacollector://MyCompany/MyDataCollector/1.0")]
    [DataCollectorFriendlyName("Collect Log Files sample", false)]
    // Designate your chosen configuration editor
    [DataCollectorConfigurationEditor(
        "configurationeditor://MyCompany/MyDataConfigEditor/1.0")]
    public class MyDataCollector : DataCollector
    {
        private DataCollectionEvents dataEvents;
        private DataCollectionLogger dataLogger;
        private DataCollectionSink dataSink;
        private XmlElement configurationSettings;

        // Required method called by the testing framework
        public override void Initialize(
            XmlElement configurationElement,
            DataCollectionEvents events,
            DataCollectionSink sink,
            DataCollectionLogger logger,
            DataCollectionEnvironmentContext environmentContext)
        {
            dataEvents = events; // The test events
            dataLogger = logger; // The error and warning log
            dataSink = sink;     // Saves collected data
            // Configuration from the test settings
            configurationSettings = configurationElement;

            // Register common events for the data collector
            // Not all of the events are used in this class
            dataEvents.SessionStart +=
                new EventHandler<SessionStartEventArgs>(OnSessionStart);
            dataEvents.SessionEnd +=
                new EventHandler<SessionEndEventArgs>(OnSessionEnd);
            dataEvents.TestCaseStart +=
                new EventHandler<TestCaseStartEventArgs>(OnTestCaseStart);
            dataEvents.TestCaseEnd +=
                new EventHandler<TestCaseEndEventArgs>(OnTestCaseEnd);
            dataEvents.DataRequest +=
                new EventHandler<DataRequestEventArgs>(OnDataRequest);
        }

        protected override void Dispose(bool disposing)
        {
            if (disposing)
            {
                dataEvents.SessionStart -=
                    new EventHandler<SessionStartEventArgs>(OnSessionStart);
                dataEvents.SessionEnd -=
                    new EventHandler<SessionEndEventArgs>(OnSessionEnd);
                dataEvents.TestCaseStart -=
                    new EventHandler<TestCaseStartEventArgs>(OnTestCaseStart);
                dataEvents.TestCaseEnd -=
                    new EventHandler<TestCaseEndEventArgs>(OnTestCaseEnd);
                dataEvents.DataRequest -=
                    new EventHandler<DataRequestEventArgs>(OnDataRequest);
            }
        }

        #region Event Handlers
        public void OnSessionStart(object sender, SessionStartEventArgs e)
        {
            // TODO: Provide implementation
        }

        public void OnSessionEnd(object sender, SessionEndEventArgs e)
        {
            // TODO: Provide implementation
        }

        public void OnTestCaseStart(object sender, TestCaseEventArgs e)
        {
            // TODO: Provide implementation
        }

        public void OnTestCaseEnd(object sender, TestCaseEndEventArgs e)
        {
            // Get any files to be collected that are
            // configured in your test settings
            List<string> files = getFilesToCollect();

            // For each of the files, send the file to the data sink
            // which will attach it to the test results or to a bug
            foreach (string file in files)
            {
                dataSink.SendFileAsync(e.Context, file, false);
            }
        }

        public void OnDataRequest(object sender, DataRequestEventArgs e)
        {
            // TODO: Provide implementation
            // Most likely this occurs because a bug is being filed
        }
        #endregion

        // A private method to collect the configured file names
        private List<string> getFilesToCollect()
        {
            // Seetup namespace manager with our namespace
            XmlNamespaceManager nsmgr =
                new XmlNamespaceManager(
                    configurationSettings.OwnerDocument.NameTable);
            nsmgr.AddNamespace("ns",
                "http://MyCompany/schemas/MyDataCollector/1.0");

            // Find all of the "File" elements under our configuration
            XmlNodeList files =
                configurationSettings.SelectNodes(
                    "//ns:MyDataCollector/ns:File");

            // Build the list of files to collect from the
            // "FullPath" attributes of the "File" nodes.
            List<string> result = new List<string>();
            foreach (XmlNode fileNode in files)
            {
                XmlAttribute pathAttribute =
                    fileNode.Attributes["FullPath"];
                if (pathAttribute != null &&
                    !String.IsNullOrEmpty(pathAttribute.Value))
                {
                    result.Add(pathAttribute.Value);
                }
            }

            return result;
        }
    }
}
```

## <a name="example-configuration-editor"></a>Editor de configuración de ejemplo

Se trata de un editor de configuración de ejemplo para el adaptador de datos de diagnóstico. Agregue un control de usuario al proyecto y cree un formulario muy sencillo con la etiqueta ("Nombre de archivo de registro" y un cuadro de texto denominado "FileTextBox".

```csharp
using Microsoft.VisualStudio.TestTools.Common;
using Microsoft.VisualStudio.TestTools.Execution;
using System.Collections.Generic;
using System.ComponentModel;
using System.Drawing;
using System.Linq;
using System.Text;
using System.Windows.Forms;
using System.Xml;
using System;

namespace MyCompany.DiagnosticDataAdapters.ConfigurationEditors
{
    [DataCollectorConfigurationEditorTypeUri(
        "configurationeditor://MyCompany/MyConfigEditor/1.0")]
    public partial class MyDataConfigEditor :
        UserControl, IDataCollectorConfigurationEditor
    {
        private DataCollectorSettings collectorSettings;

        // Create a private property for the service provider
        private IServiceProvider ServiceProvider { get; set; }

        // Constructor
        public MyConfigurationEditor()
        {
            InitializeComponent();
        }

        // Required method called by the testing framework
        public void Initialize(
            IServiceProvider svcProvider,
            DataCollectorSettings settings)
        {
            ServiceProvider = svcProvider;
            collectorSettings = settings;

            // Display the file name as listed in the settings file.
            // If the configuration has not been updated before, this
            // data will be provided by the default configuration
            // section from <nameofcollector>.dll.config:
            // <DefaultConfiguration>
            //   <MyCollectorName
            //       xmlns="http://MyCompany/schemas/ProductName/Version");
            //     <File FullPath="C:\temp\logfile1.txt" />
            //   </MyCollectorName>
            // </DefaultConfiguration>
            this.SuspendLayout();
            this.FileTextBox.Text = GetText(collectorSettings.Configuration);
            this.ResumeLayout();
        }

        // Can be used to verify data before saving it
        public bool VerifyData()
        {
            // Not currently verifying data
            return true;
        }

        // Reset to default value from XML configuration
        // using a custom method
        public void ResetToAgentDefaults()
        {
            this.FileTextBox.Text =
                getText(collectorSettings.DefaultConfiguration);
        }

        // Saves data changed in the editor to the test configuration
        // settings. Does not change the default value.
        public DataCollectorSettings SaveData()
        {
            collectorSettings.Configuration.InnerXml =
                String.Format(
                    @"<MyCollectorName
      xmlns=""http://MyCompany/schemas/MyDataCollector/1.0"">
  <File FullPath=""{0}"" />
</MyCollectorName>",
                    FileTextBox.Text);
            return collectorSettings;
        }

        // Reads the configuration settings
        private string getText(XmlElement element)
        {
            // Setup namespace manager with our namespace
            XmlNamespaceManager nsmgr =
                new XmlNamespaceManager(
                    element.OwnerDocument.NameTable);

            // Find all the "File" elements under our configuration
            XmlNodeList files = element.SelectNodes("//ns:MyDataCollector/ns:File", nsmgr);

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
    }
}
```

## <a name="example-configuration-file"></a>Archivo de configuración de ejemplo

A continuación se muestra un archivo de configuración sencillo para el editor de configuración del recopilador de datos de diagnóstico.

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <configSections>
    <section
      name="DataCollectorConfiguration"
      type="Microsoft.VisualStudio.QualityTools.Execution.DataCollectorConfigurationSection,
        Microsoft.visualStudio.QualityTools.ExecutionCommon,
        Version=4.0.0.0, Culture=neutral,
        PublicKeyToken=b03f5f7f11d50a3a" />
  </configSections>
  <DataCollectorConfiguration
      xmlns="http://microsoft.com/schemas/VisualStudio/TeamTest/11">
    <DataCollector
        typeUri="datacollector://MyCompany/MyDataCollector/1.0">
      <DefaultConfiguration>
        <!-- Your default config settings-->
        <File FullPath="c:\temp\logfile1.txt" />
      </DefaultConfiguration>
    </DataCollector>
  </DataCollectorConfiguration>
</configuration>

```

## <a name="compile-the-code"></a>Compilar el código

### <a name="to-create-the-code-project-for-this-diagnostic-adapter"></a>Para crear el proyecto de código para este adaptador de diagnóstico

1.  Cree un nuevo proyecto de biblioteca de clases denominado "MyDataCollector".

2.  En el **Explorador de soluciones**, haga clic con el botón derecho en el proyecto y, luego, elija **Propiedades**. Para seleccionar una carpeta para agregarla, elija **Rutas de acceso de referencia** y, luego, elija los puntos suspensivos (**…**).

     Se muestra el cuadro de diálogo **Seleccionar ruta de acceso de referencia**.

3.  Seleccione la ruta de acceso siguiente, en función del directorio de instalación: *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\PrivateAssemblies*. Elija **Aceptar**.

4.  Para agregar la carpeta a la ruta de acceso de referencia, elija **Agregar carpeta**.

     La carpeta se muestra en la lista de rutas de acceso de referencia.

5.  Elija el icono **Guardar todo** para guardar las rutas de acceso de referencia.

6.  Agregue el ensamblado **Microsoft.VisualStudio.QualityTools.ExecutionCommon**.

    1.  En el **Explorador de soluciones**, haga clic con el botón derecho en **Referencias** y, luego, elija **Agregar referencia**.

    2.  Elija **Examinar** y busque **Microsoft.VisualStudio.QualityTools.ExecutionCommon.dll**.

         Este ensamblado se encuentra en *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\PrivateAssemblies*.

    3.  Elija **Aceptar**.

7.  Agregue el ensamblado **Microsoft.VisualStudio.QualityTools.Common**.

    1.  En el **Explorador de soluciones**, haga clic con el botón derecho en **Referencias** y seleccione **Agregar referencia**.

    2.  Elija **Examinar** y busque **Microsoft.VisualStudio.QualityTools.Common.dll**.

         Este ensamblado se encuentra en *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\PrivateAssemblies*.

    3.  Elija **Aceptar**.

8.  Copie la clase de adaptador de datos de diagnóstico enumerada anteriormente en este documento en la clase de su biblioteca de clases. Guarde esta clase.

9. Para agregar un control de usuario al proyecto, haga clic con el botón derecho en el proyecto **MyDataCollector** en el **Explorador de soluciones**, elija **Agregar** y luego **Control de usuario**. Haga clic en **Agregar**.

10. Con el cuadro de herramientas, agregue una etiqueta al control de usuario y cambie la propiedad Texto a **Nombre de archivo:**.

11. Con el cuadro de herramientas, agregue un cuadro de texto al control de usuario y cambie el nombre por **textBoxFileName**.

12. En el **Explorador de soluciones**, haga clic con el botón derecho en el control de usuario y, luego, elija **Ver código**. Reemplace esta clase de control de usuario con la clase de control de usuario indicada anteriormente en este documento. Guarde esta clase.

    > [!NOTE]
    > De forma predeterminada, el control de usuario se denomina UserControl1. Asegúrese de que el código de la clase de control de usuario usa el nombre del control de usuario.

13. Para crear el archivo de configuración, en el **Explorador de soluciones**, haga clic con el botón derecho en la solución, seleccione **Agregar** y, luego, elija **Nuevo elemento**. Seleccione **Archivo de configuración de aplicaciones** y, luego, elija **Agregar**. Así se agrega un archivo denominado *App.config* a la solución.

14. Copie el XML del ejemplo anterior en el archivo XML. Guarde el archivo.

15. Compile la solución y luego copie el ensamblado compilado y el archivo *App.config* en el directorio *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\PrivateAssemblies\DataCollectors*.

16. Cree la configuración de pruebas que usa este adaptador de diagnóstico de datos personalizado. Establezca la configuración de pruebas para que recopile un archivo que existe.

     Si va a ejecutar las pruebas en Microsoft Test Manager, antes de ello puede asignar esta configuración de pruebas al plan de pruebas o usar el comando Ejecutar con opciones para asignar e invalidar la configuración de pruebas. Para obtener más información sobre la configuración de pruebas, vea [Recopilar información de diagnóstico con la configuración de pruebas](../test/collect-diagnostic-information-using-test-settings.md).

17. Ejecute las pruebas usando la configuración de pruebas y con el adaptador de datos de diagnóstico seleccionado.

     El archivo de datos que especificó se adjuntará a los resultados de pruebas cuando se ejecute la prueba.

## <a name="see-also"></a>Vea también

- [Cómo: Crear un adaptador de datos de diagnóstico](../test/how-to-create-a-diagnostic-data-adapter.md)
- [Cómo: Crear un editor personalizado para los datos del adaptador de datos de diagnóstico](../test/how-to-create-a-custom-editor-for-data-for-your-diagnostic-data-adapter.md)
- [Cómo: Instalar un adaptador de datos de diagnóstico personalizado](../test/how-to-install-a-custom-diagnostic-data-adapter.md)
- [Crear un adaptador de datos de diagnóstico para recopilar datos personalizados o afectar a un equipo de prueba](../test/create-a-diagnostic-data-adapter-to-collect-custom-data-or-affect-a-test-machine.md)