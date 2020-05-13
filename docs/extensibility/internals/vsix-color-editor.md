---
title: Editor de colores VSIX (VSIX Color Editor) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 70879c5d-e0f0-4845-993c-2f4229869706
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: aa3ed1f1a2a761a6602ac891eb78b5a5436abf92
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704044"
---
# <a name="vsix-color-editor"></a>Editor de colores de VSIX
La herramienta Editor de colores de extensión de Visual Studio puede crear y editar colores personalizados para Visual Studio. La herramienta también puede generar claves de recursos de tema para que los colores se puedan utilizar en el código. Esta herramienta es útil para crear colores para una extensión de Visual Studio que admite la creación de temas. Esta herramienta puede abrir archivos .pkgdef y .xml. Los temas de Visual Studio (archivos .vstheme) se pueden usar con el Editor de color es un archivo de extensión de Visual Studio cambiando la extensión de archivo a .xml. Además, los archivos .vstheme se pueden importar a un archivo .xml actual.

 ![Imagen prominente del editor de colores de VSIX](../../extensibility/internals/media/vsix-color-editor-hero.png "Imagen prominente del editor de colores de VSIX")

 **Archivos de definición del paquete**

 Los archivos de definición de paquetes (.pkgdef) son los archivos que definen temas. Los colores en sí se almacenan en archivos .xml de color de tema, que se compilan en un archivo .pkgdef. Los archivos .pkgdef se implementan en ubicaciones de búsqueda de Visual Studio, se procesan en tiempo de ejecución y se combinan para definir temas.

 **Fichas de color**

 Un token de color se compone de cuatro elementos:

- **Nombre de la categoría:** Agrupación lógica para un conjunto de colores. Use un nombre de categoría existente si ya hay colores que son específicos del elemento de interfaz de usuario deseado o un grupo de elementos de interfaz de usuario.

- **Nombre del token:** Un nombre descriptivo para el token de color y los conjuntos de tokens. Los conjuntos incluyen nombres de token de fondo y de primer plano (texto), así como todos sus estados, y estos deben tener un nombre para que sea fácil identificar los pares y los estados a los que se aplican.

- **Valores de color (o tonos):** Necesario para cada tema de color. Cree siempre valores de color de fondo y texto en pares. Los colores se emparejan para el fondo/primer plano para que el color del texto (en primer plano) siempre sea legible con respecto al color de fondo en el que se dibuja. Estos colores están vinculados y se usarán juntos en la interfaz de usuario. Si el fondo no está pensado para su uso con texto, no defina un color de primer plano.

- **Nombre del color del sistema:** Para su uso en pantallas de alto contraste.

## <a name="how-to-use-the-tool"></a>Cómo utilizar la herramienta
 En la medida de lo posible y, en su caso, los colores existentes de Visual Studio deben reutilizarse en lugar de crear otros nuevos. Sin embargo, para los casos en los que no se definen colores adecuados, se deben crear colores personalizados para mantener una temática de extensión compatible.

 **Creación de nuevas fichas de color**

 Para crear colores personalizados mediante el Editor de colores de extensión de Visual Studio, siga estos pasos:

1. Determine la categoría y los nombres de token para los nuevos tokens de color.

2. Elija los tonos que utilizará el elemento de interfaz de usuario para cada tema y el color del sistema para Contraste alto.

3. Utilice el editor de color para crear nuevos tokens de color.

4. Use los colores de una extensión de Visual Studio.

