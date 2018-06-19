---
title: Adición de búsqueda en una ventana de herramientas | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- tool windows, adding search
ms.assetid: f78c4892-8060-49c4-8ecd-4360f1b4d133
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f3b5aa52968be5a2efcf88d7a31505d94f97aaec
ms.sourcegitcommit: 928885ace538bef5b25961358d4f166d648f196a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/27/2018
ms.locfileid: "32032075"
---
# <a name="adding-search-to-a-tool-window"></a>Adición de búsqueda en una ventana de herramientas
Al crear o actualizar una ventana de herramientas en la extensión, puede agregar la misma funcionalidad de búsqueda que aparece en otros lugares en Visual Studio. Esta funcionalidad incluye las siguientes características:  
  
-   Un cuadro de búsqueda que siempre se encuentra en un área de la barra de herramientas personalizada.  
  
-   Un indicador de progreso que se superpone en el mismo cuadro de búsqueda.  
  
-   La capacidad para mostrar los resultados en cuanto escriba cada carácter (búsqueda instantánea) o únicamente después de elegir la tecla ENTRAR (búsqueda a petición).  
  
-   Una lista que muestra los términos para los que ha buscado en más recientemente.  
  
-   La capacidad para filtrar las búsquedas por campos específicos o aspectos de los destinos de búsqueda.  
  
 Si sigue este tutorial, aprenderá a realizar las siguientes tareas:  
  
1.  Cree un proyecto de VSPackage.  
  
2.  Crear una ventana de herramientas que contiene un control de usuario con un cuadro de texto de solo lectura.  
  
3.  Agregar un cuadro de búsqueda a la ventana de herramientas.  
  
4.  Agregue la implementación de la búsqueda.  
  
5.  Habilitar la búsqueda instantánea y la presentación de una barra de progreso.  
  
6.  Agregar un **Coincidir mayúsculas y minúsculas** opción.  
  
7.  Agregar un **buscar únicamente líneas incluso** filtro.  
  
## <a name="to-create-a-vsix-project"></a>Para crear un proyecto de VSIX  
  
