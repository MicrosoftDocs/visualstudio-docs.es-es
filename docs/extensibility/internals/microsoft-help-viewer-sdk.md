---
title: SDK de Microsoft Help Viewer (SDK de Microsoft Help Viewer) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 620d7dcd-d462-475e-a449-fbfa06ff12c5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 721623edabcaf3b395a143dd193cae3fd71d93d6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707150"
---
# <a name="microsoft-help-viewer-sdk"></a>SDK del Visor de Ayuda de Microsoft

Este artículo contiene las siguientes tareas para los integradores de Visual Studio Help Viewer:

- Creación de un tema (soporte F1)

- Creación de un paquete de marca de contenido del Visor de ayuda

- Despliegue de un conjunto de artículos

- Agregar ayuda al shell de Visual Studio (integrado o aislado)

- Recursos adicionales

## <a name="create-a-topic-f1-support"></a>Crear un tema (soporte F1)

En esta sección se proporciona información general sobre los componentes de un tema presentado, los requisitos del tema, una breve descripción de cómo crear un tema (incluidos los requisitos de compatibilidad con F1) y, por último, un tema de ejemplo con su resultado representado.

**Descripción general del tema del visor de ayuda**

Cuando se llama a un tema para la representación, el Visor de ayuda obtiene los elementos del paquete de personalización de marca que están asociados con el tema en el momento de la instalación o la última actualización, junto con el tema XHTML, y combina los dos para dar como resultado la vista de contenido presentada (datos de marca + datos de tema).  El paquete de personalización de marca contiene logotipos, compatibilidad con comportamientos de contenido y texto de personalización de marca (copyright, etc.).  Consulte "Creación de paquete de personalización de marca" a continuación para obtener más información sobre los elementos del paquete de personalización de marca.  En caso de que no haya ningún paquete de personalización de marca asociado al tema, el Visor de Ayuda usará el paquete de personalización de marca de reserva ubicado en la raíz de la aplicación Visor de ayuda (Branding_en-US.mshc).

**Ayudar a los requisitos del tema del espectador**

Para representarse correctamente en el Visor de ayuda, el contenido del tema sin formato debe ser W3C Basic 1.1 XHTML.

Un tema normalmente contiene dos secciones:

- Metadatos (consulte Referencia de metadatos de contenido): datos sobre el tema, por ejemplo, el identificador único del tema, el valor de la palabra clave, el identificador de TDC del tema, el identificador de nodo primario, etc.

- Contenido corporal: compatible con W3C Basic 1.1 XHTML, que incluye comportamientos de contenido admitidos (área plegable, fragmento de código, etc. A continuación se muestra una lista completa).

Controles compatibles con El paquete de personalización de marca de Visual Studio:

- Vínculos

- CodeSnippet

- CollapsibleArea

- Miembro heredado

- LanguageSpecificText

Cadenas de idioma admitidas (no distinguen entre mayúsculas y minúsculas):

- javascript

- csharp o c #

- cplusplus o visualc++ o c++

- jscript

- visualbasic o vb

- f o fsharp o fs

- otro - una cadena que representa un nombre de idioma

**Creación de un tema del Visor de ayuda**

Cree un nuevo documento XHTML denominado ContosoTopic4.htm e incluya la etiqueta de título (abajo).

```html
<html>
<head>
<title>Contoso Topic 4</title>
</head>

<body>

</body>
</html>

```

A continuación, agregue datos para definir cómo se presentará el tema (automarcado o no), cómo hacer referencia a este tema para F1, donde existe este tema dentro de la TDT, su identificador (para referencia de vínculo por otros temas), etc. Consulte la tabla "Metadatos de contenido" a continuación para obtener una lista completa de los metadatos admitidos.

- En este caso, usaremos nuestro propio paquete de personalización de marca, una variante del paquete de personalización de marca visor de ayuda de Visual Studio.

- Agregue el metanombre y el valor de F1 ("Microsoft.Help.F1" content" ContosoTopic4") que coincidirá con el valor F1 proporcionado en el contenedor de propiedades IDE. (Consulte la sección Soporte de F1 para obtener más información.) Este es el valor que coincide con la llamada F1 desde dentro del IDE para mostrar este tema cuando se elige F1 en el IDE.

- Agregue el identificador del tema. Esta es la cadena que usan otros temas para vincular a este tema. Es el identificador del Visor de ayuda para este tema.

- Para el TD.T.C., agregue el nodo primario de este tema para definir dónde aparecerá este nodo de TC de tema.

- Para la TD.T., agregue el orden de nodo de este tema. Cuando el nodo `n` primario tiene un número de nodos secundarios, defina en el orden de los nodos secundarios la ubicación de este tema. Por ejemplo, este tema es el número 4 de 4 temas secundarios.

Ejemplo de sección de metadatos:

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

El cuerpo (sin incluir el encabezado y el pie de página) del tema contendrá vínculos de página, una sección de nota, un área contraíble, un fragmento de código y una sección de texto específico del idioma.  Consulte la sección de personalización de marca para obtener información sobre las áreas del tema presentado.

1. Agregue una etiqueta de título de tema:`<div class="title">Contoso Topic 4</div>`

2. Agregue una sección de notas:`<div class="alert"> add your table tag and text </div>`

3. Agregue un área plegable:`<CollapsibleArea Expanded="1" Title="Collapsible Area Test Heading"> add text  </CollapsibleArea>`

4. Agregue un fragmento de código:`<CodeSnippet EnableCopyCode="true" Language="CSharp" ContainsMarkup="false" DisplayLanguage="C#" > a block of code </CodeSnippet>`

5. Añadir texto específico del `<LanguageSpecificText devLangcs="CS" devLangvb="VB" devLangcpp="C++" devLangnu="F#" />` idioma `devLangnu=` de código: tenga en cuenta que le permite introducir otros idiomas. Por ejemplo, `devLangnu="Fortran"` muestra Fortran cuando el fragmento de código DisplayLanguage - Fortran

6. Añadir enlaces de página:`<a href="ms-xhelp:///?Id=ContosoTopic1">Main Topic</a>`

> [!NOTE]
> Nota: para el nuevo "Lenguaje de visualización" no compatible (ejemplo, F, Cobol, Fortran) la coloración del código en el fragmento de código será monocroma.

**Ejemplo de tema del visor de ayuda** El código ilustra cómo definir metadatos, un fragmento de código, un área contraíble y texto específico del lenguaje.

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

**Soporte F1**

