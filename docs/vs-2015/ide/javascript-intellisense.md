---
title: IntelliSense para JavaScript | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology: vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IntelliSense [JavaScript]
- <reference> JavaScript XML tag
- JavaScript Code Editor
- XML code comments, JavaScript IntelliSense
- reference JavaScript XML tag
- JavaScript, IntelliSense
- code comments, JavaScript IntelliSense
- JavaScript, reference groups
- JavaScript Editor
- reference directives [JavaScript]
- JavaScript, XML documentation comments
- reference groups [JavaScript]
- JavaScript, reference directives
- IntelliSense [JavaScript], about
- IntelliSense extensibility [JavaScript]
- XML documentation comments [JavaScript]
ms.assetid: af1a3171-c9d8-45a3-9c96-a763e3b163ef
caps.latest.revision: 67
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a70e9598a6cae07a1ef6fcb861924b250a444ffe
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53864548"
---
# <a name="javascript-intellisense"></a>IntelliSense para JavaScript
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

IntelliSense le ayuda a escribir código con mayor rapidez y menos errores, ya que ofrece información mientras codifica. Cuando trabaja con script de cliente en el editor de JavaScript, IntelliSense elabora una lista de los objetos, funciones, propiedades y parámetros que están disponibles basándose en el contexto existente. Puede seleccionar una opción de codificación en la lista emergente que proporciona IntelliSense para completar el código.

 Con IntelliSense resulta más sencillo completar las tareas siguientes:

- Buscar información sobre los datos y métodos miembro.

- Insertar directamente los elementos del lenguaje en el código.

- Mantener el contexto sin necesidad de salir del editor de código.

- IntelliSense personalizado compatible con extensibilidad de Comentarios de documentación XML y JavaScript IntelliSense.

  Este tema contiene las siguientes secciones:

