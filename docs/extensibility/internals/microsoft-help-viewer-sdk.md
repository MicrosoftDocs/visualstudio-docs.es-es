---
title: Visor de Ayuda de Microsoft SDK | Microsoft Docs
description: Obtenga información Visual Studio tareas del Visor de Ayuda, como crear un artículo, crear un paquete de personal de marca de contenido del Visor de Ayuda e implementar un conjunto de artículos.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 620d7dcd-d462-475e-a449-fbfa06ff12c5
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8bc2ed473e25dc75d0155bc864aa02c157e3482f
ms.sourcegitcommit: f430d014f912aa7874e1db65026dc72688b973e4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2021
ms.locfileid: "111448329"
---
# <a name="microsoft-help-viewer-sdk"></a>SDK del Visor de Ayuda de Microsoft

Este artículo contiene las siguientes tareas para Visual Studio integradores del Visor de Ayuda:

- Creación de un tema (compatibilidad con F1)

- Creación de un paquete de personal de marca de contenido del Visor de Ayuda

- Implementación de un conjunto de artículos

- Agregar ayuda al shell Visual Studio (integrado o aislado)

- Recursos adicionales

## <a name="create-a-topic-f1-support"></a>Creación de un tema (compatibilidad con F1)

En esta sección se proporciona información general sobre los componentes de un tema presentado, los requisitos del tema, una breve descripción de cómo crear un tema (incluidos los requisitos de soporte técnico de F1) y, por último, un tema de ejemplo con su resultado representado.

**Información general sobre temas del Visor de Ayuda**

Cuando se llama a un tema para su representación, el Visor de Ayuda obtiene los elementos del paquete de personal de marca asociados al tema en el momento de la instalación o la última actualización, junto con el tema XHTML, y combina los dos para dar como resultado la vista de contenido presentada (datos de marca + datos de tema).  El paquete de personal de marca contiene logotipos, compatibilidad con comportamientos de contenido y texto de personal de marca (copyright, etc.).  Vea "Creating Branding Package" a continuación para obtener más información sobre los elementos del paquete de personal de marca.  En caso de que no haya ningún paquete de personalizaciones asociado al tema, el Visor de Ayuda usará el paquete de personalizaciones de reserva ubicado en la raíz de la aplicación Visor de Ayuda (Branding_en-US.mshc).

**Requisitos de temas del Visor de Ayuda**

Para representarse correctamente en el Visor de Ayuda, el contenido del tema sin formato debe ser XHTML de W3C Basic 1.1.

Normalmente, un tema contiene dos secciones:

- Metadatos (vea Referencia de metadatos de contenido): datos sobre el tema, por ejemplo, el identificador único del tema, el valor de palabra clave, el identificador de toc del tema, el identificador de nodo primario, etc.

- Contenido del cuerpo: compatible con W3C Basic 1.1 XHTML, que incluye comportamientos de contenido admitidos (área contraíble, fragmento de código, etc. A continuación se muestra una lista completa).

Visual Studio controles compatibles con el paquete de personal de marca:

- Vínculos

- CodeSnippet

- CollapsibleArea

- Miembro heredado

- LanguageSpecificText

Cadenas de idioma admitidas (sin distingue mayúsculas de minúsculas):

- javascript

- csharp o c #

- cplusplus, visualc++ o c++

- jscript

- visualbasic o vb

- f# o fsharp o fs

- other: una cadena que representa un nombre de idioma

**Creación de un tema del Visor de Ayuda**

Cree un nuevo documento XHTML denominado ContosoTopic4.htm e incluya la etiqueta title (a continuación).

```html
<html>
<head>
<title>Contoso Topic 4</title>
</head>

<body>

</body>
</html>

```

A continuación, agregue datos para definir cómo se va a presentar el tema (con marca propia o no), cómo hacer referencia a este tema para F1, donde este tema existe dentro de la tabla de contenido, su identificador (para la referencia de vínculo de otros temas), etc. Consulte la tabla "Metadatos de contenido" a continuación para obtener una lista completa de los metadatos admitidos.

- En este caso, usaremos nuestro propio paquete de personal de marca, una variante del paquete Visual Studio personal de marca del Visor de Ayuda.

- Agregue el nombre de meta de F1 y el valor ("Microsoft.Help.F1" content=" ContosoTopic4") que coincidirán con el valor de F1 proporcionado en el contenedor de propiedades del IDE. (Consulte la sección F1 Support (Soporte técnico de F1) para obtener más información). Este es el valor que coincide con la llamada F1 desde el IDE para mostrar este tema cuando se elige F1 en el IDE.

- Agregue el identificador del tema. Esta es la cadena que usan otros temas para vincular a este tema. Es el identificador del Visor de Ayuda de este tema.

- En el caso de la TABLA, agregue el nodo primario de este tema para definir dónde aparecerá este nodo de la tabla de temas.

- Para el toc, agregue el orden de nodo de este tema. Cuando el nodo primario tenga `n` un número de nodos secundarios, defina en el orden de los nodos secundarios la ubicación de este tema. Por ejemplo, este tema es el número 4 de 4 temas secundarios.

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

**Cuerpo del tema**

El cuerpo (sin incluir el encabezado y pie de página) del tema contendrá vínculos a páginas, una sección de nota, un área contraíble, un fragmento de código y una sección de texto específico del idioma.  Consulte la sección personal de marca para obtener información sobre esas áreas del tema presentado.

1. Agregue una etiqueta de título de tema:  `<div class="title">Contoso Topic 4</div>`

2. Agregue una sección de nota: `<div class="alert"> add your table tag and text </div>`

3. Agregue un área contraíble:  `<CollapsibleArea Expanded="1" Title="Collapsible Area Test Heading"> add text  </CollapsibleArea>`

4. Agregue un fragmento de código:  `<CodeSnippet EnableCopyCode="true" Language="CSharp" ContainsMarkup="false" DisplayLanguage="C#" > a block of code </CodeSnippet>`

5. Agregar texto específico del lenguaje de código:  `<LanguageSpecificText devLangcs="CS" devLangvb="VB" devLangcpp="C++" devLangnu="F#" />` tenga en cuenta que permite escribir otros `devLangnu=` idiomas. Por ejemplo, `devLangnu="Fortran"` muestra Fortran cuando el fragmento de código DisplayLanguage = Fortran

6. Agregar vínculos de página: `<a href="ms-xhelp:///?Id=ContosoTopic1">Main Topic</a>`

