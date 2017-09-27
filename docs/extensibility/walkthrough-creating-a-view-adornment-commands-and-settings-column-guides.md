---
title: "Crear un elemento de gráfico de la vista, los comandos y configuración | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4a2df0a3-42da-4f7b-996f-ee16a35ac922
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: c1836489b1845bca9e57daf83fc97bafeaf9da72
ms.contentlocale: es-es
ms.lasthandoff: 09/26/2017

---
# <a name="walkthrough-creating-a-view-adornment-commands-and-settings-column-guides"></a>Tutorial: Crear un elemento de gráfico de la vista, los comandos y configuración (guías de columnas)
Puede ampliar el editor de texto y código de Visual Studio con los comandos y los efectos de la vista.  En este tema se muestra cómo empezar a trabajar con una característica de extensión populares, guías de columna.  Guías de columna son visualmente claro líneas dibujadas en la vista del editor de texto para ayudarle a administrar el código a los anchos de columna específica.  Código específicamente con formato puede ser importante para los ejemplos se incluyen en los documentos, blogs, o informes de errores.  
  
 En este tutorial, aprenderá lo siguiente:  
  
-   Cree un proyecto VSIX  
  
-   Agregar un elemento de gráfico de la vista de editor  
  
-   Agregar compatibilidad para guardar y obtener configuración (donde guías de columna de dibujo y su color)  
  
-   Agregar comandos (Agregar o quitar las guías de columna, cambiar su color)  
  
-   Coloque los comandos en el menú Edición y menús contextuales de documento de texto  
  