En Visual Studio, al seleccionar F1 se generan los valores proporcionados desde la colocación del cursor dentro del IDE y se rellena una "bolsa de propiedades" con los valores proporcionados (en función de la ubicación del cursor). Cuando el cursor está sobre la característica x, la característica x está activa/en foco y rellena la bolsa de propiedades con valores.  Cuando se selecciona F1, el contenedor de propiedades se rellena y el código de Visual Studio F1 busca si el origen de la Ayuda predeterminado de los clientes es local o en línea (en línea es el valor predeterminado), crea la cadena adecuada en función de la configuración de los usuarios (en línea es el valor predeterminado) - shell execute (consulte la Guía del administrador de ayuda para los parámetros de inicio de exe) con parámetros para el visor de ayuda local + palabras clave del contenedor de propiedades si la ayuda local es la predeterminada , o la URL de MSDN con la palabra clave en la lista de parámetros.

Si se devuelven tres cadenas para F1, denominada cadena de varios valores, tome el primer término, busque un hit y, si se encuentra, hemos terminado; si no, pase a la siguiente cadena.  El orden importa. La presentación de las palabras clave de varios valores debe ser la cadena más larga a la cadena más corta.  Para comprobar esto en el caso de las palabras clave de varios valores, mire la cadena de URL F1 en línea, que incluirá la palabra clave elegida.

En Visual Studio 2012, intencionalmente creamos una división más fuerte entre en línea y sin conexión, de modo que si la configuración del usuario era para Online, simplemente pasamos la solicitud F1 directamente a nuestro servicio de consulta en línea en MSDN en lugar de enrutar a través del agente de biblioteca de ayuda que teníamos en Visual Studio 2010. A continuación, nos basamos en un estado de "contenido de proveedor instalado - true" para determinar si se debe hacer algo diferente en ese contexto. Si es true, realizamos esta lógica de análisis y enrutamiento en función de lo que desee admitir para sus clientes. Si es false, entonces simplemente vamos a MSDN. Si la configuración del usuario es Local, todas las llamadas van al motor de ayuda local.

Diagrama de flujo F1:

![Flujo de F1](../../extensibility/internals/media/f1flow.png "F1flow")

Cuando el origen de contenido de ayuda predeterminado del Visor de Ayuda se establece en línea (Iniciar en el explorador):

- Las características de Visual Studio Partner (VSP) emiten un valor al contenedor de propiedades F1 (prefijo.keyword de bolsa de propiedades y dirección URL en línea para el prefijo que se encuentra en el registro): F1 envía un VSP URL+ parámetros al explorador.

- Características de Visual Studio (editor de idioma, elementos de menú específicos de Visual Studio, etc.): F1 envía una dirección URL de Visual Studio al explorador.

Cuando el origen de contenido de ayuda predeterminado del Visor de Ayuda se establece en Ayuda local (Iniciar en el Visor de Ayuda):

- Características de VSP donde la palabra clave coincide entre el contenedor de propiedades F1 y el índice de tienda local (es decir, el prefijo de contenedor de propiedades.keyword , el valor que se encuentra en el índice de almacén local): F1 representa el tema en el Visor de ayuda.

- Características de Visual Studio (sin opción para que el VSP invalide el contenedor de propiedades emitido desde las características de Visual Studio): F1 representa un tema de Visual Studio en el Visor de ayuda.

Establezca los siguientes valores del Registro para habilitar la reserva F1 para el contenido de la Ayuda del proveedor. F1 Fallback significa que el Visor de Ayuda está configurado para buscar contenido de Ayuda F1 en línea y el contenido del proveedor se instala localmente en el disco duro de los usuarios. El Visor de ayuda debe buscar la Ayuda local para el contenido aunque la configuración predeterminada sea para la ayuda en línea.

1. Establezca el valor **VendorContent** en la clave del Registro de la Ayuda 2.3:

   - Para sistemas operativos de 32 bits:

        HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Help\v2.3\Catalogs\VisualStudio15

        "VendorContent"-dword:00000001

   - Para sistemas operativos de 64 bits:

        HKEY_LOCAL_MACHINE,SOFTWARE, Wow6432Node, Microsoft, Ayuda, v2,3, Catálogos, VisualStudio15

        "VendorContent"-dword:00000001

2. Registre el espacio de nombres del asociado en la clave del Registro de la Ayuda 2.3:

   - Para sistemas operativos de 32 bits:

      HKEY_LOCAL_MACHINE,SOFTWARE, Microsoft, Ayuda, v2.3, Espacio de nombres de<de socios<em> \\\></em>

      "ubicación" "fuera de línea"

   - Para sistemas operativos de 64 bits:

      HKEY_LOCAL_MACHINE,SOFTWARE, Wow6432Node, Microsoft, Ayuda, v2.3,<espacio de nombres de la<em> \\<de trabajo\></em>

      "ubicación" "fuera de línea"

**Análisis de espacio de nombres nativo base**

Para activar el análisis de espacios de nombres nativos base, en el registro agregue un nuevo DWORD con el nombre de: BaseNativeNamespaces y establezca su valor en 1 (en la clave de catálogo que desea admitir).  Por ejemplo, si desea usar el catálogo de Visual Studio, puede agregar la clave a la ruta de acceso:

HKEY_LOCAL_MACHINE,SOFTWARE, Wow6432Node, Microsoft, Ayuda, v2,3, Catálogos, VisualStudio15

Cuando se encuentra una palabra clave F1 con el formato HEADER/METHOD, se analizará el carácter '/', lo que dará como resultado la siguiente construcción:

- HEADER: será el espacio de nombres que se puede utilizar para registrarse en el registro

- METHOD: esto se convertirá en la palabra clave que se pasa a través.

Por ejemplo, dada una biblioteca personalizada denominada CustomLibrary y un método denominado MyTestMethod, `CustomLibrary/MyTestMethod`cuando una solicitud F1 entra en ella se formateará como .

A continuación, un usuario puede registrar CustomLibrary como espacio de nombres en el subárbol Partners y proporcionar la clave de ubicación que desee y la palabra clave que se pasa a la consulta será MyTestMethod.

**Habilitar la herramienta de depuración de ayuda en el IDE**

Agregue la siguiente clave y valor del Registro:

::: moniker range="vs-2017"

**HKEY_CURRENT_USER,Software, Microsoft, VisualStudio, 15,0, Ayuda dinámica**

::: moniker-end

::: moniker range=">=vs-2019"

**HKEY_CURRENT_USER,Software, Microsoft, VisualStudio, 16,0, Ayuda dinámica**

::: moniker-end

Valor: Mostrar salida de depuración en datos comerciales: Sí

En el IDE, en el elemento de menú Ayuda, seleccione **Depurar contexto**de ayuda .

**Metadatos de contenido**

En la tabla siguiente, cualquier cadena que aparece entre corchetes es un marcador de posición que debe reemplazarse por un valor reconocido. Por ejemplo, \<en el nombre meta "Microsoft.Help.Locale" content "[código de idioma]" />, "[código de idioma]" debe reemplazarse por un valor como "en-us".

