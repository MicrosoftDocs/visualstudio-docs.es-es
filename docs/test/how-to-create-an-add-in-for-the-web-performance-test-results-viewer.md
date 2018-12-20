---
title: Creación de un complemento para el Visor de resultados de pruebas de rendimiento web
ms.date: 10/20/2016
ms.topic: conceptual
helpviewer_keywords:
- Web performance tests, Visual Studio Add-in
- Visual Studio Add-in, Web performance tests
ms.assetid: 1118c604-4b1b-4b21-a04e-45995b676fa8
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 6672bd1e38dee5b27d350b9d2e12626cef122115
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/07/2018
ms.locfileid: "53068346"
---
# <a name="how-to-create-a-visual-studio-add-in-for-the-web-performance-test-results-viewer"></a>Procedimiento para crear un complemento de Visual Studio para el Visor de resultados de pruebas de rendimiento web

Puede extender la interfaz de usuario para el **Visor de resultados de pruebas de rendimiento web** utilizando los siguientes espacios de nombres:

-   <xref:Microsoft.VisualStudio.TestTools.LoadTesting>

-   <xref:Microsoft.VisualStudio.TestTools.WebTesting>

Además, necesita agregar una referencia al archivo DLL LoadTestPackage que se encuentra en la carpeta *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\PrivateAssemblies*.

Para extender la interfaz de usuario del **Visor de resultados de pruebas de rendimiento web**, debe crear un control de usuario y un complemento de Visual Studio. Los siguientes procedimientos explican cómo crear el complemento y el control de usuario, y cómo implementar las clases necesarias para extender la interfaz de usuario del **Visor de resultados de pruebas de rendimiento web**.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="create-or-open-a-solution-that-contains-an-aspnet-web-application-and-a-web-performance-and-load-test-project"></a>Crear o abrir una solución que contenga una aplicación web ASP.NET y un proyecto de prueba de carga y rendimiento web

### <a name="to-prepare-for-extending-the-web-performance-test-results-viewer"></a>Para preparar la extensión del Visor de resultados de pruebas de rendimiento web

Cree o abra una solución no destinada a producción con la que pueda experimentar, que contenga una aplicación web ASP.NET y un proyecto de prueba de carga y rendimiento web con una o más pruebas de rendimiento web para esa aplicación.

> [!NOTE]
> Puede crear una aplicación web ASP.NET y un proyecto de prueba de carga y rendimiento web que contenga las pruebas de rendimiento web mediante los procedimientos de [Cómo: Crear una prueba de servicios web ](../test/how-to-create-a-web-service-test.md) y [Generación y ejecución de una prueba de rendimiento web codificada](../test/generate-and-run-a-coded-web-performance-test.md).

## <a name="create-a-visual-studio-add-in"></a>Crear un complemento de Visual Studio

Un complemento es un archivo DLL compilado que se ejecuta dentro del entorno de desarrollo integrado (IDE) de Visual Studio. El compilador ayuda a proteger la propiedad intelectual y mejora el rendimiento. A pesar de que los complementos se pueden crear manualmente, es posible que le resulte más sencillo usar el **Asistente para complementos**. Este asistente crea un complemento funcional, aunque básico, que se puede ejecutar inmediatamente después de haberlo creado. Una vez que el **Asistente para complementos** genere el programa básico, puede agregarle código y personalizarlo.

 El **Asistente para complementos** le permite proporcionar un nombre para mostrar y una descripción para el complemento. Ambos aparecerán en el **Administrador de complementos**. Además, puede dejar que el asistente genere código que agrega al menú **Herramientas** un comando para abrir el complemento. También puede optar por mostrar un cuadro **Acerca de** personalizado para el complemento. Cuando se complete el asistente, aparecerá un proyecto nuevo con una sola clase que implementa el complemento. La clase se denomina Connect.

 El **Administrador de complementos** se usa al final de este artículo.

### <a name="to-create-an-add-in-by-using-the-add-in-wizard"></a>Para crear un complemento con el Asistente para complementos

1. En el **Explorador de soluciones**, haga clic con el botón derecho en la solución, elija **Agregar** y luego seleccione **Nuevo proyecto**.

    Aparecerá el cuadro de diálogo **Nuevo proyecto**.