1.  Crear un proyecto VSIX denominado `TestToolWindowSearch` con una ventana de herramientas denominada **TestSearch**. Si necesita ayuda para hacerlo, consulte [crear una extensión con una ventana de herramientas](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
## <a name="to-create-a-tool-window"></a>Para crear una ventana de herramientas  
  
1.  En el `TestToolWindowSearch` del proyecto, abra el archivo TestSearchControl.xaml.  
  
2.  Reemplazar el existente `<StackPanel>` bloque con el siguiente bloque, lo cual agrega sólo lectura <xref:System.Windows.Controls.TextBox> a la <xref:System.Windows.Controls.UserControl> en la ventana de herramientas.  
  
    ```xaml  
    <StackPanel Orientation="Vertical">  
        <TextBox Name="resultsTextBox" Height="800.0"  
            Width="800.0"  
            IsReadOnly="True">  
        </TextBox>  
    </StackPanel>  
    ```  
  
3.  En el archivo TestSearchControl.xaml.cs, agregue la siguiente instrucción using:  
  
    ```csharp  
    using System.Text;  
    ```  
  
4.  Quitar el `button1_Click()` método.  
  
     En el **TestSearchControl** de clases, agregue el código siguiente.  
  
     Este código agrega un complemento público <xref:System.Windows.Controls.TextBox> propiedad denominada **SearchResultsTextBox** y una propiedad de cadena pública denominada **SearchContent**. En el constructor, SearchResultsTextBox se establece en el cuadro de texto y SearchContent se inicializa en un conjunto de cadenas delimitada de nueva línea. El contenido del cuadro de texto también se inicializa en el conjunto de cadenas.  
  
     [!code-csharp[ToolWindowSearch#1](../extensibility/codesnippet/CSharp/adding-search-to-a-tool-window_1.cs)]
     [!code-vb[ToolWindowSearch#1](../extensibility/codesnippet/VisualBasic/adding-search-to-a-tool-window_1.vb)]  
  
5.  Compile la solución y comience la depuración. Aparece la instancia experimental de Visual Studio.  
  
6.  En la barra de menús, elija **vista**, **otras ventanas**, **TestSearch**.  
  
     Aparece la ventana de herramientas, pero no aparece todavía, el control de búsqueda.  
  
## <a name="to-add-a-search-box-to-the-tool-window"></a>Para agregar un cuadro de búsqueda a la ventana de herramientas  
  
1.  En el archivo TestSearch.cs, agregue el código siguiente a la `TestSearch` clase. El código invalida el <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.SearchEnabled%2A> propiedad para que el descriptor de acceso get devuelve `true`.  
  
     Para habilitar la búsqueda, es necesario reemplazar el <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.SearchEnabled%2A> propiedad. El <xref:Microsoft.VisualStudio.Shell.ToolWindowPane> la clase implementa <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch> y proporciona una implementación predeterminada que no habilite la búsqueda.  
  
    ```csharp  
    public override bool SearchEnabled  
    {  
        get { return true; }  
    }  
    ```  
  
2.  Compile la solución y comience la depuración. Aparece la instancia experimental.  
  
3.  En la instancia experimental de Visual Studio, abra **TestSearch**.  
  
     En la parte superior de la ventana de herramientas, aparecerá un control de búsqueda con un **búsqueda** marca de agua y un icono de lupa. Sin embargo, no funciona aún búsqueda porque no se ha implementado el proceso de búsqueda.  
  
## <a name="to-add-the-search-implementation"></a>Para agregar la implementación de búsqueda  
 Al habilitar la búsqueda en un <xref:Microsoft.VisualStudio.Shell.ToolWindowPane>, como en el procedimiento anterior, la ventana de herramientas crea un host de Microsoft search. Este host se configura y administra los procesos de búsqueda, que siempre se producen en un subproceso en segundo plano. Dado que la <xref:Microsoft.VisualStudio.Shell.ToolWindowPane> clase administra la creación del host de búsqueda y la configuración de seguridad de la búsqueda, sólo necesita crear una tarea de búsqueda y proporcionar el método de búsqueda. El proceso de búsqueda se produce en un subproceso en segundo plano y se realizan llamadas en el control de ventana de herramientas en el subproceso de interfaz de usuario. Por lo tanto, debe utilizar el <xref:Microsoft.VisualStudio.Shell.ThreadHelper.Invoke%2A> método para administrar todas las llamadas que se realicen en tratar con el control.  
  
1.  En el archivo TestSearch.cs, agregue las siguientes `using` instrucciones:  
  
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
  
2.  En la `TestSearch` de clases, agregue el código siguiente, que lleva a cabo las siguientes acciones:  
  
    -   Invalida el <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.CreateSearch%2A> método para crear una tarea de búsqueda.  
  
    -   Invalida el <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.ClearSearch%2A> método para restaurar el estado del cuadro de texto. Se llama a este método cuando un usuario cancela una tarea de búsqueda y cuando un usuario establece o unsets otra opción o filtro. Ambos <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.CreateSearch%2A> y <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.ClearSearch%2A> se llaman en el subproceso de interfaz de usuario. Por lo tanto, no es necesario obtener acceso al cuadro de texto por medio de la <xref:Microsoft.VisualStudio.Shell.ThreadHelper.Invoke%2A> método.  
  
    -   Crea una clase que se denomina `TestSearchTask` que herede de <xref:Microsoft.VisualStudio.Shell.VsSearchTask>, lo que proporciona una implementación predeterminada de <xref:Microsoft.VisualStudio.Shell.Interop.IVsSearchTask>.  
  
         En `TestSearchTask`, el constructor establece un campo privado que hace referencia a la ventana de herramientas. Para proporcionar el método de búsqueda, invalidar la <xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStartSearch%2A> y <xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStopSearch%2A> métodos. El <xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStartSearch%2A> método es donde se implementa el proceso de búsqueda. Este proceso incluye realizar la búsqueda, mostrar los resultados de búsqueda en el cuadro de texto y llamar a la implementación de la clase base de este método para indicar que la búsqueda no es completa.  
  
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
  
3.  Probar la implementación de búsqueda realizando los pasos siguientes:  
  
    1.  Recompile el proyecto e iniciar la depuración.  
  
    2.  En la instancia experimental de Visual Studio, vuelva a abrir la ventana de herramientas, escriba algún texto de búsqueda en la ventana Buscar y haga clic en ENTRAR.  
  
         Aparecerán los resultados correctos.  
  
## <a name="to-customize-the-search-behavior"></a>Para personalizar el comportamiento de búsqueda  
 Al cambiar la configuración de búsqueda, puede realizar una serie de cambios en cómo aparece el control de búsqueda y cómo se realizará la búsqueda. Por ejemplo, puede cambiar la marca de agua (el texto predeterminado que aparece en el cuadro de búsqueda), el mínimo y ancho máximo del control de búsqueda y si se debe mostrar una barra de progreso. También puede cambiar el punto en los resultados de la búsqueda empiecen a aparecer (a petición o búsqueda instantánea) y si se debe mostrar una lista de términos para los que buscan recientemente. Puede encontrar la lista completa de opciones en la <xref:Microsoft.VisualStudio.PlatformUI.SearchSettingsDataSource> clase.  
  
1.  En el archivo TestSearch.cs, agregue el código siguiente a la `TestSearch` clase. Este código permite búsqueda instantánea en lugar de la búsqueda a petición (lo que significa que el usuario no tiene que hacer clic en ENTRAR). El código invalida el `ProvideSearchSettings` método en el `TestSearch` (clase), que es necesario cambiar la configuración predeterminada.  
  
    ```csharp  
    public override void ProvideSearchSettings(IVsUIDataSource pSearchSettings)  
    {  
        Utilities.SetValue(pSearchSettings,   
            SearchSettingsDataSource.SearchStartTypeProperty.Name,   
            (uint)VSSEARCHSTARTTYPE.SST_INSTANT);}  
    ```  
  
2.  Probar la nueva configuración por volver a generar la solución y reiniciar el depurador.  
  
     Resultados de la búsqueda aparecen cada vez que se escribe un carácter en el cuadro de búsqueda.  
  
3.  En el `ProvideSearchSettings` método, agregue la siguiente línea, que permite la presentación de una barra de progreso.  
  
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
  
     En la barra de progreso que aparezca, deberá indicarse el progreso. Para informar sobre el progreso, quite el siguiente código en el `OnStartSearch` método de la `TestSearchTask` clase:  
  
    ```csharp  
    SearchCallback.ReportProgress(this, progress++, (uint)contentArr.GetLength(0));  
    ```  
  
4.  Para disminuir la velocidad de procesamiento suficiente que el progreso de la barra está visible, elimine la línea siguiente en el `OnStartSearch` método de la `TestSearchTask` clase:  
  
    ```csharp  
    System.Threading.Thread.Sleep(100);  
    ```  
  
5.  Probar la nueva configuración, volver a generar la solución y comenzar a depurar.  
  
     La barra de progreso aparece en la ventana de búsqueda (como una línea azul debajo del cuadro de texto de búsqueda) cada vez que lleva a cabo una búsqueda.  
  
## <a name="to-enable-users-to-refine-their-searches"></a>Permitir a los usuarios restringir las búsquedas  
 Puede que los usuarios pueden restringir las búsquedas por medio de opciones como **Coincidir mayúsculas y minúsculas** o **palabras completas**. Opciones pueden ser booleanos, que aparecen como comandos, que aparecen como botones o casillas de verificación. En este tutorial, creará una opción de tipo boolean.  
  
1.  En el archivo TestSearch.cs, agregue el código siguiente a la `TestSearch` clase. El código invalida el `SearchOptionsEnum` método, que permite la implementación de la búsqueda detectar si una opción determinada está activada o desactivada. El código en `SearchOptionsEnum` agrega una opción para hacer coincidir mayúsculas y minúsculas para un <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumWindowSearchOptions> enumerador. La opción Coincidir mayúsculas y minúsculas se pone a disposición como el `MatchCaseOption` propiedad.  
  
    ```csharp  
    private IVsEnumWindowSearchOptions m_optionsEnum;  
    public override IVsEnumWindowSearchOptions SearchOptionsEnum  
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
  
2.  En el `TestSearchTask` de la clase, quite el comentario de la siguiente línea en el `OnStartSearch` método:  
  
    ```csharp
    matchCase = m_toolWindow.MatchCaseOption.Value;
    ```
  
3.  Pruebe la opción:  
  
    1.  Compile la solución y comience la depuración. Aparece la instancia experimental.  
  
    2.  En la ventana de herramientas, elija la flecha de lista desplegable del lado derecho del cuadro de texto.  
  
         El **Coincidir mayúsculas y minúsculas** aparece la casilla de verificación.  
  
    3.  Seleccione el **Coincidir mayúsculas y minúsculas** casilla de verificación y, a continuación, realice alguna de las búsquedas.  
  
## <a name="to-add-a-search-filter"></a>Para agregar un filtro de búsqueda  
 Puede agregar filtros de búsqueda que permiten a los usuarios redefinir el conjunto de destinos de búsqueda. Por ejemplo, puede filtrar archivos en el Explorador de archivos, las fechas en el que se han modificado más recientemente y sus extensiones de nombre de archivo. En este tutorial, agregará un filtro incluso únicamente para las líneas. Cuando el usuario elige ese filtro, el host de búsqueda agrega las cadenas que especifican en la consulta de búsqueda. A continuación, puede identificar estas cadenas dentro del método de búsqueda y filtrar los destinos de búsqueda en consecuencia.  
  
1.  En el archivo TestSearch.cs, agregue el código siguiente a la `TestSearch` clase. El código implementa `SearchFiltersEnum` agregando un <xref:Microsoft.VisualStudio.PlatformUI.WindowSearchSimpleFilter> que especifica para filtrar los resultados de búsqueda para que aparezcan solo incluso las líneas.  
  
    ```csharp  
    public override IVsEnumWindowSearchFilters SearchFiltersEnum  
    {  
        get  
        {  
            List<IVsWindowSearchFilter> list = new List<IVsWindowSearchFilter>();  
            list.Add(new WindowSearchSimpleFilter("Search even lines only", "Search even lines only", "lines", "even"));  
            return new WindowSearchFilterEnumerator(list) as IVsEnumWindowSearchFilters;  
        }  
    }  
  
    ```  
  
     Ahora, el control de búsqueda muestra el filtro de búsqueda `Search even lines only`. Cuando el usuario elige el filtro, la cadena `lines:"even"` aparece en el cuadro de búsqueda. Otros criterios de búsqueda pueden aparecer al mismo tiempo que el filtro. Cadenas de búsqueda pueden aparecer antes que el filtro, después el filtro, o ambas cosas.  
  
2.  En el archivo TestSearch.cs, agregue los métodos siguientes para la `TestSearchTask` (clase), que se encuentra en la `TestSearch` clase. Estos métodos admiten la `OnStartSearch` método, que modificará en el paso siguiente.  
  
    ```csharp  
    private string RemoveFromString(string origString, string stringToRemove)  
    {  
        int index = origString.IndexOf(stringToRemove);  
        if (index == -1)  
            return origString;  
        else   
             return (origString.Substring(0, index) + origString.Substring(index + stringToRemove.Length)).Trim();  
    }  
  
    private string[] GetEvenItems(string[] contentArr)  
    {  
        int length = contentArr.Length / 2;  
        string[] evenContentArr = new string[length];  
  
        int indexB = 0;  
        for (int index = 1; index < contentArr.Length; index += 2)  
        {  
            evenContentArr[indexB] = contentArr[index];  
            indexB++;  
        }  
  
        return evenContentArr;  
    }  
    ```  
  
3.  En el `TestSearchTask` clase, actualice el `OnStartSearch` método por el código siguiente. Este cambio actualiza el código para admitir el filtro.  
  
    ```csharp  
    protected override void OnStartSearch()  
    {  
        // Use the original content of the text box as the target of the search.   
        var separator = new string[] { Environment.NewLine };  
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
  
4.  Probar el código.  
  
5.  Compile la solución y comience la depuración. En la instancia experimental de Visual Studio, abra la ventana de herramientas y, a continuación, elija la flecha de lista desplegable en el control de búsqueda.  
  
     El **Coincidir mayúsculas y minúsculas** casilla de verificación y **buscar únicamente líneas incluso** aparecen de filtro.  
  
6.  Elija el filtro.  
  
     El cuadro de búsqueda contiene **líneas: "incluso"**, y aparecen los siguientes resultados:  
  
     buena 2  
  
     4 buena  
  
     Adiós 6  
  
7.  Eliminar `lines:"even"` en el cuadro de búsqueda, seleccione la **Coincidir mayúsculas y minúsculas** casilla de verificación y, a continuación, escriba `g` en el cuadro de búsqueda.  
  
     Aparecen los siguientes resultados:  
  
     Ir de 1  
  
     buena 2  
  
     Adiós 5  
  
8.  Elija la X en el lado derecho del cuadro de búsqueda.  
  
     La búsqueda está desactivada, y se mostrará el contenido original. Sin embargo, el **Coincidir mayúsculas y minúsculas** todavía está activada la casilla de verificación.