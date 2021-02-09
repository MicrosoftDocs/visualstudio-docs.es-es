---
title: Crear un elemento gráfico de vista, comandos y valores | Microsoft Docs
description: Obtenga información sobre cómo extender el editor de código de Visual Studio con guías de columna mediante este tutorial.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 4a2df0a3-42da-4f7b-996f-ee16a35ac922
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d9bf88212ccc6e00dfbca14912eb15e17d106a49
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99892455"
---
# <a name="walkthrough-create-a-view-adornment-commands-and-settings-column-guides"></a>Tutorial: crear un elemento gráfico de vista, comandos y configuración (guías de columnas)
Puede extender el editor de texto/código de Visual Studio con los comandos y los efectos de la vista. En este artículo se muestra cómo empezar a trabajar con una característica de extensión popular, guías de columnas. Las guías de columnas son líneas claras visualmente dibujadas en la vista del editor de texto para ayudarle a administrar el código en anchos de columna específicos. En concreto, el código con formato puede ser importante para los ejemplos que se incluyen en documentos, entradas de blog o informes de errores.

En este tutorial realizará lo siguiente:
- Crear un proyecto VSIX
- Agregar un elemento gráfico de la vista del editor
- Agregar compatibilidad para guardar y obtener la configuración (dónde dibujar las guías de columna y su color)
- Agregar comandos (agregar o quitar guías de columna, cambiar su color)
- Coloque los comandos en el menú edición y los menús contextuales del documento de texto.
- Agregar compatibilidad para invocar los comandos desde la ventana de comandos de Visual Studio

  Puede probar una versión de la característica guías de columnas con esta[extensión](https://marketplace.visualstudio.com/items?itemName=PaulHarrington.EditorGuidelines)de la galería de Visual Studio.

  > [!NOTE]
  > En este tutorial, se pega una gran cantidad de código en algunos archivos generados por plantillas de extensión de Visual Studio. Pero pronto este tutorial hará referencia a una solución completada en GitHub con otros ejemplos de extensión. El código completado es ligeramente diferente en que tiene iconos de comando reales en lugar de usar iconos de GenericTemplate.

## <a name="get-started"></a>Introducción
A partir de Visual Studio 2015, no se instala el SDK de Visual Studio desde el centro de descarga. Se incluye como una característica opcional en el programa de instalación de Visual Studio. También puede instalar el SDK de VS después. Para obtener más información, vea [instalar el SDK de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="set-up-the-solution"></a>Configuración de la solución
En primer lugar, cree un proyecto VSIX, agregue un elemento gráfico de la vista del editor y, a continuación, agregue un comando (que agrega un VSPackage para que sea el propietario del comando). La arquitectura básica es la siguiente:
- Tiene un agente de escucha de creación de vista de texto que crea un `ColumnGuideAdornment` objeto por vista. Este objeto escucha eventos sobre la vista que cambia o cambia de configuración, actualizando o redibujando las guías de columna según sea necesario.
- Hay un `GuidesSettingsManager` que controla la lectura y la escritura desde el almacenamiento de configuración de Visual Studio. El administrador de configuración también tiene operaciones para actualizar los valores de configuración que admiten los comandos de usuario (agregar columna, quitar columna, cambiar color).
- Hay un paquete VSIP que es necesario si tiene comandos de usuario, pero simplemente es código reutilizable que inicializa el objeto de implementación de comandos.
- Hay un `ColumnGuideCommands` objeto que ejecuta los comandos de usuario y enlaza los controladores de comandos para los comandos declarados en el archivo *. Vsct* .

  **VSIX**. Use el comando **archivo &#124; nuevo...** para crear un proyecto. Elija el nodo **extensibilidad** en **C#** en el panel de navegación izquierdo y elija **Proyecto VSIX** en el panel derecho. Escriba el nombre **ColumnGuides** y elija **Aceptar** para crear el proyecto.

  **Muestra el elemento gráfico**. Presione el botón derecho del mouse en el nodo del proyecto en el Explorador de soluciones. Elija el comando **agregar &#124; nuevo elemento...** para agregar un nuevo elemento de gráfico de vista. Elija **extensibilidad &#124; editor** en el panel de navegación izquierdo y elija **elemento gráfico** de la ventanilla del editor en el panel derecho. Escriba el nombre **ColumnGuideAdornment** como el nombre del elemento y elija **Agregar** para agregarlo.

  Puede ver que esta plantilla de elemento agrega dos archivos al proyecto (así como referencias, etc.): **ColumnGuideAdornment.CS** y **ColumnGuideAdornmentTextViewCreationListener.CS**. Las plantillas dibujan un rectángulo púrpura en la vista. En la sección siguiente, cambiará un par de líneas en el agente de escucha de creación de vistas y reemplazará el contenido de **ColumnGuideAdornment.CS**.

  **Comandos**. En **Explorador de soluciones**, presione el botón derecho del mouse en el nodo del proyecto. Elija el comando **agregar &#124; nuevo elemento...** para agregar un nuevo elemento de gráfico de vista. Elija **extensibilidad &#124; VSPackage** en el panel de navegación izquierdo y elija **comando personalizado** en el panel derecho. Escriba el nombre **ColumnGuideCommands** como el nombre del elemento y elija **Agregar**. Además de varias referencias, agregar los comandos y el paquete también agregó **ColumnGuideCommands.CS**, **ColumnGuideCommandsPackage.CS** y **ColumnGuideCommandsPackage. Vsct**. En la siguiente sección, reemplazará el contenido de los archivos primero y último para definir e implementar los comandos.

## <a name="set-up-the-text-view-creation-listener"></a>Configuración del agente de escucha de creación de la vista de texto
Abra *ColumnGuideAdornmentTextViewCreationListener.CS* en el editor. Este código implementa un controlador para cada vez que Visual Studio crea vistas de texto. Hay atributos que controlan Cuándo se llama al controlador en función de las características de la vista.

El código también debe declarar una capa de elemento gráfico. Cuando el editor actualiza las vistas, obtiene las capas de elemento gráfico de la vista y de que obtiene los elementos de elemento gráfico. Puede declarar el orden de la capa en relación con otros con atributos. Reemplace la línea siguiente:

```csharp
[Order(After = PredefinedAdornmentLayers.Caret)]
```

con estas dos líneas:

```csharp
[Order(Before = PredefinedAdornmentLayers.Text)]
[TextViewRole(PredefinedTextViewRoles.Document)]
```

La línea que ha reemplazado se encuentra en un grupo de atributos que declaran una capa de elemento gráfico. La primera línea que cambió solo cambia cuando aparecen las líneas de la guía de columnas. Al dibujar las líneas "antes", el texto de la vista significa que aparecen detrás o debajo del texto. La segunda línea declara que los elementos gráficos de la guía de columna se aplican a las entidades de texto que se ajustan a la noción de un documento, pero podría declarar el elemento gráfico, por ejemplo, para que solo funcione para texto modificable. Hay más información en los [puntos de extensión del servicio de lenguaje y del editor](../extensibility/language-service-and-editor-extension-points.md)

## <a name="implement-the-settings-manager"></a>Implementación del administrador de configuración
Reemplace el contenido de *GuidesSettingsManager.CS* por el código siguiente (que se explica a continuación):

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

La mayor parte de este código crea y analiza el formato de configuración: "RGB ( \<int> , \<int> , \<int> ) \<int> , \<int> ,...".  Los enteros del final son las columnas basadas en uno donde desea guías de columna. La extensión de guías de columna captura toda su configuración en una sola cadena de valor de configuración.

Hay algunas partes del código que merece la pena resaltar. La siguiente línea de código obtiene el contenedor administrado de Visual Studio para el almacenamiento de configuración. En su mayor parte, esto abstrae sobre el registro de Windows, pero esta API es independiente del mecanismo de almacenamiento.

```csharp
internal static SettingsManager VsManagedSettingsManager =
    new ShellSettingsManager(ServiceProvider.GlobalProvider);
```

El almacenamiento de configuración de Visual Studio usa un identificador de categoría y un identificador de configuración para identificar de forma exclusiva todas las opciones de configuración:

```csharp
private const string _collectionSettingsName = "Text Editor";
private const string _settingName = "Guides";
```

No tiene que usar `"Text Editor"` como nombre de categoría. Puede elegir cualquier cosa que desee.

Las primeras funciones son los puntos de entrada para cambiar la configuración. Comprueban las restricciones de alto nivel como el número máximo de guías permitidas.  A continuación, llaman a `WriteSettings` , que compone una cadena de configuración y establece la propiedad `GuideLinesConfiguration` . Al establecer esta propiedad, se guarda el valor de configuración en el almacén de configuración de Visual Studio y se desencadena el `SettingsChanged` evento para actualizar todos los `ColumnGuideAdornment` objetos, cada uno asociado a una vista de texto.

Hay un par de funciones de punto de entrada, como `CanAddGuideline` , que se usan para implementar comandos que cambian la configuración. Cuando Visual Studio muestra menús, consulta las implementaciones de comandos para ver si el comando está habilitado actualmente, cuál es su nombre, etc.  A continuación, verá cómo enlazar estos puntos de entrada para las implementaciones de comandos. Para obtener más información sobre los comandos, vea [extender menús y comandos](../extensibility/extending-menus-and-commands.md).

## <a name="implement-the-columnguideadornment-class"></a>Implementación de la clase ColumnGuideAdornment
`ColumnGuideAdornment`Se crea una instancia de la clase para cada vista de texto que puede tener elementos gráficos. Esta clase realiza escuchas para los eventos sobre el cambio de la vista o el cambio de configuración, y las guías de columna actualizar o volver a dibujar según sea necesario.

Reemplace el contenido de *ColumnGuideAdornment.CS* por el código siguiente (que se explica a continuación):

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

Las instancias de esta clase guardan en el asociado <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView> y una lista de `Line` objetos dibujados en la vista.

El constructor (al que se llama `ColumnGuideAdornmentTextViewCreationListener` cuando Visual Studio crea nuevas vistas) crea los objetos de guía de columna `Line` .  El constructor también agrega controladores para el `SettingsChanged` evento (definido en `GuidesSettingsManager` ) y los eventos de vista `LayoutChanged` y `Closed` .

El `LayoutChanged` evento se desencadena debido a varios tipos de cambios en la vista, incluso cuando Visual Studio crea la vista. El `OnViewLayoutChanged` controlador llama `AddGuidelinesToAdornmentLayer` a para ejecutar. El código de `OnViewLayoutChanged` determina si tiene que actualizar las posiciones de línea en función de los cambios, como los cambios de tamaño de fuente, los márgenes de visualización, el desplazamiento horizontal, etc. El código de `UpdatePositions` hace que las líneas guía se dibujen entre caracteres o justo después de la columna de texto que está en el desplazamiento de caracteres especificado en la línea de texto.

Siempre que la configuración cambie la `SettingsChanged` función, se vuelve a crear todos los `Line` objetos con cualquier valor que sea la nueva configuración. Después de establecer las posiciones de línea, el código quita todos los `Line` objetos anteriores de la capa de elementos `ColumnGuideAdornment` gráficos y agrega los nuevos.

## <a name="define-the-commands-menus-and-menu-placements"></a>Definir los comandos, menús y ubicaciones de menús
Puede haber mucho que declarar comandos y menús, colocar grupos de comandos o menús en otros menús y enlazar controladores de comandos. En este tutorial se resalta cómo funcionan los comandos en esta extensión, pero para obtener información más detallada, vea [extender menús y comandos](../extensibility/extending-menus-and-commands.md).

### <a name="introduction-to-the-code"></a>Introducción al código
La extensión de guías de columnas muestra cómo declarar un grupo de comandos que pertenecen a la vez (agregar columna, quitar columna, cambiar color de línea) y, a continuación, colocar ese grupo en un submenú del menú contextual del editor.  La extensión de guías de columnas también agrega los comandos al menú **edición** principal pero los mantiene invisibles, que se describen a continuación como un patrón común.

Hay tres partes en la implementación de comandos: ColumnGuideCommandsPackage.cs, ColumnGuideCommandsPackage. Vsct y ColumnGuideCommands.cs. El código generado por las plantillas coloca un comando en el menú **herramientas** que abre un cuadro de diálogo como implementación. Puede ver cómo se implementa en los archivos *. Vsct* y *ColumnGuideCommands.CS* , ya que es sencillo. Reemplace el código de estos archivos a continuación.

El código de paquete contiene declaraciones reutilizables requeridas para que Visual Studio detecte que la extensión ofrece comandos y para buscar dónde se colocan los comandos. Cuando se inicializa el paquete, crea una instancia de la clase de implementación de comandos. Para obtener más información sobre los paquetes relacionados con los comandos, vea [extender menús y comandos](../extensibility/extending-menus-and-commands.md).

### <a name="a-common-commands-pattern"></a>Patrón de comandos comunes
Los comandos de la extensión de las guías de columnas son un ejemplo de un patrón muy común en Visual Studio. Los comandos relacionados se colocan en un grupo y el grupo se coloca en un menú principal, a menudo con " `<CommandFlag>CommandWellOnly</CommandFlag>` " establecido para que el comando sea invisible.  Al colocar comandos en los menús principales (como **Editar**), se les da un nombre agradable (como **Edit. AddColumnGuide**), que resultan útiles para buscar comandos al volver a asignar enlaces de teclado en **Opciones de herramientas**. También es útil para obtener la finalización al invocar comandos desde la **ventana de comandos**.

A continuación, agregue el grupo de comandos a los menús contextuales o submenús donde espera que el usuario Use los comandos. Visual Studio trata `CommandWellOnly` como una marca de invisibilidad solo para los menús principales. Cuando se coloca el mismo grupo de comandos en un menú contextual o en un submenú, los comandos están visibles.

Como parte del patrón común, la extensión de las guías de columna crea un segundo grupo que contiene un solo submenú. El submenú a su vez contiene el primer grupo con los comandos de la guía de cuatro columnas. El segundo grupo que contiene el submenú es el activo reutilizable que se coloca en varios menús contextuales, que coloca un submenú en esos menús contextuales.

### <a name="the-vsct-file"></a>El archivo. Vsct
El archivo *. Vsct* declara los comandos y dónde van, junto con los iconos, etc. Reemplace el contenido del archivo *. Vsct* por el código siguiente (que se explica a continuación):

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

**GUID**. Para que Visual Studio encuentre los controladores de comandos e invocarlos, debe asegurarse de que el GUID del paquete declarado en el archivo *ColumnGuideCommandsPackage.CS* (generado a partir de la plantilla de elemento de proyecto) coincide con el GUID del paquete declarado en el archivo *. Vsct* (copiado desde arriba). Si vuelve a usar este código de ejemplo, debe asegurarse de que tiene un GUID diferente para que no entre en conflicto con nadie que pueda haber copiado este código.

Busque esta línea en *ColumnGuideCommandsPackage.CS* y copie el GUID entre comillas:

```csharp
public const string PackageGuidString = "ef726849-5447-4f73-8de5-01b9e930f7cd";
```

A continuación, pegue el GUID en el archivo *. Vsct* para que tenga la siguiente línea en las `Symbols` declaraciones:

```xml
<GuidSymbol name="guidColumnGuideCommandsPkg"
            value="{ef726849-5447-4f73-8de5-01b9e930f7cd}" />
```

Los GUID para el conjunto de comandos y el archivo de imagen de mapa de bits deben ser únicos para las extensiones:

```xml
<GuidSymbol name="guidColumnGuidesCommandSet"
            value="{c2bc0047-8bfa-4e5a-b5dc-45af8c274d8e}">
<GuidSymbol name="guidImages" value="{2C99F852-587C-43AF-AA2D-F605DE2E46EF}">
```

Sin embargo, no es necesario cambiar el conjunto de comandos y los GUID de imagen de mapa de bits en este tutorial para que el código funcione. El GUID del conjunto de comandos debe coincidir con la declaración del archivo *ColumnGuideCommands.CS* , pero también puede reemplazar el contenido de ese archivo; por lo tanto, los GUID coincidirán.

Otros GUID del archivo *. Vsct* identifican los menús previamente existentes a los que se agregan los comandos de la guía de columna, por lo que nunca cambian.

**Secciones de archivo**. El *. Vsct* tiene tres secciones exteriores: comandos, ubicaciones y símbolos. La sección comandos define grupos de comandos, menús, botones o elementos de menú, y mapas de bits para iconos. La sección de ubicaciones declara dónde se ubican los grupos en los menús o ubicaciones adicionales en los menús ya existentes. En la sección Symbols se declaran los identificadores que se usan en cualquier parte del archivo *. Vsct* , lo que hace que el código *. Vsct* sea más legible que tener GUID y números hexadecimales en todas partes.

**Sección de comandos, definiciones de grupos**. En primer lugar, la sección Commands define grupos de comandos. Los grupos de comandos son comandos que aparecen en los menús con líneas grises pequeñas que separan los grupos. Un grupo también puede rellenar todo un submenú, como en este ejemplo, y no ve las líneas de separación de grises en este caso. Los archivos *. Vsct* declaran dos grupos, el elemento primario del elemento `GuidesMenuItemsGroup` `IDM_VS_MENU_EDIT` (el menú de **edición** principal) y el elemento primario del elemento `GuidesContextMenuGroup` `IDM_VS_CTXT_CODEWIN` (el menú contextual del editor de código).

La segunda declaración de grupo tiene una `0x0600` prioridad:

```xml
<Group guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup"
             priority="0x0600">
```

La idea es colocar el submenú guías de columnas al final de cualquier menú contextual al que agregue el grupo de submenú. Sin embargo, no debe preocuparse mejor y forzar que el submenú siempre sea el último mediante el uso de una prioridad de `0xFFFF` . Tiene que experimentar con el número para ver dónde se encuentra el submenú en los menús contextuales donde se coloca. En este caso, `0x0600` es lo suficientemente alto como para colocarlo al final de los menús en la medida de lo que se puede ver, pero deja espacio para que otra persona diseñe su extensión para que sea menor que la extensión de las guías de columna si es deseable.

**Sección de comandos, definición de menú**. A continuación, la sección de comandos define el submenú `GuidesSubMenu` , primario y secundario `GuidesContextMenuGroup` . `GuidesContextMenuGroup`Es el grupo que se agrega a todos los menús contextuales pertinentes. En la sección de ubicaciones, el código coloca el grupo con los comandos de la guía de cuatro columnas en este submenú.

**Sección de comandos, definiciones de botones**. A continuación, la sección comandos define los elementos de menú o botones que son los comandos de las guías de cuatro columnas. `CommandWellOnly`, descrito anteriormente, significa que los comandos son invisibles cuando se colocan en un menú principal. Dos de las declaraciones de botón del elemento de menú (agregar guía y quitar guía) también tienen una `AllowParams` marca:

```xml
<CommandFlag>AllowParams</CommandFlag>
```

Esta marca habilita, junto con los lugares del menú principal, el comando para recibir argumentos cuando Visual Studio invoca el controlador de comandos.  Si el usuario ejecuta el comando desde la ventana comandos, el argumento se pasa al controlador de comandos en los argumentos del evento.

**Secciones de comandos, definiciones de mapas de bits**. Por último, la sección de comandos declara los mapas de bits o los iconos que se usan para los comandos. Esta sección es una declaración simple que identifica el recurso del proyecto y muestra los índices basados en uno de los iconos usados. La sección Symbols del archivo *. Vsct* declara los valores de los identificadores utilizados como índices. En este tutorial se usa la franja de mapa de bits que se proporciona con la plantilla de elemento de comando personalizada agregada al proyecto.

**Sección de ubicaciones**. Una vez que la sección de comandos es la sección de ubicaciones. El primero es donde el código agrega el primer grupo descrito anteriormente que contiene los comandos de la guía de cuatro columnas al submenú en el que aparecen los comandos:

```xml
<CommandPlacement guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup"
                  priority="0x0100">
  <Parent guid="guidColumnGuidesCommandSet" id="GuidesSubMenu" />
</CommandPlacement>
```

Todas las demás ubicaciones agregan `GuidesContextMenuGroup` (que contiene `GuidesSubMenu` ) a otros menús contextuales del editor. Cuando el código declara `GuidesContextMenuGroup` , era el elemento primario del menú contextual del editor de código. Esta es la razón por la que no ve una ubicación para el menú contextual del editor de código.

**Sección de símbolos**. Como se indicó anteriormente, la sección de símbolos declara los identificadores que se usan en otro lugar del archivo *. Vsct* , lo que hace que el código *. Vsct* sea más legible que los GUID y los números hexadecimales en todas partes. Los puntos importantes de esta sección son que el GUID del paquete debe coincidir con la declaración de la clase de paquete. Y el GUID del conjunto de comandos debe estar de acuerdo con la declaración en la clase de implementación de comandos.

## <a name="implement-the-commands"></a>Implementar los comandos
El archivo *ColumnGuideCommands.CS* implementa los comandos y enlaza los controladores. Cuando Visual Studio carga el paquete y lo inicializa, el paquete a su vez llama a `Initialize` en la clase de implementación de comandos. La inicialización de los comandos simplemente crea instancias de la clase y el constructor enlaza todos los controladores de comandos.

Reemplace el contenido del archivo *ColumnGuideCommands.CS* por el código siguiente (que se explica a continuación):

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

**Corrija las referencias**. Falta una referencia en este momento. Presione el botón derecho del puntero en el nodo referencias en el Explorador de soluciones. Elija el comando **Agregar...** . El cuadro de diálogo **Agregar referencia** tiene un cuadro de búsqueda en la esquina superior derecha. Escriba "Editor" (sin las comillas dobles). Elija el elemento **Microsoft. VisualStudio. Editor** (debe activar la casilla situada a la izquierda del elemento, no solo Seleccione el elemento) y elija **Aceptar** para agregar la referencia.

**Inicialización**.  Cuando se inicializa la clase de paquete, llama a `Initialize` en la clase de implementación de comandos. La `ColumnGuideCommands` inicialización crea una instancia de la clase y guarda la instancia de clase y la referencia de paquete en los miembros de clase.

Echemos un vistazo a uno de los enlaces del controlador de comandos del constructor de clase:

```csharp
_addGuidelineCommand =
    new OleMenuCommand(AddColumnGuideExecuted, null,
                       AddColumnGuideBeforeQueryStatus,
                       new CommandID(ColumnGuideCommands.CommandSet,
                                     cmdidAddColumnGuide));

```

Cree un `OleMenuCommand` . Visual Studio usa el sistema de comandos de Microsoft Office. Los argumentos clave al crear instancias de `OleMenuCommand` es la función que implementa el comando ( `AddColumnGuideExecuted` ), la función a la que se llama cuando Visual Studio muestra un menú con el comando ( `AddColumnGuideBeforeQueryStatus` ) y el identificador de comando. Visual Studio llama a la función de estado de la consulta antes de mostrar un comando en un menú para que el comando pueda hacerse a sí mismo invisible o atenuado para una presentación determinada del menú (por ejemplo, deshabilitar la **copia** si no hay ninguna selección), cambiar su icono o incluso cambiar su nombre (por ejemplo, de agregar algo para quitar algo), etc. El identificador de comando debe coincidir con un identificador de comando declarado en el archivo *. Vsct* . Las cadenas para el conjunto de comandos y el comando Add de las guías de columna deben coincidir entre el archivo *. Vsct* y el *ColumnGuideCommands.CS*.

La línea siguiente proporciona ayuda para cuando los usuarios invocan el comando a través de la ventana de comandos (que se explica a continuación):

```csharp
_addGuidelineCommand.ParametersDescription = "<column>";
```

 **Estado** de la consulta. El estado de la consulta funciona `AddColumnGuideBeforeQueryStatus` y `RemoveColumnGuideBeforeQueryStatus` comprueba algunos valores (como el número máximo de guías o la columna Max) o si hay una guía de columna para quitar. Habilitan los comandos si las condiciones son correctas.  Las funciones de estado de consulta deben ser eficaces porque se ejecutan cada vez que Visual Studio muestra un menú y para cada comando en el menú.

 **Función AddColumnGuideExecuted**. La parte interesante de la adición de una guía es la visualización de la vista del editor actual y la ubicación del símbolo de intercalación.  En primer lugar, esta función llama a `GetApplicableColumn` , que comprueba si hay un argumento proporcionado por el usuario en los argumentos de evento del controlador de comandos y, si no hay ninguno, la función comprueba la vista del editor:

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

`GetCurrentEditorColumn` tiene que profundizar un poco para obtener una <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView> vista del código.  Si realiza el seguimiento a través `GetActiveTextView` de, `GetActiveView` y `GetTextViewFromVsTextView` , puede ver cómo hacerlo. El código siguiente es el código relevante que se abstrae, empezando por la selección actual, obteniendo el fotograma de la selección y, a continuación, obteniendo el DocView del fotograma como <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> y, a continuación, obteniendo un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData> de IVsTextView, luego obteniendo un host de vista y finalmente IWpfTextView:

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

Con la columna actual en la que el usuario hizo clic, el código simplemente llama a en el administrador de configuración para agregar o quitar la columna. El administrador de configuración activa el evento al que todos los `ColumnGuideAdornment` objetos escuchan. Cuando el evento se activa, estos objetos actualizan sus vistas de texto asociadas con la nueva configuración de la guía de columnas.

## <a name="invoke-command-from-the-command-window"></a>Comando Invoke desde la ventana comandos
El ejemplo de guías de columnas permite que los usuarios invoquen dos comandos desde la ventana de comandos como una forma de extensibilidad. Si usa el comando **ver &#124; otro** comando de la ventana de comandos de Windows &#124;, puede ver la ventana comandos. Para interactuar con la ventana de comandos, escriba "Edit." y, con el nombre de comando completado y proporcione el argumento 120, tiene el siguiente resultado:

```csharp
> Edit.AddColumnGuide 120
>
```

Las partes del ejemplo que habilitan este comportamiento se encuentran en las declaraciones del archivo *. Vsct* , el `ColumnGuideCommands` constructor de clase cuando enlaza los controladores de comandos y las implementaciones del controlador de comandos que comprueban los argumentos de evento.

Vio " `<CommandFlag>CommandWellOnly</CommandFlag>` " en el archivo *. Vsct* así como los lugares en el menú principal de **edición** aunque los comandos no se muestren en la interfaz de usuario del menú de **edición** . Tenerlos en el menú principal de **edición** les dará nombres como **Edit. AddColumnGuide**. La declaración del grupo de comandos que contiene los cuatro comandos colocó el grupo en el menú **edición** directamente:

```xml
<Group guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup"
             priority="0xB801">
        <Parent guid="guidSHLMainMenu" id="IDM_VS_MENU_EDIT" />
      </Group>

```

Posteriormente, la sección botones declaró los comandos `CommandWellOnly` para mantenerlos invisibles en el menú principal y declararlos con `AllowParams` :

```xml
<Button guid="guidColumnGuidesCommandSet" id="cmdidAddColumnGuide"
        priority="0x0100" type="Button">
  <Parent guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup" />
  <Icon guid="guidImages" id="bmpPicAddGuide" />
  <CommandFlag>CommandWellOnly</CommandFlag>
  <CommandFlag>AllowParams</CommandFlag>

```

Vio el código de enlace del controlador de comandos en el `ColumnGuideCommands` constructor de clase proporcionó una descripción del parámetro permitido:

```csharp
_addGuidelineCommand.ParametersDescription = "<column>";

```

Vio la `GetApplicableColumn` función comprueba `OleMenuCmdEventArgs` un valor antes de comprobar la vista del editor para una columna actual:

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
Ahora puede presionar **F5** para ejecutar la extensión de las guías de columnas. Abra un archivo de texto y use el menú contextual del editor para agregar líneas guía, quitarlas y cambiar su color. Haga clic en el texto (no en el espacio en blanco que ha pasado el final de la línea) para agregar una guía de columna o el editor lo agrega a la última columna de la línea. Si usa la ventana comandos e invoca los comandos con un argumento, puede Agregar guías de columna en cualquier lugar.

Si desea probar diferentes ubicaciones de comandos, cambiar nombres, cambiar iconos, etc., y tiene problemas con Visual Studio que le muestran el código más reciente en los menús, puede restablecer el subárbol experimental en el que está depurando. Abra el **menú Inicio de Windows** y escriba "restablecer". Busque y ejecute el comando y **restablezca la siguiente instancia experimental de Visual Studio**. Este comando limpia el subárbol del registro experimental de todos los componentes de la extensión. No limpia la configuración de los componentes, por lo que las guías que tenía al cerrar el subárbol experimental de Visual Studio siguen estando allí cuando el código lee el almacén de configuración en el siguiente inicio.

## <a name="finished-code-project"></a>Proyecto de código finalizado
Pronto habrá un proyecto de GitHub de ejemplos de extensibilidad de Visual Studio y el proyecto completado estará ahí. Este artículo se actualizará para apuntar allí cuando suceda. El proyecto de ejemplo completado puede tener GUID diferentes y tendrá una franja de mapas de bits diferente para los iconos de comandos.

Puede probar una versión de la característica guías de columnas con esta[extensión](https://marketplace.visualstudio.com/items?itemName=PaulHarrington.EditorGuidelines)de la galería de Visual Studio.

## <a name="see-also"></a>Vea también
- [Dentro del editor](../extensibility/inside-the-editor.md)
- [Extender el editor y los servicios de lenguaje](../extensibility/extending-the-editor-and-language-services.md)
- [Puntos de extensión de editor y servicio de lenguaje](../extensibility/language-service-and-editor-extension-points.md)
- [Extender menús y comandos](../extensibility/extending-menus-and-commands.md)
- [Agregar un submenú a un menú](../extensibility/adding-a-submenu-to-a-menu.md)
- [Crear una extensión con una plantilla de elemento de editor](../extensibility/creating-an-extension-with-an-editor-item-template.md)