> [!NOTE]
> Nota: Para los nuevos "idiomas para mostrar" no admitidos (por ejemplo, F#, Cobol, Fortran) la coloración de código en el fragmento de código será monocromática.

**Tema del Visor de Ayuda de ejemplo** El código muestra cómo definir metadatos, un fragmento de código, un área contraíble y texto específico del lenguaje.

```html
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
<li class="tocline1"><a href="#seealso" target="_self">See Also</a></li>
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
        <a href="ms-xhelp:///?Id=ContosoTopic1">Main Topic</a>
    </div>
 </div>
</div>
</div>
</body>
</html>
```

**Compatibilidad con F1**

En Visual Studio, al seleccionar F1 se generan valores proporcionados a partir de la posición del cursor dentro del IDE y se rellena un "bolsa de propiedades" con los valores proporcionados (en función de la ubicación del cursor. Cuando el cursor está sobre la característica x, la característica x está activa o en el foco y rellena el bolsa de propiedades con valores.  Cuando se selecciona F Visual Studio 1, se rellena el bolsa de propiedades y el código F1 busca ver si el origen de ayuda predeterminado de los clientes es local o en línea (en línea es el valor predeterminado) y, a continuación, crea la cadena adecuada en función de la configuración de los usuarios (el valor predeterminado es en línea): ejecución del shell (consulte la Guía del administrador de ayuda para parámetros de inicio de exe) con parámetros para el visor de ayuda local + palabras clave del bolsa de propiedades si la ayuda local es el valor predeterminado. , o la dirección URL de MSDN con la palabra clave en la lista de parámetros.

Si se devuelven tres cadenas para F1, denominada cadena de varios valores, tome el primer término, busque un resultado y, si se encuentra, ya está. Si no es así, pase a la cadena siguiente.  El orden es importante. La presentación de las palabras clave de varios valores debe ser la cadena más larga a la más corta.  Para comprobarlo en el caso de las palabras clave de varios valores, consulte la cadena de dirección URL F1 en línea, que incluirá la palabra clave elegida.

En Visual Studio 2012, hemos hecho intencionadamente una división más fuerte entre en línea y sin conexión, de modo que si la configuración del usuario era en línea, simplemente pasamos la solicitud F1 directamente a nuestro servicio de consulta en línea en MSDN en lugar de enrutar a través del agente de la biblioteca de Ayuda que teníamos en Visual Studio 2010. A continuación, nos basamos en un estado de "contenido de proveedor instalado = true" para determinar si se debe hacer algo diferente en ese contexto. Si es true, se realiza esta lógica de análisis y enrutamiento en función de lo que se quiera admitir para los clientes. Si es false, solo vamos a MSDN. Si la configuración del usuario es Local, todas las llamadas van al motor de ayuda local.

Diagrama de flujo F1:

![Flujo de F1](../../extensibility/internals/media/f1flow.png "F1flow")

Cuando el origen de contenido de ayuda predeterminado del Visor de Ayuda está establecido en en línea (iniciar en el explorador):

- Visual Studio Partner (VSP) emite un valor al contenedor de propiedades F1 (prefijo del contenedor de propiedades.palabra clave y dirección URL en línea para el prefijo que se encuentra en el registro): F1 envía un parámetro DE VSP URL+ al explorador.

- Visual Studio (editor de idioma, Visual Studio elementos de menú específicos, etc.): F1 envía una dirección URL de Visual Studio al explorador.

Cuando el origen de contenido de ayuda predeterminado del Visor de Ayuda está establecido en Ayuda local (Iniciar en el Visor de Ayuda):

- Características de VSP en las que la palabra clave coincide entre el bolsa de propiedades F1 y el índice de almacén local (es decir, el valor prefix.keyword del bolsa de propiedades = el valor encontrado en el índice del almacén local): F1 representa el tema en el Visor de Ayuda.

- Visual Studio características (ninguna opción para que VSP invalide el paquete de propiedades emitido por las características de Visual Studio): F1 representa un tema Visual Studio en el Visor de Ayuda.

Establezca los siguientes valores del Registro para habilitar la reserva F1 para el contenido de la Ayuda del proveedor. La reserva F1 significa que el Visor de Ayuda está configurado para buscar contenido de la Ayuda F1 en línea y el contenido del proveedor se instala localmente en la unidad de disco duro de los usuarios. El Visor de Ayuda debe buscar ayuda local para el contenido, aunque la configuración predeterminada sea para la ayuda en línea.

1. Establezca el **valor VendorContent** en la clave del Registro Help 2.3:

   - Para sistemas operativos de 32 bits:

        HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Help\v2.3\Catalogs\VisualStudio15

        "VendorContent"=dword:000000001

   - Para sistemas operativos de 64 bits:

        HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Catalogs\VisualStudio15

        "VendorContent"=dword:000000001

2. Registre el espacio de nombres del asociado en la clave del Registro help 2.3:

   - Para sistemas operativos de 32 bits:

      HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Help\v2.3\Partner<<em> \\ de nombres \> </em>

      "location"="offline"

   - Para sistemas operativos de 64 bits:

      HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Partner<<em> \\ de nombres \> </em>

      "location"="offline"

**Análisis de espacios de nombres nativos base**

Para activar el análisis de espacios de nombres nativos base, en el Registro agregue un nuevo DWORD con el nombre: BaseNativeNamespaces y establezca su valor en 1 (en la clave de catálogo que desea admitir).  Por ejemplo, si desea usar el catálogo de Visual Studio, podría agregar la clave a la ruta de acceso:

HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Catalogs\VisualStudio15

Cuando se encuentra una palabra clave F1 con el formato HEADER/METHOD, se analizará el carácter "/", lo que dará lugar a la construcción siguiente:

- HEADER: será el espacio de nombres que se puede usar para registrarse en el Registro.

- METHOD: se convertirá en la palabra clave que se pasa.

Por ejemplo, dada una biblioteca personalizada denominada CustomLibrary y un método denominado MyTestMethod, cuando se incluye una solicitud F1, se formateará como `CustomLibrary/MyTestMethod` .

A continuación, un usuario puede registrar CustomLibrary como espacio de nombres en el subárbol Partners y proporcionar la clave de ubicación que desee, y la palabra clave que se pasa a la consulta será MyTestMethod.

**Habilitación de la herramienta de depuración de Ayuda en el IDE**

Agregue la siguiente clave y valor del Registro:

::: moniker range="vs-2017"

**HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\15.0\Dynamic Help**

::: moniker-end

::: moniker range=">=vs-2019"

**HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\16.0\Dynamic Help**

::: moniker-end

Valor: Mostrar la salida de depuración en datos comerciales: SÍ

En el IDE, en el elemento de menú Ayuda, seleccione **Depurar contexto de ayuda.**

**Metadatos de contenido**

En la tabla siguiente, cualquier cadena que aparezca entre corchetes es un marcador de posición que debe reemplazarse por un valor reconocido. Por ejemplo, en \<meta name="Microsoft.Help.Locale" content="[language code]" /> , "[código de idioma]" debe reemplazarse por un valor como "en-us".

| Propiedad (representación HTML) | Descripción |
| - | - |
| \< meta name="Microsoft.Help.Locale" content="[language-code]" /> | Establece una configuración regional para este tema. Si esta etiqueta se usa en un tema, debe usarse una sola vez y debe insertarse encima de cualquier otra etiqueta de Ayuda de Microsoft. Si no se usa esta etiqueta, el texto del cuerpo del tema se indexa mediante el separador de palabras asociado a la configuración regional del producto, si se especifica; De lo contrario, se usa el separador de palabras en-us. Esta etiqueta se ajusta a ISOC RFC 4646. Para asegurarse de que la Ayuda de Microsoft funciona correctamente, use esta propiedad en lugar del atributo Language general. |
| \< meta name="Microsoft.Help.TopicLocale" content="[language-code]" /> | Establece una configuración regional para este tema cuando también se usan otras configuraciones regionales. Si esta etiqueta se usa en un tema, debe usarse una sola vez. Use esta etiqueta cuando el catálogo contenga contenido en más de un idioma. Varios temas de un catálogo pueden tener el mismo identificador, pero cada uno debe especificar un TopicLocale único. El tema que especifica un TopicLocale que coincide con la configuración regional del catálogo es el tema que se muestra en la tabla de contenido. Sin embargo, todas las versiones de idioma del tema se muestran en Resultados de la búsqueda. |
| \< title>[Título]\</title> | Especifica el título de este tema. Esta etiqueta es necesaria y debe usarse una sola vez en un tema. Si el cuerpo del tema no contiene una sección de título, este título se muestra en el tema y en la \<div> tabla de contenido. |
| \< meta name=" Microsoft.Help.Keywords" content="[aKeywordPhrase]"/> | Especifica el texto de un vínculo que se muestra en el panel de índice del Visor de Ayuda. Cuando se hace clic en el vínculo, se muestra el tema. Puede especificar varias palabras clave de índice para un tema o puede omitir esta etiqueta si no desea que los vínculos a este tema aparezcan en el índice. Las palabras clave "K" de versiones anteriores de la Ayuda se pueden convertir en esta propiedad. |
| \< meta name="Microsoft.Help.Id" content="[TopicID]"/> | Establece el identificador de este tema. Esta etiqueta es necesaria y debe usarse una sola vez en un tema. El identificador debe ser único entre los temas del catálogo que tengan la misma configuración regional. En otro tema, puede crear un vínculo a este tema mediante este identificador. |
| \< meta name="Microsoft.Help.F1" content="[System.Windows.Controls.Primitives.IRecyclingItemContainerGenerator]"/> | Especifica la palabra clave F1 para este tema. Puede especificar varias palabras clave F1 para un tema, o bien puede omitir esta etiqueta si no desea que este tema se muestre cuando un usuario de la aplicación presiona F1. Normalmente, solo se especifica una palabra clave F1 para un tema. Las palabras clave "F" de versiones anteriores de la Ayuda se pueden convertir en esta propiedad. |
| \< meta name="Description" content="[topic description]" /> | Proporciona un breve resumen del contenido de este tema. Si esta etiqueta se usa en un tema, debe usarse una sola vez. La biblioteca de consultas tiene acceso directamente a esta propiedad. no se almacena en el archivo de índice. |
| meta name="Microsoft.Help.TocParent" content="[parent_Id]"/> | Especifica el tema primario de este tema en la tabla de contenido. Esta etiqueta es necesaria y debe usarse una sola vez en un tema. El valor es el Microsoft.Help.Id del elemento primario. Un tema puede tener solo una ubicación en la tabla de contenido. "-1" se considera el identificador de tema para la raíz de LA C. En [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] , esa página es la página principal del Visor de Ayuda. Este es el mismo motivo por el que agregamos específicamente TocParent=-1 a algunos temas para asegurarnos de que se muestran en el nivel superior. La página principal del Visor de Ayuda es una página del sistema, por lo que no se puede reemplazar. Si un VSP intenta agregar una página con un identificador de -1, puede agregarse al conjunto de contenido, pero el Visor de Ayuda siempre usará la página del sistema : Inicio del Visor de Ayuda |
| \< meta name="Microsoft.Help.TocOrder" content="[positive integer]"/> | Especifica dónde aparece este tema en la tabla de contenido con respecto a sus temas del mismo nivel. Esta etiqueta es necesaria y debe usarse una sola vez en un tema. El valor es un entero. Un tema que especifica un entero de valor inferior aparece encima de un tema que especifica un entero de valor superior. |
| \< meta name="Microsoft.Help.Product" content="[product code]"/> | Especifica el producto que describe este tema. Si esta etiqueta se usa en un tema, debe usarse una sola vez. Esta información también se puede proporcionar como un parámetro que se pasa al indexador de Ayuda. |
| \< meta name="Microsoft.Help.ProductVersion" content="[version number]"/> | Especifica la versión del producto que describe este tema. Si esta etiqueta se usa en un tema, debe usarse una sola vez. Esta información también se puede proporcionar como un parámetro que se pasa al indexador de Ayuda. |
| \< meta name="Microsoft.Help.Category" content="[string]"/> | Usado por los productos para identificar subsecciones de contenido. Puede identificar varias subsecciones para un tema o puede omitir esta etiqueta si no desea que los vínculos identifiquen ninguna subsecciones. Esta etiqueta se usa para almacenar los atributos de TargetOS y TargetFrameworkMoniker cuando un tema se convierte desde una versión anterior de la Ayuda. El formato del contenido es AttributeName:AttributeValue. |
| \< meta name="Microsoft.Help.TopicVersion content="[topic version number]"/> | Especifica esta versión del tema cuando existen varias versiones en un catálogo. Dado que no se garantiza que Microsoft.Help.Id sea único, esta etiqueta es necesaria cuando hay más de una versión de un tema en un catálogo, por ejemplo, cuando un catálogo contiene un tema para .NET Framework 3.5 y un tema para .NET Framework 4 y ambos tienen el mismo Microsoft.Help.Id. |
| \< meta name="SelfBranded" content="[TRUE or FALSE]"/> | Especifica si este tema usa el paquete de personal de marca de inicio del Administrador de la biblioteca de Ayuda o un paquete de personal de marca específico del tema. Esta etiqueta debe ser TRUE o FALSE. Si es TRUE, el paquete de personalizar de marca del tema asociado invalida el paquete de personalizar de marca que se establece cuando se inicia el Administrador de bibliotecas de Ayuda para que el tema se represente según lo previsto, incluso si difiere de la representación de otro contenido. Si es FALSE, el tema actual se representa según el paquete de personalizar de marca que se establece cuando se inicia el Administrador de bibliotecas de Ayuda. De forma predeterminada, el Administrador de bibliotecas de Ayuda da por supuesto que la personalidad de marca es false a menos que la variable SelfBranded se declare como TRUE; por lo tanto, no es necesario declarar \<meta name="SelfBranded" content="FALSE"/> . |

## <a name="create-a-branding-package"></a>Creación de un paquete de personal de marca

La Visual Studio incluye una serie de productos Visual Studio, incluidos los shells aislados e integrados para Visual Studio asociados.  Cada uno de estos productos requiere cierto grado de compatibilidad con la personalidad de marca de contenido de Ayuda basada en temas, única para el producto.  Por ejemplo, Visual Studio temas deben tener una presentación de marca coherente, mientras que SQL Studio, que encapsula ISO Shell, requiere su propia personalización de marca de contenido de ayuda única para cada tema.  Es posible que un asociado de Shell integrado quiera que sus temas de Ayuda se encuentran dentro del contenido Visual Studio ayuda del producto principal, al tiempo que mantienen su propia personalidad de marca de tema.

El producto que contiene el Visor de Ayuda instala los paquetes de personal de marca.  Para Visual Studio productos:

- El paquete de idioma del Visor de Ayuda instala un paquete de personalización de marca de reserva (Branding_.mshc) en la raíz de la aplicación Visor de Ayuda \<locale> 2.3 (por ejemplo: C:\Archivos de programa (x86)\Visor de Ayuda de Microsoft\v2.3).  Esto se usa para los casos en los que el paquete de personal de marca del producto no está instalado (no se ha instalado ningún contenido) o donde el paquete de personal de marca instalado está dañado.  Los Visual Studio de reserva (logotipo y comentarios) se omiten cuando se usa el paquete de personalizaciones de reserva raíz de la aplicación.

- Cuando Visual Studio contenido se instala desde el servicio de paquetes de contenido, también se instala un paquete de personal de marca (por primera vez escenario de instalación de contenido).  Si hay una actualización del paquete de personal de marca, la actualización se instala cuando se produce la siguiente actualización de contenido o una acción de instalación adicional del paquete.

El Visor de Ayuda de Microsoft admite la personal de marca de los temas en función de los metadatos del tema.

- Donde los metadatos del tema definen la marca propia = true, represente el tema tal cual, no haga nada (en lo que se trata de personalizar la marca).

- Donde los metadatos del tema definen la marca propia = false, use el paquete de personalidad de marca asociado con el valor de metadatos TopicVendor.

- Donde los metadatos del tema definen name="Microsoft.Help.TopicVendor" content= , use el paquete de personalidad \< branding package name in vendor MSHA> de marca definido en el valor de contenido.

- Dentro del Visual Studio, hay una aplicación prioritaria de paquetes de personalizar marca.  En Visual Studio se aplica la personalidad de marca predeterminada y, a continuación, si se define en los metadatos del tema y se admite con el paquete de personalidad de marca asociado (tal como se define en la msha de instalación), la personalidad de marca definida por el proveedor se aplica como invalidación.

Normalmente, los elementos de personal de marca se incluyen en tres categorías principales:

- Elementos de encabezado (por ejemplo, vínculo de comentarios, texto de declinación de responsabilidades condicional, logotipo)

- Comportamientos de contenido (algunos ejemplos incluyen expandir o contraer elementos de texto de control y elementos de fragmento de código)

- Elementos de pie de página (ejemplo Copyright)

Los elementos que se consideran elementos de marca incluyen (detallado en esta especificación):

- Logotipo del catálogo o producto (ejemplo, Visual Studio)

- Vínculo de comentarios y elementos de correo electrónico

- Texto de declinación de responsabilidades

- Texto de copyright

Entre los archivos que se admiten en el Visual Studio de personal de marca del Visor de Ayuda se incluyen:

- Gráficos (logotipos, iconos, etc.)

- Branding.js: archivos de script que admiten comportamientos de contenido

- Branding.xml: cadenas que se usan de forma coherente en el contenido del catálogo.  Nota: para Visual Studio texto de localización en el branding.xml, incluya _locID=" \<unique value> "

- Branding.css: definiciones de estilo para la coherencia de la presentación

- Printing.css: definiciones de estilo para una presentación impresa coherente

Como se indicó anteriormente, los paquetes de personal de marca están asociados al tema:

- Cuando SelfBranded = false se define en los metadatos, el tema hereda el paquete de personal de marca del catálogo.

- O bien, cuando SelfBranded = false y hay un paquete de personalidad de marca único definido en la MSHA y disponible cuando se instala el contenido

Para los VSP que implementan paquetes de personalización de marca personalizados (contenido de VSP, SelfBranded=True), una manera de continuar es comenzar con el paquete de personalización de marca de reserva (instalado con el Visor de Ayuda) y cambiar el nombre del archivo según corresponda.  El Branding_ archivo .mshc es un archivo ZIP con la extensión de archivo cambiada a .mshc, por lo que basta con cambiar la extensión de .mshc a .zip y extraer el \<locale> contenido.  Consulte a continuación los elementos del paquete de personal de marca y modifique según corresponda (por ejemplo, cambie el logotipo por el logotipo de VSP y la referencia al logotipo en el archivo Branding.xml, actualice Branding.xml por las características específicas de VSP, etc.).

Cuando se realizan todas las modificaciones, cree un archivo ZIP que contenga los elementos de personal de marca deseados y cambie la extensión a .mshc.

Para asociar el paquete de personalización de marca personalizado, cree la MSHA, que contiene la referencia al archivo mshc de personalización de marca junto con el contenido mshc (que contiene los temas).  Consulte a continuación "MSHA" para obtener información sobre cómo crear una MSHA básica.

El Branding.xml contiene una lista de elementos utilizados para representar de forma coherente elementos específicos en un tema cuando el tema contiene \<meta name="Microsoft.Help.SelfBranded" content="false"/> .  A continuación Visual Studio lista de elementos del Branding.xml archivo.  Esta lista está pensada para usarse como plantilla para los adoptadores de ISO Shell, donde modifican estos elementos (por ejemplo, logotipo, comentarios y copyright) para satisfacer sus propias necesidades de personalización de marca de producto.

Nota: Las variables anotadas por "{n}" tienen dependencias de código: quitar o cambiar estos valores provocará errores y posiblemente se bloquee la aplicación. Los identificadores de localización (_locID="codesnippet.n") se incluyen en el paquete Visual Studio personalización de marca.

**Branding.xml**

| Elemento | Descripción |
| - | - |
| Característica: | **CollapsibleArea** |
| Uso: | Expandir contrae el texto del control de contenido |
| **Element** | **Valor** |
| ExpandText | Expanda |
| CollapseText | Contraer |
| Característica: | **CodeSnippet** |
| Uso: | Texto de control del fragmento de código.  Nota: El contenido del fragmento de código con espacio "Sin separación" se cambiará al espacio. |
| **Element** | **Valor** |
| CopyToClipboard | Copiar al Portapapeles |
| ViewColorizedText | Ver coloreados |
| CombinedVBTabDisplayLanguage | Visual Basic (ejemplo) |
| VBDeclaration | Declaración |
| VBUsage | Uso |
| Característica: | **Comentarios, pie de página y logotipo** |
| Uso: | Proporcione un control de comentarios para que el cliente proporcione comentarios sobre el tema actual por correo electrónico.  Texto de copyright del contenido.  Definición del logotipo. |
| **Element** | **Valor (estas cadenas se pueden modificar para satisfacer las necesidades del aprobador de contenido).** |
| Copyright | © 2013 Microsoft Corporation. Todos los derechos reservados. |
| SendFeedback | \<a href="{0}" {1}>Enviar comentarios \</a> sobre este tema a Microsoft. |
| FeedbackLink | |
| LogoTitle | [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] |
| LogoFileName | vs_logo_bk.gif |
| LogoFileNameHC | vs_logo_wh.gif |
| Característica: | **Declinación de responsabilidades** |
| Uso: | Un conjunto de declinaciones de responsabilidades específicas del caso para el contenido traducido por máquina. |
| **Element** | **Valor** |
| MT_Editable | Este artículo se ha traducido automáticamente. Si tiene una conexión a Internet, seleccione "Ver este tema en línea" para ver esta página en modo editable con el contenido original en inglés al mismo tiempo. |
| MT_NonEditable | Este artículo se ha traducido automáticamente. Si tiene una conexión a Internet, seleccione "Ver este tema en línea" para ver esta página en modo editable con el contenido original en inglés al mismo tiempo. |
| MT_QualityEditable | Este artículo se ha traducido manualmente. Si tiene una conexión a Internet, seleccione "Ver este tema en línea" para ver esta página en modo editable con el contenido original en inglés al mismo tiempo. |
| MT_QualityNonEditable | Este artículo se ha traducido manualmente. Si tiene una conexión a Internet, seleccione "Ver este tema en línea" para ver esta página en modo editable con el contenido original en inglés al mismo tiempo. |
| MT_BetaContents | Este artículo se ha traducido automáticamente para una versión preliminar. Si tiene una conexión a Internet, seleccione "Ver este tema en línea" para ver esta página en modo editable con el contenido original en inglés al mismo tiempo. |
| MT_BetaRecycledContents | Este artículo se ha traducido manualmente para una versión preliminar. Si tiene una conexión a Internet, seleccione "Ver este tema en línea" para ver esta página en modo editable con el contenido original en inglés al mismo tiempo. |
| Característica: | **LinkTable** |
| Uso: | Compatibilidad con vínculos de temas en línea |
| **Element** | **Valor** |
| LinkTableTitle | Tabla de vínculos |
| TopicEnuLinkText | Vea la versión \</a> en inglés de este tema que está disponible en el equipo. |
| TopicOnlineLinkText | Ver este tema en \<a href="{0}" {1}> línea\</a> |
| OnlineText | En línea |
| Característica: | **Control Audio de vídeo** |
| Uso: | Mostrar elementos y texto para el contenido de vídeo |
| **Element** | **Valor** |
| MultiMediaNotSupported | Internet Explorer debe instalarse 9 o superior para admitir {0} contenido. |
| Videotext | mostrar vídeo |
| AudioText | streaming de audio |
| OnlineVideoLinkText | \<p>Para ver el vídeo asociado a este tema, haga clic {0} \<a href="{1}"> {2} \</a> aquí.\</p> |
| OnlineAudioLinkText | \<p>Para escuchar el audio asociado a este tema, haga clic {0} \<a href="{1}"> {2} \</a> aquí.\</p> |
| Característica: | **Control Contenido no instalado** |
| Uso: | Elementos de texto (cadenas) usados para la representación de contentnotinstalled.htm |
| **Element** | **Valor** |
| ContentNotInstalledTitle | No se encontró contenido en el equipo. |
| ContentNotInstalledDownloadContentText | \<p>Para descargar contenido en el equipo, haga \<a href="{0}" {1}> clic en la pestaña Administrar \</a> .\</p> |
| ContentNotInstalledText | \<p>No hay ningún contenido instalado en el equipo. Consulte el administrador para obtener información sobre la instalación del contenido de ayuda local.\</p> |
| Característica: | **Control Tema no encontrado** |
| Uso: | Elementos de texto (cadenas) usados para la representación de topicnotfound.htm |
| **Element** | **Valor** |
| TopicNotFoundTitle | No se encuentra el tema solicitado en el equipo. |
| TopicNotFoundViewOnlineText | \<p>El tema que solicitó no se encontró en el equipo, pero puede \<a href="{0}" {1}> verlo en \</a> línea.\</p> |
| TopicNotFoundDownloadContentText | \<p>Consulte el panel de navegación para ver vínculos a temas similares o haga clic en \<a href="{0}" {1}> la pestaña Administrar para descargar contenido en el \</a> equipo.\</p> |
| TopicNotFoundText | \<p>El tema que solicitó no se encontró en el equipo.\</p> |
| Característica: | **Control dañado del tema** |
| Uso: | Elementos de texto (cadenas) usados para la representación de topiccorrupted.htm |
| **Element** | **Valor** |
| TopicCorruptedTitle | No se puede mostrar el tema solicitado. |
| TopicCorruptedViewOnlineText | \<p>El Visor de Ayuda no puede mostrar el tema solicitado. Puede haber un error en el contenido del tema o en una dependencia del sistema subyacente.\</p> |
| Característica: | **Control Página principal** |
| Uso: | Texto que admite la presentación del contenido del nodo de nivel superior del Visor de Ayuda. |
| **Element** | **Valor** |
| HomePageTitle | Inicio del Visor de Ayuda |
| HomePageIntroduction | \<p>Bienvenido a la Visor de Ayuda de Microsoft, una fuente esencial de información para todos los usuarios que usan herramientas, productos, tecnologías y servicios de Microsoft. El Visor de Ayuda le proporciona acceso a información de referencia, código de ejemplo, artículos técnicos y mucho más. Para buscar el contenido que necesita, examine la tabla de contenido, use la búsqueda de texto completo o navegue por el contenido mediante el índice de palabras clave.\</p> |
| HomePageContentInstallText | \<p>\<br />Use la \<a href="{0}" {1}> pestaña Administrar contenido para hacer lo \</a> siguiente: Agregar contenido al \<ul> \<li> equipo. \</li> \<li> Busque actualizaciones en el contenido local. \</li> \<li> Quite el contenido del equipo.\</li>\</ul>\</p> |
| HomePageInstalledBooks | Libros instalados |
| HomePageNoBooksInstalled | No se encontró contenido en el equipo. |
| HomePageHelpSettings | Configuración del contenido de ayuda |
| HomePageHelpSettingsText | \<p>La configuración actual es ayuda local. El Visor de Ayuda muestra el contenido que ha instalado en el equipo. \<br /> Para cambiar el origen del contenido de la Ayuda, en la barra Visual Studio menú, elija \<span style="{0}"> Ayuda, Establecer preferencia de Ayuda \</span> .\<br />\</p> |
| Megabyte | MB |

**branding.js**

El branding.js archivo contiene JavaScript utilizado por los elementos Visual Studio personal de marca del Visor de Ayuda.  A continuación se muestra una lista de los elementos de personalidad de marca y la función de JavaScript compatible.  Todas las cadenas que se van a localizar para este archivo se definen en la sección "Cadenas localizables" en la parte superior de este archivo.  El archivo ICL se ha creado para las cadenas loc dentro del branding.js archivo.

|**Característica de personal de marca**|**Función de JavaScript**|**Descripción**|
|-|-|-|
|Var...||Definición de variables|
|Obtener el lenguaje de código de usuario|setUserPreferenceLang|asigna un índice # al lenguaje de código|
|Establecer y obtener valores de cookie|getCookie, setCookie||
|Miembro heredado|changeMembersLabel|Expandir o contraer miembro heredado|
|Cuando SelfBranded=False|Onload|Lea la cadena de consulta para comprobar si se trata de una solicitud de impresión.  Establezca todos los códigosnippets para centrar la pestaña preferida del usuario.  Si se trata de una solicitud de impresión, establezca isPrinterFriendly en true. Compruebe el modo de contraste alto.|
|Fragmento de código|addSpecificTextLanguageTagSet||
||getIndexFromDevLang||
||ChangeTab||
||setCodesnippetLang||
||setCurrentLang||
||CopyToClipboard||
|CollapsibleArea|addToCollapsibleControlSet|escriba todo el objeto de control contraíble en la lista.|
||CA_Click|en función del estado del área contraíble, define qué imagen y texto se presentan|
|Compatibilidad con el contraste para el logotipo|isBlackBackground()|Se llama para determinar si el fondo es negro.  Solo es preciso cuando está en modo de contraste alto.|
||isHighContrast()|usar un intervalo de color para detectar el modo de contraste alto|
||onHighContrast(black)|Se llama cuando se detecta un contraste alto.|
|Funcionalidad LST|||
||addToLanSpecTextIdSet(id)||
||updateLST(currentLang)||
||getDevLangFromCodeSnippet(lang)||
|Funcionalidad multimedia|caption(begin, end, text, style)||
||findAllMediaControls(normalizedId)||
||getActivePlayer(normalizedId)||
||captionsOnOff(id)||
||toSeconds(t)||
||getAllComments(node)||
||styleRectify(styleName, styleValue)||
||showCC(id)||
||subtitle(id)||

**ARCHIVOS HTM**

El paquete de personal de marca contiene un conjunto de archivos HTM que admiten escenarios para comunicar información clave a los usuarios de contenido de Ayuda, por ejemplo, una página principal que contiene una sección que describe qué conjuntos de contenido están instalados y páginas que le informan al usuario cuándo no se pueden encontrar temas en el conjunto local de temas. Estos archivos HTM se pueden modificar por producto.  Los proveedores de Iso Shell pueden tomar el paquete de personalización de marca predeterminado y cambiar el comportamiento y el contenido de estas páginas para que se ajusten a sus necesidades.  Estos archivos hacen referencia a su paquete de personal de marca correspondiente para que las etiquetas de personal de marca obtengan el contenido correspondiente del archivo branding.xml marca.

|**Archivo**|**Uso**|**Origen de contenido mostrado**|
|-|-|-|
|homepage.htm|Se trata de una página que muestra el contenido instalado actualmente y cualquier otro mensaje adecuado para presentar al usuario sobre su contenido.  Este archivo tiene el atributo de metadatos adicional "Microsoft.Help.Id" content="-1", que coloca este contenido en la parte superior de la tabla de contenido local.||
||<META_HOME_PAGE_TITLE_ADD />|Branding.xml, etiqueta \<HomePageTitle>|
||<HOME_PAGE_INTRODUCTION_SECTION_ADD />|Branding.xml, etiqueta \<HomePageIntroduction>|
||<HOME_PAGE_CONTENT_INSTALL_SECTION_ADD />|Branding.xml, etiqueta \<HomePageContentInstallText>|
||<HOME_PAGE_BOOKS_INSTALLED_SECTION_ADD />|Sección de encabezado Branding.xml etiqueta , los datos generados a partir \<HomePageInstalledBooks> de la aplicación, cuando no hay libros  \<HomePageNoBooksInstalled> instalados.|
||<HOME_PAGE_SETTINGS_SECTION_ADD />|Sección de encabezado Branding.xml etiqueta \<HomePageHelpSettings> , texto de sección \<HomePageHelpSettingsText> .|
|topiccorrupted.htm|Cuando existe un tema en el conjunto local, pero por algún motivo no se puede mostrar (contenido dañado).||
||<META_TOPIC_CORRUPTED_TITLE_ADD />|Branding.xml, etiqueta \<TopicCorruptedTitle>|
||<TOPIC_CORRUPTED_SECTION_ADD />|Branding.xml, etiqueta \<TopicCorruptedViewOnlineText>|
|topicnotfound.htm|Cuando no se encuentra un tema en el conjunto de contenido local ni está disponible en línea||
||<META_TOPIC_NOT_FOUND_TITLE_ADD />|Branding.xml, etiqueta \<TopicNotFoundTitle>|
||<META_TOPIC_NOT_FOUND_ID_ADD />|Branding.xml, etiqueta \<TopicNotFoundViewOnlineText> + \<TopicNotFoundDownloadContentText>|
||<TOPIC_NOT_FOUND_SECTION_ADD />|Branding.xml, etiqueta \<TopicNotFoundText>|
|contentnotinstalled.htm|Cuando no hay ningún contenido local instalado para el producto.||
||<META_CONTENT_NOT_INSTALLED_TITLE_ADD />|Branding.xml, etiqueta \<ContentNotInstalledTitle>|
||<META_CONTENT_NOT_INSTALLED_ID_ADD />|Branding.xml, etiqueta \<ContentNotInstalledDownloadContentText>|
||<CONTENT_NOT_INSTALLED_SECTION_ADD />|Branding.xml, etiqueta \<ContentNotInstalledText>|

**Archivos CSS**

El Visual Studio de personal de marca del Visor de Ayuda contiene dos archivos CSS para admitir la presentación de contenido Visual Studio ayuda coherente:

- Branding.css: contiene elementos css para la representación donde SelfBranded=false

- Printer.css: contiene elementos css para la representación donde SelfBranded=false

Los archivos Branding.css incluyen definiciones para la presentación de un tema de Visual Studio (advertencia es que el archivo branding.css contenido en Branding_ .mshc del servicio de \<locale> paquetes puede cambiar).

**Archivos gráficos**

Visual Studio contenido muestra un Visual Studio, así como otros gráficos.  A continuación se muestra la lista completa de archivos gráficos Visual Studio paquete de personalidad de marca del Visor de Ayuda.

|**Archivo**|**Uso**|**Ejemplos**|
|-|-|-|
|clear.gif|Se usa para representar el área contraíble||
|footer_slice.gif|Presentación del pie de página||
|info_icon.gif|Se usa al mostrar información|Declinación de responsabilidades|
|online_icon.gif|Este icono se asociará a vínculos en línea||
|tabLeftBD.gif|Se usa para representar el contenedor de fragmentos de código||
|tabRightBD.gif|Se usa para representar el contenedor de fragmentos de código||
|vs_logo_bk.gif|Se usa para las referencias de logotipo de contraste normales, tal como se define Branding.xml etiqueta \<LogoFileName> .  Para Visual Studio productos, el nombre del logotipo es vs_logo_bk.gif.||
|vs_logo_wh.gif|Se usa para las referencias de logotipo de contraste alto, tal como se define en Branding.xml etiqueta \<LogoFileNameHC> .  Para Visual Studio productos, el nombre del logotipo es vs_logo_wh.gif.||
|ccOff.png|Gráfico de subtítulos||
|ccOn.png|Gráfico de subtítulos||
|ImageSprite.png|Se usa para representar el área contraíble|gráfico expandido o contraído|

## <a name="deploy-a-set-of-topics"></a>Implementación de un conjunto de temas

Se trata de un tutorial sencillo y rápido para crear un conjunto de implementación de contenido del Visor de Ayuda compuesto por un archivo MSHA y el conjunto de taxis o MSHCs que contienen los temas. MSHA es un archivo XML que describe un conjunto de archivos CAB o MSHC. El Visor de Ayuda puede leer el MSHA para obtener una lista de contenido (el .CAB o . Archivos MSHC) disponibles para la instalación local.

Se trata solo de una introducción que describe el esquema XML muy básico para el MSHA del Visor de Ayuda.  Hay una implementación de ejemplo debajo de esta breve introducción y ejemplo helpContentSetup.msha.

El nombre de MSHA, para los fines de este primer, es HelpContentSetup.msha (el nombre del archivo puede ser cualquier cosa, con la extensión . MSHA). HelpContentSetup.msha (ejemplo siguiente) debe contener una lista de los taxis o MSHC disponibles.  El tipo de archivo debe ser coherente dentro de MSHA (no admite una combinación de tipos de archivo MSHA y CAB). Para cada CAB o MSHC, debe haber \<div class="package"> un ... \</div> (vea el ejemplo siguiente).

Nota: En el ejemplo de implementación siguiente, hemos incluido el paquete de personalizado de marca. Esto es fundamental para incluir con el fin de obtener la información necesaria Visual Studio elementos de representación de contenido y comportamientos de contenido.

Archivo HelpContentSetup.msha de ejemplo: (reemplace "nombre del conjunto de contenido 1" y "nombre del conjunto de contenido 2", etc.) por los nombres de archivo.

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
</div>.
```

1. Cree una carpeta local, algo como "C:\SampleContent".

2. En este ejemplo, usaremos archivos MSHC para contener los temas.  Un MSHC es un archivo ZIP con la extensión de archivo cambiada de .zip a . MSHC.

3. Cree el archivo HelpContentSetup.msha siguiente como un archivo de texto (se usó el Bloc de notas para crear el archivo) y guárdelo en la carpeta mencionada anteriormente (consulte el paso 1).

La clase "Branding" existe y es única. El mshc de personal de marca se incluye en esta guía para que el contenido instalado tenga personal de marca y los comportamientos de contenido contenidos en los MSHCs tendrán los elementos de soporte adecuados incluidos en el paquete de personal de marca. Sin esto, se producen errores cuando el sistema busca elementos de soporte técnico que no forman parte del contenido desasistido (instalado).

Para obtener el paquete de personalización de marca de Visual Studio, copie el archivo Branding_en-US.mshc en C:\Archivos de programa (x86)\Visor de Ayuda de Microsoft\v2.3\ en la carpeta de trabajo.

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

El uso y la extensión de los pasos anteriores permitirán a los VSP implementar sus conjuntos de contenido para Visual Studio Visor de Ayuda.

### <a name="add-help-to-the-visual-studio-shell-integrated-and-isolated"></a>Agregar ayuda a Visual Studio Shell (integrado y aislado)

**Introducción**

En este tutorial se muestra cómo incorporar contenido de ayuda en una Visual Studio Shell y, a continuación, implementarlo.

**Requisitos**

1. [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)]

2. [Visual Studio 2013 redist de shell aislado](https://visualstudio.microsoft.com/vs/older-downloads/isolated-shell/)

**Información general**

Shell es una versión del IDE en la [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] que puede basar una aplicación. Estas aplicaciones contienen el shell aislado junto con las extensiones que cree. Use plantillas de proyecto de Shell aislado, que se incluyen en el [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] SDK, para compilar extensiones.

Los pasos básicos para crear una aplicación basada en Shell aislado y su Ayuda:

1. Obtenga el [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] shell ISO redistribuible (una descarga de Microsoft).

2. En Visual Studio, cree una extensión de Ayuda basada en el Shell aislado, por ejemplo, la extensión de Ayuda de Contoso que se describe más adelante en este tutorial.

3. Ajuste la extensión y el shell ISO redistribuible en una MSI de implementación (una configuración de aplicación). Este tutorial no incluye un paso de configuración.

Cree una Visual Studio de contenido. Para el escenario de Shell integrado, cambie Visual Studio12 por el nombre del catálogo de productos como se muestra a continuación:

- Cree la carpeta C:\ProgramData\Microsoft\HelpLibrary2\Catalogs\VisualStudio15.

- Cree un archivo denominado CatalogType.xml y agrégrélo a la carpeta . El archivo debe contener las siguientes líneas de código:

    ```xml
    <?xml version="1.0" encoding="UTF-8"?>
    <catalogType>UserManaged</catalogType>
    ```

Defina el almacén de contenido en el Registro. Para el Shell integrado, cambie VisualStudio15 por el nombre del catálogo de productos:

- HKLM\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Catalogs\VisualStudio15

   Clave: Valor de cadena LocationPath: C:\ProgramData\Microsoft\HelpLibrary2\Catalogs\VisualStudio15\

- HKLM\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Catalogs\VisualStudio15\en-US

   Clave: Valor de cadena CatalogName: [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] Documentación

**Creación del proyecto**

Para crear una extensión de Shell aislado:

1. En Visual Studio, en Archivo **,** elija Nuevo  proyecto **,** en Otros tipos de proyecto elija **Extensibilidad** y, a continuación, **Visual Studio Shell aislado.** Asigne al proyecto `ContosoHelpShell` el nombre ) para crear un proyecto de extensibilidad basado en Visual Studio plantilla de Shell aislado.

2. En Explorador de soluciones, en el proyecto ContosoHelpShellUI, en la carpeta Archivos de recursos, abra ApplicationCommands.vsct. Asegúrese de que esta línea está comentada (busque "No_Help"): `<!-- <define name="No_HelpMenuCommands"/> -->`

3. Elija la tecla F5 para compilar y ejecutar **Depurar**. En la instancia experimental del IDE de Shell aislado, elija el **menú** Ayuda. Asegúrese de que aparecen los comandos **Ver Ayuda,** Agregar y Quitar contenido de ayuda y **Establecer** preferencia de ayuda.

4. En Explorador de soluciones, en el proyecto ContosHelpShell, en la carpeta Personalización del shell, abra ContosoHelpShell.pkgdef. Para definir el catálogo de Ayuda de Contoso, agregue las líneas siguientes:

    ```
     [$RootKey$\Help]
    "Product"="Contoso"
    "Catalog"="Contoso"
    "Version"="100"
    "BrandingPackage"="ContosoBrandingPackage.mshc"
    ```

5. En Explorador de soluciones, en el proyecto ContosHelpShell, en la carpeta Personalización del shell, abra ContosoHelpShell.Application.pkgdef. Para habilitar la Ayuda F1, agregue las líneas siguientes:

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

6. En Explorador de soluciones, en el menú contextual de la solución ContosoHelpShell, elija el **elemento de menú** Propiedades. En **Propiedades de configuración,** **seleccione Administrador de configuración**. En la **columna Configuración,** cambie cada valor "Debug" a "Release".

7. Compile la solución. Esto crea un conjunto de archivos en una carpeta de versión, que se usará en la sección siguiente.

Para probar esto como si se implementara:

1. En la máquina en la que va a implementar Contoso, instale el shell ISO descargado (desde arriba).

2. Cree una carpeta en \\ \Archivos de programa (x86) \\ y así mismo den el nombre `Contoso` .

3. Copie el contenido de la carpeta de versión de ContosoHelpShell en la carpeta \\ \Archivos de programa (x86)\Contoso\.

4. Para iniciar el Editor del Registro,  **elija Ejecutar** en **el menú** Inicio y escriba `Regedit` . En el editor del Registro, elija **Archivo** y, a continuación, **Importar**. Vaya a la carpeta del proyecto ContosoHelpShell. En la subcarpeta ContosoHelpShell, elija ContosoHelpShell.reg.

5. Cree un almacén de contenido:

    Para shell ISO: cree un almacén de contenido de Contoso C:\ProgramData\Microsoft\HelpLibrary2\Catalogs\ContosoDev12

    Para [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] El shell integrado, cree la carpeta C:\ProgramData\Microsoft\HelpLibrary2\Catalogs\VisualStudio15.

6. Cree CatalogType.xml y agregue al almacén de contenido (paso anterior) que contiene:

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <catalogType>UserManaged</catalogType>
   ```

7. Agregue las siguientes claves del Registro:

    HKLM\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Catalogs\VisualStudio15Key: Valor de cadena LocationPath:

    Para shell ISO:

    C:ProgramDataMicrosoftHelpLibrary2CatalogsVisualStudio15

    [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] Shell integrado:

    C:ProgramDataMicrosoftHelpLibrary2CatalogsVisualStudio15en-US

    Clave: Valor de cadena CatalogName: [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] Documentación. En el shell ISO, este es el nombre del catálogo.

8. Copie el contenido (cabs o MSHC y MSHA) en una carpeta local.

9. Línea de comandos de Shell integrado de ejemplo para probar el almacén de contenido. Para ISO Shell, cambie el catálogo y los valores de launchingApp según corresponda para que coincidan con el producto.

     "C:\Archivos de programa (x86)\Microsoft Help Viewer\v2.3\HlpViewer.exe" /catalogName VisualStudio15 /helpQuery method="page&id=ContosoTopic0" /launchingApp Microsoft,VisualStudio,12.0

10. Inicie la aplicación Contoso (desde la raíz de la aplicación contoso). En shell ISO, elija el **elemento de menú** Ayuda y cambie establecer **preferencias de ayuda** para usar ayuda **local.**

11. En el shell, elija el elemento **de menú Ayuda** y, a continuación, Ver **ayuda.** Se debe iniciar el visor de Ayuda local. Elija la **pestaña Administrar** contenido. En **Origen de instalación**, elija el botón de **opción** Disco. Elija el **botón ...** y vaya a la carpeta local que contiene el contenido de Contoso (copiado en la carpeta local en el paso anterior). Elija HelpContentSetup.msha. Contoso debería aparecer ahora como un libro en las selecciones de libros. Elija **Agregar** y, a continuación, elija **el botón** Actualizar (esquina inferior derecha).

12. En el IDE de Contoso, elija la tecla F1 para probar la funcionalidad F1.

## <a name="additional-resources"></a>Recursos adicionales

Para la API en tiempo de ejecución, consulte [Api de Ayuda de Windows.](/previous-versions/windows/desktop/helpapi/helpapi-portal)

Para obtener más información sobre cómo aprovechar la API de Ayuda, vea Ejemplos [de código del Visor de Ayuda](https://marketplace.visualstudio.com/items?itemName=RobChandlerHelpMVP.HelpViewer20CodeExamples).

Puede enviar sugerencias de características en [Developer Community](https://aka.ms/feedback/suggest?space=8).