5. Pruebe los cambios en Visual Studio.

   **Paso 1: Determine la categoría y los nombres de token para los nuevos tokens de color.**

   El esquema de nomenclatura preferido para un VSColor es **[Categoría] [Tipo de interfaz de usuario] [Estado]**. No utilice la palabra "color" en los nombres vscolor, ya que es redundante.

   Los nombres de categoría proporcionan agrupaciones lógicas y deben definirse de la forma más estrecha posible. Por ejemplo, el nombre de una sola ventana de herramientas podría ser un nombre de categoría, pero el nombre de toda una unidad de negocio o equipo de proyecto no lo es. Agrupar las entradas en categorías ayuda a evitar confusiones entre colores con el mismo nombre.

   Un nombre de token debe indicar claramente el tipo de elemento y las situaciones, o "estado", para las que se aplicará el color. Por ejemplo, el **[tipo de interfaz** de usuario] de una sugerencia de datos activa podría denominarse "**DataTip**" y el **[State]** podría llamarse "**Active**," dando como resultado un nombre de color de "**DataTipActive**." Dado que las sugerencias de datos tienen texto, es necesario definir un color de primer plano y un color de fondo. Mediante el uso de un emparejamiento de fondo/primer plano, el editor de color creará automáticamente los colores "**DataTipActive**" para el fondo y "**DataTipActiveText**" para el primer plano.

   Si la parte de la interfaz de usuario solo tiene un estado, se puede omitir la parte **[State]** del nombre. Por ejemplo, si un cuadro de búsqueda tiene un borde y no hay ningún cambio de estado que afecte al color del borde, el nombre del token de color del borde simplemente se puede llamar "**SearchBoxBorder**."

   Algunos nombres de estado comunes incluyen:

- Active

- Inactivo

- MouseOver

- Mousedown

- Seleccionado

- Con foco

  Ejemplos de algunos nombres de token para partes de un control de elemento de lista:

- ListItem

- ListItemBorder

- ListItemMouseOver

- ListItemMouseOverBorder

- ListItemSelected

- ListItemSelectedBorder

- ListItemDisabled

- ListItemDisabledBorder

  **Paso 2: Elija los tonos que el elemento de interfaz de usuario usará para cada tema y el color del sistema para contraste alto.**

  Al elegir colores personalizados para la interfaz de usuario, seleccione un elemento de interfaz de usuario existente similar y use sus colores como base. Los colores de los elementos de interfaz de usuario in-the-box se han revisado y realizado pruebas, por lo que se verán apropiados y se comportarán correctamente en todos los temas.

  **Paso 3: Utilice el editor de color para crear nuevos tokens de color.**

  Inicie el editor de color y abra o cree un nuevo archivo .xml de colores de tema personalizados. Seleccione **Editar > Nuevo color** en el menú. Esto abre un cuadro de diálogo para especificar la categoría y uno o más nombres para las entradas de color dentro de esa categoría:

  ![Aplicación del Editor color de VSIX](../../extensibility/internals/media/vsix-color-editor-new-color.png "Aplicación del Editor color de VSIX")

  Seleccione una categoría existente o seleccione **Nueva categoría** para crear una nueva categoría. Se abrirá otro cuadro de diálogo, creando un nuevo nombre de categoría:

  ![Nueva categoría del Editor color de VSIX](../../extensibility/internals/media/vsix-color-editor-new-category.png "Nueva categoría del Editor color de VSIX")

  La nueva categoría estará disponible en el menú desplegable **Categoría de nuevo color.** Después de elegir una categoría, escriba un nombre por línea para cada nuevo token de color y seleccione "Crear" cuando haya terminado:

  ![Nuevo color rellenado en el Editor de colores de VSIX](../../extensibility/internals/media/vsix-color-editor-new-color-filled.png "Nuevo color rellenado en el Editor de colores de VSIX")

  Los valores de color se muestran en pares de fondo/primer plano, con "Ninguno" que indica que el color no se ha definido. Nota: si un color no tiene un par de color de texto/color de fondo, solo es necesario definir el fondo.

  ![Valores de color del editor de colores de VSIX](../../extensibility/internals/media/vsix-color-editor-color-values.png "Valores de color del editor de colores de VSIX")

  Para editar un token de color, seleccione una entrada de color para el tema (columna) de ese token. Agregue el valor de color escribiendo un valor de color hexadecimal en formato ARGB de 8 dígitos, introduciendo un nombre de color del sistema en la celda o utilizando el menú desplegable para seleccionar el color deseado a través de un conjunto de controles deslizantes de color o una lista de colores del sistema.

  ![Color de edición del editor de colores de VSIX](../../extensibility/internals/media/vsix-color-editor-edit-color.png "Color de edición del editor de colores de VSIX")

  ![Fondo del Editor de color de VSIX](../../extensibility/internals/media/vsix-color-editor-background.png "Fondo del Editor de color de VSIX")

  Para los componentes que no necesitan mostrar texto, introduzca solo un valor de color: el color de fondo. De lo contrario, introduzca valores para el fondo y el color del texto, separados por una barra diagonal.

  Al introducir valores para Contraste alto, escriba nombres de color válidos del sistema de Windows. No introduzca valores ARGB codificados de forma rígida. Puede ver una lista de nombres de color es válidos del sistema seleccionando "Fondo: Sistema" o "Primer plano: Sistema" en los menús desplegables de valores de color. Al crear elementos que tienen componentes de texto, utilice el par de colores correcto del sistema de fondo/texto o el texto podría ser ilegible.

  Cuando termine de crear, configurar y editar los tokens de color, guárdelos en el formato .xml o .pkgdef deseado. Los tokens de color sin fondo ni conjunto de primer plano se guardarán como colores vacíos en formato .xml, pero se descartarán en formato .pkgdef. Un cuadro de diálogo le advertirá de la posible pérdida de color si intenta guardar colores vacíos en un archivo .pkgdef.

  **Paso 4: Use los colores en una extensión de Visual Studio.**

  Después de definir los nuevos tokens de color, incluya el archivo .pkgdef en el archivo de proyecto con "Build Action" establecido en "Content" e "Include in VSIX" establecido en "True."

  ![pkgdef del editor de colores de VSIX](../../extensibility/internals/media/vsix-color-editor-pkgdef.png "pkgdef del editor de colores de VSIX")

  En el Editor de colores de extensión de Visual Studio, elija > archivo Ver código de recursos para ver el código que se usa para tener acceso a los colores personalizados en la interfaz de usuario basada en WPF.

  ![Visor de código de recurso del editor de colores de VSIX](../../extensibility/internals/media/vsix-color-editor-resource-code-viewer.png "Visor de código de recurso del editor de colores de VSIX")

  Incluya este código en una clase estática en el proyecto. Una referencia a **Microsoft.VisualStudio.Shell.\< VSVersion>.0.dll** debe agregarse al proyecto para usar el tipo **ThemeResourceKey.**

