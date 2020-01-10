---
title: SDK de Visor de Ayuda de Microsoft | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 620d7dcd-d462-475e-a449-fbfa06ff12c5
caps.latest.revision: 34
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 96647f362566f0687cb04b7da4459331ac56b031
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2020
ms.locfileid: "75851902"
---
# <a name="microsoft-help-viewer-sdk"></a>SDK del Visor de Ayuda de Microsoft
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Este artículo contiene las siguientes tareas para los integradores del visor de ayuda de Visual Studio:

- Crear un tema (compatibilidad con F1)

- Crear un paquete de marca de contenido del visor de ayuda

- Implementación de un conjunto de artículos

- Agregar ayuda a Visual Studio Shell (integrado o aislado)

- Recursos adicionales

### <a name="creating-a-topic-f1-support"></a>Crear un tema (compatibilidad con F1)
 En esta sección se proporciona información general sobre los componentes de un tema presentado, requisitos de tema, una breve descripción de cómo crear un tema (incluidos los requisitos de compatibilidad con F1) y, por último, un tema de ejemplo con su resultado representado.

 **Información general del tema del visor de ayuda**

 Cuando se llama a un tema para su representación, el visor de ayuda obtiene los elementos del paquete de personalización de marca asociados al tema en el momento de la instalación o última actualización, junto con el tema XHTML, y combina los dos para generar la vista de contenido presentada (datos de personalización de marca + datos del tema).  El paquete de personalización de marca contiene logotipos, compatibilidad para comportamientos de contenido y texto de personalización de marca (copyright, etc.).  Vea "crear un paquete de personalización de marca" para obtener más información sobre los elementos del paquete de personalización de marca.  En el caso de que no haya ningún paquete de personalización de marca asociado al tema, el visor de ayuda usará el paquete de marca de reserva ubicado en la raíz de la aplicación del visor de ayuda (Branding_en-US. mshc).

 **Requisitos del tema del visor de ayuda**

 Para que se representen correctamente en el visor de ayuda, el contenido del tema sin formato debe ser W3C Basic 1,1 XHTML.

 Normalmente, un tema contiene dos secciones:

- Metadatos (consulte referencia de metadatos de contenido): datos sobre el tema, por ejemplo, el identificador único del tema, el valor de la palabra clave, el identificador de TDC del tema, el identificador del nodo primario, etc.

- Contenido del cuerpo: compatible con W3C Basic 1,1 XHTML, que incluye los comportamientos de contenido admitidos (área contraíble, fragmento de código, etc.). A continuación se muestra una lista completa.

  Controles compatibles con el paquete de personalización de marca de Visual Studio:

- vínculos

- CodeSnippet

- CollapsibleArea

- Miembro heredado

- LanguageSpecificText

  Cadenas de idioma admitidas (no distinguen mayúsculas de minúsculas):

- javascript

- CSharp o c #

- CPlusPlus o VisualC + + o c++

- jscript

- VisualBasic o VB

- f # o FSharp o FS

- otro: una cadena que representa un nombre de idioma

  **Crear un tema del visor de ayuda**

  Cree un nuevo documento XHTML denominado ContosoTopic4. htm e incluya la etiqueta de título (a continuación).

```html
<html>
<head>
<title>Contoso Topic 4</title>
</head>

<body>

</body>
</html>

```

 A continuación, agregue datos para definir cómo debe presentarse el tema (con personalización de marca o no), cómo hacer referencia a este tema para F1, donde este tema existe en la TDC, su identificador (para la referencia de vínculo de otros temas), etc.  Vea la siguiente tabla de metadatos de contenido para obtener una lista completa de los metadatos admitidos.

- En este caso, usaremos nuestro propio paquete de personalización de marca, una variante del paquete de personalización de marca del visor de ayuda de Visual Studio.

- Agregue el valor y el nombre de metadatos de F1 ("Microsoft. help. F1" Content = "ContosoTopic4") que coincidirán con el valor F1 proporcionado en el contenedor de propiedades del IDE.  (Consulte la sección compatibilidad con F1 para obtener más información).   Este es el valor que se compara con la llamada F1 desde dentro del IDE para mostrar este tema cuando se elige F1 en el IDE.

- Agregue el identificador del tema. Esta es la cadena que usan otros temas para vincular a este tema.  Es el identificador del visor de ayuda de este tema.

- Para la TDC, agregue el nodo primario de este tema para definir dónde aparecerá este nodo TDC de este tema.

- Para la TDC, agregue el orden de los nodos de este tema. Cuando el nodo primario tenga n nodos secundarios, defina en el orden de los nodos secundarios la ubicación de este tema. Por ejemplo, este tema es el número 4 de 4 temas secundarios).

  Sección de metadatos de ejemplo:

```html
<html>
<head>
<title>Contoso Topic 4</title>

<meta name="SelfBranded" content="false" />
    <meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />
    <meta name="Microsoft.Help.Id" content="ContosoTopic4" />
<meta name="Microsoft.Help.F1" content=" ContosoTopic4" />
    <meta name="Language" content="en-us" />
<meta name="Microsoft.Help.TocParent" content="ContosoTopic0" />
<meta name="Microsoft.Help.TocOrder" content="4" />

</head>

<body>

</body>
</html>

```

 **El cuerpo del tema**

 El cuerpo (sin incluir el encabezado y el pie de página) del tema contendrá vínculos de página, una sección de notas, un área contraíble, un fragmento de código y una sección de texto específico del lenguaje.  Vea la sección de personalización de marca para obtener información acerca de las áreas del tema presentado.

1. Agregar una etiqueta de título de tema: `<div class="title">Contoso Topic 4</div>`

2. Agregar una sección de Nota: `<div class="alert"> add your table tag and text </div>`

3. Agregar un área contraíble: `<CollapsibleArea Expanded="1" Title="Collapsible Area Test Heading"> add text  </CollapsibleArea>`

4. Agregar un fragmento de código: `<CodeSnippet EnableCopyCode="true" Language="CSharp" ContainsMarkup="false" DisplayLanguage="C#" > a block of code </CodeSnippet>`

5. Agregar texto específico del lenguaje de código: `<LanguageSpecificText devLangcs="CS" devLangvb="VB" devLangcpp="C++" devLangnu="F#" />` tenga en cuenta que devLangnu = le permite escribir otros idiomas. Por ejemplo, devLangnu = "Fortran" mostrará Fortran cuando el fragmento de código DisplayLanguage = Fortran

6. Agregar vínculos de página: `<a href="ms-xhelp://?Id=ContosoTopic1">Main Topic</a>`

