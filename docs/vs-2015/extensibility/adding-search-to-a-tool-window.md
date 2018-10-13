---
title: Adición de búsqueda a una ventana de herramientas | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- tool windows, adding search
ms.assetid: f78c4892-8060-49c4-8ecd-4360f1b4d133
caps.latest.revision: 39
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ab478d6a007081787d8b076e906f5094caea8b2d
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49206926"
---
# <a name="adding-search-to-a-tool-window"></a>Adición de búsqueda a una ventana de herramientas
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Al crear o actualizar una ventana de herramientas en la extensión, puede agregar la misma funcionalidad de búsqueda que aparece en otro lugar en Visual Studio. Esta funcionalidad incluye las siguientes características:  
  
-   Un cuadro de búsqueda que siempre se encuentra en un área de la barra de herramientas personalizada.  
  
-   Un indicador de progreso que se superpone en el cuadro de búsqueda propio.  
  
-   La capacidad para mostrar los resultados tan pronto como escriba cada carácter (búsqueda instantánea) o únicamente después de elegir la tecla ENTRAR (búsqueda bajo demanda).  
  
-   Una lista que muestra los términos para los que ha buscado más recientemente.  
  
-   La capacidad de filtrar las búsquedas por campos específicos o aspectos de los destinos de búsqueda.  
  
 Siguiendo este tutorial, obtendrá información sobre cómo realizar las siguientes tareas:  
  
1.  Cree un proyecto de VSPackage.  
  
2.  Crear una ventana de herramientas que contiene un control de usuario con un cuadro de texto de solo lectura.  
  
3.  Agregar un cuadro de búsqueda a la ventana de herramientas.  
  
4.  Agregue la implementación de la búsqueda.  
  
5.  Habilitar la búsqueda instantánea y la presentación de una barra de progreso.  
  
6.  Agregar un **Coincidir mayúsculas y minúsculas** opción.  
  
7.  Agregar un **buscar sólo líneas incluso** filtro.  
  
## <a name="to-create-a-vsix-project"></a>Para crear un proyecto de VSIX  
  