| Propiedad (representación HTML) | Descripción |
| - | - |
| \<metaname"Microsoft.Help.Locale" content"[idioma-código]" /> | Establece una configuración regional para este tema. Si esta etiqueta se utiliza en un tema, debe usarse una sola vez y debe insertarse encima de cualquier otra etiqueta de Ayuda de Microsoft. Si no se utiliza esta etiqueta, el texto del cuerpo del tema se indiza mediante el separador de palabras asociado a la configuración regional del producto, si se especifica; de lo contrario, se utiliza el separador de palabras en-us. Esta etiqueta cumple con ISOC RFC 4646. Para asegurarse de que la Ayuda de Microsoft funciona correctamente, use esta propiedad en lugar del atributo Language general. |
| \<metaname"Microsoft.Help.TopicLocale" content"[idioma-código]" /> | Establece una configuración regional para este tema cuando también se usan otras configuraciones regionales. Si esta etiqueta se utiliza en un tema, debe usarse una sola vez. Utilice esta etiqueta cuando el catálogo contenga contenido en más de un idioma. Varios temas de un catálogo pueden tener el mismo identificador, pero cada uno debe especificar un TopicLocale único. El tema que especifica un TopicLocale que coincide con la configuración regional del catálogo es el tema que se muestra en la tabla de contenido. Sin embargo, todas las versiones de idioma del tema se muestran en los resultados de búsqueda. |
| \<título>[Título]\</título> | Especifica el título de este tema. Esta etiqueta es necesaria y debe usarse una sola vez en un tema. Si el cuerpo del tema no \<contiene un div de título> sección, este título se muestra en el tema y en la tabla de contenido. |
| \<meta name "Microsoft.Help.Keywords" content"[aKeywordPhrase]"/> | Especifica el texto de un vínculo que se muestra en el panel de índice del Visor de Ayuda. Cuando se hace clic en el vínculo, se muestra el tema. Puede especificar varias palabras clave de índice para un tema o puede omitir esta etiqueta si no desea que los vínculos a este tema aparezcan en el índice. Las palabras clave "K" de versiones anteriores de la Ayuda se pueden convertir a esta propiedad. |
| \<metaname"Microsoft.Help.Id" content"[TopicID]"/> | Establece el identificador de este tema. Esta etiqueta es necesaria y debe usarse una sola vez en un tema. El identificador debe ser único entre los temas del catálogo que tienen la misma configuración regional. En otro tema, puede crear un vínculo a este tema mediante este identificador. |
| \<metaname"Microsoft.Help.F1" content"[System.Windows.Controls.Primitives.IRecyclingItemContainerGenerator]"/> | Especifica la palabra clave F1 para este tema. Puede especificar varias palabras clave F1 para un tema o puede omitir esta etiqueta si no desea que este tema se muestre cuando un usuario de la aplicación presione F1. Normalmente, solo se especifica una palabra clave F1 para un tema. Las palabras clave "F" de versiones anteriores de la Ayuda se pueden convertir a esta propiedad. |
| \<meta name "Descripción" content"[descripción del tema]" /> | Proporciona un breve resumen del contenido de este tema. Si esta etiqueta se utiliza en un tema, debe usarse una sola vez. La biblioteca de consultas tiene acceso a esta propiedad directamente; no se almacena en el archivo de índice. |
| metaname"Microsoft.Help.TocParent" content"[parent_Id]"/> | Especifica el tema primario de este tema en la tabla de contenido. Esta etiqueta es necesaria y debe usarse una sola vez en un tema. El valor es el Microsoft.Help.Id del elemento primario. Un tema puede tener una sola ubicación en la tabla de contenido. "-1" se considera el identificador de tema para la raíz de TCA. En [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)], esa página es la página de inicio del Visor de ayuda. Esta es la misma razón por la que agregamos específicamente TocParent-1 a algunos temas para asegurarnos de que aparecen en el nivel superior. La página de inicio del Visor de ayuda es una página del sistema, por lo que no se puede reemplazar. Si un VSP intenta agregar una página con un identificador de -1, puede agregarse al conjunto de contenido, pero el Visor de Ayuda siempre usará la página del sistema - Inicio del Visor de Ayuda |
| \<metaname"Microsoft.Help.TocOrder" content"[número entero positivo]"/> | Especifica dónde en la tabla de contenido aparece este tema en relación con sus temas del mismo nivel. Esta etiqueta es necesaria y debe usarse una sola vez en un tema. El valor es un entero. Un tema que especifica un entero de valor inferior aparece encima de un tema que especifica un entero de mayor valor. |
| \<metaname"Microsoft.Help.Product" content"[código de producto]"/> | Especifica el producto que se describe en este tema. Si esta etiqueta se utiliza en un tema, debe usarse una sola vez. Esta información también se puede proporcionar como un parámetro que se pasa al indizador de ayuda. |
| \<metaname"Microsoft.Help.ProductVersion" content"[número de versión]"/> | Especifica la versión del producto que se describe en este tema. Si esta etiqueta se utiliza en un tema, debe usarse una sola vez. Esta información también se puede proporcionar como un parámetro que se pasa al indizador de ayuda. |
| \<metaname"Microsoft.Help.Category" content"[string]"/> | Utilizado por los productos para identificar subsecciones de contenido. Puede identificar varias subsecciones para un tema o puede omitir esta etiqueta si no desea que los vínculos identifiquen ninguna subsección. Esta etiqueta se utiliza para almacenar los atributos de TargetOS y TargetFrameworkMoniker cuando un tema se convierte desde una versión anterior de la Ayuda. El formato del contenido es AttributeName:AttributeValue. |
| \<meta name"Microsoft.Help.TopicVersion content"[número de versión del tema]"/> | Especifica esta versión del tema cuando existen varias versiones en un catálogo. Dado que no se garantiza que Microsoft.Help.Id sea único, esta etiqueta es necesaria cuando existe más de una versión de un tema en un catálogo, por ejemplo, cuando un catálogo contiene un tema para .NET Framework 3.5 y un tema para .NET Framework 4 y ambos tienen la misma Microsoft.Help.Id. |
| \<metaname"SelfBranded" content"[TRUE o FALSE]"/> | Especifica si este tema usa el paquete de personalización de marca de inicio del Administrador de bibliotecas de ayuda o un paquete de personalización de marca específico para el tema. Esta etiqueta debe ser TRUE o FALSE. Si es TRUE, el paquete de personalización de marca para el tema asociado reemplaza el paquete de personalización de marca que se establece cuando se inicia el Administrador de la biblioteca de ayuda para que el tema se represente según lo previsto, incluso si difiere de la representación de otro contenido. Si es FALSE, el tema actual se representa según el paquete de personalización de marca que se establece cuando se inicia el Administrador de bibliotecas de ayuda. De forma predeterminada, el Administrador de bibliotecas de ayuda asume que la automarca es false a menos que la variable SelfBranded se declare como TRUE; por lo tanto, usted \<no tiene que declarar el nombre meta "SelfBranded" content "FALSE"/>. |

