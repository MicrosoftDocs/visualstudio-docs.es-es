---
title: Creación de un adorno, comandos y configuraciones de vista ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 4a2df0a3-42da-4f7b-996f-ee16a35ac922
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4aab9e0ede95eebe6f8f54cc3f01e7e7d5f98d1c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697643"
---
# <a name="walkthrough-create-a-view-adornment-commands-and-settings-column-guides"></a>Tutorial: Crear un adorno de vista, comandos y configuración (guías de columna)
Puede ampliar el editor de texto/código de Visual Studio con comandos y efectos de vista. En este artículo se muestra cómo empezar a usar una característica de extensión popular, guías de columna. Las guías de columna son líneas visualmente claras dibujadas en la vista del editor de texto para ayudarle a administrar el código a anchos de columna específicos. Específicamente, el código con formato puede ser importante para los ejemplos que incluya en documentos, entradas de blog o informes de errores.

En este tutorial realizará lo siguiente:
- Crear un proyecto VSIX
- Añadir un adorno de vista de editor
- Agregar soporte para guardar y obtener ajustes (dónde dibujar guías de columna y su color)
- Añadir comandos (añadir/eliminar guías de columna, cambiar su color)
- Coloque los comandos en el menú Editar y en los menús contextuales del documento de texto
- Agregue compatibilidad para invocar los comandos desde la ventana de comandos de Visual Studio

  Puede probar una versión de la característica de guías de columna con esta[extensión](https://marketplace.visualstudio.com/items?itemName=PaulHarrington.EditorGuidelines)de Galería de Visual Studio.

  > [!NOTE]
  > En este tutorial, pegará una gran cantidad de código en algunos archivos generados por plantillas de extensión de Visual Studio. Pero, pronto este tutorial hará referencia a una solución completa en GitHub con otros ejemplos de extensión. El código completado es ligeramente diferente en que tiene iconos de comandos reales en lugar de usar iconos generictemplate.

## <a name="get-started"></a>Introducción
A partir de Visual Studio 2015, no se instala el SDK de Visual Studio desde el centro de descarga. Se incluye como una característica opcional en la configuración de Visual Studio. También puede instalar el SDK de VS más adelante. Para obtener más información, vea [Instalar el SDK](../extensibility/installing-the-visual-studio-sdk.md)de Visual Studio .

## <a name="set-up-the-solution"></a>Configuración de la solución
En primer lugar, cree un proyecto VSIX, agregue un adorno de vista de editor y, a continuación, agregue un comando (que agrega un VSPackage para poseer el comando). La arquitectura básica es la siguiente:
- Tiene un agente de escucha `ColumnGuideAdornment` de creación de vista de texto que crea un objeto por vista. Este objeto escucha eventos sobre el cambio de vista o la configuración cambiar, actualizar o volver a dibujar guías de columna según sea necesario.
- Hay un `GuidesSettingsManager` que controla la lectura y escritura desde el almacenamiento de configuración de Visual Studio. El administrador de configuración también tiene operaciones para actualizar la configuración que admite los comandos de usuario (agregar columna, quitar columna, cambiar color).
- Hay un paquete VSIP que es necesario si tiene comandos de usuario, pero es solo código reutilizable el que inicializa el objeto de implementación de comandos.
- Hay un `ColumnGuideCommands` objeto que ejecuta los comandos de usuario y enlaza los controladores de comandos para los comandos declarados en el archivo *.vsct.*

  **VSIX**. Utilice el comando **File &#124; New ...** para crear un proyecto. Elija el nodo **Extensibilidad** en **C-** en el panel de navegación izquierdo y elija **VSIX Project** en el panel derecho. Escriba el nombre **ColumnGuides** y elija **OK** para crear el proyecto.

  **Ver adorno**. Presione el botón derecho del puntero en el nodo del proyecto en el Explorador de soluciones. Elija el comando **Agregar &#124; nuevo elemento ...** para agregar un nuevo elemento de adorno de vista. Elija **Extensibilidad &#124; Editor** en el panel de navegación izquierdo y elija Editor Viewport **Adornment** en el panel derecho. Escriba el nombre **ColumnGuideAdornment** como el nombre del elemento y elija **Agregar** para agregarlo.

  Puede ver que esta plantilla de elemento ha agregado dos archivos al proyecto (así como referencias, etc.): **ColumnGuideAdornment.cs** y **ColumnGuideAdornmentTextViewCreationListener.cs**. Las plantillas dibujan un rectángulo púrpura en la vista. En la sección siguiente, se cambian un par de líneas en el agente de escucha de creación de vistas y se reemplaza el contenido de **ColumnGuideAdornment.cs**.

  **Comandos**. En el Explorador de **soluciones**, presione el botón derecho del puntero en el nodo del proyecto. Elija el comando **Agregar &#124; nuevo elemento ...** para agregar un nuevo elemento de adorno de vista. Elija **Extensibilidad &#124; VSPackage** en el panel de navegación izquierdo y elija **Comando personalizado** en el panel derecho. Escriba el nombre **ColumnGuideCommands** como nombre del elemento y elija **Add .** Además de varias referencias, agregar los comandos y el paquete también **ColumnGuideCommands.cs**, **ColumnGuideCommandsPackage.cs**y **ColumnGuideCommandsPackage.vsct**. En la siguiente sección, reemplazará el contenido del primer y último archivo para definir e implementar los comandos.

## <a name="set-up-the-text-view-creation-listener"></a>Configurar el agente de escucha de creación de vistas de texto
Abra *ColumnGuideAdornmentTextViewCreationListener.cs* en el editor. Este código implementa un controlador para cada vez que Visual Studio crea vistas de texto. Hay atributos que controlan cuándo se llama al controlador en función de las características de la vista.

El código también debe declarar una capa de adorno. Cuando el editor actualiza las vistas, obtiene las capas de adorno de la vista y de eso se obtienen los elementos de adorno. Puede declarar el orden de la capa en relación con otros con atributos. Reemplace la siguiente línea:

```csharp
[Order(After = PredefinedAdornmentLayers.Caret)]
```

con estas dos líneas:

```csharp
[Order(Before = PredefinedAdornmentLayers.Text)]
[TextViewRole(PredefinedTextViewRoles.Document)]
```

La línea reemplazada se encuentra en un grupo de atributos que declaran una capa de adorno. La primera línea que ha cambiado solo cambia cuando aparecen las líneas guía de columna. Dibujar las líneas "antes" del texto en la vista significa que aparecen detrás o debajo del texto. La segunda línea declara que los adornos de guía de columna son aplicables a las entidades de texto que se ajustan a la noción de un documento, pero podría declarar el adorno, por ejemplo, para que solo funcione para texto editable. Hay más información en el servicio de lenguaje y los [puntos](../extensibility/language-service-and-editor-extension-points.md) de extensión del editor

## <a name="implement-the-settings-manager"></a>Implementar el administrador de configuración
Sustituya el contenido del *GuidesSettingsManager.cs* por el siguiente código (explicado a continuación):

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

La mayor parte de este código crea y\<analiza el\<formato de\<configuración: \<"RGB( \<int>, int>, int>) int>, int>, ...".  Los enteros al final son las columnas basadas en uno donde desea guías de columna. La extensión de guías de columna captura todos sus valores en una cadena de valor de configuración única.

Hay algunas partes del código que vale la pena resaltar. La siguiente línea de código obtiene el contenedor administrado de Visual Studio para el almacenamiento de configuración. En su mayor parte, esto se abstrae sobre el registro de Windows, pero esta API es independiente del mecanismo de almacenamiento.

```csharp
internal static SettingsManager VsManagedSettingsManager =
    new ShellSettingsManager(ServiceProvider.GlobalProvider);
```

El almacenamiento de configuración de Visual Studio usa un identificador de categoría y un identificador de configuración para identificar de forma única todas las configuraciones:

```csharp
private const string _collectionSettingsName = "Text Editor";
private const string _settingName = "Guides";
```

No es necesario `"Text Editor"` utilizarcomo nombre de categoría. Puedes elegir lo que quieras.

Las primeras funciones son los puntos de entrada para cambiar la configuración. Comprueban las restricciones de alto nivel, como el número máximo de guías permitidas.  A continuación, `WriteSettings`llaman a , que compone `GuideLinesConfiguration`una cadena de configuración y establece la propiedad . Establecer esta propiedad guarda el valor de configuración en `SettingsChanged` el almacén `ColumnGuideAdornment` de configuración de Visual Studio y desencadena el evento para actualizar todos los objetos, cada uno asociado a una vista de texto.

Hay un par de funciones `CanAddGuideline`de punto de entrada, como , que se utilizan para implementar comandos que cambian la configuración. Cuando Visual Studio muestra menús, consulta las implementaciones de comandos para ver si el comando está habilitado actualmente, cuál es su nombre, etc.  A continuación puede ver cómo conectar estos puntos de entrada para las implementaciones de comandos. Para obtener más información sobre los [comandos, consulte Extender menús y comandos](../extensibility/extending-menus-and-commands.md).

## <a name="implement-the-columnguideadornment-class"></a>Implementar la clase ColumnGuideAdornment
Se `ColumnGuideAdornment` crea una instancia de la clase para cada vista de texto que puede tener adornos. Esta clase escucha eventos sobre el cambio de vista o el cambio de configuración, y las guías de columna de actualización o redibujo según sea necesario.

Sustituya el contenido del *ColumnGuideAdornment.cs* por el siguiente código (explicado a continuación):

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

Las instancias de esta clase <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView> se mantienen `Line` en la lista asociada y una lista de objetos dibujados en la vista.

El constructor (al que se llama desde `ColumnGuideAdornmentTextViewCreationListener` el `Line` momento en que Visual Studio crea nuevas vistas) crea los objetos de guía de columna.  El constructor también agrega controladores `SettingsChanged` para `GuidesSettingsManager`el evento (definido en ) y los eventos `LayoutChanged` de vista y `Closed`.

El `LayoutChanged` evento se desencadena debido a varios tipos de cambios en la vista, incluido cuando Visual Studio crea la vista. El `OnViewLayoutChanged` controlador `AddGuidelinesToAdornmentLayer` llama a ejecutar. El código `OnViewLayoutChanged` en determina si necesita actualizar las posiciones de línea en función de cambios como cambios de tamaño de fuente, canalones de vista, desplazamiento horizontal, etc. El código `UpdatePositions` de las líneas guía se dibuja entre caracteres o justo después de la columna de texto que se encuentra en el desplazamiento de caracteres especificado en la línea de texto.

Cada vez `SettingsChanged` que la configuración `Line` cambia la función simplemente vuelve a crear todos los objetos con cualquiera que sea la nueva configuración. Después de establecer las posiciones de `Line` línea, `ColumnGuideAdornment` el código elimina todos los objetos anteriores de la capa de adorno y agrega los nuevos.

## <a name="define-the-commands-menus-and-menu-placements"></a>Defina los comandos, menús y ubicaciones de menús
Puede haber mucho para declarar comandos y menús, colocar grupos de comandos o menús en varios otros menús y conectar controladores de comandos. En este tutorial se destaca cómo funcionan los comandos en esta extensión, pero para obtener información más detallada, consulte [Extender menús y comandos](../extensibility/extending-menus-and-commands.md).

### <a name="introduction-to-the-code"></a>Introducción al código
La extensión Guías de columnas muestra la declaración de un grupo de comandos que pertenecen juntos (agregar columna, quitar columna, cambiar el color de línea) y, a continuación, colocar ese grupo en un submenú del menú contextual del editor.  La extensión Guías de columnas también agrega los comandos al menú **Principal de edición,** pero los mantiene invisibles, que se describen como un patrón común a continuación.

Hay tres partes en la implementación de comandos: ColumnGuideCommandsPackage.cs, ColumnGuideCommandsPackage.vsct y ColumnGuideCommands.cs. El código generado por las plantillas coloca un comando en el menú **Herramientas** que muestra un cuadro de diálogo como implementación. Puede ver cómo se implementa en los archivos *.vsct* y *ColumnGuideCommands.cs,* ya que es sencillo. Reemplace el código de estos archivos a continuación.

El código del paquete contiene declaraciones reutilizables necesarias para que Visual Studio detecte que la extensión ofrece comandos y para encontrar dónde colocar los comandos. Cuando se inicializa el paquete, crea una instancia de la clase de implementación de comandos. Para obtener más información acerca de los paquetes relacionados con comandos, consulte [Extender menús y comandos](../extensibility/extending-menus-and-commands.md).

### <a name="a-common-commands-pattern"></a>Un patrón de comandos común
Los comandos de la extensión Guías de columnas son un ejemplo de un patrón muy común en Visual Studio. Coloca comandos relacionados en un grupo y coloca ese grupo`<CommandFlag>CommandWellOnly</CommandFlag>`en un menú principal, a menudo con " " establecido para hacer que el comando sea invisible.  Colocar comandos en los menús principales (como **Editar**) les da nombres bonitos (como **Edit.AddColumnGuide**), que son útiles para buscar comandos al volver a asignar enlaces de teclas en **Opciones**de herramientas . También es útil para obtener la finalización al invocar comandos desde la ventana de **comandos**.

A continuación, agregue el grupo de comandos a los menús contextuales o submenús donde espera que el usuario utilice los comandos. Visual Studio `CommandWellOnly` trata como una marca de invisibilidad solo para los menús principales. Al colocar el mismo grupo de comandos en un menú contextual o submenú, los comandos son visibles.

Como parte del patrón común, la extensión Guías de columnas crea un segundo grupo que contiene un único submenú. El submenú a su vez contiene el primer grupo con los comandos de guía de cuatro columnas. El segundo grupo que contiene el submenú es el activo reutilizable que se coloca en varios menús contextuales, que coloca un submenú en esos menús contextuales.

### <a name="the-vsct-file"></a>El archivo .vsct
El archivo *.vsct* declara los comandos y dónde van, junto con iconos, etc. Reemplace el contenido del archivo *.vsct* por el siguiente código (explicado a continuación):

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

**GUIDS**. Para que Visual Studio busque los controladores de comandos e invoquelos, debe asegurarse de que el GUID del paquete declarado en el archivo *ColumnGuideCommandsPackage.cs* (generado a partir de la plantilla de elemento de proyecto) coincide con el GUID del paquete declarado en el archivo *.vsct* (copiado desde arriba). Si reutiliza este código de ejemplo, debe asegurarse de que tiene un GUID diferente para no entrar en conflicto con otra persona que pueda haber copiado este código.

Busque esta línea en *ColumnGuideCommandsPackage.cs* y copie el GUID entre comillas:

```csharp
public const string PackageGuidString = "ef726849-5447-4f73-8de5-01b9e930f7cd";
```

A continuación, pegue el GUID en el archivo *.vsct* para que tenga la siguiente línea en las `Symbols` declaraciones:

```xml
<GuidSymbol name="guidColumnGuideCommandsPkg"
            value="{ef726849-5447-4f73-8de5-01b9e930f7cd}" />
```

Los GUID para el conjunto de comandos y el archivo de imagen de mapa de bits también deben ser únicos para las extensiones:

```xml
<GuidSymbol name="guidColumnGuidesCommandSet"
            value="{c2bc0047-8bfa-4e5a-b5dc-45af8c274d8e}">
<GuidSymbol name="guidImages" value="{2C99F852-587C-43AF-AA2D-F605DE2E46EF}">
```

Sin embargo, no es necesario cambiar el conjunto de comandos y los GUID de imagen de mapa de bits en este tutorial para que el código funcione. El GUID del conjunto de comandos debe coincidir con la declaración en el archivo *ColumnGuideCommands.cs,* pero también reemplaza el contenido de ese archivo; por lo tanto, los GUID coincidirán.

Otros GUID del archivo *.vsct* identifican los menús preexistentes a los que se agregan los comandos de guía de columna, por lo que nunca cambian.

**Secciones de archivo**. El *archivo .vsct* tiene tres secciones externas: comandos, ubicaciones y símbolos. La sección de comandos define grupos de comandos, menús, botones o elementos de menú, y mapas de bits para iconos. La sección de ubicaciones declara dónde van los grupos en los menús o ubicaciones adicionales en los menús preexistentes. La sección symbols declara los identificadores utilizados en otra parte del archivo *.vsct,* lo que hace que el código *.vsct* sea más legible que tener GUID y números hexadecimales en todas partes.

**Sección Comandos, definiciones de grupos**. La sección de comandos define primero los grupos de comandos. Los grupos de comandos son comandos que se ven en los menús con ligeras líneas grises que separan los grupos. Un grupo también puede rellenar un submenú completo, como en este ejemplo, y no verá las líneas de separación grises en este caso. Los archivos *.vsct* declaran `GuidesMenuItemsGroup` dos grupos, `IDM_VS_MENU_EDIT` el que se parentea en el `IDM_VS_CTXT_CODEWIN` (el menú principal de **edición)** y el `GuidesContextMenuGroup` que se parentea en el (menú contextual del editor de código).

La segunda declaración `0x0600` de grupo tiene prioridad:

```xml
<Group guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup"
             priority="0x0600">
```

La idea es poner el submenú de guías de columna al final de cualquier menú contextual al que se agregue el submenú. Pero, usted no debe asumir que usted sabe mejor y forzar el `0xFFFF`submenú para ser siempre el último mediante el uso de una prioridad de . Tienes que experimentar con el número para ver dónde se encuentra tu submenú en los menús contextuales donde lo colocas. En este `0x0600` caso, es lo suficientemente alto como para ponerlo al final de los menús hasta donde se puede ver, pero deja espacio para que otra persona diseñe su extensión para que sea inferior a la extensión de las guías de columna si eso es deseable.

**Sección Comandos, definición de menú.** A continuación, la sección `GuidesSubMenu`de comandos `GuidesContextMenuGroup`define el submenú , parented a la . Es `GuidesContextMenuGroup` el grupo que se agrega a todos los menús contextuales relevantes. En la sección de ubicaciones, el código coloca el grupo con los comandos de guía de cuatro columnas en este submenú.

**Sección Comandos, definiciones de botones.** A continuación, la sección de comandos define los elementos de menú o botones que son los comandos de guías de cuatro columnas. `CommandWellOnly`, discutido anteriormente, significa que los comandos son invisibles cuando se colocan en un menú principal. Dos de las declaraciones de botón de elemento `AllowParams` de menú (agregar guía y quitar guía) también tienen una marca:

```xml
<CommandFlag>AllowParams</CommandFlag>
```

Esta marca permite, junto con tener ubicaciones de menú principal, el comando para recibir argumentos cuando Visual Studio invoca el controlador de comandos.  Si el usuario ejecuta el comando desde la ventana de comandos, el argumento se pasa al controlador de comandos en los argumentos de evento.

**Secciones de comandos, definiciones**de mapas de bits . Por último, la sección de comandos declara los mapas de bits o iconos utilizados para los comandos. Esta sección es una declaración simple que identifica el recurso del proyecto y enumera los índices basados en uno de los iconos usados. La sección symbols del archivo *.vsct* declara los valores de los identificadores utilizados como índices. En este tutorial se usa la franja de mapa de bits proporcionada con la plantilla de elemento de comando personalizado agregada al proyecto.

**Sección Ubicaciones**. Después de la sección de comandos es la sección de ubicaciones. El primero es donde el código agrega el primer grupo discutido anteriormente que contiene los comandos de guía de cuatro columnas al submenú donde aparecen los comandos:

```xml
<CommandPlacement guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup"
                  priority="0x0100">
  <Parent guid="guidColumnGuidesCommandSet" id="GuidesSubMenu" />
</CommandPlacement>
```

Todas las demás ubicaciones agregan `GuidesContextMenuGroup` `GuidesSubMenu`el (que contiene el ) a otros menús contextuales del editor. Cuando el código `GuidesContextMenuGroup`declaró el , se engendrá del menú contextual del editor de código. Es por eso que no ve una ubicación para el menú contextual del editor de código.

**Sección Símbolos**. Como se indicó anteriormente, la sección de símbolos declara los identificadores utilizados en otra parte del archivo *.vsct,* lo que hace que el código *.vsct* sea más legible que tener GUID y números hexadecimales en todas partes. Los puntos importantes de esta sección son que el GUID del paquete debe coincidir con la declaración en la clase de paquete. Además, el GUID del conjunto de comandos debe coincidir con la declaración en la clase de implementación de comandos.

## <a name="implement-the-commands"></a>Implementar los comandos
El archivo *ColumnGuideCommands.cs* implementa los comandos y enlaza los controladores. Cuando Visual Studio carga el paquete y lo `Initialize` inicializa, el paquete a su vez llama a la clase de implementación de comandos. La inicialización de comandos simplemente crea una instancia de la clase y el constructor enlaza todos los controladores de comandos.

Sustituya el contenido del archivo *ColumnGuideCommands.cs* por el siguiente código (explicado a continuación):

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

**Corregir referencias**. Te falta una referencia en este punto. Presione el botón derecho del puntero en el referencias nodo en el Explorador de soluciones. Elija el comando **Add ....** El cuadro de diálogo **Agregar referencia** tiene un cuadro de búsqueda en la esquina superior derecha. Introduzca "editor" (sin comillas dobles). Elija el **Microsoft.VisualStudio.Editor** elemento (debe marcar la casilla a la izquierda del elemento, no sólo seleccione el elemento) y elija **Aceptar** para agregar la referencia.

**Inicialización**.  Cuando se inicializa la clase `Initialize` de paquete, llama a la clase de implementación de comandos. La `ColumnGuideCommands` inicialización crea una instancia de la clase y guarda la instancia de clase y la referencia de paquete en los miembros de clase.

Echemos un vistazo a uno de los enlaces del controlador de comandos desde el constructor de clase:

```csharp
_addGuidelineCommand =
    new OleMenuCommand(AddColumnGuideExecuted, null,
                       AddColumnGuideBeforeQueryStatus,
                       new CommandID(ColumnGuideCommands.CommandSet,
                                     cmdidAddColumnGuide));

```

Cree un `OleMenuCommand`archivo . Visual Studio usa el sistema de comandos de Microsoft Office. Los argumentos clave al crear `OleMenuCommand` instancias de an es`AddColumnGuideExecuted`la función que implementa el comando (`AddColumnGuideBeforeQueryStatus`), la función a la que se llama cuando Visual Studio muestra un menú con el comando ( ) y el identificador de comando. Visual studio llama a la función de estado de consulta antes de mostrar un comando en un menú para que el comando pueda hacerse invisible o atenuado para una visualización determinada del menú (por ejemplo, deshabilitar **Copiar** si no hay selección), cambiar su icono o incluso cambiar su nombre (por ejemplo, desde Agregar algo para quitar algo), etc. El identificador de comando debe coincidir con un identificador de comando declarado en el archivo *.vsct.* Las cadenas para el conjunto de comandos y el comando de adición de guías de columna deben coincidir entre el archivo *.vsct* y el *ColumnGuideCommands.cs*.

La siguiente línea proporciona asistencia para cuando los usuarios invocan el comando a través de la ventana de comandos (explicada a continuación):

```csharp
_addGuidelineCommand.ParametersDescription = "<column>";
```

 **Estado de la consulta**. El estado `AddColumnGuideBeforeQueryStatus` de `RemoveColumnGuideBeforeQueryStatus` la consulta funciona y comprueba algunas opciones de configuración (como el número máximo de guías o la columna max) o si hay una guía de columna que se va a quitar. Habilitan los comandos si las condiciones son correctas.  Las funciones de estado de consulta deben ser eficaces porque se ejecutan cada vez que Visual Studio muestra un menú y para cada comando del menú.

 **AddColumnGuideExecuted ( función)**. La parte interesante de agregar una guía es averiguar la vista actual del editor y la ubicación del intercalación.  En primer lugar, esta función llama `GetApplicableColumn`a , que comprueba si hay un argumento proporcionado por el usuario en los argumentos de evento del controlador de comandos y, si no hay ninguno, la función comprueba la vista del editor:

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

`GetCurrentEditorColumn`tiene que cavar un <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView> poco para obtener una vista del código.  Si realiza `GetActiveTextView`un `GetActiveView`seguimiento `GetTextViewFromVsTextView`a través de , , y , puede ver cómo hacerlo. El código siguiente es el código relevante abstraído, comenzando con la selección actual, luego obtener <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>el marco <xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData> de la selección, a continuación, obtener docView del marco como un , a continuación, obtener un de la IVsTextView, a continuación, obtener un host de vista y, finalmente, el IWpfTextView:

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

Una vez que tenga un IWpfTextView, puede obtener la columna donde se encuentra el nombre de intercalación:

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

Con la columna actual en la mano donde el usuario hace clic, el código solo llama al administrador de configuración para agregar o quitar la columna. El administrador de configuración activa `ColumnGuideAdornment` el evento en el que escuchan todos los objetos. Cuando se desencadena el evento, estos objetos actualizan sus vistas de texto asociadas con la nueva configuración de la guía de columnas.

## <a name="invoke-command-from-the-command-window"></a>Invocar comando desde la ventana de comandos
El ejemplo de guías de columna permite a los usuarios invocar dos comandos desde la ventana de comandos como una forma de extensibilidad. Si utiliza el comando **Ver &#124; otra ventana de comandos de Windows &#124;,** puede ver la ventana de comandos. Puede interactuar con la ventana de comandos escribiendo "edit.", y con el nombre del comando completion y proporcionando el argumento 120, tiene el siguiente resultado:

```csharp
> Edit.AddColumnGuide 120
>
```

Las partes del ejemplo que habilitan este comportamiento se encuentran `ColumnGuideCommands` en las declaraciones de archivo *.vsct,* el constructor de clase cuando enlaza controladores de comandos y las implementaciones del controlador de comandos que comprueban los argumentos de evento.

Ha visto`<CommandFlag>CommandWellOnly</CommandFlag>`" " en el archivo *.vsct,* así como las ubicaciones en el menú principal **Editar** aunque los comandos no se muestran en la interfaz de usuario del menú **Editar.** Tenerlos en el menú **principal Editar** les da nombres como **Edit.AddColumnGuide**. La declaración del grupo de comandos que contiene los cuatro comandos colocó el grupo en el menú **Editar** directamente:

```xml
<Group guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup"
             priority="0xB801">
        <Parent guid="guidSHLMainMenu" id="IDM_VS_MENU_EDIT" />
      </Group>

```

La sección de botones más tarde declaró los comandos `CommandWellOnly` para mantenerlos invisibles en el menú principal y los declaró con: `AllowParams`

```xml
<Button guid="guidColumnGuidesCommandSet" id="cmdidAddColumnGuide"
        priority="0x0100" type="Button">
  <Parent guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup" />
  <Icon guid="guidImages" id="bmpPicAddGuide" />
  <CommandFlag>CommandWellOnly</CommandFlag>
  <CommandFlag>AllowParams</CommandFlag>

```

Ha visto el controlador de `ColumnGuideCommands` comandos enlazar código en el constructor de clase proporcionado una descripción del parámetro permitido:

```csharp
_addGuidelineCommand.ParametersDescription = "<column>";

```

Ha visto `GetApplicableColumn` la `OleMenuCmdEventArgs` función comprueba si hay un valor antes de comprobar la vista del editor para una columna actual:

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

## <a name="try-your-extension"></a>Pruebe su extensión
Ahora puede presionar **F5** para ejecutar la extensión Guías de columnas. Abra un archivo de texto y utilice el menú contextual del editor para agregar líneas guía, eliminarlas y cambiar su color. Haga clic en el texto (no en el espacio en blanco pasó el final de la línea) para agregar una guía de columna o el editor lo agrega a la última columna de la línea. Si utiliza la ventana de comandos e invoca los comandos con un argumento, puede agregar guías de columna en cualquier lugar.

Si desea probar diferentes ubicaciones de comandos, cambiar nombres, cambiar iconos, etc., y tiene algún problema con Visual Studio que muestra el código más reciente en los menús, puede restablecer el subárbol experimental en el que está depurando. Para abrir el menú Inicio de **Windows,** escriba "reset". Busque y ejecute el comando **Reset the Next Visual Studio Experimental Instance**. Este comando limpia el subárbol del registro experimental de todos los componentes de extensión. No limpia la configuración de los componentes, por lo que las guías que tenía al apagar el subárbol experimental de Visual Studio siguen ahí cuando el código lee el almacén de configuración en el próximo inicio.

## <a name="finished-code-project"></a>Proyecto de código terminado
Pronto habrá un proyecto de GitHub de ejemplos de extensibilidad de Visual Studio y el proyecto completado estará allí. Este artículo se actualizará para que apunte allí cuando eso suceda. El proyecto de ejemplo completado puede tener diferentes guids y tendrá una tira de mapas de bits diferente para los iconos de comando.

Puede probar una versión de la característica de guías de columna con esta[extensión](https://marketplace.visualstudio.com/items?itemName=PaulHarrington.EditorGuidelines)de Galería de Visual Studio.

## <a name="see-also"></a>Vea también
- [Dentro del editor](../extensibility/inside-the-editor.md)
- [Ampliar el editor y los servicios de idiomas](../extensibility/extending-the-editor-and-language-services.md)
- [Servicio de lenguaje y puntos de extensión del editor](../extensibility/language-service-and-editor-extension-points.md)
- [Extender menús y comandos](../extensibility/extending-menus-and-commands.md)
- [Añadir un submenú a un menú](../extensibility/adding-a-submenu-to-a-menu.md)
- [Crear una extensión con una plantilla de elemento de editor](../extensibility/creating-an-extension-with-an-editor-item-template.md)