```csharp
namespace MyCustomColors
{
    public static class MyCategory
    {
        #region Autogenerated resource keys
        // These resource keys are generated by Visual Studio Extension Color Editor, and should be replaced when new colors are added to this category.
        public static readonly Guid Category = new Guid("faf7f3f9-9fe5-4dd3-9350-59679617dfbe");

        private static ThemeResourceKey _MyColor1ColorKey;
        private static ThemeResourceKey _MyColor1BrushKey;
        private static ThemeResourceKey _MyColor1TextColorKey;
        private static ThemeResourceKey _MyColor1TextBrushKey;
        public static ThemeResourceKey MyColor1ColorKey { get { return _MyColor1ColorKey ?? (_MyColor1ColorKey = new ThemeResourceKey(Category, "MyColor1", ThemeResourceKeyType.BackgroundColor)); } }
        public static ThemeResourceKey MyColor1BrushKey { get { return _MyColor1BrushKey ?? (_MyColor1BrushKey = new ThemeResourceKey(Category, "MyColor1", ThemeResourceKeyType.BackgroundBrush)); } }
        public static ThemeResourceKey MyColor1TextColorKey { get { return _MyColor1TextColorKey ?? (_MyColor1TextColorKey = new ThemeResourceKey(Category, "MyColor1", ThemeResourceKeyType.ForegroundColor)); } }
        public static ThemeResourceKey MyColor1TextBrushKey { get { return _MyColor1TextBrushKey ?? (_MyColor1TextBrushKey = new ThemeResourceKey(Category, "MyColor1", ThemeResourceKeyType.ForegroundBrush)); } }
        #endregion
    }
}
```

 Esto permite el acceso a los colores en el código XAML y permite que la interfaz de usuario responda a los cambios de tema.