2. En **Plantillas instaladas**, expanda **Otros tipos de proyectos** y seleccione **Extensibilidad**.

3. En la lista de plantillas, seleccione **Complemento de Visual Studio**.

4. En **Nombre**, escriba el nombre del complemento. Por ejemplo, **WebPerfTestResultsViewerAddin**.

5. Elija **Aceptar**.

    Se inicia el **Asistente para complementos** de Visual Studio.

6. Seleccione **Siguiente**.

7. En la página **Seleccione un lenguaje de programación**, seleccione el lenguaje de programación que quiera usar para escribir el complemento.

   > [!NOTE]
   > En este tema se utiliza Visual C# para el código muestra.

8. En la página **Seleccione una aplicación host**, seleccione **Visual Studio** y desactive **Macros de Visual Studio**.

9. Seleccione **Siguiente**.

10. Especifique un nombre y una descripción del complemento en la página **Especifique un nombre y una descripción**.

     Una vez creado el complemento, su nombre y descripción se muestran en la lista **Complementos disponibles** del **Administrador de complementos**. Agregue bastantes detalles a la descripción del complemento para que los usuarios sepan lo que hace el complemento, cómo funciona, etc.

11. Seleccione **Siguiente**.

12. En la página **Elija las opciones del complemento**, seleccione **Me gustaría que se cargue al iniciar la aplicación host**.

13. Desactive las casillas restantes.

14. En la página **Elección de información para Ayuda - Acerca de**, especifique si quiere que la información del complemento se muestre en el cuadro de diálogo **Acerca de**. Si quiere mostrar la información, active la casilla **Sí, me gustaría que mi complemento ofreciera información en el cuadro Acerca de**.

     La información que se puede agregar al cuadro de diálogo **Acerca de** de Visual Studio incluye número de versión, detalles de compatibilidad, datos de la licencia, etc.

15. Seleccione **Siguiente**.

16. Use la página **Resumen** para revisar las opciones seleccionadas en el asistente. Si está de acuerdo, elija **Finalizar** para crear el complemento. Si quiere cambiar algo, elija el botón **Atrás**.

     Se crean el nuevo proyecto y la solución, y se muestra el archivo *Connect.cs* del nuevo complemento en el **Editor de código**.

     Después del siguiente procedimiento se agrega código al archivo *Connect.cs*; el procedimiento crea un control de usuario al que hace referencia el proyecto WebPerfTestResultsViewerAddin.

    Una vez creado un complemento, debe registrarlo con Visual Studio para poder activarlo en el **Administrador de complementos**. Para este fin se usa un archivo XML con una extensión de nombre de archivo *.addin*.

    Este archivo *.addin* describe la información que Visual Studio necesita para mostrar el complemento en el **Administrador de complementos**. Cuando se inicia Visual Studio, busca en la ubicación del archivo *.addin* los archivos *.addin* disponibles. Si encuentra alguno, lee el archivo XML y facilita al **Administrador de complementos** la información necesaria para iniciar el complemento cuando se haga clic en él.

    El archivo *.addin* se crea automáticamente al crear un complemento mediante el **Asistente para complementos**.

### <a name="add-in-file-locations"></a>Ubicaciones de archivos de complemento

El **Asistente para complementos** crea automáticamente dos copias del archivo *.addin*, como se muestra a continuación:

|**Ubicación del archivo .addin**|**Descripción**|
|-|----------------------------|-|
|Carpeta raíz del proyecto|Se utiliza para la implementación del proyecto de complemento. Se incluye en el proyecto para facilitar la edición y tiene la ruta de acceso local para la implementación de estilo XCopy.|
|Carpeta de complementos|Se utiliza para ejecutar el complemento en el entorno de depuración. Siempre debe señalar la ruta de acceso de los resultados de la configuración de compilación actual.|

## <a name="create-a-windows-form-control-library-project"></a>Crear un proyecto de Biblioteca de controles de Windows Forms

El complemento de Visual Studio creado en el procedimiento anterior hace referencia a un proyecto de Biblioteca de controles de Windows Forms para crear una instancia de una clase <xref:System.Windows.Forms.UserControl>.