## <a name="create-a-branding-package"></a>Crear un paquete de marca

La versión de Visual Studio abarca varios productos de Visual Studio diferentes, incluidos los shells aislados e integrados para los socios de Visual Studio.  Cada uno de estos productos requiere cierto grado de soporte de personalización de marca de contenido de Ayuda basado en temas, único en el producto.  Por ejemplo, los temas de Visual Studio deben tener una presentación de marca coherente, mientras que SQL StudioSQL Studio, que ajusta el Shell ISO, requiere su propia personalización de marca de contenido de Ayuda única para cada tema.  Un socio de Shell integrado puede desear que sus temas de Ayuda estén dentro del contenido de Ayuda del producto primario de Visual Studio mientras mantiene su propia marca de tema.

Los paquetes de personalización de marca los instala el producto que contiene el Visor de ayuda.  Para productos de Visual Studio:

- > Branding_\<El paquete de idioma del Visor de ayuda (por ejemplo, C:-Archivos de programa (x86)-Microsoft Help Viewer-v2.3) del Visor de ayuda (por ejemplo: C:-Archivos de programa (x86)-Microsoft Help Viewer-v2.3) del paquete de idioma del Visor de ayuda.  Esto se utiliza para los casos en los que el paquete de personalización de marca del producto no está instalado (no se ha instalado ningún contenido) o en los que el paquete de personalización de marca instalado está dañado.  Los elementos de Visual Studio (logotipo y comentarios) se omiten cuando se usa el paquete de personalización de marca de reserva raíz de la aplicación.

- Cuando se instala contenido de Visual Studio desde el servicio de paquete de contenido, también se instala un paquete de personalización de marca (por primera vez escenario de instalación de contenido).  Si hay una actualización del paquete de personalización de marca, la actualización se instala cuando se produce la siguiente actualización de contenido o la acción de instalación del paquete adicional.

El Visor de Ayuda de Microsoft admite la personalización de marca de temas en función de los metadatos del tema.

- Donde los metadatos del tema definen la marca de sí mismos, representan el tema tal como está, no hacen nada (en lo que respecta a la personalización de marca).

- Donde los metadatos del tema definen la marca propia: false, use el paquete de personalización de marca asociado con el valor de metadatos TopicVendor.

- Donde los metadatos del tema definen el nombre\< "Microsoft.Help.TopicVendor" nombre del paquete de personalización de marca de contenido en el proveedor MSHA>, use el paquete de personalización de marca definido en el valor de contenido.

- Dentro del catálogo de Visual Studio, hay una aplicación de prioridad de paquetes de personalización de marca.  Primero se aplica la personalización de marca predeterminada de Visual Studio y, a continuación, si se define en los metadatos del tema y se admite con el paquete de personalización de marca asociado (como se define en la msha de instalación), la personalización de marca definida por el proveedor se aplica como invalidación.

Los elementos de marca suelen dividirse en tres categorías principales:

- Elementos de encabezado (por ejemplo, enlace de comentarios, texto de exención de responsabilidad condicional, logotipo)

- Comportamientos de contenido (por ejemplo, elementos de texto de control expand/collapse y elementos de fragmento de código)

- Elementos de pie de página (ejemplo Copyright)

Los elementos considerados como elementos de marca incluyen (detallado en esta especificación):

- Logotipo de catálogo/producto (ejemplo, Visual Studio)

- Enlace de comentarios y elementos de correo electrónico

- Texto de exención de responsabilidad

- Texto de derechos de autor

Los archivos auxiliares del paquete de personalización de marca del Visor de Ayuda de Visual Studio incluyen:

- Gráficos (logos, iconos, etc.)

- Branding.js - archivos de script que admiten comportamientos de contenido

- Branding.xml: cadenas que se usan de forma coherente en el contenido del catálogo.  Nota: para los elementos de texto de localización\<de Visual Studio en el archivo branding.xml, incluya _locID " valor único>"

- Branding.css - definiciones de estilo para la coherencia de la presentación

- Printing.css - definiciones de estilo para una presentación impresa coherente

Como se indicó anteriormente, los paquetes de personalización de marca están asociados con el tema:

- Cuando SelfBranded - false se define en los metadatos, el tema hereda el paquete de personalización de marca del catálogo

- O cuando SelfBranded es false y hay un paquete de personalización de marca único definido en el MSHA y disponible cuando el contenido está instalado

Para vsP que implementan paquetes de personalización de marca personalizados (contenido de VSP, SelfBranded-True), una manera de continuar es comenzar con el paquete de personalización de marca de reserva (instalado con el Visor de ayuda) y cambiar el nombre del archivo según corresponda.  La\<Branding_ locale>.mshc es un archivo zip con la extensión de archivo cambiada a .mshc, así que simplemente cambie la extensión de .mshc a .zip y extraiga el contenido.  Consulte a continuación los elementos del paquete de personalización de marca y modifíquelo según corresponda (por ejemplo, cambie el logotipo al logotipo de VSP y la referencia al logotipo en el archivo Branding.xml, actualice Branding.xml por detalles de VSP, etc.).

Cuando se realicen todas las modificaciones, cree un archivo zip que contenga los elementos de personalización de marca deseados y cambie la extensión a .mshc.

Para asociar el paquete de personalización de marca personalizado, cree MSHA, que contiene la referencia al archivo mshc de personalización de marca junto con el contenido mshc (que contiene los temas).  Vea a continuación "MSHA" para saber cómo crear un MSHA básico.

El archivo Branding.xml contiene una lista de elementos que se usan \<para representar de forma coherente elementos específicos de un tema cuando el tema contiene el nombre meta"Microsoft.Help.SelfBranded" content"false"/>.  La lista de elementos de Visual Studio en el archivo Branding.xml se muestra a continuación.  Esta lista está diseñada para usarse como plantilla para los adoptantes de ISO Shell, donde modifican estos elementos (por ejemplo, logotipo, comentarios y derechos de autor) para satisfacer sus propias necesidades de marca de productos.

Nota: las variables que se indican por la palabra "-n" tienen dependencias de código - quitar o cambiar estos valores causará errores y posiblemente bloqueo de la aplicación. Los identificadores de localización (ejemplo_locID"codesnippet.n") se incluyen en el paquete de personalización de marca de Visual Studio.

**Branding.xml**

