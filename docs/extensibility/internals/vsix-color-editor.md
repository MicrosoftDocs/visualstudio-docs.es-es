---
title: Editor de colores VSIX | Microsoft Docs
description: Obtenga información sobre la Visual Studio Editor de colores de extensión, que puede crear y editar colores personalizados para Visual Studio generar claves de recursos de tema.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 70879c5d-e0f0-4845-993c-2f4229869706
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 95fec01beabb66180089a75e772b40788a1f7f0d
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898945"
---
# <a name="vsix-color-editor"></a>Editor de colores de VSIX
La Visual Studio editor de colores de extensión de extensión puede crear y editar colores personalizados para Visual Studio. La herramienta también puede generar claves de recursos de tema para que los colores se puedan usar en el código. Esta herramienta es útil para crear colores para una extensión de Visual Studio que admita el tema. Esta herramienta puede abrir .pkgdef y .xml archivos. Visual Studio los temas (archivos .vstheme) se pueden usar con el Editor de colores de extensión de Visual Studio cambiando la extensión de archivo a .xml. Además, los archivos .vstheme se pueden importar en un archivo .xml actual.

 ![Imagen prominente del editor de colores de VSIX](../../extensibility/internals/media/vsix-color-editor-hero.png "Imagen prominente del editor de colores de VSIX")

 **Archivos de definición del paquete**

 Los archivos de definición de paquete (.pkgdef) son los archivos que definen temas. Los colores se almacenan en el color del tema .xml archivos, que se compilan en un archivo .pkgdef. Los archivos .pkgdef se implementan en Visual Studio de búsqueda, se procesan en tiempo de ejecución y se combinan para definir temas.

 **Tokens de color**

 Un token de color se forma de cuatro elementos:

- **Nombre de categoría:** Agrupación lógica para un conjunto de colores. Use un nombre de categoría existente si ya hay colores específicos para el elemento de interfaz de usuario deseado o un grupo de elementos de interfaz de usuario.

- **Nombre del token:** Nombre descriptivo para el token de color y los conjuntos de tokens. Los conjuntos incluyen nombres de token de fondo y primer plano (texto), así como todos sus estados, y estos deben tener un nombre para que sea fácil identificar los pares y los estados a los que se aplican.

- **Valores de color (o matiz):** Necesario para cada tema coloreado. Cree siempre valores de color de fondo y texto en pares. Los colores se emparejan para el fondo y el primer plano para que el color de texto (primer plano) siempre se pueda leer con respecto al color de fondo en el que se dibuja. Estos colores están vinculados y se usarán juntos en la interfaz de usuario. Si el fondo no está pensado para su uso con texto, no defina un color de primer plano.

- **Nombre de color del sistema:** Para su uso en pantallas de contraste alto.

## <a name="how-to-use-the-tool"></a>Uso de la herramienta
 Tanto como sea posible, y cuando sea necesario, se deben reutilizar los colores Visual Studio existentes en lugar de crear otros nuevos. Sin embargo, en los casos en los que no se definen colores adecuados, se deben crear colores personalizados para mantener una compatibilidad con el tema de extensiones.

 **Creación de nuevos tokens de color**

 Para crear colores personalizados mediante el Editor de colores Visual Studio extensión, siga estos pasos:

1. Determine los nombres de categoría y token para los nuevos tokens de color.

2. Elija los matiz que usará el elemento de interfaz de usuario para cada tema y el color del sistema para contraste alto.

3. Use el editor de colores para crear nuevos tokens de color.

4. Use los colores de una extensión Visual Studio aplicación.