### <a name="to-create-a-control-to-be-used-in-the-web-test-results-viewer"></a>Para crear un control que se va a utilizar en el Visor de resultados de pruebas de rendimiento web

1.  En el **Explorador de soluciones**, haga clic con el botón derecho en la solución, elija **Agregar** y luego seleccione **Nuevo proyecto**.

     Aparecerá el cuadro de diálogo **Nuevo proyecto**.

2.  En **Plantillas instaladas**, expanda **Visual Basic** o **Visual C#** y seleccione **Windows**.

    > [!NOTE]
    > En este tema se utiliza Visual C# para el código muestra.

3.  En la lista de plantillas, seleccione **Biblioteca de controles de Windows Forms**.

4.  En **Nombre**, escriba el nombre del complemento. Por ejemplo, **WebPerfTestResultsViewerControl**.

5.  Elija **Aceptar**.

     Se agrega el proyecto de biblioteca de controles de Windows Forms WebPerfTestResultsViewerControl al **Explorador de soluciones** y se muestra *UserControl1.cs* en modo de diseño.

6.  Desde el **cuadro de herramientas**, arrastre <xref:System.Windows.Forms.DataGridView> a la superficie de userControl1.

7.  Haga clic en el glifo de etiqueta de acción (![Glifo de etiqueta inteligente](../test/media/vs_winformsmttagglyph.gif)) situado en la esquina superior derecha de <xref:System.Windows.Forms.DataGridView> y siga estos pasos:

    1.  Elija **Acoplar en contenedor primario**.

    2.  Desactive las casillas **Habilitar acción de agregar**, **Habilitar edición**, **Habilitar eliminación** y **Habilitar reordenación de columnas**.

    3.  Elija **Agregar columna**.

         Se muestra el cuadro de diálogo **Agregar columna**.

    4.  En la lista desplegable **Tipo**, seleccione **DataGridViewTextBoxColumn**.

    5.  Borre "Column1" de **Texto del encabezado**.

    6.  Haga clic en **Agregar**.

    7.  Elija **Cerrar**.

8.  En la ventana **Propiedades**, cambie la propiedad **(Nombre)** de <xref:System.Windows.Forms.DataGridView> por **resultControlDataGridView**.

9. En la superficie de diseño, haga clic con el botón derecho y seleccione **Ver código**.

     El archivo *UserControl1.cs* se abre en el **Editor de código**.

10. Cambie el nombre de clase <xref:System.Windows.Forms.UserControl> con instancias de UserContro1 a resultControl:

    ```csharp
    namespace WebPerfTestResultsViewerControl
    {
        public partial class resultControl : UserControl
        {
            public resultControl()
            {
                InitializeComponent();
            }
    ```

     En el procedimiento siguiente, se agrega código al archivo *Connect.cs* del proyecto WebPerfTestResultsViewerAddin que hace referencia a la clase resultControl.

     Después se agrega código adicional al archivo *Connect.cs*.

## <a name="add-code-to-the-webperftestresultsvieweraddin"></a>Agregar código a WebPerfTestResultsViewerAddin

### <a name="to-add-code-to-the-visual-studio-add-in-to-extend-the-web-test-results-viewer"></a>Para agregar código al complemento de Visual Studio para extender el visor de resultados de pruebas web

1.  En el **Explorador de soluciones**, haga clic con el botón derecho en el nodo **Referencias** en el proyecto WebPerfTestResultsViewerAddin y seleccione **Agregar referencia**.

2.  En el cuadro de diálogo **Agregar referencia**, elija la pestaña **.NET**.

3.  Desplácese hacia abajo y seleccione **Microsoft.VisualStudio.QualityTools.WebTestFramework** y **System.Windows.Forms**.

4.  Elija **Aceptar**.

5.  Haga clic con el botón derecho en el nodo **Referencias** otra vez y seleccione **Agregar referencia**.

6.  En el cuadro de diálogo **Agregar referencia**, elija la pestaña **Examinar**.

7.  Elija la lista desplegable **Buscar en**, vaya a *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\PrivateAssemblies* y seleccione el archivo *Microsoft.VisualStudio.QualityTools.LoadTestPackage.dll*.

8.  Elija **Aceptar**.