| | |
| - | - |
| Característica: | **CollapsibleArea** |
| Uso: | Expandir contrae el texto del control de contenido |
| **Elemento** | **Value** |
| ExpandText | Expanda |
| CollapseText | Contraer |
| Característica: | **CodeSnippet** |
| Uso: | Texto de control de fragmento de código.  Nota: El contenido del fragmento de código con el espacio "No rompedor" se cambiará al espacio. |
| **Elemento** | **Value** |
| CopyToClipboard | Copiar al Portapapeles |
| ViewColorizedText | Ver coloreado |
| CombinedVBTabDisplayLanguage | Visual Basic (ejemplo) |
| VBDeclaration | Declaración |
| VBUsage | Uso |
| Característica: | **Comentarios, pie de página y logotipo** |
| Uso: | Proporcione un control de comentarios para que el cliente proporcione comentarios sobre el tema actual a través de correo electrónico.  Texto de copyright para el contenido.  Definición del logotipo. |
| **Elemento** | **Valor (estas cadenas se pueden modificar para satisfacer las necesidades del adoptante de contenido.)** |
| Copyright | © 2013 Microsoft Corporation. Todos los derechos reservados. |
| SendFeedback | \<un href"{0} {1} ">\<Enviar comentarios /a> sobre este tema a Microsoft. |
| FeedbackLink | |
| LogoTitle | [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] |
| LogoFileName | vs_logo_bk.gif |
| LogoFileNameHC | vs_logo_wh.gif |
| Característica: | **Renuncia** |
| Uso: | Conjunto de descargos de responsabilidad específicos para contenido traducido por máquina. |
| **Elemento** | **Value** |
| MT_Editable | Este artículo fue traducido a máquina. Si tiene una conexión a Internet, seleccione "Ver este tema en línea" para ver esta página en modo editable con el contenido original en inglés al mismo tiempo. |
| MT_NonEditable | Este artículo fue traducido a máquina. Si tiene una conexión a Internet, seleccione "Ver este tema en línea" para ver esta página en modo editable con el contenido original en inglés al mismo tiempo. |
| MT_QualityEditable | Este artículo fue traducido manualmente. Si tiene una conexión a Internet, seleccione "Ver este tema en línea" para ver esta página en modo editable con el contenido original en inglés al mismo tiempo. |
| MT_QualityNonEditable | Este artículo fue traducido manualmente. Si tiene una conexión a Internet, seleccione "Ver este tema en línea" para ver esta página en modo editable con el contenido original en inglés al mismo tiempo. |
| MT_BetaContents | Este artículo fue traducido por máquina para una versión preliminar. Si tiene una conexión a Internet, seleccione "Ver este tema en línea" para ver esta página en modo editable con el contenido original en inglés al mismo tiempo. |
| MT_BetaRecycledContents | Este artículo fue traducido manualmente para una versión preliminar. Si tiene una conexión a Internet, seleccione "Ver este tema en línea" para ver esta página en modo editable con el contenido original en inglés al mismo tiempo. |
| Característica: | **LinkTable** |
| Uso: | Soporte para enlaces de temas en línea |
| **Elemento** | **Value** |
| LinkTableTitle | Tabla de enlaces |
| TopicEnuLinkText | Vea la\<versión en inglés /a> de este tema que está disponible en el equipo. |
| TopicOnlineLinkText | Vea este \<tema un{0}href" ">{1} en línea\</a> |
| OnlineText | En línea |
| Característica: | **Control de audio de vídeo** |
| Uso: | Mostrar elementos y texto para contenido de vídeo |
| **Elemento** | **Value** |
| MultiMediaNotSupported | Internet Explorer 9 o superior {0} debe estar instalado para admitir contenido. |
| Videotext | mostrar vídeo |
| AudioText | transmisión de audio |
| OnlineVideoLinkText | \<p>Para ver el vídeo {0} \<asociado a este{1}tema, haga clic en un href" ">{2}aquí\</a>. \</p> |
| OnlineAudioLinkText | \<p>Para escuchar el audio asociado {0} \<a este{1}tema, {2}\<haga clic en un href" ">aquí /a>. \</p> |
| Característica: | **Control de contenido no instalado** |
| Uso: | Elementos de texto (cadenas) utilizados para la representación de contentnotinstalled.htm |
| **Elemento** | **Value** |
| ContentNotInstalledTitle | No se encontró contenido en el equipo. |
| ContentNotInstalledDownloadContentText | \<p>Para descargar contenido \<en su{0}ordenador, un href" ">{1} haga clic en la pestaña\<Administrar /a>. \</p> |
| ContentNotInstalledText | \<p>No hay contenido instalado en el equipo. Consulte el administrador para obtener información sobre la instalación de contenido de la Ayuda local. \</p> |
| Característica: | **Tema no encontrado control** |
| Uso: | Elementos de texto (cadenas) utilizados para la representación de topicnotfound.htm |
| **Elemento** | **Value** |
| TopicNotFoundTitle | No se puede encontrar el tema solicitado en el equipo. |
| TopicNotFoundViewOnlineText | \<p>El tema que solicitó no se \<encontró en{0} {1} su equipo,\<pero puede un href " ">ver el tema en línea /a>. \</p> |
| TopicNotFoundDownloadContentText | \<p>Consulte el panel de navegación \<para obtener{0}vínculos a temas similares, o un href" ">{1} haga clic en la pestaña\<Administrar /a> para descargar contenido en el equipo. \</p> |
| TopicNotFoundText | \<p>El tema que solicitó no se encontró en su equipo. \</p> |
| Característica: | **Tema Control dañado** |
| Uso: | Elementos de texto (cadenas) utilizados para la representación de topiccorrupted.htm |
| **Elemento** | **Value** |
| TopicCorruptedTitle | No se puede mostrar el tema solicitado. |
| TopicCorruptedViewOnlineText | \<p>Visor de Ayuda no puede mostrar el tema solicitado. Puede haber un error en el contenido del tema o una dependencia del sistema subyacente. \</p> |
| Característica: | **Control de la página de inicio** |
| Uso: | Texto que admite la visualización del contenido del nodo de nivel superior del Visor de ayuda. |
| **Elemento** | **Value** |
| HomePageTitle | Ayuda al espectador a inicio |
| HomePageIntroduction | \<p>Bienvenido al Visor de Ayuda de Microsoft, una fuente esencial de información para todos los usuarios de herramientas, productos, tecnologías y servicios de Microsoft. El Visor de ayuda le da acceso a información de cómo hacer y hacer referencia, código de ejemplo, artículos técnicos y mucho más. Para encontrar el contenido que necesita, examine la tabla de contenido, use la búsqueda de texto completo o navegue por el contenido mediante el índice de palabras clave. \</p> |
| HomePageContentInstallText | \<p \<>br />\<Utilice a{0} {1} href"" ">Administrar\<contenido\</una pestaña> para hacer lo siguiente: ul>\<li>Agregar contenido a su equipo. \</li \<>>Compruebe si hay actualizaciones de su contenido local. \</li \<>>Eliminar contenido de su ordenador. \</li \<>/ul>\</p> |
| HomePageInstalledBooks | Libros instalados |
| HomePageNoBooksInstalado | No se encontró contenido en el equipo. |
| HomePageHelpSettings | Configuración del contenido de la ayuda |
| HomePageHelpSettingsText | \<p>Su configuración actual es ayuda local. El Visor de Ayuda muestra el contenido que ha instalado en el equipo. \<br />Para cambiar el origen del contenido de \<la Ayuda,{0}en la barra\<de menús de Visual Studio, elija span style" ">Help, Set Help Preference /span>. \<br />\</p> |
| Megabyte | MB |

