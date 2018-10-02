---
title: Analizar el uso de CPU en una aplicación universal de Windows | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: c122b08e-e3bf-43e6-bd6c-e776e178fd9a
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: f57fdf99c6ccb19c6d8add600943d799d3a28ca4
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47566209"
---
# <a name="analyze-cpu-usage-in-a-windows-universal-app"></a>Analizar el uso de CPU en una aplicación universal de Windows
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [analizar el uso de CPU en una aplicación Windows Universal](https://docs.microsoft.com/visualstudio/profiling/analyze-cpu-usage-in-a-windows-universal-app).  
  
Se aplica a Windows y Windows Phone] (.. /Image/windows_and_phone_content.png "windows_and_phone_content")  
  
 Si necesita investigar problemas de rendimiento de la aplicación, un buen punto de partida es entender cómo utiliza la CPU. La herramienta **Uso de CPU** muestra que la CPU dedica tiempo a ejecutar código. Para centrarse en escenarios concretos, uso de CPU se puede ejecutar con la [IU XAML](http://msdn.microsoft.com/library/4ff84cd1-4e63-4fda-b34f-3ef862a6e480) herramienta, el [consumo de energía](../profiling/analyze-energy-use-in-store-apps.md) herramienta o ambas herramientas en una única sesión de diagnóstico.  
  
> [!NOTE]
>  La herramienta **Uso de CPU** no se puede utilizar con las aplicaciones de Windows Phone Silverlight 8.1.  
  
 Este tutorial le ofrece información sobre la recopilación y el análisis de datos de Uso de CPU de una aplicación sencilla de XAML universal de Windows.  
  
##  <a name="BKMK_Create_the_CpuUseDemo_project"></a> Crear el proyecto CpuUseDemo  
 **CpuUseDemo** es una aplicación creada para mostrar cómo recopilar y analizar datos de Uso de CPU. Los botones generan un número al llamar a un método que selecciona el valor máximo de varias llamadas a una función. La función llamada crea un número muy alto de valores aleatorios y luego devuelve el último. Los datos se muestran en un cuadro de texto.  
  
1.  Cree un proyecto nuevo de la aplicación de Windows Universal de C# denominado **CpuUseDemo** mediante la plantilla **BlankApp**.  
  
     ![Cree el proyecto CpuUseDemoProject](../profiling/media/cpu-use-newproject.png "CPU_USE_NewProject")  
  
2.  Reemplace MainPage.xaml con [este código](#BKMK_MainPage_xaml).  
  
3.  Reemplace MainPage.xaml.cs con [este código](#BKMK_MainPage_xaml_cs).  
  
4.  Cree la aplicación y pruébela. La aplicación es lo suficientemente sencilla para mostrar algunos casos comunes de análisis de datos de Uso de CPU.  
  
##  <a name="BKMK_Collect_CPU_usage_data"></a> Recopilar datos de Uso de CPU  
 ![Ejecute una compilación de la versión de la aplicación en el simulador](../profiling/media/cpu-use-wt-setsimulatorandretail.png "CPU_USE_WT_SetSimulatorAndRetail")  
  
1.  En Visual Studio, establezca el destino de implementación en **Simulator** y la configuración de la solución en **Release**.  
  
    -   La ejecución de la aplicación en el simulador le permite alternar fácilmente entre la aplicación y el IDE de Visual Studio.  
  
    -   La ejecución de esta aplicación en modo **Release** le ofrece una mejor visión del rendimiento real de la aplicación.  
  
2.  En el menú **Depurar** , elija **Performance Profiler...**(Generador de perfiles de rendimiento...).  
  
3.  En el concentrador Rendimiento y diagnósticos, elija **Uso de CPU** y, a continuación, elija **Inicio**.  
  
     ![Iniciar la sesión de diagnóstico de CpuUsage](../profiling/media/cpu-use-wt-perfdiaghub.png "CPU_USE_WT_PerfDiagHub")  
  
4.  Cuando se inicie la aplicación, haga clic en **Obtener número máximo**. Espere aproximadamente un segundo después de que se muestre el resultado y elija **Obtener async del número máximo**. Esperar entre los clics de botón hace que resulte más fácil aislar las rutinas de clic de botón en el informe de diagnóstico.  
  
5.  Cuando aparezca la segunda línea de resultados, elija **Detener recolección** en el hub Rendimiento y diagnósticos.  
  
 ![Detener la recolección de datos de CpuUsage](../profiling/media/cpu-use-wt-stopcollection.png "CPU_USE_WT_StopCollection")  
  
 La herramienta Uso de CPU analiza y muestra el informe.  
  
 ![Informe de CpuUsage](../profiling/media/cpu-use-wt-report.png "CPU_USE_WT_Report")  
  
##  <a name="BKMK_Analyze_the_CPU_Usage_report"></a> Analizar el informe de Uso de CPU  
  
###  <a name="BKMK_CPU_utilization_timeline_graph"></a> Gráfico de escala de tiempo de utilización de CPU  
 ![Gráfico de escala de tiempo (%) de CpuUtilization](../profiling/media/cpu-use-wt-timelinegraph.png "CPU_USE_WT_TimelineGraph")  
  
 El gráfico Uso de CPU muestra la actividad de CPU de la aplicación como un porcentaje del tiempo total de CPU de todos los núcleos de procesador del dispositivo. Los datos de este informe se recopilaron en un equipo de doble núcleo. Los dos grandes picos representan la actividad de CPU de los dos clic de botón. `GetMaxNumberButton_Click` se ejecuta de forma síncrona en un único núcleo, así que tiene sentido que la altura del gráfico del método nunca supere el 50 %. `GetMaxNumberAsycButton_Click` se ejecuta de forma asíncrona en ambos núcleos, así que una vez más parece correcto que el pico se acerque a la utilización de todos los recursos de la CPU en ambos núcleos.  
  
####  <a name="BKMK_Select_timeline_segments_to_view_details"></a> Seleccione segmentos de la escala de tiempo para ver detalles  
 Utilice las barras de selección de la escala de tiempo de **Sesión de diagnóstico** para centrarse en los datos de GetMaxNumberButton_Click:  
  
 ![GetMaxNumberButton_Click seleccionado](../profiling/media/cpu-use-wt-getmaxnumberreport.png "CPU_USE_WT_GetMaxNumberReport")  
  
 La escala de tiempo de **Sesión de diagnóstico** ahora muestra el tiempo empleado en el segmento seleccionado (un poco más de 2 segundos en este informe) y filtra el árbol de llamadas para mostrar solo esos métodos que se ejecutaron en la selección.  
  
 Ahora seleccione el segmento `GetMaxNumberAsyncButton_Click`.  
  
 ![Selección de informes GetMaxNumberAsyncButton_Click](../profiling/media/cpu-use-wt-getmaxnumberasync-selected.png "CPU_USE_WT_GetMaxNumberAsync_Selected")  
  
 Este método se completa aproximadamente un segundo más rápido que `GetMaxNumberButton_Click`, pero el significado de las entradas del árbol de llamadas es menos obvio.  
  
###  <a name="BKMK_The_CPU_Usage_call_tree"></a> Árbol de llamadas de Uso de CPU  
 Para comenzar a comprender la información del árbol de llamadas, vuelva a seleccionar el segmento `GetMaxNumberButton_Click` y vea los detalles del árbol de llamadas.  
  
####  <a name="BKMK_Call_tree_structure"></a> Estructura del árbol de llamadas  
 ![Árbol de llamadas GetMaxNumberButton_Click](../profiling/media/cpu-use-wt-getmaxnumbercalltree-annotated.png "CPU_USE_WT_GetMaxNumberCallTree_annotated")  
  
|||  
|-|-|  
|![Paso 1](../profiling/media/procguid-1.png "ProcGuid_1")|El nodo de nivel superior de los árboles de llamadas de Uso de CPU es un pseudonodo|  
|![Paso 2](../profiling/media/procguid-2.png "ProcGuid_2")|En la mayoría de las aplicaciones, si la opción **Mostrar código externo** está deshabilitada, el nodo de segundo nivel es un nodo **[Código externo]** que contiene el código del sistema y Framework que inicia y detiene la aplicación, dibuja la IU, controla la programación de subprocesos y ofrece otros servicios de bajo nivel a la aplicación.|  
|![Paso 3](../profiling/media/procguid-3.png "ProcGuid_3")|Los elementos secundarios del nodo de segundo nivel son los métodos de código de usuario y las rutinas asíncronas llamados o creados por el sistema de segundo nivel y el código de Framework.|  
|![Paso 4](../profiling/media/procguid-4.png "ProcGuid_4")|Los nodos secundarios de un método contienen datos únicamente de las llamadas del método principal. Cuando está deshabilitada la opción **Mostrar código externo** , los métodos de aplicación también pueden contener un nodo **[Código externo]** .|  
  
####  <a name="BKMK_External_Code"></a> Código externo  
 El código externo son funciones de los componentes del sistema y del marco que ejecuta el código que usted escribe. El código externo incluye funciones que inician y detienen la aplicación, dibujan la UI, controlan los subprocesos y proporcionan otros servicios de bajo nivel a la aplicación. En la mayoría de los casos, no le interesará el código externo, por lo que el árbol de llamadas de Uso de CPU reúne las funciones externas de un método de usuario en un nodo **[Código externo]** .  
  
 Si quiere ver las rutas de acceso a las llamadas de código externo, elija **Mostrar código externo** en la lista **Vista de filtro** y luego **Aplicar**.  
  
 ![Elegir la vista Filtro y, después, Mostrar código externo](../profiling/media/cpu-use-wt-filterview.png "CPU_USE_WT_FilterView")  
  
 Tenga en cuenta que muchas cadenas de llamadas de código externo están profundamente anidadas, así que el ancho de la columna Nombre de la función puede superar el ancho de pantalla de todos los monitores, excepto de los más grandes. Si ese es el caso, los nombres de función se muestran como **[…]**:  
  
 ![Código externo anidado en el árbol de llamadas](../profiling/media/cpu-use-wt-showexternalcodetoowide.png "CPU_USE_WT_ShowExternalCodeTooWide")  
  
 Use el cuadro de búsqueda para localizar un nodo que esté buscando y luego use la barra de desplazamiento horizontal para visualizar los datos:  
  
 ![Buscar código externo anidado](../profiling/media/cpu-use-wt-showexternalcodetoowide-found.png "CPU_USE_WT_ShowExternalCodeTooWide_Found")  
  
###  <a name="BKMK_Call_tree_data_columns"></a> Columnas de datos del árbol de llamadas  
  
|||  
|-|-|  
|**CPU total (%)**|![% total de ecuación de datos](../profiling/media/cpu-use-wt-totalpercentequation.png "CPU_USE_WT_TotalPercentEquation")<br /><br /> El porcentaje de actividad de la CPU de la aplicación en el intervalo de tiempo seleccionado que usaron las llamadas a la función y las funciones llamadas por la función. Tenga en cuenta que esto no es lo mismo que el gráfico de línea cronológica **Utilización de CPU** , que compara la actividad total de la aplicación en un intervalo de tiempo con la capacidad total de CPU disponible.|  
|**Solo CPU (%)**|![% de autoecuación](../profiling/media/cpu-use-wt-selflpercentequation.png "CPU_USE_WT_SelflPercentEquation")<br /><br /> El porcentaje de actividad de la CPU de la aplicación en el intervalo de tiempo seleccionado que usaron las llamadas a la función, excluidas la actividad de las funciones llamadas por la función.|  
|**CPU total (ms)**|El número de milisegundos empleado en llamadas a la función en el intervalo de tiempo seleccionado y las funciones que fueron llamadas por la función.|  
|**Propia CPU (ms)**|El número de milisegundos empleado en llamadas a la función en el intervalo de tiempo seleccionado y las funciones que fueron llamadas por la función.|  
|**Módulo**|El nombre del módulo que contiene la función o el número de módulos que contienen las funciones en un nodo [Código externo].|  
  
###  <a name="BKMK_Asynchronous_functions_in_the_CPU_Usage_call_tree"></a> Funciones asincrónicas en el árbol de llamadas de Uso de CPU  
 Cuando el compilador encuentra un método asincrónico, crea una clase oculta para controlar la ejecución del método. Conceptualmente, la clase es una máquina de estados que incluye una lista de funciones generadas por el compilador que llaman a operaciones del método original de forma asincrónica, así como las devoluciones de llamadas, el programador y los iteradores necesarios para que funcionen correctamente. Cuando un método principal llama al método original, el tiempo de ejecución quita al método del contexto de ejecución del elemento principal y ejecuta los métodos de la clase oculta en el contexto del código del sistema y Framework que controla la ejecución de la aplicación. A menudo, aunque no siempre, los métodos asincrónicos se ejecutan en uno o varios subprocesos diferentes. Este código se muestra en el árbol de llamadas de Uso de CPU como elementos secundarios del nodo **[Código externo]** que se encuentra justo debajo del nodo superior del árbol.  
  
 Para verlo en el ejemplo, vuelva a seleccionar el segmento `GetMaxNumberAsyncButton_Click` en la escala de tiempo.  
  
 ![Selección de informes GetMaxNumberAsyncButton_Click](../profiling/media/cpu-use-wt-getmaxnumberasync-selected.png "CPU_USE_WT_GetMaxNumberAsync_Selected")  
  
 Los dos primeros nodos bajo **[Código externo]** son los métodos generados por el compilador de la clase de la máquina de estados. El tercero es la llamada al método original. Al expandir los métodos generados se muestra lo que está sucediendo.  
  
 ![Árbol de llamadas GetMaxNumberAsyncButton_Click expandido](../profiling/media/cpu-use-wt-getmaxnumberasync-expandedcalltree.png "CPU_USE_WT_GetMaxNumberAsync_ExpandedCallTree")  
  
-   `MainPage::GetMaxNumberAsyncButton_Click` hace poca cosa; administra una lista de valores de la tarea, calcula el valor máximo de los resultados y muestra el resultado.  
  
-   `MainPage+<GetMaxNumberAsyncButton_Click>d__3::MoveNext` muestra la actividad necesaria para programar e iniciar las 48 tareas que incluyen la llamada en `GetNumberAsync`.  
  
-   `MainPage::<GetNumberAsync>b__b` muestra la actividad de las tareas que llaman a `GetNumber`.  
  
##  <a name="BKMK_Next_steps"></a> Pasos siguientes  
 La aplicación CpuUseDemo no es la más brillante de las aplicaciones, pero puede aumentar su utilidad si la usa para experimentar con el funcionamiento asíncrono y otras herramientas del hub Rendimiento y diagnósticos.  
  
-   Tenga en cuenta que `MainPage::<GetNumberAsync>b__b` emplea más tiempo en [Código externo] que en la ejecución del método GetNumber. La mayor parte de este tiempo es la sobrecarga de las operaciones asíncronas. Intente aumentar el número de tareas (establecido en la constante `NUM_TASKS` de MainPage.xaml.cs) y reducir el número de iteraciones de `GetNumber` (cambie el valor `MIN_ITERATIONS`). Ejecute el escenario de recopilación y compare la actividad de CPU de `MainPage::<GetNumberAsync>b__b` con la de la sesión de diagnóstico original de Uso de CPU. Intente reducir las tareas y aumentar las iteraciones.  
  
-   A los usuarios no les suele preocupar el rendimiento real de la aplicación; les importa su rendimiento y capacidad de respuesta percibidos. La herramienta Capacidad de respuesta de la IU de XAML muestra detalles de actividad en el subproceso de la IU que afecta a la capacidad de respuesta percibida.  
  
     Cree una nueva sesión en el hub Rendimiento y diagnósticos y agregue las herramientas Capacidad de respuesta de la IU de XAML y Uso de CPU. Ejecute el escenario de colecciones. Si ha leído hasta aquí, el informe probablemente no le diga nada que ya no haya descubierto, pero las diferencias en el gráfico de escala de tiempo de **utilización del subproceso de IU** de los dos métodos son impactantes. En aplicaciones complejas del mundo real, la combinación de herramientas puede resultar muy útil.  
  
##  <a name="BKMK_MainPage_xaml"></a> MainPage.xaml  
  
```csharp  
<Page  
    x:Class="CpuUseDemo.MainPage"  
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
    xmlns:local="using:CpuUseDemo"  
    xmlns:d="http://schemas.microsoft.com/expression/blend/2008"  
    xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
    mc:Ignorable="d">  
  
    <Page.Resources>  
        <Style TargetType="TextBox">  
            <Setter Property="FontFamily"  Value="Lucida Console" />  
        </Style>  
    </Page.Resources>  
    <Grid Background="{ThemeResource ApplicationPageBackgroundThemeBrush}">  
        <Grid.RowDefinitions>  
            <RowDefinition Height="Auto" />  
            <RowDefinition Height="*" />  
        </Grid.RowDefinitions>  
        <StackPanel Grid.Row="0" Orientation="Horizontal"  Margin="0,40,0,0">  
            <Button Name="GetMaxNumberButton" Click="GetMaxNumberButton_Click"  Content="Get Max Number" />  
            <Button Name="GetMaxNumberAsyncButton" Click="GetMaxNumberAsyncButton_Click"  Content="Get Max Number Async" />  
        </StackPanel>  
        <StackPanel Grid.Row="1">  
            <TextBox Name="TextBox1" AcceptsReturn="True" />  
        </StackPanel>  
    </Grid>  
  
</Page>  
  
```  
  
##  <a name="BKMK_MainPage_xaml_cs"></a> MainPage.xaml.cs  
  
```csharp  
using System;  
using System.Collections.Generic;  
using System.IO;  
using System.Linq;  
using System.Runtime.InteropServices.WindowsRuntime;  
using Windows.Foundation;  
using Windows.Foundation.Collections;  
using Windows.UI.Xaml;  
using Windows.UI.Xaml.Controls;  
using Windows.UI.Xaml.Controls.Primitives;  
using Windows.UI.Xaml.Data;  
using Windows.UI.Xaml.Input;  
using Windows.UI.Xaml.Media;  
using Windows.UI.Xaml.Navigation;  
using Windows.Foundation.Diagnostics;  
using System.Threading;  
using System.Threading.Tasks;  
using System.Collections.Concurrent;  
  
// The Blank Page item template is documented at http://go.microsoft.com/fwlink/?LinkId=234238  
  
namespace CpuUseDemo  
{  
    /// <summary>  
    /// An empty page that can be used on its own or navigated to within a Frame.  
    /// </summary>  
    public sealed partial class MainPage : Page  
    {  
        public MainPage()  
        {  
            this.InitializeComponent();  
        }  
  
        const int NUM_TASKS = 48;  
        const int MIN_ITERATIONS = int.MaxValue / 1000;  
        const int MAX_ITERATIONS = MIN_ITERATIONS + 10000;  
  
        long m_totalIterations = 0;  
        readonly object m_totalItersLock = new object();  
  
        private void GetMaxNumberButton_Click(object sender, RoutedEventArgs e)  
        {  
            GetMaxNumberAsyncButton.IsEnabled = false;  
            lock (m_totalItersLock)  
            {  
                m_totalIterations = 0;  
            }  
            List<int> tasks = new List<int>();  
            for (var i = 0; i < NUM_TASKS; i++)  
            {  
                var result = 0;  
                result = GetNumber();  
                tasks.Add(result);  
            }  
            var max = tasks.Max();  
            var s = GetOutputString("GetMaxNumberButton_Click", NUM_TASKS, max, m_totalIterations);  
            TextBox1.Text += s;  
            GetMaxNumberAsyncButton.IsEnabled = true;  
        }  
  
        private async void GetMaxNumberAsyncButton_Click(object sender, RoutedEventArgs e)  
        {  
            GetMaxNumberButton.IsEnabled = false;  
            GetMaxNumberAsyncButton.IsEnabled = false;  
            lock (m_totalItersLock)  
            {  
                m_totalIterations = 0;  
            }  
            var tasks = new ConcurrentBag<Task<int>>();  
            for (var i = 0; i < NUM_TASKS; i++)  
            {  
                tasks.Add(GetNumberAsync());  
            }  
            await Task.WhenAll(tasks.ToArray());  
            var max = 0;  
            foreach (var task in tasks)  
            {  
                max = Math.Max(max, task.Result);  
            }  
            var func = "GetMaxNumberAsyncButton_Click";  
            var outputText = GetOutputString(func, NUM_TASKS, max, m_totalIterations);  
            TextBox1.Text += outputText;  
            this.GetMaxNumberButton.IsEnabled = true;  
            GetMaxNumberAsyncButton.IsEnabled = true;  
        }  
  
        private int GetNumber()  
        {  
            var rand = new Random();  
            var iters = rand.Next(MIN_ITERATIONS, MAX_ITERATIONS);  
            var result = 0;  
            lock (m_totalItersLock)  
            {  
                m_totalIterations += iters;  
            }  
            // we're just spinning here  
            // and using Random to frustrate compiler optimizations  
            for (var i = 0; i < iters; i++)  
            {  
                result = rand.Next();  
            }  
            return result;  
        }  
  
        private Task<int> GetNumberAsync()  
        {  
            return Task<int>.Run(() =>  
            {  
                return GetNumber();  
            });  
        }  
  
        string GetOutputString(string func, int cycles, int max, long totalIters)  
        {  
            var fmt = "{0,-35}Tasks:{1,3}    Maximum:{2, 12}    Iterations:{3,12}\n";  
            return String.Format(fmt, func, cycles, max, totalIters);  
        }  
  
    }  
}  
  
```



