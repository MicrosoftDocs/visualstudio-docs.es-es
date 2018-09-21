---
title: Creación de un elemento de gráfico de vista, comandos y configuración | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 4a2df0a3-42da-4f7b-996f-ee16a35ac922
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8d4f701b58c95a08f9017043138c98b824d4e406
ms.sourcegitcommit: 9765b3fcf89375ca499afd9fc42cf4645b66a8a2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/20/2018
ms.locfileid: "46496108"
---
# <a name="walkthrough-create-a-view-adornment-commands-and-settings-column-guides"></a>Tutorial: Crear un elemento de gráfico de vista, comandos y configuración (guías de columnas)
Puede ampliar el editor de texto y código de Visual Studio con los comandos y los efectos de la vista. Este artículo muestra cómo empezar a trabajar con una característica de extensión popular, guías de columnas. Guías de columnas son líneas visualmente clara dibujadas en la vista del editor de texto para ayudarle a administrar el código para los anchos de columna específicos. En concreto, con formato de código puede ser importante para los ejemplos se incluyen en los documentos, blogs, o los informes de errores.  
  
 En este tutorial, puede:  
  
-   Cree un proyecto VSIX  
  
-   Agregar un elemento de gráfico de vista de editor  
  
-   Agregar compatibilidad para guardar y obtener la configuración (donde a draw guías de columnas y su color)  
  
-   Agregar comandos (Agregar o quitar guías de columnas, cambiar su color)  
  
-   Coloque los comandos en el menú de edición y menús contextuales de documento de texto  
  