**branding.js**

El archivo branding.js contiene JavaScript utilizado por los elementos de personalización de marca del Visor de Ayuda de Visual Studio.  A continuación se muestra una lista de los elementos de personalización de marca y la función JavaScript compatible.  Todas las cadenas que se van a localizar para este archivo se definen en la sección "Cadenas localizables" en la parte superior de este archivo.  Se ha creado un archivo ICL para cadenas loc dentro del archivo branding.js.

||||
|-|-|-|
|**Característica de marca**|**Función JavaScript**|**Descripción**|
|Var...||Definición de variables|
|Obtener el idioma del código de usuario|setUserPreferenceLang|asigna un índice a lenguaje de código|
|Establecer y obtener valores de cookies|getCookie, setCookie||
|Miembro heredado|changeMembersLabel|Expandir/contraer miembro heredado|
|Cuando SelfBranded-False|Onload|Lea la cadena de consulta para comprobar si se trata de una solicitud de impresión.  Establezca todos los códigos para enfocar la pestaña preferida por el usuario.  Si se trata de una solicitud de impresión, establezca isPrinterFriendly en true. Compruebe si hay modo de alto contraste.|
|Fragmento de código|addSpecificTextLanguageTagSet||
||getIndexFromDevLang||
||ChangeTab||
||setCodesnippetLang||
||setCurrentLang||
||CopyToClipboard||
|CollapsibleArea|addToCollapsibleControlSet|escribir todo el objeto de control contraíble en la lista.|
||CA_Click|en función del estado del área contraíble, define qué imagen y texto presentar|
|Soporte de contraste para logo|isBlackBackground()|Se llama para determinar si el fondo es negro.  Sólo es preciso cuando está en modo de alto contraste.|
||isHighContrast()|utilizar un palmo de color para detectar el modo de alto contraste|
||onHighContrast(negro)|Se llama cuando se detecta un alto contraste|
|Funcionalidad LST|||
||addToLanSpecTextIdSet(id)||
||updateLST(currentLang)||
||getDevLangFromCodeSnippet(lang)||
|Funcionalidad MultiMedia|subtítulo (comienzo, fin, texto, estilo)||
||findAllMediaControls(normalizedId)||
||getActivePlayer(normalizedId)||
||captionsOnOff(id)||
||toSeconds(t)||
||getAllComments(node)||
||styleRectify(styleName, styleValue)||
||showCC(id)||
||subtítulo (id)||

**ARCHIVOS HTM**

El paquete de personalización de marca contiene un conjunto de archivos HTM que admiten escenarios para comunicar información clave a los usuarios de contenido de Ayuda, por ejemplo, una página de inicio que contiene una sección que describe qué conjuntos de contenido están instalados y páginas que le dicen al usuario cuándo no se pueden encontrar temas en el conjunto local de temas. Estos archivos HTM se pueden modificar por producto.  Los proveedores de ISO Shell pueden tomar el paquete de personalización de marca predeterminado y cambiar el comportamiento y el contenido de estas páginas para que se ajusten a sus necesidades.  Estos archivos hacen referencia a su respectivo paquete de personalización de marca para que las etiquetas de marca obtengan el contenido correspondiente del archivo branding.xml.

||||
|-|-|-|
|**Archivo**|**Uso**|**Fuente de contenido mostrada**|
|homepage.htm|Esta es una página que muestra el contenido instalado actualmente y cualquier otro mensaje apropiado para presentar al usuario acerca de su contenido.  Este archivo tiene el atributo de metadatos adicional "Microsoft.Help.Id" content"-1" que coloca este contenido en la parte superior del contenido local TOC.||
||<META_HOME_PAGE_TITLE_ADD />|Branding.xml, \<etiqueta HomePageTitle>|
||<HOME_PAGE_INTRODUCTION_SECTION_ADD />|Branding.xml, \<etiqueta HomePageIntroduction>|
||<HOME_PAGE_CONTENT_INSTALL_SECTION_ADD />|Branding.xml, \<etiqueta HomePageContentInstallText>|
||<HOME_PAGE_BOOKS_INSTALLED_SECTION_ADD />|Encabezado sección Branding.xml etiqueta\<HomePageInstalledBooks>, los \<datos generados desde la aplicación, HomePageNoBooksInstalled> cuando no hay libros instalados.|
||<HOME_PAGE_SETTINGS_SECTION_ADD />|Sección de encabezado \<Branding.xml etiqueta HomePageHelpSettings>, texto \<de sección HomePageHelpSettingsText>.|
|topiccorrupted.htm|Cuando existe un tema en el conjunto local, pero por alguna razón no se puede mostrar (contenido dañado).||
||<META_TOPIC_CORRUPTED_TITLE_ADD />|Branding.xml, \<etiqueta TopicCorruptedTitle>|
||TOPIC_CORRUPTED_SECTION_ADD </>|Branding.xml, \<etiqueta TopicCorruptedViewOnlineText>|
|topicnotfound.htm|Cuando no se encuentra un tema en el conjunto de contenido local, ni está disponible en línea||
||<META_TOPIC_NOT_FOUND_TITLE_ADD />|Branding.xml, \<etiqueta TopicNotFoundTitle>|
||<META_TOPIC_NOT_FOUND_ID_ADD />|Branding.xml, \<etiqueta TopicNotFoundViewOnlineText \<> + TopicNotFoundDownloadContentText>|
||<TOPIC_NOT_FOUND_SECTION_ADD />|Branding.xml, \<etiqueta TopicNotFoundText>|
|contentnotinstalled.htm|Cuando no hay ningún contenido local instalado para el producto.||
||<META_CONTENT_NOT_INSTALLED_TITLE_ADD />|Branding.xml, \<etiqueta ContentNotInstalledTitle>|
||<META_CONTENT_NOT_INSTALLED_ID_ADD />|Branding.xml, \<etiqueta ContentNotInstalledDownloadContentText>|
||CONTENT_NOT_INSTALLED_SECTION_ADD de </>|Branding.xml, \<etiqueta ContentNotInstalledText>|