```xaml
<UserControl x:Class="NewTestProject.TestPackageControl" Name="MyToolWindow"
             xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
             xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
             xmlns:ns="clr-namespace:MyCustomColors">
  <Grid>
    <TextBlock Background="{DynamicResource {x:Static ns:MyCategory.MyColor1BrushKey}}"
               Foreground="{DynamicResource {x:Static ns:MyCategory.MyColor1TextBrushKey}}"
      >Sample Text</TextBlock>

  </Grid>
</UserControl>
```

 **Paso 5: pruebe los cambios en Visual Studio.**

 El editor de color puede aplicar temporalmente tokens de color a las instancias en ejecución de Visual Studio para ver los cambios en vivo en los colores sin volver a generar el paquete de extensión. Para ello, haga clic en el botón "Aplicar este tema a las ventanas de Visual Studio en ejecución" ubicado en el encabezado de cada columna de tema. Este tema temporal desaparecerá cuando se cierre el Editor de colores VSIX.

 ![Aplicación del Editor color de VSIX](../../extensibility/internals/media/vsix-color-editor-apply.png "Aplicación del Editor color de VSIX")

 Para que los cambios sean permanentes, vuelva a generar y vuelva a implementar la extensión de Visual Studio después de agregar los nuevos colores al archivo .pkgdef y escribir el código que usará esos colores. Volver a generar la extensión de Visual Studio combinará los valores del Registro para los nuevos colores en el resto de los temas. A continuación, vuelva a iniciar Visual Studio, vea la interfaz de usuario y compruebe que los nuevos colores aparecen como se esperaba.