-   Agregar compatibilidad para invocar los comandos desde la ventana de comandos de Visual Studio  
  
 Puede probar una versión de la característica de las guías de columna con esta galería de Visual Studio[extensión](https://marketplace.visualstudio.com/items?itemName=PaulHarrington.EditorGuidelines).  
  
 **Tenga en cuenta**: en este tutorial, pega una gran cantidad de código en unos pocos archivos generados por las plantillas de extensión de Visual Studio. Sin embargo, pronto en este tutorial hará referencia a una solución completa en github con otros ejemplos de extensión. El código completo es ligeramente diferente porque tiene iconos de comando real en lugar de usar generictemplate iconos.  
  
## <a name="get-started"></a>Primeros pasos  
 A partir de Visual Studio 2015, no instale el SDK de Visual Studio desde el centro de descarga. Ha incluido como una característica opcional en el programa de instalación de Visual Studio. También puede instalar el SDK de VS más adelante. Para obtener más información, consulte [instalar el SDK de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="set-up-the-solution"></a>Configurar la solución  
 En primer lugar, cree un proyecto VSIX, agregue un elemento de gráfico de vista de editor y, a continuación, agregue un comando (que se agrega un paquete VSPackage para poseer el comando). La arquitectura básica es la siguiente:  
  
-   Tiene un agente de escucha de creación de la vista de texto que se crea un `ColumnGuideAdornment` objeto por cada vista. Este objeto de escucha los eventos sobre el cambio de vista o cambio de configuración, guías de recomposición o actualizar una columna según sea necesario.  
  
-   Hay un `GuidesSettingsManager` que controla la lectura y escritura desde el almacenamiento de configuración de Visual Studio. El Administrador de configuración también tiene operaciones para actualizar las configuraciones compatibles con los comandos de usuario (Agregar columna, quite la columna, cambiar el color).  
  
-   Hay un paquete VSIP que es necesario si tiene los comandos de usuario, pero es solo código reutilizable que inicializa el objeto de implementación de comandos.  
  
-   Hay un `ColumnGuideCommands` comandos de objeto que se ejecuta el usuario y enlaza los controladores de comandos para comandos declaran en el *.vsct* archivo.  
  
 **VSIX**. Use **archivo &#124; nuevo...**  comando para crear un proyecto. Elija la **extensibilidad** nodo bajo **C#** en el panel de navegación izquierdo y elija **proyecto VSIX** en el panel derecho. Escriba el nombre **ColumnGuides** y elija **Aceptar** para crear el proyecto.  
  
 **Ver elemento gráfico**. Presione el botón derecho del puntero en el nodo del proyecto en el Explorador de soluciones. Elija la **agregar &#124; nuevo elemento...**  comando para agregar un nuevo elemento de elemento gráfico de vista. Elija **extensibilidad &#124; Editor** en el panel de navegación izquierdo y elija **elemento gráfico de área de visualización de Editor** en el panel derecho. Escriba el nombre **ColumnGuideAdornment** como el elemento de un nombre y elija **agregar** para agregarlo.  
  
 Puede ver esta plantilla de elemento agregado dos archivos al proyecto (así como las referencias y así sucesivamente): **ColumnGuideAdornment.cs** y **ColumnGuideAdornmentTextViewCreationListener.cs**. Las plantillas de dibujar un rectángulo de color púrpura en la vista. En la sección siguiente, cambia un par de líneas en el agente de escucha de creación de vista y reemplace el contenido de **ColumnGuideAdornment.cs**.  
  
 **Comandos**. En **el Explorador de soluciones**, presione el botón derecho del puntero en el nodo del proyecto. Elija la **agregar &#124; nuevo elemento...**  comando para agregar un nuevo elemento de elemento gráfico de vista. Elija **extensibilidad &#124; VSPackage** en el panel de navegación izquierdo y elija **comando personalizado** en el panel derecho. Escriba el nombre **ColumnGuideCommands** como el elemento de un nombre y elija **agregar**. Además de varias referencias, agregar los comandos y también agrega el paquete **ColumnGuideCommands.cs**, **ColumnGuideCommandsPackage.cs**, y **ColumnGuideCommandsPackage.vsct** . En la sección siguiente, reemplace el contenido de los archivos primeros y últimos para definir e implementar los comandos.  
  
## <a name="set-up-the-text-view-creation-listener"></a>Configurar el agente de escucha de creación de la vista de texto  
 Abra *ColumnGuideAdornmentTextViewCreationListener.cs* en el editor. Este código implementa un controlador para cada vez que Visual Studio crea las vistas de texto. Hay atributos que controlan cuándo se llama al controlador según las características de la vista.  
  
 El código también debe declarar un nivel del elemento gráfico. Cuando el editor de vistas de las actualizaciones, obtiene las capas del elemento gráfico de la vista y de obtiene los elementos del elemento gráfico. Puede declarar la ordenación de la capa en relación con otros usuarios con atributos. Reemplace la línea siguiente:  
  
```csharp  
[Order(After = PredefinedAdornmentLayers.Caret)]  
```  
  
 con estas dos líneas:  
  
```csharp  
[Order(Before = PredefinedAdornmentLayers.Text)]  
[TextViewRole(PredefinedTextViewRoles.Document)]  
```  
  
 Es la línea que se ha reemplazado en un grupo de atributos que declaran un nivel del elemento gráfico. La primera línea ha cambiado a solo los cambios que deben aparecer las líneas de guía de columna. Dibujar las líneas de "antes" significa que el texto en la vista que aparecen detrás de o por debajo del texto. La segunda línea declara que los elementos gráficos de guía de columna son aplicables a las entidades de texto que se ajusten a la noción de un documento, pero podría declarar el elemento de gráfico, por ejemplo, solo trabajo de texto editable. Hay más información [puntos de extensión de editor y el servicio de lenguaje](../extensibility/language-service-and-editor-extension-points.md)  
  
## <a name="implement-the-settings-manager"></a>Implementar el Administrador de configuración  
 Reemplace el contenido de la *GuidesSettingsManager.cs* con el código siguiente (se explica más adelante):  
  
```csharp  
using Microsoft.VisualStudio.Settings;  
using Microsoft.VisualStudio.Shell;  
using Microsoft.VisualStudio.Shell.Settings;  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using System.Windows.Media;  
  
namespace ColumnGuides  
{  
    internal static class GuidesSettingsManager  
    {  
        // Because my code is always called from the UI thred, this succeeds.  
        internal static SettingsManager VsManagedSettingsManager =  
            new ShellSettingsManager(ServiceProvider.GlobalProvider);  
  
        private const int _maxGuides = 5;  
        private const string _collectionSettingsName = "Text Editor";  
        private const string _settingName = "Guides";  
        // 1000 seems reasonable since primary scenario is long lines of code  
        private const int _maxColumn = 1000;   
  
        static internal bool AddGuideline(int column)  
        {  
            if (! IsValidColumn(column))  
                throw new ArgumentOutOfRangeException(  
                    "column",  
                    "The paramenter must be between 1 and " + _maxGuides.ToString());  
            var offsets = GuidesSettingsManager.GetColumnOffsets();  
            if (offsets.Count() >= _maxGuides)  
                return false;  
            // Check for duplicates  
            if (offsets.Contains(column))  
                return false;  
            offsets.Add(column);  
            WriteSettings(GuidesSettingsManager.GuidelinesColor, offsets);  
            return true;  
        }  
  
        static internal bool RemoveGuideline(int column)  
        {  
            if (!IsValidColumn(column))  
                throw new ArgumentOutOfRangeException(  
                    "column", "The paramenter must be between 1 and 10,000");  
            var columns = GuidesSettingsManager.GetColumnOffsets();  
            if (! columns.Remove(column))  
            {  
                // Not present.  Allow user to remove the last column   
                // even if they're not on the right column.  
                if (columns.Count != 1)  
                    return false;  
  
                columns.Clear();  
            }  
            WriteSettings(GuidesSettingsManager.GuidelinesColor, columns);  
            return true;  
        }  
  
        static internal bool CanAddGuideline(int column)  
        {  
            if (!IsValidColumn(column))  
                return false;  
            var offsets = GetColumnOffsets();  
            if (offsets.Count >= _maxGuides)  
                return false;  
            return ! offsets.Contains(column);  
        }  
  
        static internal bool CanRemoveGuideline(int column)  
        {  
            if (! IsValidColumn(column))  
                return false;  
            // Allow user to remove the last guideline regardless of the column.  
            // Okay to call count, we limit the number of guides.  
            var offsets = GuidesSettingsManager.GetColumnOffsets();  
            return offsets.Contains(column) || offsets.Count() == 1;  
        }  
  
        static internal void RemoveAllGuidelines()  
        {  
            WriteSettings(GuidesSettingsManager.GuidelinesColor, new int[0]);  
        }  
  
        private static bool IsValidColumn(int column)  
        {  
            // zero is allowed (per user request)  
            return 0 <= column && column <= _maxColumn;  
        }  
  
        // This has format "RGB(<int>, <int>, <int>) <int> <int>...".  
        // There can be any number of ints following the RGB part,   
        // and each int is a column (char offset into line) where to draw.  
        static private string _guidelinesConfiguration;  
        static private string GuidelinesConfiguration  
        {  
            get  
            {  
                if (_guidelinesConfiguration == null)  
                {  
                    _guidelinesConfiguration =   
                        GetUserSettingsString(  
                            GuidesSettingsManager._collectionSettingsName,  
                            GuidesSettingsManager._settingName)  
                        .Trim();  
                }  
                return _guidelinesConfiguration;  
            }  
  
            set  
            {  
                if (value != _guidelinesConfiguration)  
                {  
                    _guidelinesConfiguration = value;  
                    WriteUserSettingsString(  
                        GuidesSettingsManager._collectionSettingsName,  
                        GuidesSettingsManager._settingName, value);  
                    // Notify ColumnGuideAdornments to update adornments in views.  
                    var handler = GuidesSettingsManager.SettingsChanged;  
                    if (handler != null)  
                        handler();  
                }  
            }  
        }  
  
        internal static string GetUserSettingsString(string collection, string setting)  
        {  
            var store = GuidesSettingsManager  
                            .VsManagedSettingsManager  
                            .GetReadOnlySettingsStore(SettingsScope.UserSettings);  
            return store.GetString(collection, setting, "RGB(255,0,0) 80");  
        }  
  
        internal static void WriteUserSettingsString(string key, string propertyName,  
                                                     string value)  
        {  
            var store = GuidesSettingsManager  
                            .VsManagedSettingsManager  
                            .GetWritableSettingsStore(SettingsScope.UserSettings);  
            store.CreateCollection(key);  
            store.SetString(key, propertyName, value);  
        }  
  
        // Persists settings and sets property with side effect of signaling  
        // ColumnGuideAdornments to update.  
        static private void WriteSettings(Color color, IEnumerable<int> columns)  
        {  
            string value = ComposeSettingsString(color, columns);  
            GuidelinesConfiguration = value;  
        }  
  
        private static string ComposeSettingsString(Color color,  
                                                    IEnumerable<int> columns)  
        {  
            StringBuilder sb = new StringBuilder();  
            sb.AppendFormat("RGB({0},{1},{2})", color.R, color.G, color.B);  
            IEnumerator<int> columnsEnumerator = columns.GetEnumerator();  
            if (columnsEnumerator.MoveNext())  
            {  
                sb.AppendFormat(" {0}", columnsEnumerator.Current);  
                while (columnsEnumerator.MoveNext())  
                {  
                    sb.AppendFormat(", {0}", columnsEnumerator.Current);  
                }  
            }  
            return sb.ToString();  
        }  
  
        // Parse a color out of a string that begins like "RGB(255,0,0)"  
        static internal Color GuidelinesColor  
        {  
            get  
            {  
                string config = GuidelinesConfiguration;  
                if (!String.IsNullOrEmpty(config) && config.StartsWith("RGB("))  
                {  
                    int lastParen = config.IndexOf(')');  
                    if (lastParen > 4)  
                    {  
                        string[] rgbs = config.Substring(4, lastParen - 4).Split(',');  
  
                        if (rgbs.Length >= 3)  
                        {  
                            byte r, g, b;  
                            if (byte.TryParse(rgbs[0], out r) &&  
                                byte.TryParse(rgbs[1], out g) &&  
                                byte.TryParse(rgbs[2], out b))  
                            {  
                                return Color.FromRgb(r, g, b);  
                            }  
                        }  
                    }  
                }  
                return Colors.DarkRed;  
            }  
  
            set  
            {  
                WriteSettings(value, GetColumnOffsets());  
            }  
        }  
  
        // Parse a list of integer values out of a string that looks like  
        // "RGB(255,0,0) 1, 5, 10, 80"  
        static internal List<int> GetColumnOffsets()  
        {  
            var result = new List<int>();  
            string settings = GuidesSettingsManager.GuidelinesConfiguration;  
            if (String.IsNullOrEmpty(settings))  
                return new List<int>();  
  
            if (!settings.StartsWith("RGB("))  
                return new List<int>();  
  
            int lastParen = settings.IndexOf(')');  
            if (lastParen <= 4)  
                return new List<int>();  
  
            string[] columns = settings.Substring(lastParen + 1).Split(',');  
  
            int columnCount = 0;  
            foreach (string columnText in columns)  
            {  
                int column = -1;  
                // VS 2008 gallery extension didn't allow zero, so per user request ...  
                if (int.TryParse(columnText, out column) && column >= 0)  
                {  
                    columnCount++;  
                    result.Add(column);  
                    if (columnCount >= _maxGuides)  
                        break;  
                }  
            }  
            return result;  
        }  
  
        // Delegate and Event to fire when settings change so that ColumnGuideAdornments   
        // can update.  We need nothing special in this event since the settings manager   
        // is statically available.  
        //  
        internal delegate void SettingsChangedHandler();  
        static internal event SettingsChangedHandler SettingsChanged;  
  
    }  
}  
  
```  
  
 La mayor parte de este código crea y analiza el formato de configuración: "RGB (\<int >,\<int >,\<int >) \<int >, \<int >,...".  Los enteros al final son las columnas basadas en uno donde desee guías de columnas. La extensión de las guías de columna captura a toda su configuración en una cadena de valor de configuración único.  
  
 Hay algunas partes del código que conviene destacar. La siguiente línea de código obtiene el contenedor administrado de Visual Studio para el almacenamiento de configuración. En su mayor parte, esto abstrae sobre el registro de Windows, pero esta API es independiente del mecanismo de almacenamiento.  
  
```csharp  
internal static SettingsManager VsManagedSettingsManager =  
    new ShellSettingsManager(ServiceProvider.GlobalProvider);  
```  
  
 El almacenamiento de configuración de Visual Studio usa un identificador de categoría y un identificador de configuración para identificar de forma exclusiva toda la configuración:  
  
```csharp  
private const string _collectionSettingsName = "Text Editor";  
private const string _settingName = "Guides";  
```  
  
 No es necesario usar `"Text Editor"` como el nombre de categoría. Puede elegir que desee.  
  
 El primer algunas funciones son los puntos de entrada para cambiar la configuración. Comprueban las restricciones de alto nivel como el número máximo de guías permitido.  A continuación, llaman a `WriteSettings`, que crea una cadena de configuración y establece la propiedad `GuideLinesConfiguration`. Al establecer esta propiedad, guarda el valor de configuración en el almacén de configuración de Visual Studio y se activa el `SettingsChanged` eventos para actualizar todos los `ColumnGuideAdornment` objetos, cada uno asociado con una vista de texto.  
  
 Hay un par de funciones de punto de entrada, como `CanAddGuideline`, que se usan para implementar los comandos que cambian la configuración. Cuando Visual Studio muestra los menús, consulta las implementaciones de comando para ver si el comando está habilitado actualmente, ¿cuál es su nombre y así sucesivamente.  A continuación verá cómo enlazar estos puntos de entrada para las implementaciones de comando. Para obtener más información sobre los comandos, consulte [amplían los menús y comandos](../extensibility/extending-menus-and-commands.md).  
  
## <a name="implement-the-columnguideadornment-class"></a>Implementar la clase ColumnGuideAdornment  
 El `ColumnGuideAdornment` se crea una instancia de clase para cada vista de texto que puede tener los elementos gráficos. Esta clase realiza escuchas para los eventos sobre la vista que cambia o cambio de configuración y las guías de columna de actualización o recomposición según sea necesario.  
  
 Reemplace el contenido de la *ColumnGuideAdornment.cs* con el código siguiente (se explica más adelante):  
  
```csharp  
using System;  
using System.Windows.Media;  
using Microsoft.VisualStudio.Text.Editor;  
using System.Collections.Generic;  
using System.Windows.Shapes;  
using Microsoft.VisualStudio.Text.Formatting;  
using System.Windows;  
  
namespace ColumnGuides  
{  
    /// <summary>  
    /// Adornment class, one instance per text view that draws a guides on the viewport  
    /// </summary>  
    internal sealed class ColumnGuideAdornment  
    {  
        private const double _lineThickness = 1.0;  
        private IList<Line> _guidelines;  
        private IWpfTextView _view;  
        private double _baseIndentation;  
        private double _columnWidth;  
  
        /// <summary>  
        /// Creates editor column guidelines  
        /// </summary>  
        /// <param name="view">The <see cref="IWpfTextView"/> upon   
        /// which the adornment will be drawn</param>  
        public ColumnGuideAdornment(IWpfTextView view)  
        {  
            _view = view;  
            _guidelines = CreateGuidelines();  
            GuidesSettingsManager.SettingsChanged +=   
                new GuidesSettingsManager.SettingsChangedHandler(SettingsChanged);  
            view.LayoutChanged +=   
                new EventHandler<TextViewLayoutChangedEventArgs>(OnViewLayoutChanged);  
            _view.Closed += new EventHandler(OnViewClosed);  
        }  
  
        void SettingsChanged()  
        {  
            _guidelines = CreateGuidelines();  
            UpdatePositions();  
            AddGuidelinesToAdornmentLayer();  
        }  
  
        void OnViewClosed(object sender, EventArgs e)  
        {  
            _view.LayoutChanged -= OnViewLayoutChanged;  
            _view.Closed -= OnViewClosed;  
            GuidesSettingsManager.SettingsChanged -= SettingsChanged;  
        }  
  
        private bool _firstLayoutDone;  
  
        void OnViewLayoutChanged(object sender, TextViewLayoutChangedEventArgs e)  
        {  
            bool fUpdatePositions = false;  
  
            IFormattedLineSource lineSource = _view.FormattedLineSource;  
            if (lineSource == null)  
            {  
                return;  
            }  
            if (_columnWidth != lineSource.ColumnWidth)  
            {  
                _columnWidth = lineSource.ColumnWidth;  
                fUpdatePositions = true;  
            }  
            if (_baseIndentation != lineSource.BaseIndentation)  
            {  
                _baseIndentation = lineSource.BaseIndentation;  
                fUpdatePositions = true;  
            }  
            if (fUpdatePositions ||  
                e.VerticalTranslation ||  
                e.NewViewState.ViewportTop != e.OldViewState.ViewportTop ||  
                e.NewViewState.ViewportBottom != e.OldViewState.ViewportBottom)  
            {  
                UpdatePositions();  
            }  
            if (!_firstLayoutDone)  
            {  
                AddGuidelinesToAdornmentLayer();  
                _firstLayoutDone = true;  
            }  
        }  
  
        private static IList<Line> CreateGuidelines()  
        {  
            Brush lineBrush = new SolidColorBrush(GuidesSettingsManager.GuidelinesColor);  
            DoubleCollection dashArray = new DoubleCollection(new double[] { 1.0, 3.0 });  
            IList<Line> result = new List<Line>();  
            foreach (int column in GuidesSettingsManager.GetColumnOffsets())  
            {  
                Line line = new Line()  
                {  
                    // Use the DataContext slot as a cookie to hold the column  
                    DataContext = column,  
                    Stroke = lineBrush,  
                    StrokeThickness = _lineThickness,  
                    StrokeDashArray = dashArray  
                };  
                result.Add(line);  
            }  
            return result;  
        }  
  
        void UpdatePositions()  
        {  
            foreach (Line line in _guidelines)  
            {  
                int column = (int)line.DataContext;  
                line.X2 = _baseIndentation + 0.5 + column * _columnWidth;  
                line.X1 = line.X2;  
                line.Y1 = _view.ViewportTop;  
                line.Y2 = _view.ViewportBottom;  
            }  
        }  
  
        void AddGuidelinesToAdornmentLayer()  
        {  
            // Grab a reference to the adornment layer that this adornment   
            // should be added to  
            // Must match exported name in ColumnGuideAdornmentTextViewCreationListener  
            IAdornmentLayer adornmentLayer =   
                _view.GetAdornmentLayer("ColumnGuideAdornment");  
            if (adornmentLayer == null)  
                return;  
            adornmentLayer.RemoveAllAdornments();  
            // Add the guidelines to the adornment layer and make them relative   
            // to the viewport  
            foreach (UIElement element in _guidelines)  
                adornmentLayer.AddAdornment(AdornmentPositioningBehavior.OwnerControlled,  
                                            null, null, element, null);  
        }  
    }  
  
}  
```  
  
 Las instancias de esta clase retener asociado <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView> y una lista de `Line` dibujados en la vista de objetos.  
  
 El constructor (llamado desde `ColumnGuideAdornmentTextViewCreationListener` cuando Visual Studio crea nuevas vistas) crea la Guía de la columna `Line` objetos.  El constructor también agrega controladores para el `SettingsChanged` eventos (definido en `GuidesSettingsManager`) y los eventos de vista `LayoutChanged` y `Closed`.  
  
 El `LayoutChanged` desencadena el evento debido a varios tipos de cambios en la vista, incluso cuando Visual Studio crea la vista. El `OnViewLayoutChanged` llamadas del controlador `AddGuidelinesToAdornmentLayer` para ejecutar. El código en `OnViewLayoutChanged` determina si es necesario actualizar las posiciones de línea según los cambios, como los cambios de tamaño de fuente, vista medianiles, desplazamiento horizontal y así sucesivamente. El código en `UpdatePositions` hace que las líneas de guía dibujar entre caracteres o justo después de la columna de texto que se encuentra en el desplazamiento de caracteres especificado en la línea de texto.  
  
 Cada vez que cambie la configuración de la `SettingsChanged` función vuelve a crear todos los `Line` objetos con los valores nuevos. Después de establecer las posiciones de línea, el código quita todos los anteriores `Line` objetos desde el `ColumnGuideAdornment` nivel del elemento gráfico y agrega los nuevos.  
  
## <a name="define-the-commands-menus-and-menu-placements"></a>Definir las ubicaciones de menú, menús y comandos  
 Puede haber mucha para declarar los menús y comandos, colocación de grupos de menús o comandos en varios otros menús y enlazar controladores de comandos. Este tutorial resalta cómo funcionan los comandos de esta extensión, pero para obtener información más detallada, vea [amplían los menús y comandos](../extensibility/extending-menus-and-commands.md).  
  
### <a name="introduction-to-the-code"></a>Introducción al código  
 La extensión de guías de columnas muestra la declaración de un grupo de comandos que forman un conjunto (Agregar columna, quitar la columna, cambiar el color de línea) y, a continuación, colocar ese grupo en un submenú del menú contextual del editor.  La extensión de guías de columnas también agrega los comandos a los principales **editar** menú pero manteniéndolas invisible, tratado como un patrón común que aparece a continuación.  
  
 Hay tres partes para la implementación de comandos: ColumnGuideCommandsPackage.cs, ColumnGuideCommandsPackage.vsct y ColumnGuideCommands.cs. El código generado por las plantillas coloca un comando en el **herramientas** menú que aparece un cuadro de diálogo como la implementación. Puede observar cómo que se implementa en el *.vsct* y *ColumnGuideCommands.cs* archivos, ya que resulta sencillo. Reemplace el código de estos archivos siguientes.  
  
 El código de paquete contiene declaraciones de reutilizable necesarias para Visual Studio para detectar que la extensión ofrece comandos y para encontrar la ubicación de los comandos. Cuando se inicializa el paquete, crea una instancia de la clase de implementación de comandos. Para obtener más información acerca de los paquetes relacionados con los comandos, consulte [amplían los menús y comandos](../extensibility/extending-menus-and-commands.md).  
  
### <a name="a-common-commands-pattern"></a>Un patrón común de comandos  
 Los comandos de la extensión de guías de columnas son un ejemplo de un patrón muy común en Visual Studio. Colocar comandos relacionados en un grupo, y coloque ese grupo en un menú principal, a menudo con "`<CommandFlag>CommandWellOnly</CommandFlag>`" establecido para que el comando sea invisible.  Colocación de comandos en los menús principales (como **editar**) les agradables nombres (como **Edit.AddColumnGuide**), que son útiles para buscar comandos al volver a asignar los enlaces de teclado en **herramientas Opciones de**. También es útil para obtener la finalización al invocar comandos desde el **ventana de comandos**.  
  
 A continuación, agregue el grupo de comandos a menús contextuales o sub donde se espera al usuario que utilice los comandos de menús. Visual Studio trata `CommandWellOnly` como una marca de invisibilidad de menús principales solo. Cuando se coloca el mismo grupo de comandos en un menú contextual o sub, los comandos son visibles.  
  
 Como parte del patrón común, la extensión de guías de columnas crea un segundo grupo que contiene un submenú único. El submenú a su vez contiene el primer grupo con los comandos de la Guía de cuatro columnas. El segundo grupo que contiene el submenú es el recurso reutilizable que se coloca en varios menús contextuales, que coloca un submenú en los menús contextuales.  
  
### <a name="the-vsct-file"></a>El archivo .vsct  
 El *.vsct* archivo declara los comandos y donde vaya, junto con los iconos y así sucesivamente. Reemplace el contenido de la *.vsct* archivo con el código siguiente (se explica más adelante):  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
  
  <!--  This is the file that defines the actual layout and type of the commands.  
        It is divided in different sections (e.g. command definition, command  
        placement, ...), with each defining a specific set of properties.  
        See the comment before each section for more details about how to  
        use it. -->  
  
  <!--  The VSCT compiler (the tool that translates this file into the binary  
        format that VisualStudio will consume) has the ability to run a preprocessor  
        on the vsct file; this preprocessor is (usually) the C++ preprocessor, so  
        it is possible to define includes and macros with the same syntax used  
        in C++ files. Using this ability of the compiler here, we include some files  
        defining some of the constants that we will use inside the file. -->  
  
  <!--This is the file that defines the IDs for all the commands exposed by   
      VisualStudio. -->  
  <Extern href="stdidcmd.h"/>  
  
  <!--This header contains the command ids for the menus provided by the shell. -->  
  <Extern href="vsshlids.h"/>  
  
  <!--The Commands section is where commands, menus, and menu groups are defined.  
      This section uses a Guid to identify the package that provides the command   
      defined inside it. -->  
  <Commands package="guidColumnGuideCommandsPkg">  
    <!-- Inside this section we have different sub-sections: one for the menus, another    
    for the menu groups, one for the buttons (the actual commands), one for the combos   
    and the last one for the bitmaps used. Each element is identified by a command id  
    that is a unique pair of guid and numeric identifier; the guid part of the identifier  
    is usually called "command set" and is used to group different command inside a  
    logically related group; your package should define its own command set in order to  
    avoid collisions with command ids defined by other packages. -->  
  
    <!-- In this section you can define new menu groups. A menu group is a container for   
         other menus or buttons (commands); from a visual point of view you can see the   
         group as the part of a menu contained between two lines. The parent of a group   
         must be a menu. -->  
    <Groups>  
  
      <!-- The main group is parented to the edit menu. All the buttons within the group  
           have the "CommandWellOnly" flag, so they're actually invisible, but it means  
           they get canonical names that begin with "Edit". Using placements, the group  
           is also placed in the GuidesSubMenu group. -->  
      <!-- The priority 0xB801 is chosen so it goes just after   
           IDG_VS_EDIT_COMMANDWELL -->  
      <Group guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup"  
             priority="0xB801">  
        <Parent guid="guidSHLMainMenu" id="IDM_VS_MENU_EDIT" />  
      </Group>  
  
      <!-- Group for holding the "Guidelines" sub-menu anchor (the item on the menu that  
           drops the sub menu). The group is parented to  
           the context menu for code windows. That takes care of most editors, but it's  
           also placed in a couple of other windows using Placements -->  
      <Group guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup"   
             priority="0x0600">  
        <Parent guid="guidSHLMainMenu" id="IDM_VS_CTXT_CODEWIN" />  
      </Group>  
  
    </Groups>  
  
    <Menus>  
      <Menu guid="guidColumnGuidesCommandSet" id="GuidesSubMenu" priority="0x1000"  
            type="Menu">  
        <Parent guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup" />  
        <Strings>  
          <ButtonText>&Column Guides</ButtonText>  
        </Strings>  
      </Menu>  
    </Menus>  
  
    <!--Buttons section. -->  
    <!--This section defines the elements the user can interact with, like a menu command or a button   
        or combo box in a toolbar. -->  
    <Buttons>  
      <!--To define a menu group you have to specify its ID, the parent menu and its   
          display priority.   
          The command is visible and enabled by default. If you need to change the   
          visibility, status, etc, you can use the CommandFlag node.  
          You can add more than one CommandFlag node e.g.:  
              <CommandFlag>DefaultInvisible</CommandFlag>  
              <CommandFlag>DynamicVisibility</CommandFlag>  
          If you do not want an image next to your command, remove the Icon node or   
          set it to <Icon guid="guidOfficeIcon" id="msotcidNoIcon" /> -->  
  
      <Button guid="guidColumnGuidesCommandSet" id="cmdidAddColumnGuide"   
              priority="0x0100" type="Button">  
        <Parent guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup" />  
        <Icon guid="guidImages" id="bmpPicAddGuide" />  
        <CommandFlag>CommandWellOnly</CommandFlag>  
        <CommandFlag>AllowParams</CommandFlag>  
        <Strings>  
          <ButtonText>&Add Column Guide</ButtonText>  
        </Strings>  
      </Button>  
  
      <Button guid="guidColumnGuidesCommandSet" id="cmdidRemoveColumnGuide"   
              priority="0x0101" type="Button">  
        <Parent guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup" />  
        <Icon guid="guidImages" id="bmpPicRemoveGuide" />  
        <CommandFlag>CommandWellOnly</CommandFlag>  
        <CommandFlag>AllowParams</CommandFlag>  
        <Strings>  
          <ButtonText>&Remove Column Guide</ButtonText>  
        </Strings>  
      </Button>  
  
      <Button guid="guidColumnGuidesCommandSet" id="cmdidChooseGuideColor"   
              priority="0x0103" type="Button">  
        <Parent guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup" />  
        <Icon guid="guidImages" id="bmpPicChooseColor" />  
        <CommandFlag>CommandWellOnly</CommandFlag>  
        <Strings>  
          <ButtonText>Column Guide &Color...</ButtonText>  
        </Strings>  
      </Button>  
  
      <Button guid="guidColumnGuidesCommandSet" id="cmdidRemoveAllColumnGuides"   
              priority="0x0102" type="Button">  
        <Parent guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup" />  
        <CommandFlag>CommandWellOnly</CommandFlag>  
        <Strings>  
          <ButtonText>Remove A&ll Columns</ButtonText>  
        </Strings>  
      </Button>  
    </Buttons>  
  
    <!--The bitmaps section is used to define the bitmaps that are used for the  
        commands.-->  
    <Bitmaps>  
      <!--  The bitmap id is defined in a way that is a little bit different from the  
            others:   
            the declaration starts with a guid for the bitmap strip, then there is the  
            resource id of the bitmap strip containing the bitmaps and then there are   
            the numeric ids of the elements used inside a button definition. An important  
            aspect of this declaration is that the element id   
            must be the actual index (1-based) of the bitmap inside the bitmap strip. -->  
      <Bitmap guid="guidImages" href="Resources\ColumnGuideCommands.png"   
              usedList="bmpPicAddGuide, bmpPicRemoveGuide, bmpPicChooseColor" />  
    </Bitmaps>  
  
  </Commands>  
  
  <CommandPlacements>  
  
    <!-- Define secondary placements for our groups -->  
  
    <!-- Place the group containing the three commands in the sub-menu -->  
    <CommandPlacement guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup"   
                      priority="0x0100">  
      <Parent guid="guidColumnGuidesCommandSet" id="GuidesSubMenu" />  
    </CommandPlacement>  
  
    <!-- The HTML editor context menu, for some reason, redefines its own groups  
         so we need to place a copy of our context menu there too. -->  
    <CommandPlacement guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup"   
                      priority="0x1001">  
      <Parent guid="CMDSETID_HtmEdGrp" id="IDMX_HTM_SOURCE_HTML" />  
    </CommandPlacement>  
  
    <!-- The HTML context menu in Dev12 changed. -->  
    <CommandPlacement guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup"   
                      priority="0x1001">  
      <Parent guid="CMDSETID_HtmEdGrp_Dev12" id="IDMX_HTM_SOURCE_HTML_Dev12" />  
    </CommandPlacement>  
  
    <!-- Similarly for Script -->  
    <CommandPlacement guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup"  
                      priority="0x1001">  
      <Parent guid="CMDSETID_HtmEdGrp" id="IDMX_HTM_SOURCE_SCRIPT" />  
    </CommandPlacement>  
  
    <!-- Similarly for ASPX  -->  
    <CommandPlacement guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup"   
                      priority="0x1001">  
      <Parent guid="CMDSETID_HtmEdGrp" id="IDMX_HTM_SOURCE_ASPX" />  
    </CommandPlacement>  
  
    <!-- Similarly for the XAML editor context menu -->  
    <CommandPlacement guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup"  
                      priority="0x0600">  
      <Parent guid="guidXamlUiCmds" id="IDM_XAML_EDITOR" />  
    </CommandPlacement>  
  
  </CommandPlacements>  
  
  <!-- This defines the identifiers and their values used above to index resources  
       and specify commands. -->  
  <Symbols>  
    <!-- This is the package guid. -->  
    <GuidSymbol name="guidColumnGuideCommandsPkg"   
                value="{e914e5de-0851-4904-b361-1a3a9d449704}" />  
  
    <!-- This is the guid used to group the menu commands together -->  
    <GuidSymbol name="guidColumnGuidesCommandSet"   
                value="{c2bc0047-8bfa-4e5a-b5dc-45af8c274d8e}">  
      <IDSymbol name="GuidesContextMenuGroup" value="0x1020" />  
      <IDSymbol name="GuidesMenuItemsGroup" value="0x1021" />  
      <IDSymbol name="GuidesSubMenu" value="0x1022" />  
      <IDSymbol name="cmdidAddColumnGuide" value="0x0100" />  
      <IDSymbol name="cmdidRemoveColumnGuide" value="0x0101" />  
      <IDSymbol name="cmdidChooseGuideColor" value="0x0102" />  
      <IDSymbol name="cmdidRemoveAllColumnGuides" value="0x0103" />  
    </GuidSymbol>  
  
    <GuidSymbol name="guidImages" value="{2C99F852-587C-43AF-AA2D-F605DE2E46EF}">  
      <IDSymbol name="bmpPicAddGuide" value="1" />  
      <IDSymbol name="bmpPicRemoveGuide" value="2" />  
      <IDSymbol name="bmpPicChooseColor" value="3" />  
    </GuidSymbol>  
  
    <GuidSymbol name="CMDSETID_HtmEdGrp_Dev12"   
                value="{78F03954-2FB8-4087-8CE7-59D71710B3BB}">  
      <IDSymbol name="IDMX_HTM_SOURCE_HTML_Dev12" value="0x1" />  
    </GuidSymbol>  
  
    <GuidSymbol name="CMDSETID_HtmEdGrp" value="{d7e8c5e1-bdb8-11d0-9c88-0000f8040a53}">  
      <IDSymbol name="IDMX_HTM_SOURCE_HTML" value="0x33" />  
      <IDSymbol name="IDMX_HTM_SOURCE_SCRIPT" value="0x34" />  
      <IDSymbol name="IDMX_HTM_SOURCE_ASPX" value="0x35" />  
    </GuidSymbol>  
  
    <GuidSymbol name="guidXamlUiCmds" value="{4c87b692-1202-46aa-b64c-ef01faec53da}">  
      <IDSymbol name="IDM_XAML_EDITOR" value="0x103" />  
    </GuidSymbol>  
  </Symbols>  
  
</CommandTable>  
  
```  
  
 **GUID**. Para que Visual Studio buscar los controladores de comandos e invocarlos, deberá asegurarse el declarado en el GUID del paquete el *ColumnGuideCommandsPackage.cs* archivo (generado a partir de la plantilla de elemento de proyecto) coincide con el paquete GUID declarado en el *.vsct* archivo (copiado desde arriba). Si volver a usar este código de ejemplo, debe asegurarse de que tiene un GUID diferente para que los no entren en conflicto con cualquier persona que puede haber copiado este código.  
  
 Busque esta línea en *ColumnGuideCommandsPackage.cs* y copie el GUID entre comillas:  
  
```csharp  
public const string PackageGuidString = "ef726849-5447-4f73-8de5-01b9e930f7cd";  
```  
  
 A continuación, pegue el GUID de la *.vsct* de archivos para que tenga la siguiente línea su `Symbols` declaraciones:  
  
```xml  
<GuidSymbol name="guidColumnGuideCommandsPkg"   
            value="{ef726849-5447-4f73-8de5-01b9e930f7cd}" />  
```  
  
 Establece el GUID del comando y el archivo de imagen de mapa de bits debe ser único para las extensiones, demasiado:  
  
```xml  
<GuidSymbol name="guidColumnGuidesCommandSet"   
            value="{c2bc0047-8bfa-4e5a-b5dc-45af8c274d8e}">  
<GuidSymbol name="guidImages" value="{2C99F852-587C-43AF-AA2D-F605DE2E46EF}">  
```  
  
 Sin embargo, no es necesario cambiar el conjunto de comandos y los GUID de la imagen en este tutorial para obtener el código funcione de mapa de bits. El conjunto de comandos GUID debe coincidir con la declaración en el *ColumnGuideCommands.cs* archivo, pero reemplace el contenido de ese archivo, demasiado; por consiguiente, coincidirá con los GUID.  
  
 El resto de GUID en la *.vsct* archivo identificar menús ya existentes a la que se agregan los comandos de la Guía de columna, por lo que nunca cambian.  
  
 **Las secciones de archivos**. El *.vsct* tiene tres secciones externas: comandos, ubicaciones y símbolos. La sección de comandos define los grupos de comandos, menús, botones o elementos de menú y los mapas de bits para los iconos. La sección ubicaciones declara dónde grupos en los menús o ubicaciones adicionales en los menús existentes previamente. La sección symbols declara los identificadores utilizados en otro lugar en el *.vsct* archivo, lo que hace que el *.vsct* números de código más legible que tener GUID y valores hexadecimales en todas partes.  
  
 **Sección de los comandos, las definiciones de grupos**. La sección de comandos primero define los grupos de comandos. Los grupos de comandos son comandos que aparecen en los menús con pequeñas líneas grises separa los grupos. Un grupo también puede rellenar un submenú completo, como en este ejemplo, y no ve el gris separar las líneas en este caso. El *.vsct* archivos declaran dos grupos, el `GuidesMenuItemsGroup` que tiene un elemento primario la `IDM_VS_MENU_EDIT` (principal **editar** menú) y la `GuidesContextMenuGroup` que está asociado al `IDM_VS_CTXT_CODEWIN` (el código menú contextual del Editor).  
  
 La segunda declaración de grupo tiene un `0x0600` prioridad:  
  
```xml  
<Group guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup"   
             priority="0x0600">  
```  
  
 La idea es colocar la columna de guías de submenú al final de cualquier menú contextual a la que agregar el grupo de menús de sub. Sin embargo, no debería suponer que conoce mejor y forzar el submenú que siempre sea último mediante el uso de una prioridad de `0xFFFF`. Tendrá que experimentar con el número para ver dónde reside su submenú en los menús contextuales donde se coloca. En este caso, `0x0600` es suficientemente alto como para colocarla al final de los menús, lo puede ver, pero deja espacio para otra persona para diseñar su extensión a ser inferior a la extensión de las guías de columna si así lo desea.  
  
 **Sección de definición del menú de comandos**. A continuación, la sección de comandos define el submenú `GuidesSubMenu`, relacionada para el `GuidesContextMenuGroup`. El `GuidesContextMenuGroup` es el grupo que agregue a todos los menús de contexto pertinente. En la sección de ubicaciones, el código coloca el grupo con los comandos de la Guía de cuatro columnas en este elemento de submenú.  
  
 **Sección de los comandos, botones definiciones**. La sección de comandos, a continuación, define los elementos de menú o botones que se muestran los comandos de las guías de cuatro columnas. `CommandWellOnly`, se ha explicado anteriormente, significa que los comandos no están visibles cuando se coloca en un menú principal. Las declaraciones de dos del elemento de menú de botones (Guía de agregar y quitar guía) también tienen un `AllowParams` marca:  
  
```xml  
<CommandFlag>AllowParams</CommandFlag>  
```  
  
 Esta marca habilita, junto con tener ubicaciones del menú principal, el comando para recibir los argumentos cuando Visual Studio invoca el controlador de comandos.  Si el usuario ejecuta el comando desde la ventana de comandos, el argumento se pasa al controlador de comando en el evento argumentos.  
  
 **Comando secciones, las definiciones de los mapas de bits**. Por último, la sección comandos declara los mapas de bits o iconos que se usan para los comandos. En esta sección es una declaración simple que identifica el recurso del proyecto y enumera los índices basados en uno de los iconos de uso. La sección symbols de la *.vsct* archivo declara los valores de los identificadores usados como los índices. Este tutorial utiliza la Tira de mapa de bits proporcionada con la plantilla de elemento de comando personalizado agregada al proyecto.  
  
 **Sección de ubicaciones**. Después de los comandos de sección es la sección de ubicaciones. La primera de ellas es que el código agrega el primer grupo que explicamos anteriormente que contiene a la Guía de cuatro columnas comandos en el submenú dónde aparecen los comandos:  
  
```xml  
<CommandPlacement guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup"   
                  priority="0x0100">  
  <Parent guid="guidColumnGuidesCommandSet" id="GuidesSubMenu" />  
</CommandPlacement>  
```  
  
 Todas las demás ubicaciones de agregan el `GuidesContextMenuGroup` (que contiene el `GuidesSubMenu`) a otros menús contextuales del editor. Cuando el código declara los `GuidesContextMenuGroup`, era un elemento primario en el menú contextual del editor de código. Por eso no ve una ubicación para el menú contextual del editor de código.  
  
 **Símbolos sección**. Como se indicó anteriormente, la sección symbols declara los identificadores utilizados en otro lugar en el *.vsct* archivo, lo que hace que el *.vsct* números de código más legible que tener GUID y valores hexadecimales en todas partes. Los puntos importantes en esta sección son que el GUID del paquete debe coincidir con la declaración de la clase de paquete. Y el GUID del conjunto de comandos debe coincidir con la declaración de la clase de implementación del comando.  
  
## <a name="implement-the-commands"></a>Implementar los comandos  
 El *ColumnGuideCommands.cs* archivo implementa los comandos y enlaza los controladores. Cuando Visual Studio carga el paquete y lo inicializa, el paquete a su vez llama a `Initialize` en la clase de implementación de comandos. La inicialización de comandos simplemente crea una instancia de la clase, y el constructor enlaza todos los controladores de comandos.  
  
 Reemplace el contenido de la *ColumnGuideCommands.cs* archivo con el código siguiente (se explica más adelante):  
  
```csharp  
using System;  
using System.ComponentModel.Design;  
using System.Globalization;  
using Microsoft.VisualStudio.Shell;  
using Microsoft.VisualStudio.Shell.Interop;  
using Microsoft.VisualStudio.TextManager.Interop;  
using Microsoft.VisualStudio.Text.Editor;  
using Microsoft.VisualStudio;  
  
namespace ColumnGuides  
{  
    /// <summary>  
    /// Command handler  
    /// </summary>  
    internal sealed class ColumnGuideCommands  
    {  
  
        const int cmdidAddColumnGuide = 0x0100;  
        const int cmdidRemoveColumnGuide = 0x0101;  
        const int cmdidChooseGuideColor = 0x0102;  
        const int cmdidRemoveAllColumnGuides = 0x0103;  
  
        /// <summary>  
        /// Command menu group (command set GUID).  
        /// </summary>  
        static readonly Guid CommandSet =   
            new Guid("c2bc0047-8bfa-4e5a-b5dc-45af8c274d8e");  
  
        /// <summary>  
        /// VS Package that provides this command, not null.  
        /// </summary>  
        private readonly Package package;  
  
        OleMenuCommand _addGuidelineCommand;  
        OleMenuCommand _removeGuidelineCommand;  
  
        /// <summary>  
        /// Initializes the singleton instance of the command.  
        /// </summary>  
        /// <param name="package">Owner package, not null.</param>  
        public static void Initialize(Package package)  
        {  
            Instance = new ColumnGuideCommands(package);  
        }  
  
        /// <summary>  
        /// Gets the instance of the command.  
        /// </summary>  
        public static ColumnGuideCommands Instance  
        {  
            get;  
            private set;  
        }  
  
        /// <summary>  
        /// Initializes a new instance of the <see cref="ColumnGuideCommands"/> class.  
        /// Adds our command handlers for menu (commands must exist in the command   
        /// table file)  
        /// </summary>  
        /// <param name="package">Owner package, not null.</param>  
        private ColumnGuideCommands(Package package)  
        {  
            if (package == null)  
            {  
                throw new ArgumentNullException("package");  
            }  
  
            this.package = package;  
  
            // Add our command handlers for menu (commands must exist in the .vsct file)  
  
            OleMenuCommandService commandService =  
                this.ServiceProvider.GetService(typeof(IMenuCommandService))  
                    as OleMenuCommandService;  
            if (commandService != null)  
            {  
                // Add guide  
                _addGuidelineCommand =   
                    new OleMenuCommand(AddColumnGuideExecuted, null,  
                                       AddColumnGuideBeforeQueryStatus,  
                                       new CommandID(ColumnGuideCommands.CommandSet,  
                                                     cmdidAddColumnGuide));  
                _addGuidelineCommand.ParametersDescription = "<column>";  
                commandService.AddCommand(_addGuidelineCommand);  
                // Remove guide  
                _removeGuidelineCommand =  
                    new OleMenuCommand(RemoveColumnGuideExecuted, null,  
                                       RemoveColumnGuideBeforeQueryStatus,  
                                       new CommandID(ColumnGuideCommands.CommandSet,  
                                                     cmdidRemoveColumnGuide));  
                _removeGuidelineCommand.ParametersDescription = "<column>";  
                commandService.AddCommand(_removeGuidelineCommand);  
                // Choose color  
                commandService.AddCommand(  
                    new MenuCommand(ChooseGuideColorExecuted,  
                                    new CommandID(ColumnGuideCommands.CommandSet,  
                                                  cmdidChooseGuideColor)));  
                // Remove all  
                commandService.AddCommand(  
                    new MenuCommand(RemoveAllGuidelinesExecuted,  
                                    new CommandID(ColumnGuideCommands.CommandSet,  
                                                  cmdidRemoveAllColumnGuides)));  
            }  
        }  
  
        /// <summary>  
        /// Gets the service provider from the owner package.  
        /// </summary>  
        private IServiceProvider ServiceProvider  
        {  
            get  
            {  
                return this.package;  
            }  
        }  
  
        private void AddColumnGuideBeforeQueryStatus(object sender, EventArgs e)  
        {  
            int currentColumn = GetCurrentEditorColumn();  
            _addGuidelineCommand.Enabled =  
                GuidesSettingsManager.CanAddGuideline(currentColumn);  
        }  
  
        private void RemoveColumnGuideBeforeQueryStatus(object sender, EventArgs e)  
        {  
            int currentColumn = GetCurrentEditorColumn();  
            _removeGuidelineCommand.Enabled =  
                GuidesSettingsManager.CanRemoveGuideline(currentColumn);  
        }  
  
        private int GetCurrentEditorColumn()  
        {  
            IVsTextView view = GetActiveTextView();  
            if (view == null)  
            {  
                return -1;  
            }  
  
            try  
            {  
                IWpfTextView textView = GetTextViewFromVsTextView(view);  
                int column = GetCaretColumn(textView);  
  
                // Note: GetCaretColumn returns 0-based positions. Guidelines are 1-based  
                // positions.  
                // However, do not subtract one here since the caret is positioned to the  
                // left of  
                // the given column and the guidelines are positioned to the right. We  
                // want the  
                // guideline to line up with the current caret position. e.g. When the  
                // caret is  
                // at position 1 (zero-based), the status bar says column 2. We want to  
                // add a  
                // guideline for column 1 since that will place the guideline where the  
                // caret is.  
                return column;  
            }  
            catch (InvalidOperationException)  
            {  
                return -1;  
            }  
        }  
  
        /// <summary>  
        /// Find the active text view (if any) in the active document.  
        /// </summary>  
        /// <returns>The IVsTextView of the active view, or null if there is no active  
        /// document or the  
        /// active view in the active document is not a text view.</returns>  
        private IVsTextView GetActiveTextView()  
        {  
            IVsMonitorSelection selection =  
                this.ServiceProvider.GetService(typeof(IVsMonitorSelection))  
                                                    as IVsMonitorSelection;  
            object frameObj = null;  
            ErrorHandler.ThrowOnFailure(  
                selection.GetCurrentElementValue(  
                    (uint)VSConstants.VSSELELEMID.SEID_DocumentFrame, out frameObj));  
  
            IVsWindowFrame frame = frameObj as IVsWindowFrame;  
            if (frame == null)  
            {  
                return null;  
            }  
  
            return GetActiveView(frame);  
        }  
  
        private static IVsTextView GetActiveView(IVsWindowFrame windowFrame)  
        {  
            if (windowFrame == null)  
            {  
                throw new ArgumentException("windowFrame");  
            }  
  
            object pvar;  
            ErrorHandler.ThrowOnFailure(  
                windowFrame.GetProperty((int)__VSFPROPID.VSFPROPID_DocView, out pvar));  
  
            IVsTextView textView = pvar as IVsTextView;  
            if (textView == null)  
            {  
                IVsCodeWindow codeWin = pvar as IVsCodeWindow;  
                if (codeWin != null)  
                {  
                    ErrorHandler.ThrowOnFailure(codeWin.GetLastActiveView(out textView));  
                }  
            }  
            return textView;  
        }  
  
        private static IWpfTextView GetTextViewFromVsTextView(IVsTextView view)  
        {  
  
            if (view == null)  
            {  
                throw new ArgumentNullException("view");  
            }  
  
            IVsUserData userData = view as IVsUserData;  
            if (userData == null)  
            {  
                throw new InvalidOperationException();  
            }  
  
            object objTextViewHost;  
            if (VSConstants.S_OK  
                   != userData.GetData(Microsoft.VisualStudio  
                                                .Editor  
                                                .DefGuidList.guidIWpfTextViewHost,  
                                       out objTextViewHost))  
            {  
                throw new InvalidOperationException();  
            }  
  
            IWpfTextViewHost textViewHost = objTextViewHost as IWpfTextViewHost;  
            if (textViewHost == null)  
            {  
                throw new InvalidOperationException();  
            }  
  
            return textViewHost.TextView;  
        }  
  
        /// <summary>  
        /// Given an IWpfTextView, find the position of the caret and report its column  
        /// number. The column number is 0-based  
        /// </summary>  
        /// <param name="textView">The text view containing the caret</param>  
        /// <returns>The column number of the caret's position. When the caret is at the  
        /// leftmost column, the return value is zero.</returns>  
        private static int GetCaretColumn(IWpfTextView textView)  
        {  
            // This is the code the editor uses to populate the status bar.  
            Microsoft.VisualStudio.Text.Formatting.ITextViewLine caretViewLine =  
                textView.Caret.ContainingTextViewLine;  
            double columnWidth = textView.FormattedLineSource.ColumnWidth;  
            return (int)(Math.Round((textView.Caret.Left - caretViewLine.Left)  
                                       / columnWidth));  
        }  
  
        /// <summary>  
        /// Determine the applicable column number for an add or remove command.  
        /// The column is parsed from command arguments, if present. Otherwise  
        /// the current position of the caret is used to determine the column.  
        /// </summary>  
        /// <param name="e">Event args passed to the command handler.</param>  
        /// <returns>The column number. May be negative to indicate the column number is  
        /// unavailable.</returns>  
        /// <exception cref="ArgumentException">The column number parsed from event args  
        /// was not a valid integer.</exception>  
        private int GetApplicableColumn(EventArgs e)  
        {  
            var inValue = ((OleMenuCmdEventArgs)e).InValue as string;  
            if (!string.IsNullOrEmpty(inValue))  
            {  
                int column;  
                if (!int.TryParse(inValue, out column) || column < 0)  
                    throw new ArgumentException("Invalid column");  
                return column;  
            }  
  
            return GetCurrentEditorColumn();  
        }  
  
        /// <summary>  
        /// This function is the callback used to execute a command when the a menu item  
        /// is clicked. See the Initialize method to see how the menu item is associated  
        /// to this function using the OleMenuCommandService service and the MenuCommand  
        /// class.  
        /// </summary>  
        private void AddColumnGuideExecuted(object sender, EventArgs e)  
        {  
            int column = GetApplicableColumn(e);  
            if (column >= 0)  
            {  
                GuidesSettingsManager.AddGuideline(column);  
            }  
        }  
  
        private void RemoveColumnGuideExecuted(object sender, EventArgs e)  
        {  
            int column = GetApplicableColumn(e);  
            if (column >= 0)  
            {  
                GuidesSettingsManager.RemoveGuideline(column);  
            }  
        }  
  
        private void RemoveAllGuidelinesExecuted(object sender, EventArgs e)  
        {  
            GuidesSettingsManager.RemoveAllGuidelines();  
        }  
  
        private void ChooseGuideColorExecuted(object sender, EventArgs e)  
        {  
            System.Windows.Media.Color color = GuidesSettingsManager.GuidelinesColor;  
  
            using (System.Windows.Forms.ColorDialog picker =   
                new System.Windows.Forms.ColorDialog())  
            {  
                picker.Color = System.Drawing.Color.FromArgb(255, color.R, color.G,  
                                                             color.B);  
                if (picker.ShowDialog() == System.Windows.Forms.DialogResult.OK)  
                {  
                    GuidesSettingsManager.GuidelinesColor =   
                        System.Windows.Media.Color.FromRgb(picker.Color.R,  
                                                           picker.Color.G,   
                                                           picker.Color.B);  
                }  
            }  
        }  
  
    }  
}  
  
```  
  
 **Corregir referencias**. Falta una referencia en este momento. Presione el botón derecho del puntero en el nodo referencias en el Explorador de soluciones. Elija el **agregar...**  comando.  El **Agregar referencia** cuadro de diálogo tiene un cuadro de búsqueda en la esquina superior derecha. Escriba "editor" (sin las comillas dobles). Elija la **Microsoft.VisualStudio.Editor** elemento (que debe seleccionar la casilla a la izquierda del elemento, no solo tiene que seleccionar el elemento) y elija **Aceptar** para agregar la referencia.  
  
 **Inicialización**.  Cuando se inicializa la clase de paquete, llama a `Initialize` en la clase de implementación de comandos. El `ColumnGuideCommands` crea una instancia de la clase de inicialización y guarda la instancia de clase y la referencia de paquete en los miembros de clase.  
  
 Echemos un vistazo a uno de lo comandos controlador gancho-ups desde el constructor de clase:  
  
```csharp  
_addGuidelineCommand =   
    new OleMenuCommand(AddColumnGuideExecuted, null,  
                       AddColumnGuideBeforeQueryStatus,  
                       new CommandID(ColumnGuideCommands.CommandSet,  
                                     cmdidAddColumnGuide));  
  
```  
  
 Crear un `OleMenuCommand`. Visual Studio usa el sistema de comandos de Microsoft Office. Los argumentos claves al crear instancias de un `OleMenuCommand` es la función que implementa el comando (`AddColumnGuideExecuted`), la función que se va a llamar cuando Visual Studio muestra un menú con el comando (`AddColumnGuideBeforeQueryStatus`) y el identificador de comando. Visual studio llama a la función de estado de la consulta antes de mostrar un comando en un menú para que el comando puede hacer que esté oculto o atenuado para una determinada pantalla del menú (por ejemplo, si deshabilita **copia** si no hay ninguna selección), cambiar el icono, o incluso cambiar su nombre (por ejemplo, en Agregar algo a quitar algo) y así sucesivamente. El identificador de comando debe coincidir con un comando identificador declarado en el *.vsct* archivo. Las cadenas para el conjunto de comandos y las guías de columnas Agregar comando debe coincidir entre el *.vsct* archivo y la *ColumnGuideCommands.cs*.  
  
 La siguiente línea proporciona asistencia para cuando los usuarios invocan el comando a través de la ventana de comandos (se explica más adelante):  
  
```csharp  
_addGuidelineCommand.ParametersDescription = "<column>";  
```  
  
 **Consultar el estado**. Las funciones de estado de consulta `AddColumnGuideBeforeQueryStatus` y `RemoveColumnGuideBeforeQueryStatus` comprobar algunos valores de configuración (por ejemplo, el número máximo de las guías o columna max) o si hay una guía de columna para quitar. Permiten a los comandos si cumplen las condiciones.  Funciones de consulta de estado deben ser eficaz porque se ejecutan cada vez que Visual Studio muestra un menú y para cada comando en el menú.  
  
 **Función AddColumnGuideExecuted**. La parte interesante de agregar a una guía es averiguar la ubicación del símbolo de intercalación y de vista del editor actual.  En primer lugar, esta función llama a `GetApplicableColumn`, que comprueba si hay un argumento proporcionado por el usuario en argumentos de eventos del controlador de comandos y, si no hay ninguno, la función comprueba la vista del editor:  
  
```csharp  
private int GetApplicableColumn(EventArgs e)  
{  
    var inValue = ((OleMenuCmdEventArgs)e).InValue as string;  
    if (!string.IsNullOrEmpty(inValue))  
    {  
        int column;  
        if (!int.TryParse(inValue, out column) || column < 0)  
            throw new ArgumentException("Invalid column");  
        return column;  
    }  
  
    return GetCurrentEditorColumn();  
}  
  
```  
  
 `GetCurrentEditorColumn` tiene que investigar un poco para obtener un <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView> vista del código.  Si realiza un seguimiento a través de `GetActiveTextView`, `GetActiveView`, y `GetTextViewFromVsTextView`, puede ver cómo hacerlo. El código siguiente es el código pertinente que abstrae, empezando por la selección actual, obtener el marco de la selección y, luego, obtener DocView del marco como un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>, a continuación, obtener un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData> desde el objeto IVsTextView y, después, obtener un host de vista, y Por último el IWpfTextView:  
  
```csharp  
   IVsMonitorSelection selection =  
       this.ServiceProvider.GetService(typeof(IVsMonitorSelection))   
           as IVsMonitorSelection;  
   object frameObj = null;  
  
ErrorHandler.ThrowOnFailure(selection.GetCurrentElementValue(  
                                (uint)VSConstants.VSSELELEMID.SEID_DocumentFrame,  
                                out frameObj));  
  
   IVsWindowFrame frame = frameObj as IVsWindowFrame;  
   if (frame == null)  
       <<do nothing>>;  
  
...  
   object pvar;  
   ErrorHandler.ThrowOnFailure(frame.GetProperty((int)__VSFPROPID.VSFPROPID_DocView,  
                                                  out pvar));  
  
   IVsTextView textView = pvar as IVsTextView;  
   if (textView == null)  
   {  
       IVsCodeWindow codeWin = pvar as IVsCodeWindow;  
       if (codeWin != null)  
       {  
           ErrorHandler.ThrowOnFailure(codeWin.GetLastActiveView(out textView));  
       }  
   }  
  
...  
   if (textView == null)  
       <<do nothing>>  
  
   IVsUserData userData = textView as IVsUserData;  
   if (userData == null)  
       <<do nothing>>  
  
   object objTextViewHost;  
   if (VSConstants.S_OK   
           != userData.GetData(Microsoft.VisualStudio.Editor.DefGuidList  
                                                            .guidIWpfTextViewHost,  
                                out objTextViewHost))  
   {  
       <<do nothing>>  
   }  
  
   IWpfTextViewHost textViewHost = objTextViewHost as IWpfTextViewHost;  
   if (textViewHost == null)  
       <<do nothing>>  
  
   IWpfTextView textView = textViewHost.TextView;  
  
```  
  
 Una vez que tenga un IWpfTextView, puede obtener la columna donde se encuentra el símbolo de intercalación:  
  
```csharp  
private static int GetCaretColumn(IWpfTextView textView)  
{  
    // This is the code the editor uses to populate the status bar.  
    Microsoft.VisualStudio.Text.Formatting.ITextViewLine caretViewLine =  
        textView.Caret.ContainingTextViewLine;  
    double columnWidth = textView.FormattedLineSource.ColumnWidth;  
    return (int)(Math.Round((textView.Caret.Left - caretViewLine.Left)  
                                / columnWidth));  
}  
  
```  
  
 Con la columna actual en la mano cuando el usuario hizo clic, el código simplemente llama a en el Administrador de configuración para agregar o quitar la columna. El Administrador de configuración activa el evento para que todos los `ColumnGuideAdornment` escuchan los objetos. Cuando se desencadena el evento, estos objetos actualización sus vistas de texto asociado con la nueva configuración de la Guía de columna.  
  
## <a name="invoke-command-from-the-command-window"></a>Invocar comando de la ventana de comandos  
 El ejemplo de las guías de columna permite a los usuarios invocar los dos comandos desde la ventana de comandos como una forma de extensibilidad. Si usas el **vista &#124; Other Windows &#124; ventana de comandos** de comandos, puede ver la ventana de comandos. Puede interactuar con la ventana de comandos escribiendo "Editar" y con Autocompletar nombres de comando y proporcionando el argumento 120, tendrá el siguiente resultado:  
  
```csharp  
> Edit.AddColumnGuide 120  
>  
```  
  
 Las partes del ejemplo que habilitar este comportamiento se encuentran en el *.vsct* archivo declaraciones, el `ColumnGuideCommands` constructor de clase cuando enlaza los controladores de comandos y las implementaciones de controlador de comandos que comprobación los argumentos de evento.  
  
 Vio "`<CommandFlag>CommandWellOnly</CommandFlag>`" en el *.vsct* archivo, así como las selecciones de ubicación en la **editar** menú principal, aunque no se muestran los comandos en el **editar** menú de la interfaz de usuario. Tenerlas en el método main **editar** les nombres como menú **Edit.AddColumnGuide**. La declaración del grupo de comandos que contiene los cuatro comandos coloca el grupo en el **editar** menú directamente:  
  
```xml  
<Group guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup"  
             priority="0xB801">  
        <Parent guid="guidSHLMainMenu" id="IDM_VS_MENU_EDIT" />  
      </Group>  
  
```  
  
 La sección de botones de los comandos declaró `CommandWellOnly` para mantenerlos invisible en el menú principal y se ha declarado con `AllowParams`:  
  
```xml  
<Button guid="guidColumnGuidesCommandSet" id="cmdidAddColumnGuide"   
        priority="0x0100" type="Button">  
  <Parent guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup" />  
  <Icon guid="guidImages" id="bmpPicAddGuide" />  
  <CommandFlag>CommandWellOnly</CommandFlag>  
  <CommandFlag>AllowParams</CommandFlag>  
  
```  
  
 Vio el controlador de comandos enlazar el código en el `ColumnGuideCommands` constructor de clase proporciona una descripción de los parámetros permitidos:  
  
```csharp  
_addGuidelineCommand.ParametersDescription = "<column>";  
  
```  
  
 Ha visto la `GetApplicableColumn` función comprobaciones `OleMenuCmdEventArgs` para un valor antes de comprobar la vista del editor para una columna actual:  
  
```csharp  
private int GetApplicableColumn(EventArgs e)  
{  
    var inValue = ((OleMenuCmdEventArgs)e).InValue as string;  
    if (!string.IsNullOrEmpty(inValue))  
    {  
        int column;  
        if (!int.TryParse(inValue, out column) || column < 0)  
            throw new ArgumentException("Invalid column");  
        return column;  
    }  
  
```  
  
## <a name="try-your-extension"></a>Pruebe la extensión  
 Ahora puede presionar **F5** para ejecutar la extensión de guías de columnas. Abra un archivo de texto y utilizar el menú contextual del editor para agregar líneas de guía, quitarlos y cambiar su color. Haga clic en el texto (no un espacio en blanco alcanzó el final de la línea) para agregar una columna manual, o el editor lo agrega a la última columna en la línea. Si utiliza la ventana de comandos e invocar los comandos con un argumento, puede agregar las guías de columnas en cualquier lugar.  
  
 Si desea probar diferentes comandos la ubicación, cambiar nombres, cambiar los iconos y así sucesivamente, y tiene problemas con Visual Studio que muestra el código más reciente en los menús, puede restablecer el subárbol experimental en el que está depurando. Abrir el **menú de inicio de Windows** y escriba "Restablecer". Busque y ejecute el comando, **restablecer la próxima Visual Studio Experimental Instance**. Este comando elimina el subárbol del registro experimental de todos los componentes de extensión. No lo limpia out de la configuración de componentes, por lo que cualquier guías que tenía cuando apaga el subárbol experimental de Visual Studio siguen estando disponibles cuando el código lee el almacén de configuración en el siguiente inicio.  
  
## <a name="finished-code-project"></a>Proyecto de código finalizada  
 Pronto habrá un proyecto de github de ejemplos de extensibilidad de Visual Studio y el proyecto completado estará allí. En este artículo se actualizará para que apunte existe cuando esto ocurre. El proyecto de ejemplo completo puede tener un GUID diferente y tendrá una tira de mapas de bits diferentes para los iconos de comando.  
  
 Puede probar una versión de la característica de las guías de columna con esta galería de Visual Studio[extensión](https://marketplace.visualstudio.com/items?itemName=PaulHarrington.EditorGuidelines).  
  
## <a name="see-also"></a>Vea también  
 [Dentro del editor](../extensibility/inside-the-editor.md)   
 [Ampliar los servicios de editor y lenguaje](../extensibility/extending-the-editor-and-language-services.md)   
 [Puntos de extensión de editor y el servicio de lenguaje](../extensibility/language-service-and-editor-extension-points.md)   
 [Extender los menús y comandos](../extensibility/extending-menus-and-commands.md)   
 [Agregar un submenú a un menú](../extensibility/adding-a-submenu-to-a-menu.md)   
 [Crear una extensión con una plantilla de elementos de editor](../extensibility/creating-an-extension-with-an-editor-item-template.md)