**Archivos CSS**

El paquete de personalización de marca del Visor de Ayuda de Visual Studio contiene dos archivos css para admitir la presentación de contenido coherente de la Ayuda de Visual Studio:

- Branding.css - contiene elementos css para la representación donde SelfBranded-false

- Printer.css - contiene elementos css para la representación donde SelfBranded-false

Los archivos Branding.css incluyen definiciones para la presentación de temas de Visual\<Studio (caveat es que el archivo branding.css contenido en la configuración regional de Branding_>.mshc del servicio de paquetepuede cambiar).

**Archivos gráficos**

El contenido de Visual Studio muestra un logotipo de Visual Studio, así como otros gráficos.  La lista completa de archivos gráficos en el paquete de personalización de marca visor de Ayuda de Visual Studio se muestra a continuación.

||||
|-|-|-|
|**Archivo**|**Uso**|**Ejemplos**|
|clear.gif|Se utiliza para renderizar el área plegable||
|footer_slice.gif|Presentación del pie de página||
|info_icon.gif|Se utiliza al mostrar información|Renuncia de responsabilidades|
|online_icon.gif|Este icono debe asociarse con enlaces en línea||
|tabLeftBD.gif|Se utiliza para representar el contenedor de fragmentos de código||
|tabRightBD.gif|Se utiliza para representar el contenedor de fragmentos de código||
|vs_logo_bk.gif|Se utiliza para las referencias de logotipo \<de contraste normal tal como se define en la etiqueta Branding.xml LogoFileName>.  Para los productos de Visual Studio, el nombre del logotipo es vs_logo_bk.gif.||
|vs_logo_wh.gif|Se utiliza para referencias de logotipos \<altos normales tal como se define en la etiqueta Branding.xml LogoFileNameHC>.  Para los productos de Visual Studio, el nombre del logotipo es vs_logo_wh.gif.||
|ccOff.png|Gráfico de subtítulos||
|ccOn.png|Gráfico de subtítulos||
|ImageSprite.png|Se utiliza para renderizar el área plegable|expandido o colapso gráfico|

## <a name="deploy-a-set-of-topics"></a>Implementar un conjunto de temas

Este es un tutorial sencillo y rápido para crear un conjunto de implementación de contenido del Visor de Ayuda compuesto por un archivo MSHA y el conjunto de cabinas o MSHCs que contienen los temas. El MSHA es un archivo XML que describe un conjunto de cabs o archivos MSHC. El Visor de Ayuda puede leer el MSHA para obtener una lista de contenido (el archivo . CAB o . MSHC) disponibles para la instalación local.

Esto es sólo una imprimación que describe el esquema XML muy básico para el Visor de ayuda MSHA.  Hay un ejemplo de implementación debajo de esta breve descripción general y ejemplo HelpContentSetup.msha.

El nombre de la MSHA, a los efectos de este primer, es HelpContentSetup.msha (el nombre del archivo puede ser cualquier cosa, con la extensión . MSHA). HelpContentSetup.msha (ejemplo a continuación) debe contener una lista de las cabinas o MSHC disponibles.  El tipo de archivo debe ser coherente dentro de MSHA (no admite una combinación de tipos de archivo MSHA y CAB). Para cada CAB o MSHC, \<debe haber una clase div "paquete">... \</div> (véase el ejemplo a continuación).

Nota: en el ejemplo de implementación siguiente, hemos incluido el paquete de personalización de marca. Esto es fundamental para incluir para obtener los elementos de representación de contenido de Visual Studio y los comportamientos de contenido necesarios.

Ejemplo de archivo HelpContentSetup.msha: (Reemplazar "nombre de conjunto de contenido 1" y "nombre de conjunto de contenido 2", etc. por sus nombres de archivo.)

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

1. Crear carpeta local, algo así como "C:-SampleContent"

2. En este ejemplo, usaremos archivos MSHC para contener los temas.  Un MSHC es un zip con la extensión de archivo cambiado de .zip a . MSHC.

3. Cree el siguiente HelpContentSetup.msha como un archivo de texto (el bloc de notas se utilizó para crear el archivo) y guárdelo en la carpeta indicada anteriormente (consulte el paso 1).

La clase "Branding" existe y es única. El mshc de branding se incluye en este primer para que el contenido instalado tenga personalización de marca, y los comportamientos de contenido contenido contenidos en los MSHC tendrán los elementos de soporte adecuados contenidos en el paquete de personalización de marca. Sin esto, se producirán errores cuando el sistema busque elementos de soporte que no formen parte del contenido rasgado (instalado).

Para obtener el paquete de personalización de marca de Visual Studio, copie el archivo Branding_en-US.mshc en c:-Archivos de programa (x86)-Microsoft Help Viewer-v2.3- en la carpeta de trabajo.

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

Usar y ampliar los pasos anteriores permitirá a los VSP implementar sus conjuntos de contenido para el Visor de Ayuda de Visual Studio.

### <a name="add-help-to-the-visual-studio-shell-integrated-and-isolated"></a>Agregar ayuda al Shell de Visual Studio (integrado y aislado)

**Introducción**

En este tutorial se muestra cómo incorporar contenido de Ayuda en una aplicación de Shell de Visual Studio y, a continuación, implementarlo.

**Requisitos**

1. [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)]

2. [Visual Studio 2013 Aislado Shell Redist](https://visualstudio.microsoft.com/vs/older-downloads/isolated-shell/)

**Información general**

El [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] Shell es una [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] versión del IDE en la que puede basar una aplicación. Estas aplicaciones contienen el Shell aislado junto con las extensiones que cree. Use plantillas de proyecto de Shell [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] aislado, que se incluyen en el SDK, para crear extensiones.

Los pasos básicos para crear una aplicación basada en Shell aislado y su Ayuda:

1. Obtenga [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] el Shell ISO redistribuible (una descarga de Microsoft).

2. En Visual Studio, cree una extensión de Ayuda basada en el Shell aislado, por ejemplo, la extensión de Ayuda de Contoso que se describe más adelante en este tutorial.

3. Envuelva la extensión y el Shell ISO redistribuible en un MSI de implementación (una configuración de aplicación). Este tutorial no incluye un paso de configuración.

Cree un almacén de contenido de Visual Studio. Para el escenario Shell integrado, cambie Visual Studio12 por el nombre del catálogo de productos de la siguiente manera:

- Cree la carpeta C:-ProgramData-Microsoft-HelpLibrary2-Catalogs-VisualStudio15.

- Cree un archivo denominado CatalogType.xml y agréguelo a la carpeta. El archivo debe contener las siguientes líneas de código:

    ```xml
    <?xml version="1.0" encoding="UTF-8"?>
    <catalogType>UserManaged</catalogType>
    ```

Defina el almacén de contenido en el registro. Para el Shell integrado, cambie VisualStudio15 al nombre del catálogo de productos:

- HKLM-SOFTWARE-Wow6432Node-Microsoft-Help-v2.3-Catalogs-VisualStudio15

   Clave: LocationPath Valor de cadena: C:-ProgramData-Microsoft-HelpLibrary2-Catalogs-VisualStudio15-

- HKLM-SOFTWARE-Wow6432Node-Microsoft-Help-v2.3-Catalogs-VisualStudio15-en-US

   Clave: Valor de [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] cadena CatalogName: Documentación

**Crear el proyecto**

Para crear una extensión de vaciado aislado:

1. En Visual Studio, en **Archivo**, elija **Nuevo proyecto**, en Otros tipos de **proyecto,** **Extensibilidad**y, a continuación, elija **Visual Studio Shell Isolated**. Asigne al `ContosoHelpShell`proyecto el nombre ) para crear un proyecto de extensibilidad basado en la plantilla Shell aislado de Visual Studio.