> [!NOTE]
> Nota: para la nueva coloración del código "display Language" ( F#ejemplo, Cobol, Fortran) no compatible en el fragmento de código, será monocromo.

 **Ejemplo de tema del visor de ayuda** El código muestra cómo definir metadatos, un fragmento de código, un área contraíble y un texto específico del lenguaje.

```
<?xml version="1.0" encoding="utf-8"?>
<html>
<head>
<title>Contoso Topic 4</title>

    <meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />
    <meta name="Microsoft.Help.Id" content="ContosoTopic4" />
<meta name="Microsoft.Help.F1" content=" ContosoTopic4" />
    <meta name="Language" content="en-us" />
<meta name="Microsoft.Help.TocParent" content="ContosoTopic0" />
<meta name="Microsoft.Help.TocOrder" content="4" />
<meta name="SelfBranded" content="false" />
</head>

<body>
<div class="title">Contoso Topic 4</div>

  <div id="header">
<table id="bottomTable" cellpadding="0" cellspacing="0"  width="100%">
        <tr id="headerTableRow2"><td align="left">
            <span id="nsrTitle">Contoso Topic 1</span>
          </td>
<td align="right">
</td></tr>
<tr id="headerTableRow1"><td align="left">
            <span id="runningHeaderText">Contoso Widgets & Sprockets</span>
          </td></tr>
      </table>
</div>

<h2>Table of Contents</h2>

<ul class="toc">
<li class="tocline1"><a href="#introduction" target="_self">1.0 Introduction</a></li>
<li class="tocline1"><a href="#seealso" target="_self">2.1 See Also</a></li>
</ul>

<div class="topic">

<div id="mainSection">
<div id="mainBody">

<a name="introduction"></a>
<h2>1.0 Introduction</h2>
<p>[This documentation is for sample purposes only.]</p>

<p>Contoso Topic 1 contains examples of:
<ul>
<li>Collapsible Area</li>
<li>Bookmark ("See also")</li>
<li>Code Snippets from Branding Package</li>
</ul>
 </p>
<div class="alert"><table><tr><th>
<strong>Note </strong></th></tr>
<tr><td>
<p>This is an example of a <span class="label">Note </span>section.
Call out important items for your reader in this <span class="label">Note </span>box.
</p></td></tr>
</table>
</div>
</div>

<CollapsibleArea Expanded="1" Title="Collapsible Area Test Heading">

            <a id="sectionToggle0"><!----></a>

<div>
Example of Collapsible Area
<br/>
Lorem ipsum dolor sit amet...
</div>
</CollapsibleArea>

<div id="snippetGroup" >
<CodeSnippet EnableCopyCode="true" Language="VisualBasic" ContainsMarkup="false" DisplayLanguage="Visual Basic" >
Private Sub ToolStripRenderer1_RenderGrip(sender as Object, e as ToolStripGripRenderEventArgs) _ Handles ToolStripRenderer1.RenderGrip
Dim messageBoxVB as New System.Text.StringBuilder()
    messageBoxVB.AppendFormat("{0} = {1}", "GripBounds", e.GripBounds)
    messageBoxVB.AppendLine()
 ...
    MessageBox.Show(messageBoxVB.ToString(),"RenderGrip Event")
End Sub
</CodeSnippet>

<CodeSnippet EnableCopyCode="true" Language="CSharp" ContainsMarkup="false" DisplayLanguage="C#" >
private void ToolStripRenderer1_RenderGrip(Object sender, ToolStripGripRenderEventArgs e)
{
System.Text.StringBuilder messageBoxCS = new System.Text.StringBuilder();
messageBoxCS.AppendFormat("{0} = {1}", "GripBounds", e.GripBounds );
messageBoxCS.AppendLine();
...
MessageBox.Show(messageBoxCS.ToString(), "RenderGrip Event" );
}
</CodeSnippet>

<CodeSnippet EnableCopyCode="true" Language="fsharp" ContainsMarkup="false" DisplayLanguage="F#" >
some F# code
</CodeSnippet>
</div>

<h4 class="subHeading">Example of code specific text</h4>Language = <LanguageSpecificText devLangcs="CS" devLangvb="VB" devLangcpp="C++" devLangnu="F#" />

<a name="seealso"></a>
<h1 class="heading">See Also</h1>

    <div id="seeAlsoSection" class="section">
    <div class="seeAlsoStyle">
        <a href="ms-xhelp://?Id=ContosoTopic1">Main Topic</a>
    </div>
 </div>
</div>
</div>
</body>
</html>

```

 **Compatibilidad con F1**

 En Visual Studio, al seleccionar F1 se generan los valores proporcionados a partir de la posición del cursor en el IDE y se rellena un "contenedor de propiedades" con los valores proporcionados (basados en la ubicación del cursor). Cuando el cursor está sobre la característica x, la característica x está activa/en el foco y rellena el contenedor de propiedades con valores.  Cuando se selecciona F1, el contenedor de propiedades se rellena y el código F1 de Visual Studio comprueba si el origen de la ayuda predeterminada de los clientes es local o está en línea (el valor predeterminado es online). a continuación, crea la cadena adecuada en función de la configuración de los usuarios (online es el valor predeterminado): Shell Execute (consulte la guía del administrador de la ayuda de los parámetros de inicio de exe) con parámetros para el visor de ayuda local + palabras clave de la bolsa de propiedades si la ayuda local es el valor predeterminado, o la dirección URL de MSDN con la palabra clave en la lista de parámetros.

 Si se devuelven tres cadenas para F1, a las que se hace referencia como una cadena de varios valores, se toma el primer término, se busca un acierto y, si se encuentra, se hace. Si no es así, desplácese a la cadena siguiente.  El orden es importante. La presentación de las palabras clave de varios valores debe ser una cadena más larga que la cadena más corta.  Para comprobarlo en el caso de palabras clave de varios valores, consulte la cadena de dirección URL F1 en línea, que incluirá la palabra clave elegida.

 En Visual Studio 2012, hemos realizado una división más fuerte entre Internet y sin conexión, de modo que si la configuración del usuario fuera para línea, simplemente pasaremos la solicitud de F1 directamente a nuestro servicio de consultas en línea en MSDN en lugar de enrutarse a través del agente de biblioteca de ayuda que teníamos en Visual Studio 2010. A continuación, confiamos en un estado de "contenido del proveedor instalado = true" para determinar si realizar algo diferente en ese contexto. Si es true, se realizará este análisis y la lógica de enrutamiento en función de lo que desee dar soporte a sus clientes. Si es false, simplemente vamos a MSDN. Si la configuración del usuario es local, todas las llamadas van al motor de ayuda local.

 Diagrama de flujo de F1:

 ![Flujo de F1](../../extensibility/internals/media/f1flow.png "F1flow")

 Cuando el origen de contenido de ayuda predeterminado del visor de ayuda se establece en online (inicio en el explorador):

- Las características de asociado de Visual Studio (VSP) emiten un valor a la bolsa de propiedades de F1 (Prefijo de contenedor de propiedades. palabra clave y dirección URL en línea para el prefijo encontrado en el registro): F1 envía una dirección URL de VSP + parámetros al explorador.

- Características de Visual Studio (editor de lenguaje, elementos de menú específicos de Visual Studio, etc.): F1 envía una dirección URL de Visual Studio al explorador.

  Cuando el origen de contenido de ayuda predeterminada del visor de ayuda está establecido en ayuda local (iniciar en el visor de ayuda):

- Características de VSP en las que la palabra clave coincide entre el contenedor de propiedades F1 y el índice de almacén local (es decir, el contenedor de propiedades prefix. keyword = el valor que se encuentra en el índice del almacén local): F1 representa el tema en el visor de ayuda.

- Características de Visual Studio (no hay ninguna opción para que el VSP invalide el contenedor de propiedades emitido desde las características de Visual Studio): F1 representa un tema de Visual Studio en el visor de ayuda.

  Establezca los siguientes valores del registro para habilitar la reserva de F1 para el contenido de ayuda del proveedor. La reserva de F1 significa que el visor de ayuda está configurado para buscar el contenido de la ayuda F1 en línea y el contenido del proveedor se instala localmente en el disco duro de los usuarios. El visor de ayuda debe buscar el contenido en la ayuda local, aunque la configuración predeterminada sea para la ayuda en línea.

1. Establezca el valor **VendorContent** en la clave del registro Help 2,1:

   - Para sistemas operativos de 32 bits:

        HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Help\v2.1\Catalogs\VisualStudio12

        "VendorContent" = dword: 00000001

   - Para sistemas operativos de 64 bits:

        HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Help\v2.1\Catalogs\VisualStudio12

        "VendorContent" = dword: 00000001

2. Registre el espacio de nombres del asociado en la clave del registro Help 2,1:

   - Para sistemas operativos de 32 bits:

      HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Help\v2.1\Partner<em>\\<namespace\></em>

      "ubicación" = "sin conexión"

   - Para sistemas operativos de 64 bits:

      HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Help\v2.1\Partner<em>\\<namespace\></em>

      "ubicación" = "sin conexión"

   **Análisis del espacio de nombres nativo base**

   Para activar el análisis de un espacio de nombres nativo base, en el registro agregue un nuevo valor DWORD con el nombre de: BaseNativeNamespaces y establezca su valor en 1 (en la clave de catálogo que desea admitir).  Por ejemplo, si desea utilizar el catálogo de Visual Studio, puede Agregar la clave a la ruta de acceso:

   HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Help\v2.1\Catalogs\VisualStudio12

   Cuando se encuentra una palabra clave de F1 en el encabezado o el método de formato, se analiza el carácter '/', lo que da como resultado la construcción siguiente:

- ENCABEZADO: será el espacio de nombres que se puede usar para registrar en el registro.

- MÉTODO: se convertirá en la palabra clave que se pasa.

  Por ejemplo, dada una biblioteca personalizada denominada CustomLibrary y un método denominado MyTestMethod, cuando llega una solicitud F1, se le da formato como `CustomLibrary/MyTestMethod`.

  Después, un usuario puede registrar CustomLibrary como el espacio de nombres en el subárbol de asociados y proporcionar cualquier clave de ubicación que deseen, y la palabra clave pasada a la consulta será MyTestMethod.

  **Habilitar la herramienta de depuración de la ayuda en el IDE**

  Agregue la siguiente clave y valor del registro:

  HKEY_CURRENT_USER tecla de ayuda de \Software\Microsoft\VisualStudio\12.0\Dynamic: muestra la salida de depuración en valor comercial: sí

  En el IDE, en el elemento de menú ayuda, seleccione "contexto de ayuda de depuración".

  **Metadatos de contenido**

  En la tabla siguiente, cualquier cadena que aparezca entre corchetes es un marcador de posición que se debe reemplazar por un valor reconocido. Por ejemplo, en \<meta name = "Microsoft. help. locale" Content = "[code Language]"/>, "[language code]" debe reemplazarse por un valor como "en-US".

|Property (representación HTML)|Descripción|
|--------------------------------------|-----------------|
|\< meta name = "Microsoft. help. locale" Content = "[language-code]"/>|Establece una configuración regional para este tema. Si esta etiqueta se usa en un tema, debe usarse una sola vez y debe insertarse encima de cualquier otra etiqueta de ayuda de Microsoft. Si no se utiliza esta etiqueta, el texto del cuerpo del tema se indexa mediante el separador de palabras que está asociado a la configuración regional del producto, si se especifica; de lo contrario, se usa el separador de palabras en-US. Esta etiqueta se ajusta a ISOC RFC 4646. Para asegurarse de que la ayuda de Microsoft funciona correctamente, use esta propiedad en lugar del atributo de lenguaje general.|
|\< meta name = "Microsoft. help. TopicLocale" Content = "[language-code]"/>|Establece una configuración regional para este tema cuando también se usan otras configuraciones regionales. Si esta etiqueta se usa en un tema, debe usarse una sola vez. Use esta etiqueta cuando el catálogo contenga contenido en más de un idioma. Varios temas de un catálogo pueden tener el mismo identificador, pero cada uno debe especificar un TopicLocale único. El tema que especifica un TopicLocale que coincide con la configuración regional del catálogo es el tema que se muestra en la tabla de contenido. Sin embargo, todas las versiones de idioma del tema se muestran en los resultados de la búsqueda.|
|\< título > [título]\</title >|Especifica el título de este tema. Esta etiqueta es obligatoria y debe usarse una sola vez en un tema. Si el cuerpo del tema no contiene una sección de título \<div >, este título se muestra en el tema y en la tabla de contenido.|
|\< meta name = "Microsoft. help. keywords" Content = "[aKeywordPhrase]"/>|Especifica el texto de un vínculo que se muestra en el panel Índice del visor de ayuda. Cuando se hace clic en el vínculo, se muestra el tema. Puede especificar varias palabras clave de índice para un tema, o puede omitir esta etiqueta si no desea que los vínculos a este tema aparezcan en el índice. Las palabras clave "K" de las versiones anteriores de la ayuda se pueden convertir en esta propiedad.|
|\< meta name = "Microsoft. help. ID" Content = "[TopicID]"/>|Establece el identificador de este tema. Esta etiqueta es obligatoria y debe usarse una sola vez en un tema. El identificador debe ser único entre los temas del catálogo que tienen la misma configuración regional. En otro tema, puede crear un vínculo a este tema con este identificador.|
|\< meta name = "Microsoft. help. F1" Content = "[System. Windows. Controls. Primitives. IRecyclingItemContainerGenerator]"/>|Especifica la palabra clave F1 para este tema. Puede especificar varias palabras clave de F1 para un tema, o puede omitir esta etiqueta si no desea que se muestre este tema cuando un usuario de la aplicación Presione F1. Normalmente, solo se especifica una palabra clave F1 para un tema. Las palabras clave "F" de las versiones anteriores de la ayuda se pueden convertir en esta propiedad.|
|\< meta name = "Description" Content = "[Descripción del tema]"/>|Proporciona un breve resumen del contenido de este tema. Si esta etiqueta se usa en un tema, debe usarse una sola vez. La biblioteca de consultas accede a esta propiedad directamente. no se almacena en el archivo de índice.|
 meta name = "Microsoft. help. TocParent" Content = "[parent_Id]"/>|Especifica el tema primario de este tema en la tabla de contenido. Esta etiqueta es obligatoria y debe usarse una sola vez en un tema. El valor es el Microsoft.Help.Id del elemento primario. Un tema solo puede tener una ubicación en la tabla de contenido. "-1" se considera el identificador del tema para la raíz de la TDC. En [!INCLUDE[vs_dev12](../../includes/vs-dev12-md.md)], esa página es la Página principal del visor de ayuda. Esta es la misma razón por la que se agrega TocParent =-1 a algunos temas para asegurarse de que se muestran en el nivel superior. La Página principal del visor de ayuda es una página del sistema y, por tanto, no reemplazable. Si un VSP intenta agregar una página con un identificador de-1, es posible que se agregue al conjunto de contenido, pero el visor de ayuda siempre usará la página del sistema-Página principal del visor de ayuda.|
|\< meta name = "Microsoft. help. TocOrder" Content = "[entero positivo]"/>|Especifica en qué lugar de la tabla de contenido este tema aparece en relación con sus temas del mismo nivel. Esta etiqueta es obligatoria y debe usarse una sola vez en un tema. El valor es un entero. Un tema que especifica un entero de valor inferior aparece sobre un tema que especifica un entero de valor superior.|
|\< meta name = "Microsoft. help. Product" Content = "[code product]"/>|Especifica el producto que se describe en este tema. Si esta etiqueta se usa en un tema, debe usarse una sola vez. Esta información también se puede proporcionar como un parámetro que se pasa al indizador de la ayuda.|
|\< meta name = "Microsoft. help. ProductVersion" Content = "[número de versión]"/>|Especifica la versión del producto que se describe en este tema. Si esta etiqueta se usa en un tema, debe usarse una sola vez. Esta información también se puede proporcionar como un parámetro que se pasa al indizador de la ayuda.|
|\< meta name = "Microsoft. help. Category" Content = "[cadena]"/>|Lo utilizan los productos para identificar subsecciones de contenido. Puede identificar varias subsecciones para un tema, o puede omitir esta etiqueta si no desea que los vínculos identifiquen las subsecciones. Esta etiqueta se utiliza para almacenar los atributos de los destinos y TargetFrameworkMoniker cuando se convierte un tema de una versión anterior de la ayuda. El formato del contenido es AttributeName: AttributeValue.|
|\< meta name = "Microsoft. help. TopicVersion Content =" [número de versión del tema] "/>|Especifica esta versión del tema cuando existen varias versiones en un catálogo. Como no se garantiza que Microsoft.Help.Id sea único, esta etiqueta es necesaria cuando existe más de una versión de un tema en un catálogo, por ejemplo, cuando un catálogo contiene un tema para el .NET Framework 3,5 y un tema para el .NET Framework 4 y ambos tienen el mismo micro blando. Help.Id.|
|\< meta name = "SelfBranded" Content = "[TRUE o FALSE]"/>|Especifica si este tema usa el paquete de personalización de marca de inicio del administrador de bibliotecas de ayuda o un paquete de personalización de marca específico del tema. Esta etiqueta debe ser TRUE o FALSE. Si es TRUE, el paquete de personalización de marca del tema asociado invalida el paquete de personalización de marca que se establece cuando se inicia el administrador de bibliotecas de ayuda, de modo que el tema se represente de la manera prevista, incluso si difiere de la representación de otro contenido. Si es FALSE, el tema actual se representa según el paquete de personalización de marca que se establece cuando se inicia el administrador de bibliotecas de ayuda. De forma predeterminada, el administrador de bibliotecas de ayuda supone que la automarca es falsa, a menos que la variable SelfBranded se declare como TRUE. por lo tanto, no tiene que declarar \<meta name = "SelfBranded" Content = "FALSE"/>.|

### <a name="creating-a-branding-package"></a>Creación de un paquete de personalización de marca
 La versión de Visual Studio incluye una serie de distintos productos de Visual Studio, incluidos los shells aislados e integrados para los asociados de Visual Studio.  Cada uno de estos productos requiere cierto grado de compatibilidad con la personalización de marca del contenido de la ayuda basada en temas, exclusiva para el producto.  Por ejemplo, los temas de Visual Studio deben tener una presentación de marca coherente, mientras que SQL Studio, que incluye el shell ISO, requiere su propia personalización de marca de contenido de ayuda para cada tema.  Es posible que un asociado de Shell integrado quiera que sus temas de ayuda estén dentro del contenido de la ayuda del producto primario de Visual Studio, a la vez que mantiene su propia personalización de marca de tema.

 El producto que contiene el visor de ayuda instala los paquetes de personalización de marca.  Para productos de Visual Studio:

- El paquete de idioma del visor de ayuda incluye un paquete de personalización de marca de reserva (Branding_\<configuración regional >. mshc) en el visor de ayuda 2,1 raíz de la aplicación (por ejemplo: C:\Archivos de programa (x86) \Microsoft Help Viewer\v2.1).  Se utiliza para los casos en los que el paquete de personalización de marca de producto no está instalado (no se ha instalado ningún contenido) o donde el paquete de marca instalado está dañado.  Los elementos de Visual Studio (logotipo y comentarios) se omiten cuando se usa el paquete de personalización de marca de reserva de la aplicación.

- Cuando el contenido de Visual Studio se instala desde el servicio de paquete de contenido, también se instala un paquete de personalización de marca (por primera vez en el escenario de instalación de contenido).  Si hay una actualización del paquete de personalización de marca, la actualización se instalará cuando se produzca la siguiente actualización de contenido o la acción de instalación del paquete adicional.

  El Visor de Ayuda de Microsoft admite la personalización de marca de temas basados en los metadatos del tema.

- Cuando los metadatos del tema definen la personalización de marca = true, representan el tema tal cual, no hacen nada (en lo que se refiere a la personalización de marca).

- Donde metadatos de tema define la personalización de marca = false, use el paquete de personalización de marca asociado con el valor de metadatos TopicVendor.

- Donde los metadatos del tema definen name = "Microsoft. help. TopicVendor" Content =\< nombre del paquete de personalización de marca en el > del proveedor, use el paquete de personalización de marca definido en el valor de contenido.

- En el catálogo de Visual Studio, hay una aplicación prioritaria de los paquetes de personalización de marca.  La primera marca predeterminada de Visual Studio se aplica y, a continuación, si se define en el tema metadatos y se admite con el paquete de personalización de marca asociado (como se define en el MSHA de instalación), la personalización de marca definida por el proveedor se aplica como una invalidación.

  Normalmente, los elementos de personalización de marca se dividen en tres categorías principales:

- Elementos de encabezado (ejemplos: vínculo de comentarios, texto de declinación de responsabilidades condicional, logotipo)

- Comportamientos de contenido (algunos ejemplos incluyen elementos de texto de control de expansión/contracción y elementos de fragmento de código)

- Elementos de pie de página (por ejemplo, copyright)

  Los elementos considerados como elementos de marca incluyen (se detalla en esta especificación):

- Logotipo de catálogo/producto (ejemplo, Visual Studio)

- Vínculo de comentarios y elementos de correo electrónico

- Texto de declinación de responsabilidades

- Texto de copyright

  Los archivos auxiliares en el paquete de personalización de marca del visor de ayuda de Visual Studio incluyen:

- Gráficos (logotipos, iconos, etc.)

- Branding. js: archivos de script que admiten comportamientos de contenido

- Branding. xml: cadenas que se usan de forma coherente en todo el contenido del catálogo.  Nota: para los elementos de texto de localización de Visual Studio en la personalización de marca. XML, incluya _locID = "\<valor único >"

- Personalización de marca. CSS: definiciones de estilo para la coherencia de la presentación

- Imprimir. CSS: definiciones de estilo para una presentación impresa coherente

  Como se indicó anteriormente, los paquetes de personalización de marca están asociados al tema:

- Cuando SelfBranded = false se define en los metadatos, el tema hereda el paquete de personalización de marca del catálogo

- O cuando SelfBranded = false y hay un paquete de personalización de marca único definido en MSHA y disponible cuando se instala el contenido

  En el caso de VSPs que implementa paquetes de marca personalizada (contenido VSP, SelfBranded = true), una manera de proceder es comenzar con el paquete de marca de reserva (instalado con el visor de ayuda) y cambiar el nombre del archivo según corresponda.  La Branding_\<configuración regional > archivo. mshc es un archivo zip con la extensión de archivo cambiada a. mshc, por lo que solo tiene que cambiar la extensión de. mshc a. zip y extraer el contenido.  Consulte a continuación los elementos del paquete de personalización de marca y modifíquelo según corresponda (por ejemplo, cambie el logotipo al logotipo de VSP y la referencia al logotipo en el archivo de personalización de marca. XML, actualice la marca. XML por las características de VSP, etc.).

  Cuando se hayan realizado todas las modificaciones, cree un archivo zip que contenga los elementos de personalización de marca que desee y cambie la extensión a. mshc.

  Para asociar el paquete de personalización de marca personalizada, cree MSHA, que contiene la referencia al archivo de personalización de marca mshc junto con el contenido mshc (que contiene los temas).  Vea a continuación "MSHA" para obtener más datos sobre cómo crear un MSHA básico.

  El archivo branding. xml contiene un elemento de lista que se usa para representar de forma coherente los elementos específicos de un tema cuando el tema contiene \<meta name = "Microsoft. help. SelfBranded" Content = "false"/>.  A continuación se muestra la lista de elementos de Visual Studio en el archivo branding. Xml.  Esta lista está pensada para usarse como plantilla para los adoptadores de Shell ISO, donde modifican estos elementos (por ejemplo, el logotipo, los comentarios y el copyright) para satisfacer sus propias necesidades de personalización de marca del producto.

  Nota: las variables indicadas por "{n}" tienen dependencias de código; si se quitan o se cambian estos valores, se producirán errores y posiblemente se bloqueará la aplicación. Los identificadores de localización (ejemplo _locID = "CodeSnippet. n") se incluyen en el paquete de personalización de marca de Visual Studio.

  **Branding.xml**

|||
|-|-|
|Característica:|**CollapsibleArea**|
|Use:|Expandir contrae el texto del control de contenido|
|**Element**|**Valor**|
|ExpandText|Expandir|
|CollapseText|Contraer|
|Característica:|**CodeSnippet**|
|Use:|Texto del control del fragmento de código.  Nota: el contenido del fragmento de código con espacio "no problemático" se cambiará a espacio.|
|**Element**|**Valor**|
|CopyToClipboard|Copiar en el Portapapeles|
|ViewColorizedText|Ver texto coloreado|
|CombinedVBTabDisplayLanguage|Visual Basic (ejemplo)|
|VBDeclaration|Declaración|
|VBUsage|Usage|
|Característica:|**Comentarios, pies de página y logotipo**|
|Use:|Proporcionar un control de comentarios para que el cliente proporcione comentarios sobre el tema actual por correo electrónico.  Texto de copyright para el contenido.  Definición del logotipo.|
|**Element**|**Valor (estas cadenas se pueden modificar para satisfacer la necesidad de que el contenido adopte).**|
|SSoftware|© 2013 Microsoft Corporation. Reservados todos los derechos.|
|SendFeedback|\<a href = "{0}" {1}> Enviar comentarios\</a > de este tema a Microsoft.|
|FeedbackLink||
|LogoTitle|[!INCLUDE[vs_dev12](../../includes/vs-dev12-md.md)]|
|LogoFileName|vs_logo_bk.gif|
|LogoFileNameHC|vs_logo_wh.gif|
|Característica:|**Declinación de responsabilidades**|
|Use:|Conjunto de notificaciones de declinación de mayúsculas y minúsculas para el contenido traducido de la máquina.|
|**Element**|**Valor**|
|MT_Editable|Este artículo se ha traducido a la máquina. Si tiene una conexión a Internet, seleccione "ver este tema en línea" para ver esta página en modo editable con el contenido original en inglés al mismo tiempo.|
|MT_NonEditable|Este artículo se ha traducido a la máquina. Si tiene una conexión a Internet, seleccione "ver este tema en línea" para ver esta página en modo editable con el contenido original en inglés al mismo tiempo.|
|MT_QualityEditable|Este artículo se tradujo manualmente. Si tiene una conexión a Internet, seleccione "ver este tema en línea" para ver esta página en modo editable con el contenido original en inglés al mismo tiempo.|
|MT_QualityNonEditable|Este artículo se tradujo manualmente. Si tiene una conexión a Internet, seleccione "ver este tema en línea" para ver esta página en modo editable con el contenido original en inglés al mismo tiempo.|
|MT_BetaContents|En este artículo se ha traducido el equipo para una versión preliminar. Si tiene una conexión a Internet, seleccione "ver este tema en línea" para ver esta página en modo editable con el contenido original en inglés al mismo tiempo.|
|MT_BetaRecycledContents|Este artículo se tradujo manualmente para una versión preliminar. Si tiene una conexión a Internet, seleccione "ver este tema en línea" para ver esta página en modo editable con el contenido original en inglés al mismo tiempo.|
|Característica:|**LinkTable**|
|Use:|Compatibilidad con vínculos de temas en línea|
|**Element**|**Valor**|
|LinkTableTitle|Vincular tabla|
|TopicEnuLinkText|Vea la versión inglesa\</a > de este tema que está disponible en el equipo.|
|TopicOnlineLinkText|Vea este tema \<a href = "{0}" {1}> en línea\</a >|
|OnlineText|Online|
|Característica:|**Control de audio de vídeo**|
|Use:|Mostrar elementos y texto para el contenido de vídeo|
|**Element**|**Valor**|
|MultiMediaNotSupported|Se debe instalar Internet Explorer 9 o posterior para admitir {0} contenido.|
|VideoText|Mostrar vídeo|
|AudioText|transmisión por secuencias de audio|
|OnlineVideoLinkText|\<p > para ver el vídeo asociado a este tema, haga clic en {0}\<a href = "{1}" >{2}\</a >.\</p >|
|OnlineAudioLinkText|\<p > para escuchar el audio asociado a este tema, haga clic en {0}\<a href = "{1}" >{2}\</a >.\</p >|
|Característica:|**Control contenido no instalado**|
|Use:|Elementos de texto (cadenas) utilizados para la representación de contentnotinstalled. htm|
|**Element**|**Valor**|
|ContentNotInstalledTitle|No se encontró contenido en el equipo.|
|ContentNotInstalledDownloadContentText|\<p > para descargar contenido en el equipo \<a href = "{0}" {1}haga clic en la pestaña administrar >/a\<.\</p >|
|ContentNotInstalledText|\<p > no hay ningún contenido instalado en el equipo. Consulte a su administrador para la instalación del contenido de la ayuda local.\</p >|
|Característica:|**Control de tema no encontrado**|
|Use:|Elementos de texto (cadenas) utilizados para la representación de topicnotfound. htm|
|**Element**|**Valor**|
|TopicNotFoundTitle|No se encuentra el tema solicitado en el equipo.|
|TopicNotFoundViewOnlineText|\<p > el tema que solicitó no se encontró en el equipo, pero puede \<a href = "{0}" {1}> ver el tema en línea\</a >.\</p >|
|TopicNotFoundDownloadContentText|\<p > vea el panel de navegación para obtener vínculos a temas similares o \<a href = "{0}" {1}> haga clic en la pestaña administrar\</a > para descargar contenido en el equipo.\</p >|
|TopicNotFoundText|\<p > el tema que solicitó no se encontró en el equipo.\</p >|
|Característica:|**Control dañado de tema**|
|Use:|Elementos de texto (cadenas) utilizados para la representación de topiccorrupted. htm|
|**Element**|**Valor**|
|TopicCorruptedTitle|No se puede mostrar el tema solicitado.|
|TopicCorruptedViewOnlineText|\<p > visor de ayuda no puede mostrar el tema solicitado. Puede haber un error en el contenido del tema o en una dependencia del sistema subyacente.\</p >|
|Característica:|**Control de página principal**|
|Use:|Texto que admite la visualización del contenido del nodo de nivel superior del visor de ayuda.|
|**Element**|**Valor**|
|HomePageTitle|Página principal del visor de ayuda|
|HomePageIntroduction|\<p > la Visor de Ayuda de Microsoft, una fuente esencial de información para todos los usuarios que usan herramientas, productos, tecnologías y servicios de Microsoft. El visor de ayuda le proporciona acceso a información de procedimientos y de referencia, código de ejemplo, artículos técnicos, etc. Para encontrar el contenido que necesita, examine la tabla de contenido, use la búsqueda de texto completo o navegue por el contenido con el índice de palabras clave.\</p >|
|HomePageContentInstallText|\<p >\<br/> Use la \<pestaña a href = "{0}" {1}> administrar contenido\</a > para hacer lo siguiente:\<UL >\<li > agregar contenido al equipo.\</li >\<li > buscar actualizaciones en el contenido local.\</li >\<li > quitar contenido del equipo.\</li >\</UL >\</p >|
|HomePageInstalledBooks|Libros instalados|
|HomePageNoBooksInstalled|No se encontró contenido en el equipo.|
|HomePageHelpSettings|Configuración del contenido de la ayuda|
|HomePageHelpSettingsText|\<p > la configuración actual es la ayuda local. El visor de ayuda muestra el contenido que ha instalado en el equipo.\<br/> para cambiar el origen del contenido de la ayuda, en la barra de menús de Visual Studio, elija \<span style = "{0}" > ayuda, establecer preferencias de la ayuda\</span >.\<br/>\</p >|
|MegaByte|MB|

 **branding.js**

 El archivo branding. js contiene JavaScript que usan los elementos de personalización de marca del visor de ayuda de Visual Studio.  A continuación se muestra una lista de los elementos de personalización de marca y la función de JavaScript auxiliar.  Todas las cadenas que se van a localizar para este archivo se definen en la sección "cadenas localizables" en la parte superior de este archivo.  El archivo ICL se ha creado para las cadenas de ubicación dentro del archivo branding. js.

||||
|-|-|-|
|**Característica de personalización de marca**|**Función de JavaScript**|**Descripción**|
|Var...||Definición de variables|
|Obtención del idioma del código de usuario|setUserPreferenceLang|asigna un índice # al lenguaje de código|
|Establecer y obtener valores de cookie|getCookie, setCookie||
|Miembro heredado|changeMembersLabel|Expandir o contraer miembro heredado|
|Cuando SelfBranded = false|onLoad|Lea la cadena de consulta para comprobar si se trata de una solicitud de impresión.  Establezca todas las codesnippets para que se centren en la pestaña preferida del usuario.  Si se trata de una solicitud de impresión, establezca isPrinterFriendly en true. Compruebe el modo de contraste alto.|
|Fragmento de código|addSpecificTextLanguageTagSet||
||getIndexFromDevLang||
||ChangeTab||
||setCodesnippetLang||
||setCurrentLang||
||CopyToClipboard||
|CollapsibleArea|addToCollapsibleControlSet|Escriba todo el objeto de control contraíble en la lista.|
||CA_Click|en función del estado del área contraíble, define la imagen y el texto que se van a presentar.|
|Contraste de la compatibilidad con el logotipo|isBlackBackground()|Se llama para determinar si el fondo es negro.  Solo es preciso en el modo de contraste alto.|
||isHighContrast()|usar un intervalo de colores para detectar el modo de contraste alto|
||onHighContrast (negro)|Se llama cuando se detecta un contraste alto|
|Funcionalidad LST|||
||addToLanSpecTextIdSet(id)||
||updateLST(currentLang)||
||getDevLangFromCodeSnippet(lang)||
|Funcionalidad MultiMedia|título (Inicio, fin, texto, estilo)||
||findAllMediaControls(normalizedId)||
||getActivePlayer(normalizedId)||
||captionsOnOff(id)||
||toSeconds (t)||
||getAllComments (nodo)||
||styleRectify (styleName, styleValue)||
||showCC (ID.)||
||subtítulo (ID.)||

 **ARCHIVOS HTM**

 El paquete de personalización de marca contiene un conjunto de archivos HTM que admiten escenarios para la comunicación de información clave para ayudar a los usuarios de contenido, por ejemplo, una página principal que contiene una sección que describe qué conjuntos de contenido están instalados y páginas que indican al usuario Cuándo no pueden se encuentra en el conjunto local de temas. Estos archivos HTM se pueden modificar por producto.  Los proveedores de Shell ISO pueden tomar el paquete de personalización de marca predeterminado y cambiar el comportamiento y el contenido de estas páginas para adaptarse a sus necesidades.  Estos archivos hacen referencia a su correspondiente paquete de personalización de marca con el fin de que las etiquetas de personalización de marca obtengan el contenido correspondiente del archivo de personalización de marca. Xml.

||||
|-|-|-|
|**Archivo**|**Uso**|**Origen de contenido mostrado**|
|homepage.htm|Se trata de una página que muestra contenido instalado actualmente, así como cualquier otro mensaje adecuado para presentar al usuario sobre su contenido.  Este archivo tiene el atributo de metadatos adicional "Microsoft.Help.Id" Content = "-1", que coloca este contenido en la parte superior de la TDC del contenido local.||
||<META_HOME_PAGE_TITLE_ADD />|Branding. XML, Tag \<HomePageTitle >|
||HOME_PAGE_INTRODUCTION_SECTION_ADD de </>|Branding. XML, Tag \<HomePageIntroduction >|
||<HOME_PAGE_CONTENT_INSTALL_SECTION_ADD />|Branding. XML, Tag \<HomePageContentInstallText >|
||<HOME_PAGE_BOOKS_INSTALLED_SECTION_ADD />|Título de la sección de encabezado. XML de la etiqueta\<HomePageInstalledBooks >, los datos generados desde la aplicación \<HomePageNoBooksInstalled > cuando no hay ningún libro instalado.|
||<HOME_PAGE_SETTINGS_SECTION_ADD />|Encabezado de la sección branding. XML \<HomePageHelpSettings >, texto de sección \<HomePageHelpSettingsText >.|
|topiccorrupted. htm|Cuando existe un tema en el conjunto local, pero por alguna razón no se puede mostrar (contenido dañado).||
||<META_TOPIC_CORRUPTED_TITLE_ADD />|Branding. XML, Tag \<TopicCorruptedTitle >|
||<TOPIC_CORRUPTED_SECTION_ADD />|Branding. XML, Tag \<TopicCorruptedViewOnlineText >|
|topicnotfound. htm|Cuando no se encuentra un tema en el conjunto de contenido local, ni disponible en línea||
||<META_TOPIC_NOT_FOUND_TITLE_ADD />|Branding. XML, Tag \<TopicNotFoundTitle >|
||META_TOPIC_NOT_FOUND_ID_ADD de </>|Branding. XML, Tag \<TopicNotFoundViewOnlineText > + \<TopicNotFoundDownloadContentText >|
||<TOPIC_NOT_FOUND_SECTION_ADD />|Branding. XML, Tag \<TopicNotFoundText >|
|contentnotinstalled. htm|Cuando no hay ningún contenido local instalado para el producto.||
||<META_CONTENT_NOT_INSTALLED_TITLE_ADD />|Branding. XML, Tag \<ContentNotInstalledTitle >|
||<META_CONTENT_NOT_INSTALLED_ID_ADD />|Branding. XML, Tag \<ContentNotInstalledDownloadContentText >|
||<CONTENT_NOT_INSTALLED_SECTION_ADD />|Branding. XML, Tag \<ContentNotInstalledText >|

 **Archivos CSS**

 El paquete de personalización de marca del visor de ayuda de Visual Studio contiene dos archivos CSS para admitir la presentación de contenido de ayuda de Visual Studio coherente:

- Branding. CSS: contiene elementos CSS para la representación donde SelfBranded = false

- Printer. CSS: contiene elementos CSS para la representación donde SelfBranded = false

  Los archivos de personalización de marca. CSS incluyen definiciones para la presentación de temas de Visual Studio (tenga en cuenta que la personalización de marca. CSS contenida en el Branding_\<configuración regional >. mshc del servicio de paquete puede cambiar).

  **Archivos gráficos**

  Contenido de Visual Studio muestra un logotipo de Visual Studio, así como otros gráficos.  A continuación se muestra la lista completa de archivos gráficos en el paquete de personalización de marca del visor de ayuda de Visual Studio.

||||
|-|-|-|
|**Archivo**|**Uso**|**Ejemplos**|
|borrar. gif|Se usa para representar el área contraíble||
|footer_slice.gif|Presentación de pie de página||
|info_icon. gif|Se usa al Mostrar información|Declinación de responsabilidades|
|online_icon.gif|Este icono se asociará a vínculos en línea||
|tabLeftBD.gif|Se usa para representar el contenedor de fragmentos de código||
|tabRightBD. gif|Se usa para representar el contenedor de fragmentos de código||
|vs_logo_bk.gif|Se usa para las referencias de logotipo de contraste normales según se define en la etiqueta Branding. XML \<LogoFileName >.  En el caso de los productos de Visual Studio, el nombre del logotipo es vs_logo_bk. gif.||
|vs_logo_wh.gif|Se usa para las referencias de logotipo alto normales según se define en la etiqueta Branding. XML \<LogoFileNameHC >.  En el caso de los productos de Visual Studio, el nombre del logotipo es vs_logo_wh. gif.||
|ccOff. png|Gráfico de subtítulos||
|ccOn. png|Gráfico de subtítulos||
|ImageSprite.png|Se usa para representar el área contraíble|gráfico expandido o contraído|

### <a name="deploying-a-set-of-topics"></a>Implementación de un conjunto de temas
 Este es un tutorial sencillo y rápido para crear un conjunto de implementación de contenido del visor de ayuda compuesto por un archivo MSHA y el conjunto de archivos. cab o MSHCs que contiene los temas. MSHA es un archivo XML que describe un conjunto de archivos. cab o de MSHC. El visor de ayuda puede leer el MSHA para obtener una lista de contenido (. CAB o. Archivos de MSHC) disponibles para la instalación local.

 Este es solo un manual que describe el esquema XML muy básico para el visor de ayuda MSHA.  Hay una implementación de ejemplo por debajo de esta breve introducción y el ejemplo de archivos helpcontentsetup. MSHA.

 El nombre del MSHA, para los fines de este manual, es archivos helpcontentsetup. MSHA (el nombre del archivo puede ser cualquier cosa, con la extensión. MSHA). Archivos helpcontentsetup. MSHA (ejemplo siguiente) debe contener una lista de los CAB o MSHCs disponibles.  El tipo de archivo debe ser coherente dentro de MSHA (no admite una combinación de tipos de archivo MSHA y CAB). Para cada archivo. CAB o MSHC, debe haber una \<div class = "Package" >...\</div > (vea el ejemplo siguiente).

 Nota: en el ejemplo de implementación siguiente, hemos incluido el paquete de personalización de marca. Es fundamental incluir para obtener los elementos de representación de contenido de Visual Studio necesarios y los comportamientos de contenido.

 Archivo archivos helpcontentsetup. MSHA de ejemplo: (reemplace "nombre del conjunto de contenido 1" y "nombre del conjunto de contenido 2", etc. por los nombres de archivo).

```
<html>
<head />
<body class="vendor-book">
<div class="details">
<span class="vendor">Your Company</span>
<span class="locale">en-us</span>
<span class="product">Your Company Help Content</span>
<span class="name">Your Company Help Content</span>
</div>
<div class="package-list">
<div class="package">
<span class="name">Your_Company _Content_Set_1</span>
<span class="deployed">True</span>
<a class="current-link" href="Your_Company _Content_Set_1.mshc">Your_Company _Content_Set_1.mshc </a>
</div>
<div class="package">
<span class="name">Your_Company _Content_Set_2</span>
<span class="deployed">True</span>
<a class="current-link"href=" Your_Company _Content_Set_2.mshc "> Your_Company _Content_Set_2.mshc </a>
</div>.

```

1. Cree una carpeta local, algo como "C:\SampleContent".

2. En este ejemplo, usaremos archivos MSHC para contener los temas.  Un MSHC es un archivo zip con la extensión de archivo modificada de. zip a. MSHC.

3. Cree el siguiente archivos helpcontentsetup. MSHA como archivo de texto (se usó el Bloc de notas para crear el archivo) y guárdelo en la carpeta indicada anteriormente (consulte el paso 1).

   La clase "branding" existe y es única. La mshc de personalización de marca se incluye en este manual para que el contenido instalado tenga personalización de marca, y los comportamientos de contenido contenidos en el MSHCs tendrán los elementos de soporte adecuados contenidos en el paquete de personalización de marca. Sin esto, se producirán errores cuando el sistema busque elementos de soporte que no formen parte del contenido copiado (instalado).

   Para obtener el paquete de personalización de marca de Visual Studio, copie Branding_en archivo-US. mshc en C:\Archivos de programa (x86) \Microsoft Help Viewer\v2.1\ en la carpeta de trabajo.

```html
<html>
<head />
<body class="vendor-book">
<div class="details">
<span class="vendor">Your Company</span>
<span class="locale">en-us</span>
<span class="product">Your Company Help Content</span>
<span class="name">Your Company Help Content</span>
</div>
<div class="package-list">
<div class="package">
<span class="name">Your_Company _Content_Set_1</span>
<span class="deployed">True</span>
<a class="current-link" href="Your_Company _Content_Set_1.mshc">Your_Company _Content_Set_1.mshc </a>
</div>
<div class="package">
<span class="name">Your_Company _Content_Set_2</span>
<span class="deployed">True</span>
<a class="current-link"href=" Your_Company _Content_Set_2.mshc "> Your_Company _Content_Set_2.mshc </a>
</div>
<div class="package">
<span class="packageType">branding</span>
<span class="name">Branding_en-US</span>
<span class="deployed">True</span>
<a class="current-link" href="Branding_en-US.mshc">Branding_en-US.mshc</a>
</div>
</div>
</body>
</html>

```

 **Resumen**

 El uso y la extensión de los pasos anteriores permitirá a VSPs implementar sus conjuntos de contenido para el visor de ayuda de Visual Studio.

### <a name="adding-help-to-the-visual-studio-shell-integrated-and-isolated"></a>Agregar ayuda a Visual Studio Shell (integrado y aislado)
 **Introducción**

 En este tutorial se muestra cómo incorporar el contenido de la ayuda en una aplicación de Visual Studio Shell y, a continuación, implementarlo.

 **Requisitos**

1. [!INCLUDE[vs_dev12](../../includes/vs-dev12-md.md)]

2. [Visual Studio 2013 Redist. de Shell aislado](https://aka.ms/VS2013/IsoShell-LP/all)

   **Información general**

   El shell de [!INCLUDE[vs_dev12](../../includes/vs-dev12-md.md)] es una versión del IDE de [!INCLUDE[vs_dev12](../../includes/vs-dev12-md.md)] en el que puede basar una aplicación. Estas aplicaciones contienen el shell aislado junto con las extensiones que se crean. Use las plantillas de proyecto de Shell aislado, que se incluyen en el SDK de [!INCLUDE[vs_dev12](../../includes/vs-dev12-md.md)], para compilar las extensiones.

   Los pasos básicos para crear una aplicación aislada basada en Shell y su ayuda:

3. Obtenga el [!INCLUDE[vs_dev12](../../includes/vs-dev12-md.md)] el paquete redistribuible de Shell ISO (descarga de Microsoft).

4. En Visual Studio, cree una extensión de ayuda basada en el shell aislado, por ejemplo, la extensión de ayuda de Contoso que se describe más adelante en este tutorial.

5. Ajuste la extensión y el paquete redistribuible de Shell ISO en un MSI de implementación (una configuración de la aplicación). Este tutorial no incluye un paso de configuración.

   Cree un almacén de contenido de Visual Studio. En el escenario de Shell integrado, cambie visual Studio12 al nombre del catálogo de productos como se indica a continuación:

- Crear carpeta C:\ProgramData\Microsoft\HelpLibrary2\Catalogs\VisualStudio12.

- Cree un archivo denominado CatalogType. XML y agréguelo a la carpeta. El archivo debe contener las siguientes líneas de código:

  ```
  <?xml version="1.0" encoding="UTF-8"?>
  <catalogType>UserManaged</catalogType>
  ```

  Defina el almacén de contenido en el registro. Para el shell integrado, cambie VisualStudio12 por el nombre del catálogo de productos:

- HKLM\SOFTWARE\Wow6432Node\Microsoft\Help\v2.1\Catalogs\VisualStudio12

   Clave: LocationPath valor de cadena: C:\ProgramData\Microsoft\HelpLibrary2\Catalogs\VisualStudio12\

- HKLM\SOFTWARE\Wow6432Node\Microsoft\Help\v2.1\Catalogs\VisualStudio12\en-US

   Clave: Nombrecatálogo valor de cadena: [!INCLUDE[vs_dev12](../../includes/vs-dev12-md.md)] documentación

  **Crear el proyecto**

  Para crear una extensión de Shell aislado:

1. En el **archivo**de Visual Studio, elija **nuevo proyecto**, en **otros tipos de proyectos** , elija **extensibilidad**y, a continuación, elija **Visual Studio Shell aislado**. Asigne al proyecto el nombre `ContosoHelpShell`) para crear un proyecto de extensibilidad basado en la plantilla de Shell aislado de Visual Studio.

2. En Explorador de soluciones, en el proyecto ContosoHelpShellUI, en la carpeta archivos de recursos, abra ApplicationCommands. Vsct. Asegúrese de que esta línea está comentada (busque "No_Help"): `<!-- <define name=“No_HelpMenuCommands”/> -->`

3. Elija la tecla F5 para compilar y ejecutar **Debug**. En la instancia experimental del IDE de Shell aislado, elija el menú **ayuda** . Asegúrese de que aparecen los comandos **Ver ayuda**, **Agregar y quitar contenido**de la ayuda y **establecer preferencias** de la ayuda.

4. En Explorador de soluciones, en el proyecto ContosHelpShell, en la carpeta de personalización de Shell, abra ContosoHelpShell. pkgdef. Para definir el catálogo de ayuda de Contoso, agregue las líneas siguientes:

   ```
    [$RootKey$\Help]
   "Product"="Contoso"
   "Catalog"="Contoso"
   “Version"="100"
   "BrandingPackage"="ContosoBrandingPackage.mshc"
   ```

5. En Explorador de soluciones, en el proyecto ContosHelpShell, en la carpeta de personalización de Shell, abra ContosoHelpShell. Application. pkgdef. Para habilitar la ayuda de F1, agregue las líneas siguientes:

   ```
   // F1 Help Provider

   [$RootKey$\HelpProviders\{C99BDC23-FF29-46bf-9658-ADD634CCAED8}]
   "Name"="13407"
   "Package"="{DA9FB551-C724-11d0-AE1F-00A0C90FFFC3}"
   @="Help3 Provider"
   [$RootKey$\HelpProviders]
   @="{C99BDC23-FF29-46bf-9658-ADD634CCAED8}"
   [$RootKey$\Services\{C99BDC23-FF29-46bf-9658-ADD634CCAED8}]
   "Name"="Help3 Provider"
   @="{4A791146-19E4-11D3-B86B-00C04F79F802}"
   ```

6. En Explorador de soluciones, en el menú contextual de la solución ContosoHelpShell, elija el elemento de menú **propiedades** . En **propiedades de configuración**, seleccione **Configuration Manager**. En la columna **configuración** , cambie todos los valores de "debug" a "release".

7. Compile la solución. Esto crea un conjunto de archivos en una carpeta de versión, que se usará en la sección siguiente.

   Para probar esto como si se hubiera implementado:

8. En el equipo en el que va a implementar Contoso, instale el shell ISO descargado (desde arriba).

9. Cree una carpeta en \\\Archivos de programa (x86)\\y asígnele el nombre `Contoso`.

10. Copie el contenido de la carpeta ContosoHelpShell Release a \\carpeta \Archivos de programa (x86) \Contoso\

11. Para iniciar el editor del registro, elija **Ejecutar** en el menú **inicio** y escriba `Regedit`. En el editor del registro, elija **archivo**y, a continuación, **importar**. Vaya a la carpeta del proyecto ContosoHelpShell. En la subcarpeta ContosoHelpShell, elija ContosoHelpShell. reg.

12. Cree un almacén de contenido:

     Para el shell ISO: creación de un almacén de contenido de Contoso C:\ProgramData\Microsoft\HelpLibrary2\Catalogs\ContosoDev12

     Para [!INCLUDE[vs_dev12](../../includes/vs-dev12-md.md)] Shell integrado, cree la carpeta C:\ProgramData\Microsoft\HelpLibrary2\Catalogs\VisualStudio12

13. Cree CatalogType. XML y agregue al almacén de contenido (paso anterior) que contiene:

    ```
    <?xml version="1.0" encoding="UTF-8"?>
    <catalogType>UserManaged</catalogType>
    ```

14. Agregue las claves del registro siguientes:

     HKLM\SOFTWARE\Wow6432Node\Microsoft\Help\v2.1\Catalogs\VisualStudio12Key: LocationPath valor de cadena:

     Para el shell ISO:

     C:ProgramDataMicrosoftHelpLibrary2CatalogsVisualStudio12

     Shell integrado de [!INCLUDE[vs_dev12](../../includes/vs-dev12-md.md)]:

     C:ProgramDataMicrosoftHelpLibrary2CatalogsVisualStudio12en-US

     Clave: Nombrecatálogo valor de cadena: [!INCLUDE[vs_dev12](../../includes/vs-dev12-md.md)] documentación. En el caso del shell ISO, es el nombre del catálogo.

15. Copie el contenido (CAB o MSHC y MSHA) en una carpeta local.

16. Ejemplo de línea de comandos de Shell integrada para probar el almacén de contenido. En el caso del shell ISO, cambie los valores de catálogo y launchingApp según corresponda para que coincidan con el producto.

      "C:\Archivos de programa (x86) \Microsoft Help Viewer\v2.1\HlpViewer.exe"/catalogName VisualStudio12/helpQuery Method = "page & ID = ContosoTopic0"/launchingApp Microsoft, VisualStudio, 12.0

17. Inicie la aplicación contoso (desde la raíz de la aplicación contoso). En el shell ISO, elija el elemento de menú **ayuda** y cambie **establecer preferencia de ayuda** a **usar la ayuda local**.

18. En el Shell, elija el elemento de menú **ayuda** y, a continuación, **Ver ayuda**. Debe iniciar el visor de ayuda local. Elija la pestaña **administrar contenido** . En **origen**de la instalación, elija el botón de opción **disco** . Elija el botón **...** y busque la carpeta local que contiene el contenido de Contoso (copiada en la carpeta local del paso anterior). Elija el archivos helpcontentsetup. MSHA. Contoso debe aparecer ahora como un libro en las selecciones de los libros. Elija **Agregar**y, a continuación, elija el botón **Actualizar** (esquina inferior derecha).

19. En el IDE de Contoso, elija la tecla F1 para probar la funcionalidad de F1.

### <a name="additional-resources"></a>Recursos adicionales

Para la API en tiempo de ejecución, consulte [API de ayuda de Windows](https://msdn.microsoft.com/library/windows/desktop/hh447318\(v=vs.85\).aspx).

Para obtener más información sobre cómo aprovechar la API de ayuda, vea [ejemplos de código del visor de ayuda](https://marketplace.visualstudio.com/items?itemName=RobChandlerHelpMVP.HelpViewer20CodeExamples).

Para obtener actualizaciones sobre problemas problemáticos, consulte el [archivo Léame del visor de ayuda](https://go.microsoft.com/fwlink/?LinkId=255960).