9. Haga clic con el botón derecho en el nodo del proyecto WebPerfTestResultsViewerAddin y seleccione **Agregar referencia**.

10. En el cuadro de diálogo **Agregar referencia**, elija la pestaña **Proyectos**.

11. En **Nombre de proyecto**, seleccione el proyecto **WebPerfTestResultsViewerControl** y elija **Aceptar**.

12. Si el archivo *Connect.cs* todavía no está abierto, en el **Explorador de soluciones**, haga clic con el botón derecho en el archivo **Connect.cs** del proyecto WebPerfTestResultsViewerAddin y seleccione **Ver código**.

13. Agregue las siguientes instrucciones Using al archivo *Connect.cs*:

    ```csharp
    using System.IO;
    using System.Windows.Forms;
    using System.Collections.Generic;
    using Microsoft.VisualStudio.TestTools.LoadTesting;
    using Microsoft.VisualStudio.TestTools.WebTesting;
    using WebPerfTestResultsViewerControl;
    ```

14. Desplácese a la parte inferior del archivo *Connect.cs*. Debe agregar una lista de GUID para <xref:System.Windows.Forms.UserControl> en caso de que haya más de una instancia del **Visor de resultados de pruebas de rendimiento web** abierta. Agregará código que utilizará después esta lista.

     Una segunda lista de cadena se usa en el método OnDiscconection que se programa más adelante.

    ```csharp
    private DTE2 _applicationObject;
    private AddIn _addInInstance;

    private Dictionary<Guid, List<UserControl>> m_controls = new Dictionary<Guid, List<UserControl>>();        private List<string> temporaryFilePaths = new List<string>();
    ```

15. El archivo *Connect.cs* crea instancias de una clase denominada Connect de la clase <xref:Extensibility.IDTExtensibility2> y también incluye métodos para implementar el complemento de Visual Studio. Uno de los métodos es el método OnConnection, al que se notifica que el complemento se está cargando. En el método OnConnection, utilizará la clase LoadTestPackageExt para crear el paquete de extensibilidad para el **Visor de resultados de pruebas de rendimiento web**. Agregue el siguiente código al método OnConnection:

    ```csharp
    public void OnConnection(object application, ext_ConnectMode connectMode, object addInInst, ref Array custom)
                {
                _applicationObject = (DTE2)application;
                _addInInstance = (AddIn)addInInst;

                // Create a load test packge extensibility class.            LoadTestPackageExt loadTestPackageExt = _applicationObject.GetObject("Microsoft.VisualStudio.TestTools.LoadTesting.LoadTestPackageExt") as LoadTestPackageExt;            // Process open windows.            foreach (WebTestResultViewer webTestResultViewer in loadTestPackageExt.WebTestResultViewerExt.ResultWindows)            {                WindowCreated(webTestResultViewer);            }            // Create event handlers.            loadTestPackageExt.WebTestResultViewerExt.WindowCreated += new EventHandler<WebTestResultViewerExt.WindowCreatedEventArgs>(WebTestResultViewerExt_WindowCreated);            loadTestPackageExt.WebTestResultViewerExt.WindowClosed += new EventHandler<WebTestResultViewerExt.WindowClosedEventArgs>(WebTesResultViewer_WindowClosed);            loadTestPackageExt.WebTestResultViewerExt.SelectionChanged += new EventHandler<WebTestResultViewerExt.SelectionChangedEventArgs>(WebTestResultViewer_SelectedChanged);
            }
    ```

16. Agregue el siguiente código a la clase Connect para crear el método WebTestResultViewerExt_WindowCreated para el controlador de eventos loadTestPackageExt.WebTestResultViewerExt.WindowCreated que agregó en el método OnConnection y para el método WindowCreated, al que llama el método WebTestResultViewerExt_WindowCreated.

    ```csharp
            void WebTestResultViewerExt_WindowCreated(object sender, WebTestResultViewerExt.WindowCreatedEventArgs e)
            {
                // New control added to new result viewer window.
                WindowCreated(e.WebTestResultViewer);
            }

    private void WindowCreated(WebTestResultViewer viewer)        {            // Instantiate an instance of the resultControl referenced in the WebPerfTestResultsViewerControl project.
                resultControl resultControl = new resultControl();            // Add to the dictionary of open playback windows.            System.Diagnostics.Debug.Assert(!m_controls.ContainsKey(viewer.TestResultId));            List<UserControl> userControls = new List<UserControl>();            userControls.Add(resultControl);            // Add Guid to the m_control List to manage Result viewers and controls.            m_controls.Add(viewer.TestResultId, userControls);            // Add tabs to the playback control.            resultControl.Dock = DockStyle.Fill;            viewer.AddResultPage(new Guid(), "Sample", resultControl);        }
    ```

