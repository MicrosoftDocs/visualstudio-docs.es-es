---
title: Adición de búsqueda a una ventana de herramientas ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- tool windows, adding search
ms.assetid: f78c4892-8060-49c4-8ecd-4360f1b4d133
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f9112a3368ba604c4291f9018e763022e953c4fc
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740138"
---
# <a name="add-search-to-a-tool-window"></a>Añadir búsqueda a una ventana de herramientas
Al crear o actualizar una ventana de herramientas en la extensión, puede agregar la misma funcionalidad de búsqueda que aparece en otro lugar de Visual Studio. Esta funcionalidad incluye las siguientes características:

- Un cuadro de búsqueda que siempre se encuentra en un área personalizada de la barra de herramientas.

- Un indicador de progreso que está superpuesto en el propio cuadro de búsqueda.

- La capacidad de mostrar los resultados tan pronto como introduzca cada carácter (búsqueda instantánea) o solo después de elegir la tecla **Intro** (búsqueda a petición).

- Una lista que muestra los términos para los que ha buscado más recientemente.

- La capacidad de filtrar las búsquedas por campos o aspectos específicos de los destinos de búsqueda.

Siguiendo este tutorial, aprenderá a realizar las siguientes tareas:

1. Crear un proyecto de VSPackage.

2. Cree una ventana de herramientas que contenga un UserControl con un cuadro de texto de solo lectura.

3. Agregue un cuadro de búsqueda a la ventana de herramientas.

4. Agregue la implementación de búsqueda.

5. Habilite la búsqueda instantánea y la visualización de una barra de progreso.

6. Agregue una opción **Coincidir mayúsculas y minúsculas.**

7. Agregue un filtro **Buscar solo líneas uniformes.**

## <a name="to-create-a-vsix-project"></a>Para crear un proyecto de VSIX

1. Cree un proyecto `TestToolWindowSearch` VSIX denominado con una ventana de herramientas denominada **TestSearch**. Si necesita ayuda para hacerlo, consulte Creación de una extensión con una ventana de [herramientas.](../extensibility/creating-an-extension-with-a-tool-window.md)

## <a name="to-create-a-tool-window"></a>Para crear una ventana de herramientas

1. En `TestToolWindowSearch` el proyecto, abra el archivo *TestSearchControl.xaml.*

2. Reemplace el `<StackPanel>` bloque existente por el siguiente bloque, <xref:System.Windows.Controls.TextBox> que <xref:System.Windows.Controls.UserControl> agrega un solo lectura al bloque de la ventana de herramientas.

    ```xaml
    <StackPanel Orientation="Vertical">
        <TextBox Name="resultsTextBox" Height="800.0"
            Width="800.0"
            IsReadOnly="True">
        </TextBox>
    </StackPanel>
    ```

3. En el archivo *TestSearchControl.xaml.cs,* agregue la siguiente directiva using:

    ```csharp
    using System.Text;
    ```

