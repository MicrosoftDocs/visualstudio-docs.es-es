---
title: Editor de colores de VSIX | Microsoft Docs
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: 70879c5d-e0f0-4845-993c-2f4229869706
caps.latest.revision: 6
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ea5695c41b19cbd77c56a63f22b52fca5ee6f1eb
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2019
ms.locfileid: "74295441"
---
# <a name="vsix-color-editor"></a>Editor de colores de VSIX
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La herramienta editor de colores de extensión de Visual Studio puede crear y editar colores personalizados para Visual Studio. La herramienta también puede generar claves de recursos de tema para que los colores se puedan usar en el código. Esta herramienta es útil para crear colores para una extensión de Visual Studio que admita la realización de la conversión. Esta herramienta puede abrir archivos. pkgdef y. Xml. Los temas de Visual Studio (archivos. vstheme) se pueden usar con el editor de colores de extensión de Visual Studio cambiando la extensión de archivo a. Xml. Además, los archivos. vstheme se pueden importar en un archivo. XML actual.  
  
 ![Héroe del editor de colores de VSIX](../../extensibility/internals/media/vsix-color-editor-hero.png "Imagen prominente del editor de colores de VSIX")  
  
 **Archivos de definición del paquete**  
  
 Los archivos de definición de paquete (. pkgdef) son los archivos que definen los temas. Los colores se almacenan en los archivos de color. xml del tema, que se compilan en un archivo. pkgdef. Los archivos. pkgdef se implementan en ubicaciones en las que se pueden realizar búsquedas en Visual Studio, se procesan en tiempo de ejecución y se combinan juntos para definir temas.  
  
 **Tokens de color**  
  
 Un token de color se compone de cuatro elementos:  
  
- **Nombre de categoría:** Agrupación lógica para un conjunto de colores. Use un nombre de categoría existente si ya hay colores que son específicos del elemento de la interfaz de usuario deseado o un grupo de elementos de la interfaz de usuario.  
  
- **Nombre del token:** Un nombre descriptivo para el token de color y los conjuntos de tokens. Los conjuntos incluyen nombres de token de fondo y de primer plano (texto), así como todos sus Estados, y se les debe asignar un nombre para que sea fácil identificar los pares y los Estados a los que se aplican.  
  
- **Valores de color (o matices):** Necesario para cada tema de color. Cree siempre valores de color de fondo y de texto en parejas. Los colores se emparejan para el fondo o el primer plano para que el color del texto (primer plano) siempre sea legible en el color de fondo en el que se dibuja. Estos colores se vinculan y se usarán juntos en la interfaz de usuario. Si el fondo no está pensado para usarse con texto, no defina un color de primer plano.  
  
- **Nombre del color del sistema:** Para su uso en pantallas de contraste alto.  
  
## <a name="how-to-use-the-tool"></a>Cómo usar la herramienta  
 En la medida de lo posible, y cuando corresponda, los colores existentes de Visual Studio se deben volver a usar en lugar de crear otros nuevos. Sin embargo, para los casos en los que no se definen colores adecuados, se deben crear colores personalizados para mantener la compatibilidad con la extensión.  
  
 **Crear nuevos tokens de color**  
  
 Para crear colores personalizados mediante el editor de colores de extensión de Visual Studio, siga estos pasos:  
  
1. Determine los nombres de categoría y token para los nuevos tokens de color.  
  
2. Elija los matices que el elemento de la interfaz de usuario usará para cada tema y el color del sistema para contraste alto.  
  
3. Utilice el editor de colores para crear nuevos tokens de color.  
  
4. Use los colores en una extensión de Visual Studio.  
  