17. Agregue el siguiente código a la clase Connect para crear el método WebTestResultViewer_SelectedChanged para el controlador de eventos loadTestPackageExt.WebTestResultViewerExt.SelectionChanged que agregó en el método OnConnection:

    ```csharp
    void WebTestResultViewer_SelectedChanged(object sender, WebTestResultViewerExt.SelectionChangedEventArgs e)
    {
        foreach (UserControl userControl in m_controls[e.TestResultId])            {                // Update the userControl in each result viewer.                resultControl resultControl = userControl as resultControl;                if (resultControl != null)                    // Call the resultControl's Update method (This will be added in the next procedure).                    resultControl.Update(e.WebTestRequestResult);            }
    }
    ```

18. Agregue el siguiente código a la clase Connect para crear el método WebTesResultViewer_WindowClosed para el controlador de eventos loadTestPackageExt.WebTestResultViewerExt.WindowClosed que agregó en el método OnConnection:

    ```csharp
    void WebTesResultViewer_WindowClosed(object sender, WebTestResultViewerExt.WindowClosedEventArgs e)
    {
        if (m_controls.ContainsKey(e.WebTestResultViewer.TestResultId))
        {
            m_controls.Remove(e.WebTestResultViewer.TestResultId);
        }
    }
    ```

     Ahora que el código se ha completado para el complemento de Visual Studio, necesita agregar el método Update a resultControl en el proyecto WebPerfTestResultsViewerControl.

## <a name="add-code-to-the-webperftestresultsviewercontrol"></a>Agregar código a WebPerfTestResultsViewerControl

### <a name="to-add-code-to-the-user-control"></a>Para agregar código al control de usuario

1.  En el **Explorador de soluciones**, haga clic con el botón derecho en el nodo del proyecto WebPerfTestResultsViewerControl y seleccione **Propiedades**.

2.  Seleccione la pestaña **Aplicación**, elija la lista desplegable **Plataforma de destino**, seleccione **.NET Framework 4** y cierre **Propiedades**.

     Esto es necesario por compatibilidad con las referencias DLL que se necesitan para extender el **Visor de resultados de pruebas de rendimiento web**.

3.  En el **Explorador de soluciones**, en el proyecto WebPerfTestResultsViewerControl, haga clic con el botón derecho en el nodo **Referencias** y seleccione **Agregar referencia**.

4.  En el cuadro de diálogo **Agregar referencia**, haga clic en la pestaña **.NET**.

5.  Desplácese y seleccione **Microsoft.VisualStudio.QualityTools.WebTestFramework**.

6.  Elija **Aceptar**.

7.  Agregue las instrucciones Using siguientes al archivo *UserControl1.cs*:

    ```csharp
    using Microsoft.VisualStudio.TestTools.WebTesting;
    using Microsoft.VisualStudio.TestTools.WebTesting.Rules;
    ```

8.  Agregue el método Update que se llama y se pasa a WebTestRequestResult desde el método WebPerfTestResultsViewerAddin WebTestResultViewer_SelectedChanged del archivo *Connect.cs*. El método Update rellena DataGridView con varias propiedades que se le pasan en WebTestRequestResult.

    ```csharp
    public void Update(WebTestRequestResult WebTestResults)
            {
                // Clear the DataGridView when a request is selected.
                resultControlDataGridView.Rows.Clear();
                // Populate the DataGridControl with properties from the WebTestResults.
                this.resultControlDataGridView.Rows.Add("Request: " + WebTestResults.Request.Url.ToString());
                this.resultControlDataGridView.Rows.Add("Response: " + WebTestResults.Response.ResponseUri.ToString());
                foreach (RuleResult ruleResult in WebTestResults.ExtractionRuleResults)
                {
                    this.resultControlDataGridView.Rows.Add("Extraction rule results: " + ruleResult.Message.ToString());
                }
                foreach (RuleResult ruleResult in WebTestResults.ValidationRuleResults)
                {
                    this.resultControlDataGridView.Rows.Add("Validation rule results: " + ruleResult.Message.ToString());
                }
                foreach (WebTestError webTestError in WebTestResults.Errors)
                {
                    this.resultControlDataGridView.Rows.Add("Error: " + webTestError.ErrorType.ToString() + " " + webTestError.ErrorSubtype.ToString() + " " + webTestError.ExceptionText.ToString());
                }
            }
    ```