-   Agregar compatibilidad para llamar a los comandos de la ventana de comandos de Visual Studio  
  
 Puede probar una versión de la característica de guías de columna con esta galería de Visual Studio[extensión](https://visualstudiogallery.msdn.microsoft.com/da227a0b-0e31-4a11-8f6b-3a149cf2e459?SRC=Home).  
  
 **Tenga en cuenta**: en este tutorial se pegue una gran cantidad de código en unos pocos archivos generados por plantillas de extensión de visual studio, pero pronto en este tutorial hará referencia a una solución completa en github con otros ejemplos de extensión.  El código completo es ligeramente diferente porque tiene iconos del comando real en lugar de usar iconos generictemplate.  
  
## <a name="getting-started"></a>Introducción  
 A partir de Visual Studio 2015, no instale el SDK de Visual Studio desde el centro de descarga. Se incluye como una característica opcional en el programa de instalación de Visual Studio. También puede instalar el SDK de VS más adelante. Para obtener más información, consulte [instalar el SDK de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="setting-up-the-solution"></a>Configuración de la solución  
 Primero se cree un proyecto VSIX, agregue un elemento de gráfico de la vista de editor y, a continuación, agregue un comando (que agrega un VSPackage que pertenecerá el comando).  La arquitectura básica es la siguiente:  
  
-   Tiene un agente de escucha de creación de vista de texto que se crea un `ColumnGuideAdornment` objeto en cada vista.  Este objeto realiza escuchas para los eventos sobre los cambios en la vista o cambio de configuración, actualización o recomposición columna guías según sea necesario.  
  
-   Hay un `GuidesSettingsManager` que controla la lectura y escritura desde el almacenamiento de configuración de Visual Studio.  El Administrador de configuración también tiene operaciones para actualizar las configuraciones compatibles con los comandos de usuario (Agregar columna, quite la columna, cambiar color).  
  
-   Hay un paquete VSIP que es necesario si tiene comandos de usuario, pero resulta que solo código reutilizable que inicializa el objeto de implementación de comandos.  
  
-   Hay un `ColumnGuideCommands` declarar el objeto que implementa los comandos de usuario y enlaza los controladores de comandos para los comandos en el archivo .vsct.  
  
 **VSIX**.  Use **archivo &#124; Nuevo... ** comando para crear un proyecto.  Elija el nodo de extensibilidad en C# en el panel de navegación izquierdo y elija **proyecto VSIX** en el panel derecho.  Escriba el nombre ColumnGuides y elija **Aceptar** para crear el proyecto.  
  
 **Ver elementos gráficos**.  Presione el botón derecho del puntero en el nodo de proyecto en el Explorador de soluciones.  Elija la **Agregar &#124; Nuevo elemento... ** comando para agregar un nuevo elemento de elementos gráficos de la vista.  Elija **extensibilidad &#124; Editor de** en el panel de navegación izquierdo y elija **elementos gráficos de área de visualización de Editor** en el panel derecho.  Escriba el nombre ColumnGuideAdornment como el nombre del elemento y elija **agregar** para agregarlo.  
  
 Puede ver esta plantilla de elemento agregado dos archivos al proyecto (así como las referencias y así sucesivamente): ColumnGuideAdornment.cs y ColumnGuideAdornmentTextViewCreationListener.cs.  Las plantillas de dibujar un rectángulo de color púrpura en la vista.  A continuación se cambia un par de líneas en el agente de escucha de creación de vista y reemplace el contenido de ColumnGuideAdornment.cs.  
  
 **Comandos**.  Presione el botón derecho del puntero en el nodo de proyecto en el Explorador de soluciones.  Elija la **Agregar &#124; Nuevo elemento... ** comando para agregar un nuevo elemento de elementos gráficos de la vista.  Elija **extensibilidad &#124; VSPackage** en el panel de navegación izquierdo y elija **comando personalizado** en el panel derecho.  Escriba el nombre ColumnGuideCommands como el nombre del elemento y elija **agregar** para agregarlo.  Además de las varias referencias, agregar los comandos y el paquete agrega ColumnGuideCommands.cs, ColumnGuideCommandsPackage.cs y ColumnGuideCommandsPackage.vsct.  A continuación, se reemplazará el contenido de los archivos primeros y últimos para definir e implementar los comandos.  
  
## <a name="setting-up-the-text-view-creation-listener"></a>Configurar el agente de escucha de creación de vista de texto  
 Abra ColumnGuideAdornmentTextViewCreationListener.cs en el editor.  Este código implementa un controlador para cada vez que Visual Studio crea vistas de texto.  Hay atributos que controlan cuando se llama al controlador dependiendo de las características de la vista.  
  
 El código también debe declarar un nivel de elementos gráficos.  Cuando el editor de vistas de las actualizaciones, obtiene las capas de elementos gráficos de la vista y de obtiene los elementos de elementos gráficos.  Puede declarar el orden de la capa en relación con otros usuarios con atributos.  Reemplace la línea siguiente:  
  
```csharp  
[Order(After = PredefinedAdornmentLayers.Caret)]  
```  
  
 con estas dos líneas:  
  
```csharp  
[Order(Before = PredefinedAdornmentLayers.Text)]  
[TextViewRole(PredefinedTextViewRoles.Document)]  
```  
  
 La línea reemplaza está en un grupo de atributos que declaran una capa de elementos gráficos.   La primera línea cambiar únicamente los cambios que deben aparecer las líneas de guía de columna.  Dibujar las líneas de "antes" significa que el texto de la vista que aparecen detrás o debajo del texto.  La segunda línea declara que los elementos de gráficos de guía de columna son aplicables a las entidades de texto que se ajusten a la noción de un documento, pero podría declarar el elemento de gráfico, por ejemplo, solo trabajo de texto editable.  Hay más información en [servicio de lenguaje y puntos de extensión del Editor](../extensibility/language-service-and-editor-extension-points.md)  
  
## <a name="implementing-the-settings-manager"></a>Implementar el Administrador de configuración  
 Reemplace el contenido de la GuidesSettingsManager.cs con el código siguiente (que se explica más adelante):  
  
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
  
 La mayor parte de este código simplemente crea y analiza el formato de configuración: "RGB (\<int >,\<int >,\<int >) \<int >, \<int >,...".  Los enteros al final son las columnas de basado en uno en la que desea guías de columna.  La extensión de guías de columna captura a todas sus opciones en una cadena de valores de configuración de inicio único.  
  
 Hay algunas partes del código que conviene destacar.  La siguiente línea de código obtiene el contenedor administrado de Visual Studio para el almacenamiento de configuración.  En su mayor parte, esto se resume en el registro de Windows, pero esta API es independiente del mecanismo de almacenamiento.  
  
```csharp  
internal static SettingsManager VsManagedSettingsManager =  
    new ShellSettingsManager(ServiceProvider.GlobalProvider);  
```  
  
 El almacenamiento de información de configuración de Visual Studio usa un identificador de categoría y un identificador de configuración para identificar de forma exclusiva todas las configuraciones:  
  
```csharp  
private const string _collectionSettingsName = "Text Editor";  
private const string _settingName = "Guides";  
```  
  
 No es necesario usar `"Text Editor"` como la categoría de nombre y se puede elegir que desee.  
  
 Las primeras algunas funciones son los puntos de entrada para cambiar la configuración.  Comprueban las restricciones de alto nivel como número máximo de guías permitido.  A continuación, llaman a `WriteSettings` que crea una cadena de configuración y establece la propiedad `GuideLinesConfiguration`.  Al establecer esta propiedad, guarda el valor de configuración en el almacén de configuración de Visual Studio y se activa la `SettingsChanged` evento para actualizar todos los `ColumnGuideAdornment` objetos, cada uno asociado a una vista de texto.  
  
 Hay un par de funciones de punto de entrada, como `CanAddGuideline`, que se usan para implementar los comandos que cambien la configuración.  Cuando Visual Studio muestra los menús, consulta las implementaciones de comando para ver si el comando está habilitado actualmente, ¿cuál es su nombre, etcetera.  A continuación verá cómo enlazar estos puntos de entrada para las implementaciones de comando.  Vea [extender menús y comandos de](../extensibility/extending-menus-and-commands.md) para obtener más información acerca de los comandos.  
  
## <a name="implementing-the-columnguideadornment-class"></a>Implementación de la clase ColumnGuideAdornment  
 El `ColumnGuideAdornment` se crea una instancia de clase para cada vista de texto que puede tener opciones gráficas.  Esta clase realiza escuchas para los eventos sobre el cambio de vista o cambio de configuración, actualización o recomposición columna guías según sea necesario.  
  
 Reemplace el contenido de la ColumnGuideAdornment.cs con el código siguiente (que se explica más adelante):  
  
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
  
 Instancias de esta clase retener asociado <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView> y una lista de `Line` objetos dibujados en la vista.  
  
 El constructor (llamado desde `ColumnGuideAdornmentTextViewCreationListener` cuando Visual Studio crea nuevas vistas) crea la Guía de columna `Line` objetos.  El constructor también agrega los controladores para la `SettingsChanged` evento (definido en `GuidesSettingsManager`) y los eventos de vista `LayoutChanged` y `Closed`.  
  
 El `LayoutChanged` desencadena el evento debido a varios tipos de cambios en la vista, incluso cuando Visual Studio crea la vista.  El `OnViewLayoutChanged` las llamadas del controlador `AddGuidelinesToAdornmentLayer` para ejecutar.  El código en `OnViewLayoutChanged` determina si es necesario actualizar las posiciones de línea según los cambios, como cambios de tamaño de fuente, vista medianiles, desplazamiento horizontal y así sucesivamente.  El código de `UpdatePositions` hace que las líneas de guía dibujar entre caracteres o justo después de la columna de texto que se encuentra en el desplazamiento de caracteres especificado en la línea de texto.  
  
 Cada vez que cambia la configuración de la `SettingsChanged` función vuelve a crear todos los `Line` objetos con cualquier la nueva configuración es.  Después de establecer las posiciones de línea, el código quita todas las `Line` objetos desde la `ColumnGuideAdornment` capa de elementos gráficos y agrega los nuevos.  
  
## <a name="defining-the-commands-menus-and-menu-placements"></a>Definir las ubicaciones de menú, menús y comandos  
 Puede haber mucho para declarar los menús y comandos, colocar grupos de menús o comandos en varios otros menús y enlazar los controladores de comandos.  En este tutorial se destaca cómo funcionan los comandos en esta extensión, pero para obtener información más detallada, vea [extender menús y comandos de](../extensibility/extending-menus-and-commands.md).  
  
### <a name="introduction-to-the-code"></a>Introducción al código  
 La extensión de guías de columna muestra la declaración de un grupo de comandos que forman un conjunto (Agregar columna, quitar columna, cambiar el color de línea) y, a continuación, colocar ese grupo en un submenú del menú contextual del editor.  La extensión de guías de columna también agrega los comandos a los principales **editar** menú pero mantiene vuelven invisibles, tratado como un patrón común a continuación.  
  
 Hay tres partes para la implementación de comandos: ColumnGuideCommandsPackage.cs, ColumnGuideCommandsPackage.vsct y ColumnGuideCommands.cs.  El código generado por las plantillas coloca un comando en el **herramientas** menú que se abre un cuadro de diálogo como la implementación.  También puede buscar en la que se implementa en los archivos de ColumnGuideCommands.cs y .vsct ya que es bastante sencillo.  Reemplazará el código de estos archivos.  
  
 El código del paquete es declaraciones reutilizable que son necesarias para Visual Studio detectar que la extensión ofrece comandos y dónde colocar los comandos.  Cuando se inicializa el paquete, solo una instancia de la clase de implementación de comandos.  Ver los comandos de vínculo para obtener más información acerca de los paquetes relacionados con los comandos.  
  
### <a name="a-common-commands-pattern"></a>Un patrón común de comandos  
 Los comandos de la extensión de guías de columna son un ejemplo de un modelo muy común en Visual Studio.  Incluir comandos relacionados en un grupo, y coloque ese grupo en un menú principal, a menudo con "`<CommandFlag>CommandWellOnly</CommandFlag>`" establecido en hacer que el comando sea invisible.  Colocar los comandos en los menús principales (como **editar**) les nombres "nice" de esta forma (como **Edit.AddColumnGuide**) que son útiles para buscar comandos al volver a asignar los enlaces de teclado en ** Opciones de las herramientas** y obtener finalización al invocar comandos desde el **ventana de comandos**.  
  
 A continuación, agregue el grupo de comandos a menús contextuales o sub donde se espera al usuario que utilice los comandos de menús.  Visual Studio trata `CommandWellOnly` como una marca de invisibilidad de los menús principales solo.  Cuando se coloca el mismo grupo de comandos en un menú contextual o sub, los comandos están visibles.  
  
 Como parte del patrón común, la extensión de guías de columnas crea un segundo grupo que contiene un menú de sub único.  El submenú a su vez contiene el primer grupo con los comandos de la Guía de cuatro columnas.  El segundo grupo que contiene el menú de sub es el activo reutilizable que le dé a varios menús contextuales, que coloca un submenú en los menús contextuales.  
  
### <a name="the-vsct-file"></a>El archivo .vsct  
 El archivo .vsct declara los comandos y la ubicación donde, junto con los iconos y así sucesivamente.  Reemplace el contenido del archivo vsct con el código siguiente (que se explica más adelante):  
  
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
  
 **GUID**.  Para que Visual Studio buscar los controladores de comandos e invocarlos, debe asegurarse de que el paquete de GUID que se declara en el archivo de ColumnGuideCommandsPackage.cs (generado desde la plantilla de elemento de proyecto) coincide con el paquete que GUID declarado en el archivo .vsct (copiado desde arriba ).  Si vuelve a usar este código de ejemplo, debe asegurarse de que tener un GUID diferente para no entren en conflicto con cualquier otra persona que puede haber copiado este código.  
  
 Encuentre esta línea en ColumnGuideCommandsPackage.cs y copie el GUID entre comillas:  
  
```csharp  
public const string PackageGuidString = "ef726849-5447-4f73-8de5-01b9e930f7cd";  
```  
  
 A continuación, pegue el GUID en el archivo .vsct para que tenga la siguiente línea su `Symbols` declaraciones:  
  
```xml  
<GuidSymbol name="guidColumnGuideCommandsPkg"   
            value="{ef726849-5447-4f73-8de5-01b9e930f7cd}" />  
```  
  
 Establece el GUID para el comando y el archivo de imagen de mapa de bits debe ser único para las extensiones demasiado:  
  
```xml  
<GuidSymbol name="guidColumnGuidesCommandSet"   
            value="{c2bc0047-8bfa-4e5a-b5dc-45af8c274d8e}">  
<GuidSymbol name="guidImages" value="{2C99F852-587C-43AF-AA2D-F605DE2E46EF}">  
```  
  
 Sin embargo, no es necesario cambiar el conjunto de comandos y el GUID de la imagen en este tutorial para obtener el código funcione de mapa de bits.  El comando set GUID debe coincidir con la declaración en el archivo ColumnGuideCommands.cs, pero se reemplazará el contenido de ese archivo demasiado; por lo tanto, se corresponderá con el GUID.  
  
 El resto de GUID en el archivo .vsct identifica menús existentes al que se agregan los comandos de la Guía de columna, para que nunca cambian.  
  
 **Secciones de archivos**.  El archivo .vsct contiene tres secciones externas: comandos, ubicaciones y símbolos.  La sección de comandos define grupos de comandos, menús, botones o elementos de menú y mapas de bits de iconos.  La sección ubicaciones declara dónde de grupos en los menús o ubicaciones adicionales en los menús ya existentes.  La sección de símbolos declara identificadores usados en otro lugar en el archivo .vsct, que hace que el código de vsct sea más legible a no tener GUID y los números hexadecimales en cualquier lugar.  
  
 **Sección de comandos, las definiciones de grupos**.  La sección de comandos primero define grupos de comandos.  Los grupos de comandos son comandos que se ven en los menús con pequeñas líneas gris separan los grupos.  Un grupo también puede rellenar un submenú completo, como en este ejemplo, y no ve la separación en este caso las líneas de color gris.  Los archivos .vsct declara dos grupos, el `GuidesMenuItemsGroup` que tiene un elemento primario a la `IDM_VS_MENU_EDIT` (principal **editar** menú) y la `GuidesContextMenuGroup` que tiene un elemento primario a la `IDM_VS_CTXT_CODEWIN` (menú contextual del editor de código).  
  
 La segunda declaración de grupo no tiene un `0x0600` prioridad:  
  
```xml  
<Group guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup"   
             priority="0x0600">  
```  
  
 La idea es colocar la columna guías de submenú al final de cualquier menú contextual en el que se agregue el grupo de menús de sub.  Sin embargo, no se debe suponer que conoce mejor y forzar el submenú para que siempre esté última mediante el uso de una prioridad de `0xFFFF`.  Tendrá que experimentar con este número para ver dónde se encuentra el submenú en los menús contextuales dónde se coloca.  En este caso `0x0600` es lo suficientemente alto como para colocar al final de los menús en lo que podemos ver, pero deja espacio a otra persona para diseñar su extensión sea inferior a la extensión de guías de columna si es conveniente.  
  
 **Sección, definición de menú de comandos**.  A continuación la sección del comando define el submenú `GuidesSubMenu`, primario para el `GuidesContextMenuGroup`.  El `GuidesContextMenuGroup` es el grupo se agrega a todos los menús de contexto pertinente.  En la sección ubicaciones, el código coloca el grupo con los comandos de la Guía de cuatro columnas en este menú sub.  
  
 **Sección de comandos, botones definiciones**.  La sección de comandos, a continuación, define los elementos de menú o botones de la columna cuatro guías de comandos.  `CommandWellOnly`, se explicó anteriormente, significa que los comandos no son visibles cuando se coloca en un menú principal.  Las declaraciones de dos del elemento de menú botones (Guía de agregar y quitar guía) también tienen un `AllowParams` marca:  
  
```xml  
<CommandFlag>AllowParams</CommandFlag>  
```  
  
 Esta marca permite que, junto con que tenga ubicaciones de menú principal, el comando para recibir argumentos cuando Visual Studio, se invoca el controlador de comandos.  Si el usuario invoca el comando desde la ventana de comandos, el argumento se pasa al controlador de comandos en el evento argumentos.  
  
 **Comandos secciones, definiciones de mapas de bits**.  Por último, la sección de comandos declara los mapas de bits o iconos que se utilizan para los comandos.  Se trata de una declaración simple que identifica el recurso del proyecto y enumera los índices basados en uno de los iconos de uso.  La sección de símbolos del archivo vsct declara los valores de los identificadores usados como índices.  Este tutorial utiliza la franja de mapa de bits proporcionada con la plantilla de elemento de comando personalizado agregada al proyecto.  
  
 **Sección de ubicaciones**.  Después de los comandos de sección es la sección de ubicaciones.  La primera de ellas es que el código agrega el primer grupo descrito anteriormente que contiene a la Guía de cuatro columna comandos al menú sub donde aparecen los comandos:  
  
```xml  
<CommandPlacement guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup"   
                  priority="0x0100">  
  <Parent guid="guidColumnGuidesCommandSet" id="GuidesSubMenu" />  
</CommandPlacement>  
```  
  
 Todas las demás ubicaciones agregan el `GuidesContextMenuGroup` (que contiene el `GuidesSubMenu`) a otros menús contextuales del editor.  Cuando el código declara los `GuidesContextMenuGroup`, se ha asociado al menú contextual del editor de código.  Que es la razón por la que no se ve una selección de ubicación para el menú contextual del editor de código.  
  
 **Símbolos sección**.  Como se mencionó anteriormente, la sección de símbolos declara identificadores usados en otro lugar en el archivo .vsct, que hace que el código de vsct sea más legible a no tener GUID y los números hexadecimales en cualquier lugar.  Los puntos son importantes en esta sección son que el GUID del paquete debe coincidir con la declaración de la clase de paquete y el conjunto de comandos que GUID debe coincidir con la declaración de la clase de implementación del comando.  
  
## <a name="implementing-the-commands"></a>Implementar los comandos  
 El archivo ColumnGuideCommands.cs implementa los comandos y enlaza los controladores.  Cuando Visual Studio carga el paquete y lo inicializa, el paquete a su vez llama `Initialize` en la clase de implementación de comandos.  La inicialización de comandos simplemente crea una instancia de la clase y el constructor enlaza todos los controladores de comandos.  
  
 Reemplace el contenido del archivo ColumnGuideCommands.cs con el código siguiente (que se explica más adelante):  
  
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
  
 **Corregir las referencias**.  Falta una referencia en este momento.  Presione el botón derecho del puntero en el nodo referencias en el Explorador de soluciones.  Elija la **agregar... ** comando.  El **Agregar referencia** cuadro de diálogo tiene un cuadro de búsqueda en la esquina superior derecha.  Escriba "editor" (sin las comillas dobles).  Elija la **Microsoft.VisualStudio.Editor** elemento (debe seleccionar la casilla a la izquierda del elemento, no simplemente seleccione el elemento) y elija **Aceptar** para agregar la referencia.  
  
 **Inicialización**.  Cuando se inicializa la clase de paquete, se llama a `Initialize` en la clase de implementación de comandos.  El `ColumnGuideCommands` crea una instancia de la clase de inicialización y guarda la instancia de clase y la referencia de paquete en los miembros de clase.  
  
 Echemos un vistazo a uno de los SAI (UPS) enlace de controlador de comandos desde el constructor de clase:  
  
```csharp  
_addGuidelineCommand =   
    new OleMenuCommand(AddColumnGuideExecuted, null,  
                       AddColumnGuideBeforeQueryStatus,  
                       new CommandID(ColumnGuideCommands.CommandSet,  
                                     cmdidAddColumnGuide));  
  
```  
  
 Crear un `OleMenuCommand`.  Visual Studio usa el sistema de comandos de Microsoft Office.  Los argumentos de clave al crear instancias de un OleMenuCommand es la función que implementa el comando (`AddColumnGuideExecuted`), la función que se llamará cuando Visual Studio muestra un menú con el comando (`AddColumnGuideBeforeQueryStatus`) y el identificador del comando.  Visual studio llama a la función de estado de la consulta antes de mostrar un comando en un menú para que el comando puede hacer lo mismo atenuados para una pantalla concreta del menú o invisible (por ejemplo, si deshabilita **copia** si no hay ninguna selección), cambiar el icono, o incluso cambiar su nombre (por ejemplo, de agregar algo a quitar algo) y así sucesivamente.  El identificador de comando debe coincidir con un identificador de comando que se declaran en el archivo .vsct.  Establece las cadenas para el comando y las guías de columna Agregar comando debe coincidir entre el archivo .vsct y el ColumnGuideCommands.cs.  
  
 La siguiente línea proporciona ayuda para cuando los usuarios invocan el comando a través de la ventana de comandos (que se explica más adelante):  
  
```csharp  
_addGuidelineCommand.ParametersDescription = "<column>";  
```  
  
 **Consultar el estado**.  Las funciones de estado de consulta `AddColumnGuideBeforeQueryStatus` y `RemoveColumnGuideBeforeQueryStatus` Compruebe algunas configuraciones (por ejemplo, el número máximo de las guías o una columna max) o si hay una guía de columna para quitar.  Permiten a los comandos si las condiciones son correctas.  Funciones de consulta de estado deben ser muy eficaz porque se ejecutan cada vez que Visual Studio muestra un menú, para cada comando en el menú.  
  
 **Función AddColumnGuideExecuted**.  La parte interesante de agregar a una guía es pensar en la ubicación actual del símbolo de intercalación y de vista editor.  En primer lugar, esta función llama `GetApplicableColumn` que comprueba si hay un argumento proporcionado por el usuario en los argumentos de evento del controlador de comandos, y si no hay ninguno, la función comprueba la vista del editor:  
  
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
  
 `GetCurrentEditorColumn`tiene que examine un poco para obtener un <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView> vista del código.  Si realiza un seguimiento a través de `GetActiveTextView`, `GetActiveView`, y `GetTextViewFromVsTextView`, puede ver cómo hacerlo.  El siguiente es el código relevante abstraído, a partir de la selección actual y obtener el marco de la selección y, luego, obtener DocView del marco como un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>, a continuación, obtener un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData> desde el objeto IVsTextView, a continuación, obtener un host de la vista, y Por último, el objeto IWpfTextView:  
  
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
  
 Una vez que tenga un objeto IWpfTextView, puede obtener la columna donde se encuentra el símbolo de intercalación:  
  
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
  
 Con la columna actual en la parte donde el usuario hizo clic, el código simplemente llama en el Administrador de configuración para agregar o quitar la columna.  El Administrador de configuración activa el evento para que todos los `ColumnGuideAdornment` objetos escuchan.  Cuando se desencadena el evento, estos objetos actualizan sus vistas de texto asociado con una nueva configuración de la Guía de columna.  
  
## <a name="invoking-command-from-the-command-window"></a>Invocar comando de la ventana de comandos  
 El ejemplo de guías de columna permite a los usuarios invocar dos comandos de la ventana de comandos como una forma de extensibilidad.  Si usas el **vista &#124; Otras ventanas &#124; Ventana de comandos** de comandos, puede ver la ventana de comandos.  Puede interactuar con la ventana de comandos escribiendo "Editar" y con Autocompletar nombres de comando y se proporciona el argumento 120, dispone de lo siguiente:  
  
```  
> Edit.AddColumnGuide 120  
>  
```  
  
 Las partes del ejemplo que habilitan esta están en las declaraciones de archivo .vsct, el `ColumnGuideCommands` constructor de clase cuando enlaza controladores de comandos y las implementaciones de controlador de comandos que comprobación los argumentos de evento.  
  
 Ha visto "`<CommandFlag>CommandWellOnly</CommandFlag>`" en el archivo .vsct, así como ubicaciones en el menú principal de edición, aunque no mostramos los comandos en el **editar** menú interfaz de usuario.  Indica que existen en el menú de edición principal les nombres como **Edit.AddColumnGuide**.  Los comandos de grupo declaración que contiene que los cuatro comandos colocan el grupo en el menú Editar directamente:  
  
```xml  
<Group guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup"  
             priority="0xB801">  
        <Parent guid="guidSHLMainMenu" id="IDM_VS_MENU_EDIT" />  
      </Group>  
  
```  
  
 La sección de botones declaró los comandos `CommandWellOnly` para que sean visibles en el menú principal y se ha declarado con `AllowParams`:  
  
```xml  
<Button guid="guidColumnGuidesCommandSet" id="cmdidAddColumnGuide"   
        priority="0x0100" type="Button">  
  <Parent guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup" />  
  <Icon guid="guidImages" id="bmpPicAddGuide" />  
  <CommandFlag>CommandWellOnly</CommandFlag>  
  <CommandFlag>AllowParams</CommandFlag>  
  
```  
  
 Ha visto el controlador de comandos enlazar código en el `ColumnGuideCommands` una descripción del parámetro permitido proporcionada por el constructor de clase:  
  
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
  
## <a name="trying-your-extension"></a>Tratar la extensión  
 Ahora puede presionar **F5** para ejecutar la extensión de guías de columna.  Abra un archivo de texto y utilice el menú contextual del editor para agregar las líneas de guía, quitar y cambiar su color.  Debe hacer clic en texto (no un espacio en blanco alcanzó el final de la línea) para agregar una columna guía o el editor agrega a la última columna en la línea.  Si utiliza la ventana de comandos e invocar los comandos con un argumento, puede agregar a guías de columna en cualquier lugar.  
  
 Si desea intentarlo ubicaciones de comando diferente, cambiar nombres, cambiar los iconos y así sucesivamente, y tiene problemas con Visual Studio que muestra el código más reciente en los menús, puede restablecer el subárbol experimental en el que está depurando.  Mostrar la **menú Inicio en Windows** y escriba "Restablecer".  Busque e invocar el comando **restablecer la siguiente Visual Studio la instancia Experimental**.  Esto limpia el subárbol del registro experimental de todos los componentes de extensión.  No limpieza fuera de la configuración de componentes, por lo que tenía cuando cierra el subárbol experimental de Visual Studio incluye cualquier guía seguirá estando ahí cuando el código lee el almacén de configuración en el siguiente inicio.  
  
## <a name="finished-code-project"></a>Proyecto de código terminado  
 Pronto habrá un proyecto de github de ejemplos de extensibilidad de Visual Studio y el proyecto completado estarán disponibles.  Actualizamos este tema para que se señale cuando esto ocurre.  El proyecto de ejemplo completo que tenga GUID diferentes y tendrá una banda de mapas de bits diferentes de los iconos de comando.  
  
 Puede probar una versión de la característica de guías de columna con esta galería de Visual Studio[extensión](https://visualstudiogallery.msdn.microsoft.com/da227a0b-0e31-4a11-8f6b-3a149cf2e459?SRC=Home).  
  
## <a name="see-also"></a>Vea también  
 [Dentro del Editor](../extensibility/inside-the-editor.md)   
 [Extender el Editor y los servicios de lenguaje](../extensibility/extending-the-editor-and-language-services.md)   
 [Servicio de lenguaje y puntos de extensión del Editor](../extensibility/language-service-and-editor-extension-points.md)   
 [Extender menús y comandos](../extensibility/extending-menus-and-commands.md)   
 [Agregar un submenú a un menú](../extensibility/adding-a-submenu-to-a-menu.md)   
 [Creación de una extensión con una plantilla de elemento de editor](../extensibility/creating-an-extension-with-an-editor-item-template.md)