5. Pruebe los cambios en Visual Studio.  
  
   **Paso 1: determinar los nombres de categoría y token para los nuevos tokens de color.**  
  
   El esquema de nomenclatura preferido para un VSColor es **[Category] [UI type] [State]** . No use la palabra "color" en los nombres de VSColor, ya que es redundante.  
  
   Los nombres de categoría proporcionan agrupaciones lógicas y deben definirse de la manera más estrecha posible. Por ejemplo, el nombre de una única ventana de herramientas puede ser un nombre de categoría, pero el nombre de una unidad de negocio o un equipo de proyecto completos no lo es. La agrupación de entradas en categorías ayuda a evitar la confusión entre colores con el mismo nombre.  
  
   Un nombre de token debe indicar claramente el tipo de elemento y las situaciones, o "estado", para los que se aplicará el color. Por ejemplo, un **[tipo de interfaz de usuario]** de la sugerencia de datos activo se podría denominar **"información sobre herramientas**" y el **[Estado]** podría denominarse "**activo**", lo que da como resultado un nombre de color de "**DataTipActive**". Dado que las sugerencias de datos tienen texto, es necesario definir un color de primer plano y de fondo. Mediante el uso de un emparejamiento en segundo plano y en primer plano, el editor de colores creará automáticamente los colores "**DataTipActive**" para el fondo y "**DataTipActiveText**" para el primer plano.  
  
   Si el elemento de la interfaz de usuario solo tiene un estado, se puede omitir la parte **[State]** del nombre. Por ejemplo, si un cuadro de búsqueda tiene un borde y no hay ningún cambio de estado que afecte al color del borde, el nombre del token de color del borde se puede llamar simplemente "**SearchBoxBorder**".  
  
   Algunos nombres de estado comunes incluyen:  
  
- Activa  
  
- Inactive  
  
- MouseOver  
  
- MouseDown  
  
- Seleccionado  
  
- Con foco  
  
  Ejemplos de algunos nombres de token para las partes de un control de elemento de lista:  
  
- ListItem  
  
- ListItemBorder  
  
- ListItemMouseOver  
  
- ListItemMouseOverBorder  
  
- ListItemSelected  
  
- ListItemSelectedBorder  
  
- ListItemDisabled  
  