5. Pruebe los cambios en Visual Studio.

   **Paso 1: Determinar los nombres de categoría y token de los nuevos tokens de color.**

   El esquema de nomenclatura preferido para un VSColor es **[Category] [UI type] [State]**. No use la palabra "color" en los nombres de VSColor, ya que es redundante.

   Los nombres de categoría proporcionan agrupaciones lógicas y deben definirse lo más estrechamente posible. Por ejemplo, el nombre de una sola ventana de herramientas podría ser un nombre de categoría, pero el nombre de toda una unidad de negocio o equipo de proyecto no lo es. La agrupación de entradas en categorías ayuda a evitar confusiones entre colores con el mismo nombre.

   Un nombre de token debe indicar claramente el tipo de elemento y las situaciones, o "estado", para las que se aplicará el color. Por ejemplo, el [tipo de interfaz de **usuario]** de una sugerencia de datos activa podría denominarse **"Información** sobre datos" y **[Estado]** podría denominarse **"Activo",** lo que da lugar a un nombre de color de **"DataTipActive".** Puesto que las sugerencias de datos tienen texto, es necesario definir un color de primer plano y un color de fondo. Mediante el uso de un emparejamiento de fondo y primer plano, el editor de colores creará automáticamente los colores "**DataTipActive**" para el fondo y "**DataTipActiveText**" para el primer plano.

   Si la parte de la interfaz de usuario solo tiene un estado, se puede omitir la parte **[State]** del nombre. Por ejemplo, si un cuadro de búsqueda tiene un borde y no hay ningún cambio de estado que afecte al color del borde, el nombre del token de color del borde se puede llamar simplemente **"SearchBoxBorder".**

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

  **Paso 2: elija los matiz que usará el elemento de interfaz de usuario para cada tema y el color del sistema para contraste alto.**

  Al elegir colores personalizados para la interfaz de usuario, seleccione un elemento de interfaz de usuario similar y use sus colores como base. Los colores de los elementos de la interfaz de usuario de cuadro se han sometido a revisión y pruebas, por lo que tendrán un aspecto adecuado y se comportarán correctamente en todos los temas.

  **Paso 3: Use el editor de colores para crear nuevos tokens de color.**

  Inicie el editor de colores y abra o cree un nuevo archivo de colores de tema .xml personalizado. Seleccione **Editar > Nuevo color** en el menú. Se abrirá un cuadro de diálogo para especificar la categoría y uno o varios nombres para las entradas de color dentro de esa categoría:

  ![Aplicación del Editor color de VSIX](../../extensibility/internals/media/vsix-color-editor-new-color.png "Aplicación del Editor color de VSIX")

  Seleccione una categoría existente o seleccione **Nueva categoría** para crear una nueva categoría. Se abrirá otro cuadro de diálogo, creando un nuevo nombre de categoría:

  ![Nueva categoría del Editor color de VSIX](../../extensibility/internals/media/vsix-color-editor-new-category.png "Nueva categoría del Editor color de VSIX")

  La nueva categoría estará disponible en el menú **desplegable** Categoría de nuevo color. Después de elegir una categoría, escriba un nombre por línea para cada nuevo token de color y seleccione "Crear" cuando termine:

  ![Nuevo color rellenado en el Editor de colores de VSIX](../../extensibility/internals/media/vsix-color-editor-new-color-filled.png "Nuevo color rellenado en el Editor de colores de VSIX")

  Los valores de color se muestran en pares de fondo/primer plano, con "None" que indica que el color no se ha definido. Nota: Si un color no tiene un par de color de texto y color de fondo, solo es necesario definir el fondo.

  ![Valores de color del editor de colores de VSIX](../../extensibility/internals/media/vsix-color-editor-color-values.png "Valores de color del editor de colores de VSIX")

  Para editar un token de color, seleccione una entrada de color para el tema (columna) de ese token. Para agregar el valor de color, escriba un valor de color hexadecimal en formato ARGB de 8 dígitos, escriba un nombre de color del sistema en la celda o use el menú desplegable para seleccionar el color deseado a través de un conjunto de controles deslizantes de color o una lista de colores del sistema.

  ![Color de edición del editor de colores de VSIX](../../extensibility/internals/media/vsix-color-editor-edit-color.png "Color de edición del editor de colores de VSIX")

  ![Fondo del Editor de color de VSIX](../../extensibility/internals/media/vsix-color-editor-background.png "Fondo del Editor de color de VSIX")

  Para los componentes que no necesitan mostrar texto, escriba solo un valor de color: el color de fondo. De lo contrario, escriba valores para el fondo y el color de texto, separados por una barra diagonal.

  Al escribir valores para contraste alto, escriba nombres de color válidos del sistema Windows. No escriba valores ARGB codificados de forma rígida. Puede ver una lista de nombres de color del sistema válidos seleccionando "Fondo: Sistema" o "Primer plano: Sistema" en los menús desplegables de valores de color. Al crear elementos que tienen componentes de texto, use el par de colores correcto del sistema de fondo y texto o el texto podría ser ilegible.

  Cuando termine de crear, establecer y editar los tokens de color, guárdelos en el formato .xml o .pkgdef deseado. Los tokens de color sin un fondo ni un conjunto de primer plano se guardarán como colores vacíos en formato .xml, pero se descartarán en formato .pkgdef. Un cuadro de diálogo le advertirá de una posible pérdida de color si intenta guardar colores vacíos en un archivo .pkgdef.

  **Paso 4: Usar los colores de una Visual Studio extensión.**

  Después de definir los nuevos tokens de color, incluya .pkgdef en el archivo de proyecto con "Acción de compilación" establecido en "Contenido" e "Incluir en VSIX" establecido en "True".

  ![pkgdef del editor de colores de VSIX](../../extensibility/internals/media/vsix-color-editor-pkgdef.png "pkgdef del editor de colores de VSIX")

  En el Editor de colores Visual Studio extensión, elija Archivo > Ver código de recursos para ver el código que se usa para acceder a los colores personalizados en la interfaz de usuario basada en WPF.

  ![Visor de código de recurso del editor de colores de VSIX](../../extensibility/internals/media/vsix-color-editor-resource-code-viewer.png "Visor de código de recurso del editor de colores de VSIX")

  Incluya este código en una clase estática en el proyecto. Una referencia a **Microsoft.VisualStudio.Shell. \<VSVersion>.0.dll** debe agregarse al proyecto para usar el **tipo ThemeResourceKey.**

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

 Esto permite el acceso a los colores del código XAML y permite que la interfaz de usuario responda a los cambios de tema.

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

 **Paso 5: Probar los cambios en Visual Studio.**

 El editor de colores puede aplicar temporalmente tokens de color a las instancias en ejecución de Visual Studio ver los cambios en directo en los colores sin volver a generar el paquete de extensión. Para ello, haga clic en el botón "Aplicar este tema a la ejecución Visual Studio ventanas" situado en el encabezado de cada columna de tema. Este tema temporal desaparecerá cuando se cierre el Editor de colores VSIX.

 ![Aplicación del Editor color de VSIX](../../extensibility/internals/media/vsix-color-editor-apply.png "Aplicación del Editor color de VSIX")

 Para que los cambios se hagan permanentes, vuelva a generar y volver a implementar la extensión Visual Studio después de agregar los nuevos colores al archivo .pkgdef y escribir el código que usará esos colores. Al volver a generar Visual Studio extensión se combinarán los valores del Registro de los nuevos colores en el resto de los temas. Después, vuelva a Visual Studio, vea la interfaz de usuario y compruebe que los nuevos colores aparecen según lo previsto.

## <a name="notes"></a>Notas
 Esta herramienta está pensada para usarse para crear colores personalizados para los temas Visual Studio preexistente o para editar los colores de un tema Visual Studio personalizado. Para crear temas de Visual Studio personalizados completos, descargue Visual Studio Editor de temas de [color](https://marketplace.visualstudio.com/items?itemName=VisualStudioProductTeam.VisualStudio2015ColorThemeEditor) de la galería Visual Studio de contenido.

## <a name="sample-output"></a>Salida de ejemplo
 **Salida de color XML**

 El .xml generado por la herramienta será similar al siguiente:

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

 **Salida de color de PKGDEF**

 El archivo .pkgdef generado por la herramienta será similar al siguiente:

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

 **Contenedor de claves de recursos de C#**

 Las claves de recursos de color generadas por la herramienta serán similares a las siguientes:

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

 **Contenedor de diccionario de recursos de WPF**

 El color **ResourceDictionary** keys generado por la herramienta será similar al siguiente:

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