2. En el Explorador de soluciones, en el proyecto ContosoHelpShellUI, en la carpeta Archivos de recursos, abra ApplicationCommands.vsct. Asegúrese de que esta línea está comentada (busque "No_Help"):`<!-- <define name="No_HelpMenuCommands"/> -->`

3. Elija la clave F5 para compilar y ejecutar **Debug**. En la instancia experimental del IDE de Shell aislado, elija el menú **Ayuda.** Asegúrese de que aparecen los comandos **Ver ayuda**, Agregar y quitar contenido de **ayuda**y Establecer preferencia de **ayuda.**

4. En el Explorador de soluciones, en el proyecto ContosHelpShell, en la carpeta Personalización de Shell, abra ContosoHelpShell.pkgdef. Para definir el catálogo de Ayuda de Contoso, agregue las siguientes líneas:

    ```
     [$RootKey$\Help]
    "Product"="Contoso"
    "Catalog"="Contoso"
    "Version"="100"
    "BrandingPackage"="ContosoBrandingPackage.mshc"
    ```

5. En el Explorador de soluciones, en el proyecto ContosHelpShell, en la carpeta Personalización de Shell, abra ContosoHelpShell.Application.pkgdef. Para habilitar la Ayuda de F1, agregue las siguientes líneas:

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

6. En el Explorador de soluciones, en el menú contextual de la solución ContosoHelpShell, elija el elemento de menú **Propiedades.** En **Propiedades de configuración**, seleccione Configuration **Manager**. En la columna **Configuración,** cambie cada valor de "Depurar" a "Liberar".

7. Compile la solución. Esto crea un conjunto de archivos en una carpeta de versión, que se usará en la siguiente sección.

Para probar esto como si estuviera implementado:

1. En el equipo en el que va a implementar Contoso, instale el Shell ISO descargado (desde arriba).

2. Cree una \\carpeta en .Archivos de\\programa (x86) y asímóquela. `Contoso`

3. Copie el contenido de la carpeta \\de la versión ContosoHelpShell en la carpeta .archivos de programa (x86)-Contoso.

4. Inicie el Editor del Registro seleccionando `Regedit` **Ejecutar** en el menú **Inicio** e introduciendo . En el editor del Registro, elija **Archivo**y, a continuación, **Importar**. Vaya a la carpeta del proyecto ContosoHelpShell. En la subcarpeta ContosoHelpShell, elija ContosoHelpShell.reg.

5. Crear un almacén de contenido:

    Para Shell ISO: cree un almacén de contenido de Contoso C:-ProgramData-Microsoft-HelpLibrary2-Catalogs-ContosoDev12

    Para [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] el Shell integrado, cree la carpeta C:-ProgramData-Microsoft-HelpLibrary2-Catalogs-VisualStudio15

6. Cree CatalogType.xml y agréguelo al almacén de contenido (paso anterior) que contiene:

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <catalogType>UserManaged</catalogType>
   ```

7. Agregue las siguientes claves del Registro:

    HKLM-SOFTWARE-Wow6432Node-Microsoft-Help-v2.3-Catalogs-VisualStudio15Key: LocationPath Valor de cadena:

    Para ISO Shell:

    C:ProgramDataMicrosoftHelpLibrary2CatalogsVisualStudio15

    [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)]Shell integrado:

    C:ProgramDataMicrosoftHelpLibrary2CatalogsVisualStudio15en-US

    Clave: Valor de [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] cadena CatalogName: Documentación. Para ISO Shell, este es el nombre del catálogo.

8. Copie el contenido (cabs o MSHC y MSHA) en una carpeta local.

9. Ejemplo de línea de comandos de Shell integrado para probar el almacén de contenido. Para ISO Shell, cambie el catálogo y lanzarlos los valores según corresponda para que coincidan con el producto.

     "C:-Archivos de programa (x86)-Microsoft Help Viewer-v2.3-HlpViewer.exe" /catalogName VisualStudio15 /helpQuery method-"page&id-ContosoTopic0" /launchingApp Microsoft,VisualStudio,12.0

10. Inicie la aplicación Contoso (desde la raíz de la aplicación Contoso). En ISO Shell, elija el elemento de menú **Ayuda** y cambie **Establecer preferencia** de ayuda para usar la **Ayuda local**.

11. En el shell, elija el elemento de menú **Ayuda** y, a continuación, **Ver ayuda**. El visor de Ayuda local debe iniciarse. Elija la pestaña **Manage Content (Administrar contenido).** En **Origen de instalación**, elija el botón de opción **Disco.** Elija el botón **...** y vaya a la carpeta local que contiene el contenido de Contoso (copiado en la carpeta local en el paso anterior). Elija HelpContentSetup.msha. Contoso ahora debe aparecer como un libro en las selecciones de libros. Elija **Add**y, a continuación, elija el botón **Update** (esquina inferior derecha).

12. En el IDE de Contoso, elija la tecla F1 para probar la funcionalidad de F1.

## <a name="additional-resources"></a>Recursos adicionales

Para la API de tiempo de ejecución, consulte API de ayuda de [Windows](/previous-versions/windows/desktop/helpapi/helpapi-portal).

Para obtener más información sobre cómo aprovechar la API de ayuda, consulte Ejemplos de código del Visor de [ayuda.](https://marketplace.visualstudio.com/items?itemName=RobChandlerHelpMVP.HelpViewer20CodeExamples)

Puede enviar sugerencias de características en [la Comunidad de desarrolladores](https://developercommunity.visualstudio.com/content/idea/post.html?space=8).