## <a name="notes"></a>Notas
 Esta herramienta está diseñada para usarse para crear colores personalizados para los temas de Visual Studio preexistentes o para editar los colores de un tema de Visual Studio personalizado. Para crear temas personalizados completos de Visual Studio, descargue la extensión Editor de temas de color de [Visual Studio](https://marketplace.visualstudio.com/items?itemName=VisualStudioProductTeam.VisualStudio2015ColorThemeEditor) desde la Galería de extensiones de Visual Studio.

## <a name="sample-output"></a>Salida de ejemplo
 **Salida de color XML**

 El archivo .xml generado por la herramienta será similar a esto:

```xml
<Themes>
  <Theme Name="Light" GUID="{de3dbbcd-f642-433c-8353-8f1df4370aba}">
    <Category Name="CategoryName" GUID="{eee9d521-dac2-48d9-9a5e-5c625ba2040c}">
      <Color Name="ColorName1">
        <Background Type="CT_RAW" Source="FFFFFFFF" />
      </Color>
      <Color Name="ColorName2">
        <Background Type="CT_RAW" Source="FFFFFFFF" />
        <Foreground Type="CT_RAW" Source="FF000000" />
      </Color>
      <Color Name="ColorName3">
        <Background Type="CT_RAW" Source="FFFF0000" />
      </Color>
      <Color Name="ColorName4">
        <Background Type="CT_RAW" Source="FF000088" />
        <Foreground Type="CT_RAW" Source="FFFFFFFF" />
      </Color>
    </Category>
  </Theme>
  <Theme Name="Dark" GUID="{1ded0138-47ce-435e-84ef-9ec1f439b749}">...</Theme>
  <Theme Name="Blue" GUID="{a4d6a176-b948-4b29-8c66-53c97a1ed7d0}">...</Theme>
  <Theme Name="HighContrast" GUID="{a5c004b4-2d4b-494e-bf01-45fc492522c7}">...</Theme>
</Themes>

```

 **Salida de color PKGDEF**

 El archivo .pkgdef generado por la herramienta será similar a esto:

```
[$RootKey$\Themes\{de3dbbcd-f642-433c-8353-8f1df4370aba}\CategoryName]
"Data"=hex:78,00,00,00,0b,00,00,00,01,00,00,00,21,d5,e9,ee,c2,da,d9,48,9a,5e,5c,62,5b,a2,04,0c,04,00,00,00,0a,00,00,00,43,6f,6c,6f,72,4e,61,6d,65,31,01,ff,ff,ff,ff,00,0a,00,00,00,43,6f,6c,6f,72,4e,61,6d,65,32,01,ff,ff,ff,ff,01,00,00,00,ff,0a,00,00,00,43,6f,6c,6f,72,4e,61,6d,65,33,01,ff,00,00,ff,00,0a,00,00,00,43,6f,6c,6f,72,4e,61,6d,65,34,01,00,00,88,ff,01,ff,ff,ff,ff
[$RootKey$\Themes\{1ded0138-47ce-435e-84ef-9ec1f439b749}\CategoryName]
"Data"=hex:...
[$RootKey$\Themes\{a4d6a176-b948-4b29-8c66-53c97a1ed7d0}\CategoryName]
"Data"=hex:...
[$RootKey$\Themes\{a5c004b4-2d4b-494e-bf01-45fc492522c7}\CategoryName]
"Data"=hex:...

```

 **Contenedor de claves de recursos de CTM**

 Las claves de recursos de color generadas por la herramienta serán similares a esto:

```csharp
namespace MyNamespace
{
    public static class MyColors
    {
        #region Autogenerated resource keys
        // These resource keys are generated by Visual Studio Extension Color Editor, and should be replaced when new colors are added to this category.

        public static string ColorName1ColorKey { get { return "ColorName1ColorKey"; } }
        public static string ColorName1BrushKey { get { return "ColorName1BrushKey"; } }

        public static string ColorName2ColorKey { get { return "ColorName2ColorKey"; } }
        public static string ColorName2BrushKey { get { return "ColorName2BrushKey"; } }
        public static string ColorName2TextColorKey { get { return "ColorName2TextColorKey"; } }
        public static string ColorName2TextBrushKey { get { return "ColorName2TextBrushKey"; } }

        public static string ColorName3ColorKey { get { return "ColorName4ColorKey"; } }
        public static string ColorName3BrushKey { get { return "ColorName4BrushKey"; } }
        public static string ColorName3TextColorKey { get { return "ColorName4TextColorKey"; } }
        public static string ColorName3TextBrushKey { get { return "ColorName4TextBrushKey"; } }
        #endregion
    }
}
```

 **Contenedor de diccionario de recursos WPF**

 Las claves **ResourceDictionary** de color generadas por la herramienta serán similares a esto:

```xaml
<ResourceDictionary xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:colors="clr-namespace:MyNamespace">

  <SolidColorBrush x:Key="{x:Static colors:MyColors.ColorName1BrushKey}" Color="#FFFFFFFF" />
  <Color x:Key="{x:Static colors:MyColors.ColorName1ColorKey}" A="255" R="255" G="255" B="255" />

  <SolidColorBrush x:Key="{x:Static colors:MyColors.ColorName2BrushKey}" Color="#FFFFFFFF" />
  <Color x:Key="{x:Static colors:MyColors.ColorName2ColorKey}" A="255" R="255" G="255" B="255" />
  <SolidColorBrush x:Key="{x:Static colors:MyColors.ColorName2TextBrushKey}" Color="#FF000000" />
  <Color x:Key="{x:Static colors:MyColors.ColorName2TextColorKey}" A="255" R="0" G="0" B="0" />

  <SolidColorBrush x:Key="{x:Static colors:MyColors.ColorName3BrushKey}" Color="#FFFF0000" />
  <Color x:Key="{x:Static colors:MyColors.ColorName3ColorKey}" A="255" R="255" G="0" B="0" />

  <SolidColorBrush x:Key="{x:Static colors:MyColors.ColorName4BrushKey}" Color="#FF000088" />
  <Color x:Key="{x:Static colors:MyColors.ColorName4ColorKey}" A="255" R="0" G="0" B="136" />
  <SolidColorBrush x:Key="{x:Static colors:MyColors.ColorName4TextBrushKey}" Color="#FFFFFFFF" />
  <Color x:Key="{x:Static colors:MyColors.ColorName4TextColorKey}" A="255" R="255" G="255" B="255" />
</ResourceDictionary>
```