4. Quite `button1_Click()` el método.

     En la clase **TestSearchControl,** agregue el código siguiente.

     Este código agrega <xref:System.Windows.Controls.TextBox> una propiedad pública denominada **SearchResultsTextBox** y una propiedad de cadena pública denominada **SearchContent**. En el constructor, SearchResultsTextBox se establece en el cuadro de texto y SearchContent se inicializa en un conjunto de cadenas delimitado por nueva línea. El contenido del cuadro de texto también se inicializa en el conjunto de cadenas.

     [!code-csharp[ToolWindowSearch#1](../extensibility/codesnippet/CSharp/adding-search-to-a-tool-window_1.cs)]
     [!code-vb[ToolWindowSearch#1](../extensibility/codesnippet/VisualBasic/adding-search-to-a-tool-window_1.vb)]

5. Compile la solución y comience la depuración. Aparece la instancia experimental de Visual Studio.

6. En la barra de menús, elija **Ver** > otras**Pruebas**de**Windows.** > 

     Aparece la ventana de herramientas, pero el control de búsqueda aún no aparece.

## <a name="to-add-a-search-box-to-the-tool-window"></a>Para añadir un cuadro de búsqueda a la ventana de herramientas

1. En el *archivo TestSearch.cs,* agregue `TestSearch` el código siguiente a la clase. El código reemplaza <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.SearchEnabled%2A> la propiedad para `true`que el descriptor de acceso get devuelva .

     Para habilitar la búsqueda, <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.SearchEnabled%2A> debe invalidar la propiedad. La <xref:Microsoft.VisualStudio.Shell.ToolWindowPane> clase <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch> implementa y proporciona una implementación predeterminada que no habilita la búsqueda.

    ```csharp
    public override bool SearchEnabled
    {
        get { return true; }
    }
    ```

2. Compile la solución y comience la depuración. Aparece la instancia experimental.

3. En la instancia experimental de Visual Studio, abra **TestSearch**.

     En la parte superior de la ventana de herramientas, aparece un control de búsqueda con una marca de agua **de búsqueda** y un icono de lupa. Sin embargo, la búsqueda aún no funciona porque el proceso de búsqueda no se ha implementado.

## <a name="to-add-the-search-implementation"></a>Para agregar la implementación de búsqueda
 Al habilitar la <xref:Microsoft.VisualStudio.Shell.ToolWindowPane>búsqueda en un , como en el procedimiento anterior, la ventana de herramientas crea un host de búsqueda. Este host configura y administra los procesos de búsqueda, que siempre se producen en un subproceso en segundo plano. Dado <xref:Microsoft.VisualStudio.Shell.ToolWindowPane> que la clase administra la creación del host de búsqueda y la configuración de la búsqueda, solo necesita crear una tarea de búsqueda y proporcionar el método de búsqueda. El proceso de búsqueda se produce en un subproceso en segundo plano y las llamadas al control de ventana de herramientas se producen en el subproceso de interfaz de usuario. Por lo tanto, debe usar el [método ThreadHelper.Invoke*](https://msdn.microsoft.com/data/ee197798(v=vs.85)) para administrar las llamadas que realice al tratar con el control.

1. En el archivo *TestSearch.cs,* agregue las siguientes `using` directivas:

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Runtime.InteropServices;
    using System.Text;
    using System.Windows.Controls;
    using Microsoft.Internal.VisualStudio.PlatformUI;
    using Microsoft.VisualStudio;
    using Microsoft.VisualStudio.PlatformUI;
    using Microsoft.VisualStudio.Shell;
    using Microsoft.VisualStudio.Shell.Interop;
    ```

2. En `TestSearch` la clase, agregue el código siguiente, que realiza las siguientes acciones:

    - Reemplaza el <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.CreateSearch%2A> método para crear una tarea de búsqueda.

    - Reemplaza el <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.ClearSearch%2A> método para restaurar el estado del cuadro de texto. Se llama a este método cuando un usuario cancela una tarea de búsqueda y cuando un usuario establece o desestablece opciones o filtros. Ambos <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.CreateSearch%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.ClearSearch%2A> y se llaman en el subproceso de interfaz de usuario. Por lo tanto, no es necesario tener acceso al cuadro de texto mediante el [ThreadHelper.Invoke*](https://msdn.microsoft.com/data/ee197798(v=vs.85)) método.

    - Crea una clase con `TestSearchTask` el nombre <xref:Microsoft.VisualStudio.Shell.VsSearchTask>que hereda de <xref:Microsoft.VisualStudio.Shell.Interop.IVsSearchTask>, que proporciona una implementación predeterminada de .

         En `TestSearchTask`, el constructor establece un campo privado que hace referencia a la ventana de herramientas. Para proporcionar el método de <xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStartSearch%2A> <xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStopSearch%2A> búsqueda, invalide los métodos y. El <xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStartSearch%2A> método es donde se implementa el proceso de búsqueda. Este proceso incluye realizar la búsqueda, mostrar los resultados de la búsqueda en el cuadro de texto y llamar a la implementación de la clase base de este método para informar de que la búsqueda se ha completado.

    ```csharp
    public override IVsSearchTask CreateSearch(uint dwCookie, IVsSearchQuery pSearchQuery, IVsSearchCallback pSearchCallback)
    {
        if (pSearchQuery == null || pSearchCallback == null)
            return null;
         return new TestSearchTask(dwCookie, pSearchQuery, pSearchCallback, this);
    }

    public override void ClearSearch()
    {
        TestSearchControl control = (TestSearchControl)this.Content;
        control.SearchResultsTextBox.Text = control.SearchContent;
    }

    internal class TestSearchTask : VsSearchTask
    {
        private TestSearch m_toolWindow;

        public TestSearchTask(uint dwCookie, IVsSearchQuery pSearchQuery, IVsSearchCallback pSearchCallback, TestSearch toolwindow)
            : base(dwCookie, pSearchQuery, pSearchCallback)
        {
            m_toolWindow = toolwindow;
        }

        protected override void OnStartSearch()
        {
            // Use the original content of the text box as the target of the search.
            var separator = new string[] { Environment.NewLine };
            TestSearchControl control = (TestSearchControl)m_toolWindow.Content;
            string[] contentArr = control.SearchContent.Split(separator, StringSplitOptions.None);

            // Get the search option.
            bool matchCase = false;
            // matchCase = m_toolWindow.MatchCaseOption.Value;

                // Set variables that are used in the finally block.
                StringBuilder sb = new StringBuilder("");
                uint resultCount = 0;
                this.ErrorCode = VSConstants.S_OK;

                try
                {
                    string searchString = this.SearchQuery.SearchString;

                    // Determine the results.
                    uint progress = 0;
                    foreach (string line in contentArr)
                    {
                        if (matchCase == true)
                        {
                            if (line.Contains(searchString))
                            {
                                sb.AppendLine(line);
                                resultCount++;
                            }
                        }
                        else
                            {
                                if (line.ToLower().Contains(searchString.ToLower()))
                                {
                                    sb.AppendLine(line);
                                    resultCount++;
                                }
                            }

                            // SearchCallback.ReportProgress(this, progress++, (uint)contentArr.GetLength(0));

                            // Uncomment the following line to demonstrate the progress bar.
                            // System.Threading.Thread.Sleep(100);
                        }
                    }
                    catch (Exception e)
                    {
                        this.ErrorCode = VSConstants.E_FAIL;
                    }
                    finally
                    {
                        ThreadHelper.Generic.Invoke(() =>
                        { ((TextBox)((TestSearchControl)m_toolWindow.Content).SearchResultsTextBox).Text = sb.ToString(); });

                        this.SearchResults = resultCount;
                    }

            // Call the implementation of this method in the base class.
            // This sets the task status to complete and reports task completion.
            base.OnStartSearch();
        }

        protected override void OnStopSearch()
        {
            this.SearchResults = 0;
        }
    }
    ```

3. Pruebe la implementación de la búsqueda realizando los pasos siguientes:

    1. Vuelva a generar el proyecto e inicie la depuración.

    2. En la instancia experimental de Visual Studio, vuelva a abrir la ventana de herramientas, escriba texto de búsqueda en la ventana de búsqueda y haga clic en **ENTRAR**.

         Deberían aparecer los resultados correctos.

## <a name="to-customize-the-search-behavior"></a>Para personalizar el comportamiento de búsqueda
 Al cambiar la configuración de búsqueda, puede realizar una variedad de cambios en cómo aparece el control de búsqueda y cómo se lleva a cabo la búsqueda. Por ejemplo, puede cambiar la marca de agua (el texto predeterminado que aparece en el cuadro de búsqueda), el ancho mínimo y máximo del control de búsqueda y si desea mostrar una barra de progreso. También puede cambiar el punto en el que los resultados de búsqueda comienzan a aparecer (a petición o búsqueda instantánea) y si desea mostrar una lista de términos para los que ha buscado recientemente. Puede encontrar la lista completa <xref:Microsoft.VisualStudio.PlatformUI.SearchSettingsDataSource> de ajustes en la clase.

1. En el archivo TestSearch.cs*, agregue el `TestSearch` código siguiente a la clase. Este código permite la búsqueda instantánea en lugar de la búsqueda bajo demanda (lo que significa que el usuario no tiene que hacer clic en **ENTRAR**). El código reemplaza `ProvideSearchSettings` el `TestSearch` método de la clase, que es necesario para cambiar la configuración predeterminada.

    ```csharp
    public override void ProvideSearchSettings(IVsUIDataSource pSearchSettings)
    {
        Utilities.SetValue(pSearchSettings,
            SearchSettingsDataSource.SearchStartTypeProperty.Name,
            (uint)VSSEARCHSTARTTYPE.SST_INSTANT);}
    ```

2. Pruebe la nueva configuración reconstruyendo la solución y reiniciando el depurador.

     Los resultados de la búsqueda aparecen cada vez que se introduce un carácter en el cuadro de búsqueda.

3. En `ProvideSearchSettings` el método, agregue la siguiente línea, que permite la visualización de una barra de progreso.

    ```csharp
    public override void ProvideSearchSettings(IVsUIDataSource pSearchSettings)
    {
        Utilities.SetValue(pSearchSettings,
            SearchSettingsDataSource.SearchStartTypeProperty.Name,
             (uint)VSSEARCHSTARTTYPE.SST_INSTANT);
        Utilities.SetValue(pSearchSettings,
            SearchSettingsDataSource.SearchProgressTypeProperty.Name,
             (uint)VSSEARCHPROGRESSTYPE.SPT_DETERMINATE);
    }
    ```

     Para que aparezca la barra de progreso, se debe notificar el progreso. Para informar del progreso, quite el `OnStartSearch` comentario `TestSearchTask` del siguiente código en el método de la clase:

    ```csharp
    SearchCallback.ReportProgress(this, progress++, (uint)contentArr.GetLength(0));
    ```

4. Para ralentizar el procesamiento lo suficiente como para que `OnStartSearch` la barra `TestSearchTask` de progreso esté visible, quite el comentario de la siguiente línea en el método de la clase:

    ```csharp
    System.Threading.Thread.Sleep(100);
    ```

5. Pruebe la nueva configuración reconstruyendo la solución y empezando a depurar.

     La barra de progreso aparece en la ventana de búsqueda (como una línea azul debajo del cuadro de texto de búsqueda) cada vez que realiza una búsqueda.

## <a name="to-enable-users-to-refine-their-searches"></a>Para permitir a los usuarios refinar sus búsquedas
 Puede permitir a los usuarios refinar sus búsquedas mediante opciones como **Coincidir mayúsculas** y minúsculas o **Coincidir con palabra completa.** Las opciones pueden ser booleanas, que aparecen como casillas de verificación, o comandos, que aparecen como botones. Para este tutorial, creará una opción booleana.

1. En el *archivo TestSearch.cs,* agregue `TestSearch` el código siguiente a la clase. El código reemplaza `SearchOptionsEnum` el método, lo que permite que la implementación de búsqueda detecte si una opción determinada está activada o desactivada. El código `SearchOptionsEnum` de agrega una opción <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumWindowSearchOptions> para que coincida con mayúsculas y minúsculas con un enumerador. La opción de coincidir con el `MatchCaseOption` caso también está disponible como la propiedad.

    ```csharp
    private IVsEnumWindowSearchOptions m_optionsEnum;
    public override IVsEnumWindowSearchOptions SearchOptionsEnum
    {
        get
        {
            if (m_optionsEnum == null)
            {
                List<IVsWindowSearchOption> list = new List<IVsWindowSearchOption>();

                list.Add(this.MatchCaseOption);

                m_optionsEnum = new WindowSearchOptionEnumerator(list) as IVsEnumWindowSearchOptions;
            }
            return m_optionsEnum;
        }
    }

    private WindowSearchBooleanOption m_matchCaseOption;
    public WindowSearchBooleanOption MatchCaseOption
    {
        get
        {
            if (m_matchCaseOption == null)
            {
                m_matchCaseOption = new WindowSearchBooleanOption("Match case", "Match case", false);
            }
            return m_matchCaseOption;
        }
    }
    ```

2. En `TestSearchTask` la clase, quite el `OnStartSearch` comentario de la siguiente línea en el método:

    ```csharp
    matchCase = m_toolWindow.MatchCaseOption.Value;
    ```

3. Pruebe la opción:

    1. Compile la solución y comience la depuración. Aparece la instancia experimental.

    2. En la ventana de herramientas, elija la flecha hacia abajo en el lado derecho del cuadro de texto.

         Aparece la casilla de verificación **Coincidir mayúsculas y** minúsculas.

    3. Active la casilla de verificación **Coincidir mayúsculas y** minúsculas y, a continuación, realice algunas búsquedas.

## <a name="to-add-a-search-filter"></a>Para añadir un filtro de búsqueda
 Puede agregar filtros de búsqueda que permitan a los usuarios refinar el conjunto de destinos de búsqueda. Por ejemplo, puede filtrar archivos en el Explorador de archivos por las fechas en las que se modificaron más recientemente y sus extensiones de nombre de archivo. En este tutorial, agregará un filtro solo para líneas uniformes. Cuando el usuario elige ese filtro, el host de búsqueda agrega las cadenas que especifique a la consulta de búsqueda. A continuación, puede identificar estas cadenas dentro del método de búsqueda y filtrar los destinos de búsqueda en consecuencia.

1. En el *archivo TestSearch.cs,* agregue `TestSearch` el código siguiente a la clase. El código `SearchFiltersEnum` se implementa <xref:Microsoft.VisualStudio.PlatformUI.WindowSearchSimpleFilter> agregando un que especifica filtrar los resultados de la búsqueda para que solo aparezcan líneas par.

    ```csharp
    public override IVsEnumWindowSearchFilters SearchFiltersEnum
    {
        get
        {
            List<IVsWindowSearchFilter> list = new List<IVsWindowSearchFilter>();
            list.Add(new WindowSearchSimpleFilter("Search even lines only", "Search even lines only", "lines", "even"));
            return new WindowSearchFilterEnumerator(list) as IVsEnumWindowSearchFilters;
        }
    }

    ```

     Ahora el control de `Search even lines only`búsqueda muestra el filtro de búsqueda . Cuando el usuario elige el `lines:"even"` filtro, la cadena aparece en el cuadro de búsqueda. Pueden aparecer otros criterios de búsqueda al mismo tiempo que el filtro. Las cadenas de búsqueda pueden aparecer antes del filtro, después del filtro o ambas.

2. En el *archivo TestSearch.cs,* agregue `TestSearchTask` los métodos siguientes `TestSearch` a la clase, que se encuentra en la clase. Estos métodos `OnStartSearch` admiten el método, que modificará en el paso siguiente.

    ```csharp
    private string RemoveFromString(string origString, string stringToRemove)
    {
        int index = origString.IndexOf(stringToRemove);
        if (index == -1)
            return origString;
        else 
             return (origString.Substring(0, index) + origString.Substring(index + stringToRemove.Length)).Trim();
    }

    private string[] GetEvenItems(string[] contentArr)
    {
        int length = contentArr.Length / 2;
        string[] evenContentArr = new string[length];

        int indexB = 0;
        for (int index = 1; index < contentArr.Length; index += 2)
        {
            evenContentArr[indexB] = contentArr[index];
            indexB++;
        }

        return evenContentArr;
    }
    ```

3. En `TestSearchTask` la clase, `OnStartSearch` actualice el método con el código siguiente. Este cambio actualiza el código para admitir el filtro.

    ```csharp
    protected override void OnStartSearch()
    {
        // Use the original content of the text box as the target of the search. 
        var separator = new string[] { Environment.NewLine };
        string[] contentArr = ((TestSearchControl)m_toolWindow.Content).SearchContent.Split(separator, StringSplitOptions.None);

        // Get the search option. 
        bool matchCase = false;
        matchCase = m_toolWindow.MatchCaseOption.Value;

        // Set variables that are used in the finally block.
        StringBuilder sb = new StringBuilder("");
        uint resultCount = 0;
        this.ErrorCode = VSConstants.S_OK;

        try
        {
            string searchString = this.SearchQuery.SearchString;

            // If the search string contains the filter string, filter the content array. 
            string filterString = "lines:\"even\"";

            if (this.SearchQuery.SearchString.Contains(filterString))
            {
                // Retain only the even items in the array.
                contentArr = GetEvenItems(contentArr);

                // Remove 'lines:"even"' from the search string.
                searchString = RemoveFromString(searchString, filterString);
            }

            // Determine the results. 
            uint progress = 0;
            foreach (string line in contentArr)
            {
                if (matchCase == true)
                {
                    if (line.Contains(searchString))
                    {
                        sb.AppendLine(line);
                        resultCount++;
                    }
                }
                else
                {
                    if (line.ToLower().Contains(searchString.ToLower()))
                    {
                        sb.AppendLine(line);
                        resultCount++;
                    }
                }

                SearchCallback.ReportProgress(this, progress++, (uint)contentArr.GetLength(0));

                // Uncomment the following line to demonstrate the progress bar. 
                // System.Threading.Thread.Sleep(100);
            }
        }
        catch (Exception e)
        {
            this.ErrorCode = VSConstants.E_FAIL;
        }
        finally
        {
            ThreadHelper.Generic.Invoke(() =>
            { ((TextBox)((TestSearchControl)m_toolWindow.Content).SearchResultsTextBox).Text = sb.ToString(); });

            this.SearchResults = resultCount;
        }

        // Call the implementation of this method in the base class. 
        // This sets the task status to complete and reports task completion. 
        base.OnStartSearch();
    }
    ```

4. Pruebe el código.

5. Compile la solución y comience la depuración. En la instancia experimental de Visual Studio, abra la ventana de herramientas y, a continuación, elija la flecha abajo en el control de búsqueda.

     Aparece la casilla de verificación **Coincidir mayúsculas** y minúsculas y el filtro **Buscar solo líneas uniformes.**

6. Elija el filtro.

     El cuadro de búsqueda contiene **líneas:"par"** y aparecen los siguientes resultados:

     2 buenos

     4 Bueno

     6 Adiós

7. Eliminar `lines:"even"` del cuadro de búsqueda, active la casilla `g` **Coincidir mayúsculas** y minúsculas y, a continuación, escriba en el cuadro de búsqueda.

     Aparecen los siguientes resultados:

     1 ir

     2 buenos

     5 adiós

8. Elija la X en el lado derecho del cuadro de búsqueda.

     La búsqueda se borra y aparece el contenido original. Sin embargo, la casilla de verificación **Coincidir mayúsculas** y minúsculas sigue activada.