## <a name="build-the-webperftestresultsvieweraddin-solution"></a>Compilar la solución WebPerfTestResultsViewerAddin

### <a name="to-build-the-solution"></a>Para compilar la solución

-   En el menú **Compilar**, seleccione **Compilar solución**.

## <a name="register-the-webperftestresultsvieweraddin-add-in"></a>Registrar el complemento WebPerfTestResultsViewerAddin

### <a name="to-register-the-add-in-using-the-add-in-manager"></a>Para registrar el complemento mediante el Administrador de complementos

1.  Seleccione **Administrador de complementos** en el menú **Herramientas**.

2.  Se muestra el cuadro de diálogo **Administrador de complementos**.

3.  Active la casilla del complemento WebPerfTestResultsViewerAddin en la columna **Complementos disponibles** y desactive las casillas bajo las columnas **Inicio** y **Línea de comandos**.

4.  Elija **Aceptar**.

## <a name="run-the-web-performance-test-using-the-build-the-webperftestresultsvieweraddin-add-in"></a>Ejecutar la prueba de rendimiento web con el complemento WebPerfTestResultsViewerAddin

### <a name="to-run-the-new-vs-add-in-for-the-web-test-results-viewer"></a>Para ejecutar el nuevo complemento de Visual Studio para el visor de resultados de pruebas web

1.  Ejecute la prueba de rendimiento web y verá la nueva pestaña del complemento WebPerfTestResultsViewerAddin en el **Visor de resultados de pruebas de rendimiento web**.

2.  Elija la pestaña para ver las propiedades de DataGridView.

## <a name="net-framework-security"></a>Seguridad de .NET Framework

Para mejorar la seguridad evitando que complementos malintencionados se activen de forma automática, Visual Studio proporciona configuraciones en una página de **Opciones de herramientas** denominada **Seguridad de macros/complementos**.

Además, esta página de opciones permite especificar las carpetas en las que Visual Studio busca los archivos de registro *.AddIn*. Esto mejora la seguridad porque permite limitar las ubicaciones donde se pueden leer los archivos de registro *.AddIn*. Esto ayuda a evitar que se usen involuntariamente archivos *.AddIn* malintencionados.

 **Configuración de seguridad de complementos**

 La configuración en la página de opciones relativa a la seguridad de los complementos es la siguiente:

-   **Permitir la carga de componentes de complementos.** Esta opción está seleccionada de forma predeterminada. Cuando se activa, es posible cargar complementos en Visual Studio. De lo contrario, no es posible cargar complementos en Visual Studio.

-   **Permitir la carga de componentes de complementos desde direcciones URL.** Esta opción está seleccionada de forma predeterminada. Cuando está seleccionada, los complementos se pueden cargar desde sitios web externos. De lo contrario, no es posible cargar complementos remotos en Visual Studio. Si un complemento no se puede cargar por alguna razón, no es posible cargarlo desde Internet. Esta configuración controla sólo la carga de los archivos DLL del complemento. Los archivos de registro *.Addin* siempre se deben ubicar en el sistema local.

## <a name="see-also"></a>Vea también

- <xref:System.Windows.Forms.UserControl>
- <xref:Microsoft.VisualStudio.TestTools.LoadTesting>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules>
- <xref:System.Windows.Forms.UserControl>
- <xref:System.Windows.Forms.DataGrid>
- [Crear código y complementos personalizados para las pruebas de carga](../test/create-custom-code-and-plug-ins-for-load-tests.md)