1.  Cree un proyecto VSIX denominado `TestToolWindowSearch` con una ventana de herramientas denominada **TestSearch**. Si necesita ayuda para hacerlo, consulte [Creating an Extension with a Tool Window](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
## <a name="to-create-a-tool-window"></a>Para crear una ventana de herramientas  
  
1.  En el `TestToolWindowSearch` del proyecto, abra el archivo TestSearchControl.xaml.  
  
2.  Reemplazar existente `<StackPanel>` bloque con el siguiente bloque, que agrega solo lectura <xref:System.Windows.Controls.TextBox> a la <xref:System.Windows.Controls.UserControl> en la ventana de herramientas.  
  
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
  
     Este código agrega una pública <xref:System.Windows.Controls.TextBox> propiedad denominada **SearchResultsTextBox** y una propiedad de cadena pública denominada **SearchContent**. En el constructor, SearchResultsTextBox se establece en el cuadro de texto y SearchContent se inicializa en un conjunto delimitado de nueva línea de cadenas. También se inicializa el contenido del cuadro de texto para el conjunto de cadenas.  
  
    ```csharp  
    public partial class TestSearchControl : UserControl  
    {  
        public TextBox SearchResultsTextBox { get; set; }  
        public string SearchContent { get; set; }  
  
        public TestSearchControl()  
        {  
            InitializeComponent();  
  
            this.SearchResultsTextBox = resultsTextBox;  
            this.SearchContent = BuildContent();  
  
            this.SearchResultsTextBox.Text = this.SearchContent;  
        }  
  
        private string BuildContent()  
        {  
            StringBuilder sb = new StringBuilder();  
            sb.AppendLine("1 go");  
            sb.AppendLine("2 good");  
            sb.AppendLine("3 Go");  
            sb.AppendLine("4 Good");  
            sb.AppendLine("5 goodbye");  
            sb.AppendLine("6 Goodbye");  
  
            return sb.ToString();  
        }  
    }  
    ```  
  
     [!code-csharp[ToolWindowSearch#1](../snippets/csharp/VS_Snippets_VBCSharp/toolwindowsearch/cs/mycontrol.xaml.cs#1)]
     [!code-vb[ToolWindowSearch#1](../snippets/visualbasic/VS_Snippets_VBCSharp/toolwindowsearch/vb/mycontrol.xaml.vb#1)]  
  
5.  Compile la solución y comience la depuración. Aparece la instancia experimental de Visual Studio.  
  
6.  En la barra de menús, elija **vista**, **Other Windows**, **TestSearch**.  
  
     Aparece la ventana de herramientas, pero aún no aparece el control de búsqueda.  
  
## <a name="to-add-a-search-box-to-the-tool-window"></a>Para agregar un cuadro de búsqueda a la ventana de herramientas  
  
1.  En el archivo TestSearch.cs, agregue el código siguiente a la `TestSearch` clase. El código invalida el <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.SearchEnabled%2A> propiedad para que devuelva el descriptor de acceso get `true`.  
  
     Para habilitar la búsqueda, se debe reemplazar el <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.SearchEnabled%2A> propiedad. El <xref:Microsoft.VisualStudio.Shell.ToolWindowPane> la clase implementa <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch> y proporciona una implementación predeterminada que no permite la búsqueda.  
  
    ```csharp  
    public override bool SearchEnabled  
    {  
        get { return true; }  
    }  
    ```  
  
2.  Compile la solución y comience la depuración. Aparece la instancia experimental.  
  
3.  En la instancia experimental de Visual Studio, abra **TestSearch**.  
  
     En la parte superior de la ventana de herramientas, aparece un control de búsqueda con un **búsqueda** marca de agua y un icono de lupa de cristal. Sin embargo, no funciona todavía búsqueda porque no se ha implementado el proceso de búsqueda.  
  
## <a name="to-add-the-search-implementation"></a>Para agregar la implementación de búsqueda  
 Al habilitar la búsqueda en un <xref:Microsoft.VisualStudio.Shell.ToolWindowPane>, como en el procedimiento anterior, la ventana de herramientas crea un host de búsqueda. Este host se configura y administra los procesos de búsqueda, que siempre se producen en un subproceso en segundo plano. Dado que la <xref:Microsoft.VisualStudio.Shell.ToolWindowPane> clase administra la creación de lo host de búsqueda y la configuración de seguridad de la búsqueda, sólo necesita crear una tarea de búsqueda y proporcionar el método de búsqueda. Se produce el proceso de búsqueda en un subproceso en segundo plano y se realizan llamadas al control de ventana de herramienta en el subproceso de interfaz de usuario. Por lo tanto, debe usar el <xref:Microsoft.VisualStudio.Shell.ThreadHelper.Invoke%2A> método para administrar todas las llamadas que realice en tratar con el control.  
  
1.  En el archivo TestSearch.cs, agregue la siguiente `using` instrucciones:  
  
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
  
2.  En el `TestSearch` de clases, agregue el código siguiente, que lleva a cabo las siguientes acciones:  
  
    -   Invalida el <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.CreateSearch%2A> método para crear una tarea de búsqueda.  
  
    -   Invalida el <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.ClearSearch%2A> método para restaurar el estado del cuadro de texto. Este método se llama cuando un usuario cancela una tarea de búsqueda y cuando un usuario establece o unsets opciones o filtros. Ambos <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.CreateSearch%2A> y <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.ClearSearch%2A> se llaman en el subproceso de interfaz de usuario. Por lo tanto, no es necesario tener acceso al cuadro de texto por medio de la <xref:Microsoft.VisualStudio.Shell.ThreadHelper.Invoke%2A> método.  
  
    -   Crea una clase que se denomina `TestSearchTask` que herede de <xref:Microsoft.VisualStudio.Shell.VsSearchTask>, que proporciona una implementación predeterminada de <xref:Microsoft.VisualStudio.Shell.Interop.IVsSearchTask>.  
  
         En `TestSearchTask`, el constructor establece un campo privado que hace referencia a la ventana de herramientas. Para proporcionar el método de búsqueda, invalida el <xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStartSearch%2A> y <xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStopSearch%2A> métodos. El <xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStartSearch%2A> método es donde se implementa el proceso de búsqueda. Este proceso incluye la búsqueda, mostrar los resultados de búsqueda en el cuadro de texto y una llamada a la implementación de la clase base de este método para informar de que la búsqueda está completa.  
  
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
  
3.  Probar la implementación de la búsqueda mediante los pasos siguientes:  
  
    1.  Recompilar el proyecto e iniciar la depuración.  
  
    2.  En la instancia experimental de Visual Studio, vuelva a abrir la ventana de herramientas, escriba algún texto de búsqueda en la ventana Buscar y haga clic en ENTRAR.  
  
         Aparecerán los resultados correctos.  
  
## <a name="to-customize-the-search-behavior"></a>Para personalizar el comportamiento de búsqueda  
 Cambiando la configuración de búsqueda, puede realizar una serie de cambios en cómo aparece el control de búsqueda y cómo se realiza la búsqueda. Por ejemplo, puede cambiar la marca de agua (el texto predeterminado que aparece en el cuadro de búsqueda), el mínimo y ancho máximo del control de búsqueda y si se debe mostrar una barra de progreso. También puede cambiar el punto en que los resultados de búsqueda empiecen a aparecer (a petición o búsqueda instantánea) y si se debe mostrar una lista de términos que recientemente buscó. Puede encontrar una lista completa de la configuración en el <xref:Microsoft.VisualStudio.PlatformUI.SearchSettingsDataSource> clase.  
  
1.  En el archivo TestSearch.cs, agregue el código siguiente a la `TestSearch` clase. Este código permite que la búsqueda instantánea en lugar de búsqueda y a petición (lo que significa que el usuario no tiene que hacer clic en ENTRAR). El código invalida el `ProvideSearchSettings` método en el `TestSearch` (clase), que es necesario cambiar la configuración predeterminada.  
  
    ```csharp  
    public override void ProvideSearchSettings(IVsUIDataSource pSearchSettings)  
    {  
        Utilities.SetValue(pSearchSettings,   
            SearchSettingsDataSource.SearchStartTypeProperty.Name,   
            (uint)VSSEARCHSTARTTYPE.SST_INSTANT);}  
    ```  
  
2.  Probar la nueva configuración al volver a generar la solución y reiniciar el depurador.  
  
     Resultados de la búsqueda aparecen cada vez que escriba un carácter en el cuadro de búsqueda.  
  
3.  En el `ProvideSearchSettings` método, agregue la siguiente línea, que permite mostrar una barra de progreso.  
  
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
  
     Para que aparezca la barra de progreso, se debe notificar el progreso. Para notificar el progreso, quite el código siguiente en el `OnStartSearch` método de la `TestSearchTask` clase:  
  
    ```csharp  
    SearchCallback.ReportProgress(this, progress++, (uint)contentArr.GetLength(0));  
    ```  
  
4.  Para disminuir la velocidad de procesamiento suficiente que el progreso de la barra está visible, elimine la línea siguiente en el `OnStartSearch` método de la `TestSearchTask` clase:  
  
    ```csharp  
    System.Threading.Thread.Sleep(100);  
    ```  
  
5.  Volver a generar la solución y comenzar a debugb para probar la nueva configuración.  
  
     La barra de progreso aparece en la ventana de búsqueda (como una línea azul debajo del cuadro de texto de búsqueda) cada vez que realizan una búsqueda.  
  
## <a name="to-enable-users-to-refine-their-searches"></a>Los usuarios pueden restringir las búsquedas  
 Puede permitir que los usuarios restringir las búsquedas por medio de opciones, como **Coincidir mayúsculas y minúsculas** o **solo palabras completas**. Opciones pueden ser booleanos, que aparecen como comandos, que aparecen como botones o casillas de verificación. En este tutorial, creará una opción booleana.  
  
1.  En el archivo TestSearch.cs, agregue el código siguiente a la `TestSearch` clase. El código invalida el `SearchOptionsEnum` método, que permite la implementación de búsqueda detectar si una opción determinada está activada o desactivada. El código en `SearchOptionsEnum` agrega una opción para coincidir mayúsculas y minúsculas para un <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumWindowSearchOptions> enumerador. La opción para hacer coincidir caso está también disponible como el `MatchCaseOption` propiedad.  
  
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
  
2.  En el `TestSearchTask` (clase), quite el comentario de línea matchCase en el `OnStartSearch` método:  
  
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
  
3.  La opción de prueba:  
  
    1.  Compile la solución y comience la depuración. Aparece la instancia experimental.  
  
    2.  En la ventana de herramientas, elija la flecha abajo en el lado derecho del cuadro de texto.  
  
         El **Coincidir mayúsculas y minúsculas** aparece la casilla de verificación.  
  
    3.  Seleccione el **Coincidir mayúsculas y minúsculas** casilla de verificación y, a continuación, realizar algunas búsquedas.  
  
## <a name="to-add-a-search-filter"></a>Para agregar un filtro de búsqueda  
 Puede agregar filtros de búsqueda que permiten a los usuarios refinar el conjunto de destinos de búsqueda. Por ejemplo, puede filtrar los archivos en el Explorador de archivos, las fechas en el que se modificaron más recientemente y sus extensiones de nombre de archivo. En este tutorial, agregará un filtro incluso únicamente para las líneas. Cuando el usuario elige ese filtro, el host de búsqueda agrega las cadenas que especifique para la consulta de búsqueda. A continuación, puede identificar estas cadenas dentro del método de búsqueda y filtrar los destinos de búsqueda en consecuencia.  
  
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
  
     Ahora, el control de búsqueda muestra el filtro de búsqueda `Search even lines only`. Cuando el usuario elige el filtro, la cadena `lines:"even"` aparece en el cuadro de búsqueda. Otros criterios de búsqueda pueden aparecer al mismo tiempo que el filtro. Las cadenas de búsqueda pueden aparecer antes que el filtro, después el filtro, o ambas cosas.  
  
2.  En el archivo TestSearch.cs, agregue los métodos siguientes para el `TestSearchTask` (clase), que se encuentra en la `TestSearch` clase. Estos métodos admiten el `OnStartSearch` método, que se modificará en el paso siguiente.  
  
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
  
3.  En el `TestSearchTask` clase, actualice el `OnStartSearch` método con el código siguiente. Este cambio actualiza el código para admitir el filtro.  
  
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
  
5.  Compile la solución y comience la depuración. En la instancia experimental de Visual Studio, abra la ventana de herramientas y, a continuación, elija la flecha hacia abajo en el control de búsqueda.  
  
     El **Coincidir mayúsculas y minúsculas** casilla de verificación y la **buscar sólo líneas incluso** aparecen de filtro.  
  
6.  Elija el filtro.  
  
     El cuadro de búsqueda contiene **líneas: "incluso"**, y aparecen los siguientes resultados:  
  
     buena 2  
  
     4 buena  
  
     Adiós 6  
  
7.  Eliminar `lines:"even"` en el cuadro de búsqueda, seleccione el **Coincidir mayúsculas y minúsculas** casilla de verificación y, a continuación, escriba `g` en el cuadro de búsqueda.  
  
     Aparecen los siguientes resultados:  
  
     Ir de 1  
  
     buena 2  
  
     Adiós 5  
  
8.  Elija la X en el lado derecho del cuadro de búsqueda.  
  
     La búsqueda está desactivada, y se mostrará el contenido original. Sin embargo, el **Coincidir mayúsculas y minúsculas** aún está seleccionada la casilla de verificación.