- [Determinar el contexto de IntelliSense](#DeterminingIntelliSenseContext)

- [Procesar la información de IntelliSense](#ProcessingIntelliSenseInformation)

- [Características de IntelliSense para JavaScript](#Features)

- [Extensibilidad de IntelliSense para JavaScript](#Extensibility)

- [Validación de JavaScript](#Validation)

  Para más información acerca de la funcionalidad de IntelliSense de [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)], consulte [Utilizar IntelliSense](../ide/using-intellisense.md).

##  <a name="DeterminingIntelliSenseContext"></a> Determinar el contexto de IntelliSense
 IntelliSense para JavaScript proporciona opciones de codificación basadas en todos los elementos de script que resulten relevantes en el contexto de script en que se trabaja. Esto incluye los elementos de scripting del archivo actual. Asimismo, se incluye cualquier código al que se haga referencia directa o indirectamente en el script, por ejemplo, las referencias al archivo de script, al script de ensamblado, al servicio y a las páginas asociadas.

 El contexto de script se crea en función de los elementos siguientes:

-   Funciones que se definen en todos los bloques de script del documento activo. Los bloques de scripts insertados son compatibles con los archivos que tienen las extensiones de nombre de archivo .aspx, .ascx, .master, .html y .htm.

-   Elementos `script` con los atributos `src` que señalan a otro archivo de script. El archivo de script de destino debe tener la extensión de nombre de archivo .js.

-   Archivos JavaScript que hacen referencia a otros archivos JavaScript mediante la directiva `reference`.

-   Grupos de referencia para objetos globales, extensiones de IntelliSense o archivos de script cargados con retardo.

-   Referencias a servicios Web XML.

-   Controles <xref:System.Web.UI.ScriptManager> y <xref:System.Web.UI.ScriptManagerProxy>, si la aplicación web es una aplicación ASP.NET habilitada para AJAX.

-   La [!INCLUDE[atlaslib_current_ext](../includes/atlaslib-current-ext-md.md)], si está trabajando con una aplicación web ASP.NET habilitada para AJAX.

    > [!NOTE]
    >  IntelliSense no es compatible con script que esté en atributos de controladores de eventos en elementos HTML ni que se defina en atributos `href`.

##  <a name="ProcessingIntelliSenseInformation"></a> Procesar la información de IntelliSense
 Para proporcionar IntelliSense para JavaScript, el servicio del lenguaje lleva a cabo las operaciones siguientes:

-   Crea una lista de archivos JavaScript dependientes que se basa en las referencias que contiene el documento activo, así como en la realización de un examen recursivo de las referencias del script de los archivos a los que se hace referencia.

-   Recorre la lista y recopila información de los tipos y otros datos pertinentes de cada archivo.

-   Agrega los datos y los transfiere al servicio de lenguaje JavaScript, el cual pone a disposición de IntelliSense la información sobre los tipos y los datos.

-   Supervisa los archivos por si hubiera cambios que hubiesen afectado a la lista de IntelliSense y actualiza la lista según sea necesario. Los scripts de almacenes remotos (por ejemplo, a los que se hace referencia mediante HTTP) no se supervisan.

##  <a name="Features"></a> Características de IntelliSense para JavaScript
 IntelliSense para JavaScript admite los objetos siguientes:

- [Elementos del Modelo de objetos de documento (DOM)](#HTMLDom)

- [Objetos intrínsecos](#IntrinsicObjects)

- [Variables, funciones y objetos definidos por el usuario](#UserDefined)

- Objetos definidos en archivos externos mediante referencias como [referencias de script](#Script), [directivas de referencia](#ReferenceDirectives) y [grupos de referencia](#ReferenceGroups).

- Objetos definidos en archivos remotos que Visual Studio descarga.

- Objetos especificados en [Comentarios de documentación XML](#XMLDocComments), como parámetros y campos.

- Objetos descritos mediante etiquetas estándar de comentarios JavaScript (/). Para más información, consulte [Extender IntelliSense para JavaScript](../ide/extending-javascript-intellisense.md).

- Objetos admitidos utilizando el [JavaScript IntelliSense extensibilidad](#Extensibility) mecanismo. Para más información, consulte [Extender IntelliSense para JavaScript](../ide/extending-javascript-intellisense.md).

- [Objetos ASP.NET AJAX](#ASPNet)

  Cuando IntelliSense no puede determinar el tipo de un objeto, proporciona opciones para la finalización de instrucciones mediante identificadores del documento activo. Para obtener más información, consulte [finalización de instrucciones para identificadores](../ide/statement-completion-for-identifiers.md).

###  <a name="HTMLDom"></a> Elementos DOM HTML
 IntelliSense para JavaScript proporciona referencias de programación para los elementos DOM HTML dinámicos (DHTML), como `body`, `form` y `div`. IntelliSense sólo muestra los elementos que están incluidos en el documento y la página maestra actuales. IntelliSense para JavaScript también admite los objetos `window` y `document`, y sus miembros.

###  <a name="IntrinsicObjects"></a> Objetos intrínsecos
 IntelliSense para JavaScript proporciona referencias de programación para los objetos intrínsecos de forma nativa, como `Array`, `String`, `Math`, `Date` y `Number`. Para más información acerca de los objetos intrínsecos, consulte [Objetos intrínsecos](/visualstudio/scripting-docs/javascript/intrinsic-objects-javascript).

###  <a name="UserDefined"></a> Variables, funciones y objetos definidos por el usuario
 Al cambiar un archivo JavaScript, [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] examina los documentos que están abiertos y a los que se hace referencia con el fin de identificar todos los recursos de código disponibles. Esto incluye las variables, funciones y objetos que haya creado. Posteriormente, estos recursos se ponen a disposición de IntelliSense para JavaScript.

 Para más información sobre variables, funciones y objetos definidos por el usuario, consulte [Crear objetos (JavaScript)](http://go.microsoft.com/fwlink/?LinkId=108671) en el sitio web de MSDN.

###  <a name="External"></a> Referencias a archivos externos
 Puede incluir diferentes tipos de referencias a archivos externos para lograr la compatibilidad con IntelliSense en el código. Las referencias a archivos externos pueden ser referencias de script, directivas de referencia o se pueden especificar mediante grupos de referencia.

####  <a name="Script"></a> Referencias de script
 En lugar de escribir el script de cliente íntegro en una página, puede hacer referencia a los archivos externos que incluyen código del scripting. De esta forma resulta más sencilla la reutilización del código entre páginas y permite que el explorador almacene en memoria caché el script de cliente.

 Si no está trabajando con una página web habilitada para ASP.NET AJAX, puede hacer referencia a un archivo de script externo mediante el atributo `src` en la etiqueta de apertura de un elemento `script`. El atributo `src` especifica la dirección URL de un archivo externo que contiene datos o código fuente.

 En el ejemplo siguiente se muestra el marcado que emplea el atributo `src` en una etiqueta <`script`> para hacer referencia a un archivo de script.

```html
<script type="text/javascript" src="~/Scripts/JavaScript.js">

</script>
```

 Si está trabajando con una página web habilitada para ASP.NET AJAX, puede hacer referencia a los archivos de script mediante la utilización del objeto <xref:System.Web.UI.ScriptReference> del control <xref:System.Web.UI.ScriptManager>.

 En el siguiente ejemplo se muestra el marcado que utiliza un objeto <xref:System.Web.UI.ScriptReference> en un control <xref:System.Web.UI.ScriptManager> para hacer referencia a un archivo de script.

```html
<asp:ScriptManager ID="ScriptManager1" runat="server">
  <Scripts>
    <asp:ScriptReference Path="~/Scripts/JavaScript.js" />
  </Scripts>
</asp:ScriptManager>
```

 IntelliSense también admite archivos de script que se incrustan como recursos en un ensamblado en aplicaciones web ASP.NET AJAX. Para obtener más información acerca de los recursos de script incrustados, vea [Tutorial: Incrustar un archivo JavaScript como un recurso en un ensamblado](http://msdn.microsoft.com/library/d8cb78cd-95a9-4dc6-92df-391866817e89).

####  <a name="ReferenceDirectives"></a> Directivas de referencia
 Con una directiva `reference`, [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] puede establecer una relación entre el script que está modificando actualmente y otros scripts. La directiva `reference` le permite incluir un archivo de script en el contexto de scripting del archivo de script actual. Esto habilita IntelliSense para poder hacer referencias, mientras codifica, a las funciones, tipos y campos definidos externamente.

 Cree una directiva `reference` con formato de comentario XML. La directiva se debe declarar en el archivo antes que cualquier script. Una directiva `reference` puede incluir una referencia a un script basado en discos, basado en ensamblados, basado en servicios o basado en páginas.

 En el ejemplo siguiente se muestra cómo utilizar las directivas de referencia basadas en discos. En el primer ejemplo, el servicio de lenguaje busca el archivo en la misma carpeta que contiene el archivo de proyecto (por ejemplo, .jsproj).

 `/// <reference path="ScriptFile1.js" />`

 `/// <reference path="Scripts/ScriptFile2.js" />`

 `/// <reference path="../ScriptFile3.js" />`

 `/// <reference path="~/Scripts/ScriptFile4.js" />`

 En el ejemplo siguiente se muestra cómo crear una referencia a un script basado en ensamblados.

 `/// <reference name "Ajax.js" assembly="System.Web.Extensions, ..." />`

 En el ejemplo siguiente se muestra cómo hacer referencia a un script basado en servicios:

 `/// <reference path="MyService.asmx" />`

 `/// <reference path="Services/MyService.asmx" />`

 `/// <reference path="../MyService.asmx" />`

 `/// <reference path="~/Services/MyService.asmx" />`

> [!NOTE]
>  IntelliSense para JavaScript no admite scripts contenidos en archivos de servicios Web (.asmx) en proyectos de aplicaciones web (WAP).

 En el ejemplo siguiente se muestra cómo hacer referencia a un script basado en páginas.

 `/// <reference path="Default.aspx" />`

 `/// <reference path="Admin/Default.aspx" />`

 `/// <reference path="../Default.aspx" />`

 `/// <reference path="~/Admin/Default.aspx" />`

 Las reglas siguientes se aplican a una directiva `reference`.

-   El comentario XML de `reference` se debe declarar antes que cualquier script.

-   Debe utilizar la sintaxis de los comentarios XML con tres barras diagonales. Se omiten las referencias realizadas mediante sintaxis de comentarios estándar (dos barras diagonales).

-   Sólo se puede especificar un archivo o recurso por directiva.

-   No se permiten referencias múltiples a los scripts basados en páginas.

-   Si se especifica una referencia de página, no se permite ningún otro tipo de directivas de referencia.

-   Los nombres de archivo utilizan rutas de acceso relativas. Puede utilizar el operador tilde (`~`) para crear rutas relativas de acceso a la raíz de la aplicación.

-   Se omiten las rutas de acceso absolutas.

-   No se procesarán las directivas de referencia en las páginas a las que se hace referencia (es decir, las directivas de referencia no se resuelven de forma recursiva para las páginas). Únicamente se incluye el script al que hace referencia directamente la página.

####  <a name="ReferenceGroups"></a> Grupos de referencias
 Puede usar los grupos de referencias predefinidos para especificar qué archivos concretos .js de IntelliSense se incluyen en el ámbito para proyectos diferentes de JavaScript. Los siguientes tipos de grupos de referencias están disponibles:

- Implícita (Windows), para aplicaciones de la [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] que usan JavaScript. Los archivos incluidos en este grupo están en el ámbito de cada archivo .js abierto en el Editor de código para el proyecto del tipo especificado.

- Implícito (Web), para proyectos HTML5. Los archivos incluidos en este grupo están en el ámbito de cada archivo .js abierto en el Editor de código para estos tipos de proyecto.

- Grupos de referencia de trabajo dedicado, para trabajos web de HTML5. Los archivos especificados en este grupo están en el ámbito para los archivos .js que tienen una referencia explícita a un grupo de referencia de trabajo dedicado.

- Genérico, para otros tipos de proyectos JavaScript.

  En la mayoría de los casos, no es preciso modificar los grupos de referencia. Sin embargo, si desea hacer cambios, use las opciones de configuración para que el Editor de código JavaScript especifique los archivos incluidos en los grupos de referencia. Para obtener instrucciones acerca de cómo utilizar esta característica, consulte [Opciones, Editor de texto, JavaScript, IntelliSense](../ide/reference/options-text-editor-javascript-intellisense.md).

> [!TIP]
>  Las referencias de IntelliSense se utilizan normalmente para proporcionar compatibilidad con IntelliSense a los objetos globales y a las [extensiones](#Extensibility) IntelliSense. También puede utilizar esta característica para los scripts que se deben cargar en tiempo de ejecución mediante el cargador de scripts.

### <a name="remote-file-references"></a>Referencias a archivos remotos
 Puede indicar a Visual Studio que descargue archivos remotos JavaScript a los que se hace referencia en un archivo JavaScript para proporcionar compatibilidad con IntelliSense a dicho archivo remoto o biblioteca. Si se usa esta característica, los archivos se descargarán cuando se incluyan como una referencia en el archivo JavaScript.

> [!NOTE]
>  A excepción de los proyectos web, esta característica solo funciona para los archivos JavaScript que se abren fuera del contexto de un proyecto. En los proyectos web, los archivos remotos a los que se hace referencia en el proyecto se descargan de forma predeterminada.

 Para obtener instrucciones acerca de cómo utilizar esta característica, consulte [Opciones, Editor de texto, JavaScript, IntelliSense](../ide/reference/options-text-editor-javascript-intellisense.md).

> [!WARNING]
>  Si habilita esta característica y observa un rendimiento más lento en el Editor de código, se recomienda deshabilitarla.

###  <a name="XMLDocComments"></a> Comentarios de documentación XML
 Los comentarios de documentación XML son descripciones textuales de los elementos de código que se agregan a un script. Estas descripciones se mostrarán en IntelliSense cuando haga referencia al script con comentarios. Por ejemplo, puede proporcionar información sobre los parámetros y el valor devuelto de una función. Los comentarios de documentación XML únicamente están disponibles en los archivos, ensamblados y servicios a los que se hace referencia. Para obtener más información, consulte [comentarios de documentación XML](../ide/xml-documentation-comments-javascript.md) y [crear comentarios de documentación XML](../ide/create-xml-documentation-comments-for-javascript-intellisense.md).

 IntelliSense puede mostrar comentarios de documentación XML en los escenarios siguientes:

- Un archivo .js que hace referencia a otro archivo .js.

- Un archivo .js que hace referencia a un archivo .aspx.

- Un archivo .aspx que hace referencia a un archivo .js.

  IntelliSense no está disponible cuando un archivo .aspx hace referencia a otro archivo .aspx.

###  <a name="ASPNet"></a> Objetos ASP.NET AJAX
 ASP.NET AJAX también es compatible con IntelliSense para JavaScript. ASP.NET AJAX incluye un marco de cliente que amplía los tipos estándar disponibles en ECMAScript (JavaScript). Para que IntelliSense para JavaScript pueda proporcionar detalles sobre objetos ASP.NET AJAX, se han agregado comentarios de documentación XML a [!INCLUDE[atlaslib_current_ext](../includes/atlaslib-current-ext-md.md)]. Estos comentarios de documentación XML se muestran cuando se usan los tipos y miembros de la Biblioteca ASP.NET AJAX.

> [!NOTE]
>  IntelliSense para JavaScript no muestra los miembros privados. Los miembros privados se indican en ASP.NET AJAX mediante un guión bajo (_) inicial.

##  <a name="Extensibility"></a> Extensibilidad de IntelliSense para JavaScript
 El JavaScript Language Service proporciona objetos y funciones que permiten modificar la experiencia de IntelliSense a los desarrolladores que utilizan bibliotecas de otros fabricantes. Estas características son especialmente útiles cuando el servicio de lenguaje predeterminado no puede proporcionar toda la información que desearía ofrecer a los clientes. Para más información, consulte [Extender IntelliSense para JavaScript](../ide/extending-javascript-intellisense.md).

##  <a name="Validation"></a> Validación de JavaScript
 La validación de scripting JavaScript tiene lugar en segundo plano de forma constante. Cuando [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] detecta errores de sintaxis en el código JavaScript, los comentarios se proporcionan de las maneras siguientes:

-   Elementos subrayados en el editor. El subrayado ondulado en rojo indica los errores. Si mantiene el puntero del mouse sobre el error, aparecerá una ventana (información sobre herramientas) que mostrará la descripción del error.

-   **Lista de errores** (ventana) La ventana **Lista de errores** muestra la descripción del error, el archivo donde se produjo, el número de línea y de columna, y el proyecto. Para mostrar la ventana **Lista de errores**, en el menú **Ver**, haga clic en **Lista de errores**.

-   La ventana de salida muestra las referencias que no se cargaron.

## <a name="see-also"></a>Vea también
- [Usar IntelliSense](../ide/using-intellisense.md)
- [Crear comentarios de documentación XML](../ide/create-xml-documentation-comments-for-javascript-intellisense.md)
- [Extender IntelliSense para JavaScript](../ide/extending-javascript-intellisense.md)
- [Finalización de instrucciones para identificadores](../ide/statement-completion-for-identifiers.md)
- [Comentarios de documentación XML](../ide/xml-documentation-comments-javascript.md)
- [Acerca del modelo de objetos DHTML](http://go.microsoft.com/fwlink/?LinkID=92344)
- [Lista de miembros](http://msdn.microsoft.com/en-us/1b9cc469-9cd4-4d42-9999-1f9479635ff8)
- [Atributo SRC &#124; src (propiedad)](http://go.microsoft.com/fwlink/?LinkId=92345)