- ListItemDisabledBorder  
  
  **Paso 2: elija los matices que el elemento de la interfaz de usuario usará para cada tema y el color del sistema para contraste alto.**  
  
  Al elegir los colores personalizados para la interfaz de usuario, seleccione un elemento de interfaz de usuario existente similar y use sus colores como base. Los colores de los elementos de la interfaz de usuario de la caja se han sometido a revisiones y pruebas, por lo que tendrán un aspecto adecuado y se comportarán correctamente en todos los temas.  
  
  **Paso 3: usar el editor de colores para crear nuevos tokens de color.**  
  
  Inicie el editor de colores y abra o cree un nuevo archivo Custom Theme colors. Xml. En el menú, seleccione **editar > nuevo color** . Se abrirá un cuadro de diálogo para especificar la categoría y uno o varios nombres para las entradas de color dentro de esa categoría:  
  
  ![Nuevo color del editor de colores de VSIX](../../extensibility/internals/media/vsix-color-editor-new-color.png "Aplicación del Editor color de VSIX")  
  
  Seleccione una categoría existente o seleccione **nueva categoría** para crear una nueva categoría. Se abrirá otro cuadro de diálogo y se creará un nuevo nombre de categoría:  
  
  ![Nueva categoría del editor de colores de VSIX](../../extensibility/internals/media/vsix-color-editor-new-category.png "Nueva categoría del Editor color de VSIX")  
  
  La nueva categoría estará disponible en el menú desplegable nueva categoría de **color** . Después de elegir una categoría, escriba un nombre por línea para cada nuevo token de color y seleccione "crear" cuando termine:  
  
  ![Color del editor de colores de VSIX nuevo relleno](../../extensibility/internals/media/vsix-color-editor-new-color-filled.png "Nuevo color rellenado en el Editor de colores de VSIX")  
  
  Los valores de color se muestran en pares de fondo y de primer plano, con "none", lo que indica que no se ha definido el color. Nota: Si un color no tiene un par de colores de color o de fondo de texto, solo es necesario definir el fondo.  
  
  ![Valores de color del editor de colores de VSIX](../../extensibility/internals/media/vsix-color-editor-color-values.png "Valores de color del editor de colores de VSIX")  
  
  Para editar un token de color, seleccione una entrada de color para el tema (columna) de ese token. Agregue el valor de color escribiendo un valor de color Hex en formato ARGB de 8 dígitos, escribiendo un nombre de color del sistema en la celda o usando el menú desplegable para seleccionar el color deseado a través de un conjunto de controles deslizantes de color o una lista de colores del sistema.  
  
  ![Color de edición del editor de colores de VSIX](../../extensibility/internals/media/vsix-color-editor-edit-color.png "Color de edición del editor de colores de VSIX")  
  
  ![Fondo del editor de colores de VSIX](../../extensibility/internals/media/vsix-color-editor-background.png "Fondo del Editor de color de VSIX")  
  
  En el caso de los componentes que no necesitan Mostrar texto, escriba solo un valor de color: el color de fondo. De lo contrario, escriba los valores de color de fondo y de texto, separados por una barra diagonal.  
  
  Al especificar valores para contraste alto, escriba los nombres de colores del sistema Windows válidos. No escriba valores ARGB codificados. Para ver una lista de nombres de colores del sistema válidos, seleccione "background: System" o "Foreground: System" en los menús desplegables de valores de color. Al crear elementos que tienen componentes de texto, use el par de colores de fondo y de texto del sistema de texto correctos, o bien el texto podría ser ilegible.  
  
  Cuando termine de crear, configurar y editar los tokens de color, guárdelos en el formato. XML o. pkgdef deseado. Los tokens de color que no tengan un fondo ni un conjunto de primer plano se guardarán como colores vacíos en formato. XML, pero se descartarán en formato. pkgdef. Un cuadro de diálogo le avisará de la posible pérdida de color si intenta guardar colores vacíos en un archivo. pkgdef.  
  
  **Paso 4: usar los colores en una extensión de Visual Studio.**  
  
  Después de definir los nuevos tokens de color, incluya el archivo. pkgdef en el archivo de proyecto con "acción de compilación" establecida en "contenido" y "incluir en VSIX" establecido en "true".  
  
  ![Editor de colores de VSIX pkgdef](../../extensibility/internals/media/vsix-color-editor-pkgdef.png "pkgdef del editor de colores de VSIX")  
  
  En el editor de colores de extensión de Visual Studio, elija Archivo > Ver código de recursos para ver el código que se usa para tener acceso a los colores personalizados en la interfaz de usuario basada en WPF.  
  
  ![Visor de código de recursos del editor de colores de VSIX](../../extensibility/internals/media/vsix-color-editor-resource-code-viewer.png "Visor de código de recurso del editor de colores de VSIX")  
  
  Incluya este código en una clase estática del proyecto. Es necesario agregar al proyecto una referencia a **Microsoft. VisualStudio. Shell.\<VSVersion >,0. dll** para usar el tipo **ThemeResourceKey** .  
  
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
  
 Esto permite el acceso a los colores del código XAML y permite a la interfaz de usuario responder a los cambios de tema.  
  
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
  
 **Paso 5: probar los cambios en Visual Studio.**  
  
 El editor de colores puede aplicar temporalmente tokens de color a las instancias en ejecución de Visual Studio para ver los cambios en directo de los colores sin volver a generar el paquete de extensión. Para ello, haga clic en el botón "aplicar este tema a la ejecución de Visual Studio Windows" que se encuentra en el encabezado de cada columna del tema. Este tema temporal desaparecerá cuando se cierre el editor de colores de VSIX.  
  
 ![Se aplica el editor de colores de VSIX](../../extensibility/internals/media/vsix-color-editor-apply.png "Aplicación del Editor color de VSIX")  
  
 Para que los cambios sean permanentes, recompile y vuelva a implementar la extensión de Visual Studio después de agregar los nuevos colores al archivo. pkgdef y escriba el código que usará esos colores. Al volver a generar la extensión de Visual Studio, se combinan los valores del registro para los nuevos colores en el resto de los temas. A continuación, reinicie Visual Studio, vea la interfaz de usuario y compruebe que los nuevos colores aparecen como se esperaba.  
  
## <a name="notes"></a>Notas  
 Esta herramienta está destinada a usarse para crear colores personalizados para los temas de Visual Studio preexistentes o para editar los colores de un tema personalizado de Visual Studio. Para crear temas personalizados de Visual Studio, descargue la [extensión del editor de temas de color de Visual Studio](https://marketplace.visualstudio.com/items?itemName=VisualStudioProductTeam.VisualStudio2015ColorThemeEditor) desde la galería de extensiones de Visual Studio.  
  
## <a name="sample-output"></a>Salida de muestra  
 **Salida de color XML**  
  
 El archivo. XML generado por la herramienta será similar al siguiente:  
  
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
  
 El archivo. pkgdef generado por la herramienta será similar al siguiente:  
  
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
  
 **C#contenedor de claves de recursos**  
  
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
  
 **Contenedor de Diccionario de recursos WPF**  
  
 La clave de los **ResourceDictionary** de color generada por la herramienta será similar a la siguiente:  
  
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
