---
title: SDK del Visor de Ayuda de Microsoft | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 620d7dcd-d462-475e-a449-fbfa06ff12c5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 47788ccd2fb1bd03ce2f2981289d51f0d625b6a9
ms.sourcegitcommit: f685fa5e2df9dc307bf1230dd9dc3288aaa408b5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2018
ms.locfileid: "36234678"
---
# <a name="microsoft-help-viewer-sdk"></a>SDK del Visor de Ayuda de Microsoft
En este artículo contiene las siguientes tareas para los integradores del Visor de Ayuda de Visual Studio:  
  
-   Creación de un tema (soporte de F1)  
  
-   Creación de un paquete de personalización de marca de contenido del Visor de ayuda  
  
-   Implementación de un conjunto de artículos  
  
-   Agregar ayuda a Visual Studio shell (integrado o aislado)  
  
-   Recursos adicionales  
  
### <a name="creating-a-topic-f1-support"></a>Creación de un tema (soporte de F1)  
En esta sección se proporciona información general de los componentes de un tema presentado, los requisitos del tema, una breve descripción de cómo crear un tema (incluidos los requisitos de soporte técnico de F1) y, finalmente, un tema de ejemplo con el resultado representado.  
  
**Introducción al Visor de tema de ayuda**  
  
Cuando se llama a un tema para la representación, el Visor de ayuda obtiene los elementos del paquete de personalización de marca que están asociados con el tema en el momento de la instalación o la última actualización, junto con el tema de XHTML y combina los dos que resulta en la vista de contenido presentada (personalización de marca de datos + datos de tema).  El paquete de personalización de marca contiene los logotipos, compatibilidad con los comportamientos del contenido y el texto de personalización de marca (copyright, etcetera.).  Para obtener más información acerca de los elementos del paquete de personalización de marca, vea "Crear el paquete de personalización de marca" a continuación.  En caso de que no hay ningún paquete de personalización de marca asociado al tema, el Visor de ayuda usará el paquete de personalización de marca reserva ubicado en la raíz de la aplicación Visor de ayuda (Branding_en-US.mshc).  
  
**Requisitos de tema del Visor de ayuda**  
  
Para representarse correctamente en el Visor de ayuda, el contenido sin procesar del tema debe ser XHTML 1.1 básica de W3C.  
  
Normalmente, un tema contiene dos secciones:  
  
-   Metadatos (consulte la referencia de metadatos de contenido): datos sobre el tema, por ejemplo, el Id. único del tema, el valor de palabra clave, el Id. de tabla de contenido del tema primario identificador de nodo, etcetera.  
  
-   Contenido del cuerpo: compatibles con XHTML 1.1 básica de W3C, que incluye admite los comportamientos del contenido (área contraíble, fragmento de código, etcetera. A continuación se muestra una lista completa).  
  
Paquete de personalización de marca de Visual Studio admiten controles:  
  
-   Vínculos  
  
-   CodeSnippet  
  
-   CollapsibleArea  
  
-   Miembro heredado  
  
-   LanguageSpecificText  
  
Cadenas de idioma compatible (no distingue mayúsculas de minúsculas):  
  
-   JavaScript  
  
-   CSharp o c#  
  
-   cplusplus o Visual c++ o c ++  
  
-   JScript  
  
-   VisualBasic o vb  
  
-   f # o fsharp o fs  
  
-   otros - una cadena que representa un nombre de lenguaje  
  
**Creación de un tema del Visor de ayuda**  
  
Crear un nuevo documento XHTML denominado ContosoTopic4.htm e incluyen la etiqueta de título (abajo).  
  
```html  
<html>  
<head>  
<title>Contoso Topic 4</title>  
</head>  
  
<body>  
  
</body>  
</html>  
  
```  
  
A continuación, agregar datos para definir cómo se presentarán (propio con la marca o no), el tema de cómo hacer referencia en este tema para F1, donde existe en este tema dentro de la tabla de contenido, su identificador (por referencia de vínculo por otros temas), etcetera.  Consulte la tabla "Metadatos de contenido" a continuación para obtener una lista completa de metadatos admitidos.  
  
-   En este caso, usaremos nuestro propio paquete de personalización de marca, una variante del paquete de personalización de marca en el Visor de Ayuda de Visual Studio.  
  
-   Agregue el nombre de metadatos de F1 y valor (contenido de "Microsoft.Help.F1" = "ContosoTopic4") que coincidirá con el valor de F1 proporcionado en la bolsa IDE.  (Consulte la sección de soporte técnico de F1 para obtener más información).   Este es el valor que coincida con la tecla F1 llamar desde el IDE para mostrar de este tema cuando se elige la tecla F1 en el IDE.  
  
-   Agregue el identificador de tema. Se trata de la cadena que se utiliza en otros temas para vincular a este tema.  Es el identificador de Visor de ayuda para este tema.  
  
-   Para la tabla de contenido, agregue el nodo de elemento primario de este tema para definir dónde aparecerá este nodo de tabla de contenido del tema.  
  
-   La tabla de contenido, agregue el orden de los nodos de este tema. Cuando el nodo primario tiene un número n de los nodos secundarios, defina en el orden de los nodos secundarios ubicación de este tema. Por ejemplo, en este tema es el número 4 de 4 temas secundarios.)  
  
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
  
El cuerpo (sin incluir el encabezado y pie de página) del tema contendrá vínculos de página, una sección de la nota, un área contraíble, un fragmento de código y una sección de texto específico del idioma.  Consulte la sección personalización de marca para obtener información acerca de esas áreas del tema presentado.  
  
1.  Agregar una etiqueta de título de tema:  `<div class="title">Contoso Topic 4</div>`  
  
2.  Agregue una nota de sección: `<div class="alert"> add your table tag and text </div>`  
  
3.  Agregar un área contraíble:  `<CollapsibleArea Expanded="1" Title="Collapsible Area Test Heading"> add text  </CollapsibleArea>`  
  
4.  Agregue un fragmento de código:  `<CodeSnippet EnableCopyCode="true" Language="CSharp" ContainsMarkup="false" DisplayLanguage="C#" > a block of code </CodeSnippet>`  
  
5.  Agregar texto específico del lenguaje de código: `<LanguageSpecificText devLangcs="CS" devLangvb="VB" devLangcpp="C++" devLangnu="F#" />` tenga en cuenta que devLangnu = permite introducir otros lenguajes. Por ejemplo, devLangnu = "Fortran" mostrará Fortran cuando el fragmento de código DisplayLanguage = Fortran  
  
6.  Agregar vínculos de página: `<a href="ms-xhelp://?Id=ContosoTopic1">Main Topic</a>`  
  
> [!NOTE]
>  Nota: para que no es compatible con nuevos "idioma" (ejemplo, F #, Cobol o Fortran) el código en colores en el fragmento de código será monocromo.  
  
**Tema del Visor de Ayuda de ejemplo** el código muestra cómo definir los metadatos, un fragmento de código, un área contraíble y texto específicos del idioma.  
  
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
        <a href="ms-xhelp://?Id=ContosoTopic1">Main Topic</a>  
    </div>  
 </div>  
</div>  
</div>  
</body>  
</html>  
  
```  
  
**Compatibilidad con F1**  
  
En Visual Studio, seleccione F1, genera los valores proporcionados desde la posición del cursor en el IDE y rellena una "bolsa" con los valores proporcionados (según la ubicación del cursor. Cuando el cursor está sobre la característica x, la característica x es el enfoque activo/en y rellena la bolsa de propiedades con valores.  Cuando se selecciona F1 se rellena la bolsa de propiedades y el código de F1 de Visual Studio comprueba si el origen de la Ayuda de los clientes predeterminada es local o en línea (en línea es el valor predeterminado), a continuación, crea la cadena adecuada en función de los usuarios establecer (en línea es el valor predeterminado) - execute shell (consulte la Guía del administrador ayuda para exe parámetros de inicio) con parámetros para el Visor de Ayuda local + o las palabras clave de la bolsa de propiedades si ayuda local es el valor predeterminado o la dirección URL de MSDN con la palabra clave en la lista de parámetros.  
  
Si se devuelven tres cadenas para F1, conocido para como una cadena multivalor, esperar del primer término, busque un acierto, y si se encuentra, hemos terminado; Si no es así, mueva a la cadena siguiente.  Es importante el orden. Presentación de las palabras clave de varios valores debe ser una cadena más larga en la cadena más corta.  Para comprobar esto en el caso de las palabras clave de varios valores, mire la cadena de dirección URL de la tecla F1 en línea, que incluirá la palabra clave elegida.  
  
En Visual Studio 2012, intencionadamente realizamos una división más fuerte entre en línea y sin conexión, por lo que si la configuración del usuario era para Online, a continuación, simplemente pasamos la solicitud de F1 directamente a nuestro servicio de consulta en línea en MSDN, en lugar de enrutamiento a través del agente de bibliotecas de ayuda que teníamos en Visual Studio 2010. A continuación, confiamos en un estado de "contenido de proveedor instalado = true" para determinar si se debe hacer algo diferente en ese contexto. Si es true, a continuación, realizamos esta lógica de análisis y enrutamiento según lo que desea admitir a los clientes. Si es false, a continuación, se vaya a MSDN. Si la configuración del usuario es Local, todas las llamadas pasar simplemente al motor de Ayuda local.  
  
F1 diagrama de flujo:  
  
![Flujo de F1](../../extensibility/internals/media/f1flow.png "F1flow")  
  
Cuando el origen de contenido de Ayuda de Visor de Ayuda predeterminado se establece en lanzamiento en línea (en el explorador):  
  
-   Características de Visual Studio asociado (VSP) emiten un valor a la bolsa de F1 (prefix.keyword de bolsa de propiedades y la dirección URL en línea para el prefijo que se encuentra en el registro): F1 envía una dirección URL de VSP + parámetros al explorador.  
  
-   Las características de Visual Studio (editor de idiomas, los elementos de menú específico de Visual Studio, etc.): F1 envía una URL de Visual Studio en el explorador.  
  
Cuando el origen de contenido de Ayuda de Visor de Ayuda predeterminado se establece en la Ayuda local (lanzamiento en el Visor de Ayuda):  
  
-   Características VSP donde coincide con la palabra clave entre F1 bolsa de propiedades y el índice de almacén local (es decir, el prefix.keyword del contenedor de propiedad = el valor se encuentra en el índice de almacén local): F1 representa el tema en el Visor de ayuda.  
  
-   Características de Visual Studio (ninguna opción para el archivo VSP invalidar la bolsa de propiedades que se emiten desde las características de Visual Studio): F1 representa un tema de Visual Studio en el Visor de ayuda.  
  
Establezca los valores del registro siguientes para habilitar la reserva de F1 para el contenido de Ayuda del proveedor. Reserva de F1 significa que el Visor de ayuda se establece en línea para buscar contenido de Ayuda de F1, y el contenido del proveedor se instala localmente en el disco duro. El Visor de ayuda debe consultar la Ayuda local para el contenido, aunque el valor predeterminado es para obtener ayuda en línea.  
  
1.  Establecer el **VendorContent** valor bajo la clave del registro de ayudar a 2.3:  
  
    -   Para sistemas operativos de 32 bits:  
  
         HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Help\v2.3\Catalogs\VisualStudio15  
  
         "VendorContent" = dword: 00000001  
  
    -   Para los sistemas operativos de 64 bits:  
  
         HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Catalogs\VisualStudio15  
  
         "VendorContent" = dword: 00000001  
  
2.  Registrar el espacio de nombres asociado en la clave del registro de ayudar a 2.3:  
  
    -   Para sistemas operativos de 32 bits:  
  
         HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Help\v2.3\Partner*\\< espacio de nombres\>*  
  
         "ubicación"="sin conexión"  
  
    -   Para los sistemas operativos de 64 bits:  
  
         HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Partner*\\< espacio de nombres\>*  
  
         "ubicación"="sin conexión"  
  
**Base de análisis nativo Namespace**  
  
Para activar el análisis de espacio de nombres base nativo, en el registro de agregar un nuevo valor DWORD con el nombre de: BaseNativeNamespaces y establezca su valor en 1 (bajo la clave de catálogo que desean admitir).  Por ejemplo, si desea usar el catálogo de Visual Studio, puede agregar la clave para la ruta de acceso:  
  
HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Catalogs\VisualStudio15
  
Cuando una palabra clave de F1 en el formato que se encuentra el encabezado o método, el carácter '/' se va a analizar, lo que resulta en la construcción siguiente:  
  
-   ENCABEZADO: será el espacio de nombres que se puede usar para registrar en el registro  
  
-   MÉTODO: Esto se convertirá en la palabra clave que se pasa a través.  
  
Por ejemplo, dada una biblioteca personalizada denominada CustomLibrary y un método llamado MyTestMethod, cuando una solicitud entra de F1 se formatearán como `CustomLibrary/MyTestMethod`.  
  
Un usuario, a continuación, puede registrar CustomLibrary como el espacio de nombres bajo el subárbol de socios y proporcionar cualquier clave de ubicación que deseen, y la palabra clave que se pasan a la consulta será MyTestMethod.  
  
**Habilitar la Ayuda de la herramienta en el IDE de depuración**  
  
Agregue la siguiente clave del registro y el valor:  
  
Clave de ayuda HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\15.0\Dynamic: mostrar los resultados de depuración en el valor de venta: Sí  
  
En el IDE, bajo el elemento de menú Ayuda, seleccione "Depurar contexto de ayuda"  
  
**Metadatos de contenido**  
  
En la siguiente tabla, cualquier cadena que aparece entre corchetes es un marcador de posición que se debe reemplazar por un valor reconocido. Por ejemplo, en \<name="Microsoft.Help.Locale meta" contenido = "[código de idioma]" / >, "[código de idioma]" debe reemplazarse por un valor como "en-us".  
  
|Propiedad (representación de HTML)|Descripción|  
|--------------------------------------|-----------------|  
|\< contenido de meta name="Microsoft.Help.Locale" = "[lenguaje-code]" / >|Establece una configuración regional de este tema. Si esta etiqueta se usa en un tema, se debe usar una sola vez y debe insertarse por encima de otras etiquetas Microsoft Help. Si no se usa esta etiqueta, se indiza el texto del cuerpo del tema mediante el uso de separador de palabras está asociado con la configuración regional del producto, si se especifica; en caso contrario, en-us se usa el separador de palabras. Esta etiqueta se ajusta al ISOC RFC 4646. Para asegurarse de que Microsoft Help funciona correctamente, utilice esta propiedad en lugar del atributo de lenguaje general.|  
|\< contenido de meta name="Microsoft.Help.TopicLocale" = "[lenguaje-code]" / >|Establece una configuración regional de este tema cuando también se usan otras configuraciones regionales. Si esta etiqueta se usa en un tema, se debe usar una sola vez. Utilice esta etiqueta cuando el catálogo contiene contenido en varios idiomas. Varios temas en un catálogo pueden tener el mismo identificador, pero cada uno debe especificar un único TopicLocale. El tema que especifica un TopicLocale que coincida con la configuración regional del catálogo es el tema que se muestra en la tabla de contenido. Sin embargo, todas las versiones de idioma del tema se muestran en los resultados de búsqueda.|  
|\< Title > [Title] \< /title >|Especifica el título de este tema. Esta etiqueta es necesaria y se debe usar una sola vez en un tema. Si el cuerpo del tema no contiene un título \<div > sección, este título se muestra en el tema y en la tabla de contenido.|  
|\< nombre de la meta = "Microsoft.Help.Keywords" contenido = "[aKeywordPhrase]" / >|Especifica el texto de un vínculo que se muestra en el panel de índice del Visor de ayuda. Cuando se hace clic en el vínculo, se muestra el tema. Puede especificar varias palabras clave de índice para un tema o puede omitir esta etiqueta si no desea que los vínculos a este tema para que aparezca en el índice. Palabras clave "K" de las versiones anteriores de la Ayuda se pueden convertir a esta propiedad.|  
|\< contenido de meta name="Microsoft.Help.Id" = "[TopicID]" / >|Establece el identificador de este tema. Esta etiqueta es necesaria y se debe usar una sola vez en un tema. El identificador debe ser único entre los temas en el catálogo que tienen la misma configuración regional. En otro tema, puede crear un vínculo a este tema mediante el uso de este identificador.|  
|\< meta name="Microsoft.Help.F1" content="[System.Windows.Controls.Primitives.IRecyclingItemContainerGenerator]"/ >|Especifica la palabra clave F1 para este tema. Puede especificar varias palabras clave F1 para un tema o puede omitir esta etiqueta si no desea que este tema se mostrará al usuario de una aplicación presiona la tecla F1. Normalmente, se especifica una sola palabra clave de F1 para un tema. Palabras clave "F" de las versiones anteriores de la Ayuda se pueden convertir a esta propiedad.|  
|\< nombre de la meta = "Descripción" content = "[descripción del tema]" / >|Proporciona un breve resumen sobre el contenido de este tema. Si esta etiqueta se usa en un tema, se debe usar una sola vez. Se tiene acceso a esta propiedad directamente en la biblioteca de consulta; no se almacena en el archivo de índice.|  
 contenido de meta name="Microsoft.Help.TocParent" = "[parent_Id]" / >|Especifica el tema principal de este tema en la tabla de contenido. Esta etiqueta es necesaria y se debe usar una sola vez en un tema. El valor es el Microsoft.Help.Id del elemento primario. Un tema puede tener una sola ubicación en la tabla de contenido. "-1" se considera el identificador de tema para la raíz de la tabla de contenido. En [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)], esa página es la página principal de Visor de ayuda. Se trata de la misma razón que agregamos específicamente TocParent =-1 a algunos temas para asegurarse de que se muestran en la parte superior nivel. La página principal de Visor de ayuda es un sistema y por lo tanto no reemplazable. Si un VSP intenta agregar una página con un identificador de -1, es posible que obtenga agregado para el conjunto de contenido, pero el Visor de ayuda siempre usará la página system - página principal del Visor de ayuda|  
|\< contenido de meta name="Microsoft.Help.TocOrder" = "[entero]" / >|Especifica dónde en la tabla de contenido en este tema aparece en relación con sus temas del mismo nivel. Esta etiqueta es necesaria y se debe usar una sola vez en un tema. El valor es un entero. Un tema que especifica un entero menor valor aparece por encima de un tema que especifica un entero de mayor valor.|  
|\< contenido de meta name="Microsoft.Help.Product" = "[product code]" / >|Especifica el producto que se describe en este tema. Si esta etiqueta se usa en un tema, se debe usar una sola vez. Esta información también se puede proporcionar como un parámetro que se pasa al indizador de ayuda.|  
|\< contenido de meta name="Microsoft.Help.ProductVersion" = "[número de versión]" / >|Especifica la versión del producto que se describe en este tema. Si esta etiqueta se usa en un tema, se debe usar una sola vez. Esta información también se puede proporcionar como un parámetro que se pasa al indizador de ayuda.|  
|\< contenido de meta name="Microsoft.Help.Category" = "[string]" / >|Usa productos para identificar las subsecciones de contenido. Puede identificar varias subsecciones para un tema o puede omitir esta etiqueta si no desea que los vínculos para identificar cualquier subsecciones. Esta etiqueta se utiliza para almacenar los atributos para TargetOS y TargetFrameworkMoniker cuando se convierte un tema desde una versión anterior de la Ayuda. El formato del contenido es AttributeName:AttributeValue.|  
|\< el contenido de meta name="Microsoft.Help.TopicVersion ="[número de versión de tema]"/ >|Especifica esta versión del tema cuando existen varias versiones de un catálogo. Porque Microsoft.Help.Id no está garantizado que sea único, esta etiqueta es necesaria cuando más de una versión de un tema no existe en un catálogo, por ejemplo, cuando un catálogo contiene un tema de .NET Framework 3.5 y un tema para .NET Framework 4 y ambos tienen el mismo Micro suave. Help.Id.|  
|\< nombre de la meta = "SelfBranded" content = "[TRUE o FALSE]" / >|Especifica si en este tema usa el paquete de personalización de marca de inicio de administrador de bibliotecas de ayuda o un paquete de personalización de marca específica del tema. Esta etiqueta debe ser TRUE o FALSE. Si es TRUE, el paquete de personalización de marca para el tema asociado reemplaza el paquete de personalización de marca que se establece cuando se inicia el Administrador de bibliotecas de ayuda para que el tema se presenta como se espera incluso si es diferente de la representación de otro tipo de contenido. Si es FALSE, el tema actual se representa según el paquete de personalización de marca que se establece cuando se inicia el Administrador de bibliotecas de ayuda. De forma predeterminada, se supone una personalización de marca automáticamente a ser false a menos que se declara la variable SelfBranded como TRUE; Administrador de bibliotecas de ayuda por lo tanto, no es necesario declarar \<nombre meta = "SelfBranded" content = "FALSE" / >.|  
  
### <a name="creating-a-branding-package"></a>Creación de un paquete de personalización de marca  
La versión de Visual Studio incluye a una serie de diferentes productos de Visual Studio, incluido el aislado y shells integrados para Partners de Visual Studio.  Cada uno de estos productos requiere cierto grado de personalización de marca única para el producto, soporte contenido de Ayuda basada en temas.  Por ejemplo, los temas de Visual Studio deben tener una presentación de marca coherentes, mientras que SQL Studio, que ajusta el Shell de ISO, requiere su propio único ayuda contenido personalización de marca para cada tema.  Un asociado de Shell integrado podría ser dentro del elemento primario de contenido de Ayuda del producto de Visual Studio mientras mantiene su propio tema de la personalización de marca los temas de ayuda.  
  
Personalización de marca de los paquetes se instalan por el producto que contiene el Visor de ayuda.  Productos de Visual Studio:  
  
-   Un paquete de personalización de marca de reserva (Branding_\<configuración regional > MSHC) se instala en la raíz de la aplicación 2.3 de Visor de ayuda (ejemplo: C:\Program Files (x86) \Microsoft Help Viewer\v2.3) por el paquete de idioma del Visor de ayuda.  Esto se usa para los casos donde no está instalado el producto de cualquier paquete de personalización de marca (no se ha instalado contenido) o daños en el paquete de personalización de marca instalado.  Tenga en cuenta que los elementos de Visual Studio (logotipo y comentarios) se omiten cuando se usa el paquete de personalización de marca de reserva de aplicación raíz.  
  
-   Cuando se instala el contenido de Visual Studio desde el servicio de paquete de contenido, también se instala un paquete de personalización de marca (para el primer escenario de instalación del contenido de tiempo).  Si hay una actualización para el paquete de personalización de marca, la actualización se instala cuando se produce la siguiente actualización de contenido o la acción de instalación del paquete adicional.  
  
El Visor de Ayuda de Microsoft es compatible con la personalización de marca de temas basados en los metadatos de tema.  
  
-   Donde los metadatos de tema definen self marca = true, representar el tema tal cual, no hacer nada (en cuanto a la personalización de marca).  
  
-   Donde los metadatos de tema definen self marca = false, usar el paquete de personalización de marca asociado con el valor de metadatos TopicVendor.  
  
-   Contenido donde los metadatos de tema definen name="Microsoft.Help.TopicVendor" =\< nombre de paquete de personalización de marca en proveedor MSHA >, use el paquete de personalización de marca definido en el valor de contenido.  
  
-   Tenga en cuenta que en el catálogo de Visual Studio, hay una aplicación de prioridad de paquetes de personalización de marca.  Marca predeterminada del primer Visual Studio se aplica y, a continuación, si se definen en los metadatos de tema y compatible con la personalización de marca asociado del paquete (como se define en la instalación msha), se aplica la definida por el proveedor de personalización de marca como una invalidación.  
  
Normalmente, los elementos de personalización de marca se dividen en tres categorías principales:  
  
-   Elementos de encabezado (algunos ejemplos son el vínculo de comentarios, texto de renuncia condicional, logotipo)  
  
-   Contenido comportamientos (algunos ejemplos son los elementos de texto del control de expandir y contraer y elementos del fragmento de código)  
  
-   Elementos del pie de página (ejemplo, Copyright)  
  
Elementos que se consideran como incluyen elementos con marca (detallado en esta especificación):  
  
-   Logotipo de producto del catálogo (por ejemplo, Visual Studio)  
  
-   Elementos de correo electrónico y el vínculo de comentarios  
  
-   Texto de renuncia  
  
-   Texto de copyright  
  
Archivos auxiliares del paquete de personalización de marca del Visor de Ayuda de Visual Studio incluyen:  
  
-   Gráficos (logotipos, iconos, etcetera.)  
  
-   Branding.js - auxiliares los comportamientos del contenido de archivos de script  
  
-   Branding.XML - cadenas que se usan en forma coherente entre el contenido del catálogo.  Nota: para elementos de texto de localización de Visual Studio en el branding.xml, incluyen _locID = "\<valor único >"  
  
-   Branding.CSS - definiciones de estilo para la coherencia de presentación  
  
-   Printing.CSS - definiciones de estilo de presentación impresa coherente  
  
Como se mencionó anteriormente, los paquetes de personalización de marca están asociados con el tema:  
  
-   Cuando SelfBranded = false se define en los metadatos, el tema hereda el catálogo de paquete de personalización de marca  
  
-   O cuando SelfBranded = false y existe un paquete de personalización de marca única definido en el MSHA y disponibles cuando se instala el contenido  
  
Para VSPs implementar paquetes personalizados de personalización de marca (contenido VSP, SelfBranded = True), una para continuar consiste en comenzar con el paquete de personalización de marca de reserva (instalado con el Visor de Ayuda) y cambie el nombre del archivo según corresponda.  El Branding_\<configuración regional > MSHC archivo es un archivo zip con la extensión de archivo ha cambiado a MSHC, por lo que basta con cambiar la extensión de MSHC a .zip y extraiga el contenido.  A continuación puede consultar los elementos del paquete de personalización de marca y modificar según corresponda (por ejemplo, cambiar el logotipo del logotipo VSP y la referencia para el logotipo en el archivo Branding.xml, actualizar Branding.xml por características específicas VSP, etcetera.).  
  
Cuando se realizan todas las modificaciones, cree un archivo zip que contiene los elementos de personalización de marca deseados y cambie la extensión a MSHC.  
  
Para asociar el paquete de personalización de marca personalizado, cree el MSHA que contiene la referencia al archivo mshc personalización de marca junto con el contenido mshc (que contiene los temas).  Consulte a continuación "MSHA" para crear un MSHA básica.  
  
El archivo Branding.xml contiene elementos de la lista usa para representar constantemente los elementos específicos en un tema cuando el tema contiene \<name="Microsoft.Help.SelfBranded meta" contenido = "false" / >.  A continuación se enumera la lista de Visual Studio de elementos en el archivo Branding.xml.  Tenga en cuenta que esta lista está pensada para usarse como una plantilla para usuarios pioneros del Shell de ISO, en el modifican estos elementos (por ejemplo, logotipo, comentarios y Copyright) para satisfacer su propias necesidades de personalización de marca de producto.  
  
Nota: las variables que se ha indicado por "{n}" tienen las dependencias del código, quitar o cambiar estos valores hará que los errores y, posiblemente, el bloqueo de la aplicación. Los identificadores de localización (ejemplo _locID="codesnippet.n") se incluyen en el paquete de personalización de marca de Visual Studio.  
  
**Branding.Xml**  
  
|||  
|-|-|  
|Característica:|**CollapsibleArea**|  
|Usar:|Expandir el texto del control de contenido se contrae|  
|**Element**|**Valor**|  
|ExpandText|Expand|  
|CollapseText|Contraer|  
|Característica:|**CodeSnippet**|  
|Usar:|Texto del control de fragmento de código.  Nota: El contenido de fragmento de código con el espacio "Indivisible" cambiará a espacio.|  
|**Element**|**Valor**|  
|CopyToClipboard|Copiar en el Portapapeles|  
|ViewColorizedText|Ver texto coloreado|  
|CombinedVBTabDisplayLanguage|Visual Basic (ejemplo)|  
|VBDeclaration|Declaración|  
|VBUsage|Uso|  
|Característica:|**Comentarios, el pie de página y el logotipo de**|  
|Usar:|Proporcionar un control de comentarios de cliente proporcionar comentarios sobre el tema actual a través de correo electrónico.  Texto de copyright para el contenido.  Definición de logotipo.|  
|**Element**|**Valor (estas cadenas pueden modificarse para satisfacer las necesidades del usuario pionero de contenido).**|  
|CopyRight|© 2013 Microsoft Corporation. Todos los derechos reservados.|  
|SendFeedback|\<un href = "{0}" {1}> Enviar comentarios\</a > sobre este tema a Microsoft.|  
|FeedbackLink||  
|LogoTitle|[!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)]|  
|LogoFileName|vs_logo_bk.gif|  
|LogoFileNameHC|vs_logo_wh.gif|  
|Característica:|**Declinación de responsabilidades**|  
|Usar:|Un conjunto de casos renuncias de responsabilidad específicas para la máquina contenido traducido.|  
|**Element**|**Valor**|  
|MT_Editable|En este artículo es de traducción automática. Si tiene una conexión a Internet, seleccione "Ver el tema en línea" para ver esta página en modo editable con el contenido original en inglés al mismo tiempo.|  
|MT_NonEditable|En este artículo es de traducción automática. Si tiene una conexión a Internet, seleccione "Ver el tema en línea" para ver esta página en modo editable con el contenido original en inglés al mismo tiempo.|  
|MT_QualityEditable|En este artículo se tradujo manualmente. Si tiene una conexión a Internet, seleccione "Ver el tema en línea" para ver esta página en modo editable con el contenido original en inglés al mismo tiempo.|  
|MT_QualityNonEditable|En este artículo se tradujo manualmente. Si tiene una conexión a Internet, seleccione "Ver el tema en línea" para ver esta página en modo editable con el contenido original en inglés al mismo tiempo.|  
|MT_BetaContents|Este artículo es una traducción automática para una versión preliminar. Si tiene una conexión a Internet, seleccione "Ver el tema en línea" para ver esta página en modo editable con el contenido original en inglés al mismo tiempo.|  
|MT_BetaRecycledContents|En este artículo se tradujo manualmente para una versión preliminar. Si tiene una conexión a Internet, seleccione "Ver el tema en línea" para ver esta página en modo editable con el contenido original en inglés al mismo tiempo.|  
|Característica:|**LinkTable**|  
|Usar:|Compatibilidad con vínculos a temas en línea|  
|**Element**|**Valor**|  
|LinkTableTitle|Tabla de vínculos|  
|TopicEnuLinkText|Ver la versión en inglés\</a > de este tema que está disponible en el equipo.|  
|TopicOnlineLinkText|Ver el tema \<un href = "{0}" {1}> en línea\</a >|  
|OnlineText|En línea|  
|Característica:|**Control de Audio de vídeo**|  
|Usar:|Mostrar elementos y el texto para el contenido de vídeo|  
|**Element**|**Valor**|  
|MultiMediaNotSupported|Internet Explorer 9 o superior debe estar instalado para admitir {0} contenido.|  
|VideoText|Mostrar vídeo|  
|AudioText|secuencias de audio|  
|OnlineVideoLinkText|\<p > para ver el vídeo asociado a este tema, haga clic en {0} \<un href = "{1}" >{2}aquí\</a >.\< /p >|  
|OnlineAudioLinkText|\<p > para escuchar el audio asociado a este tema, haga clic en {0} \<un href = "{1}" >{2}aquí\</a >.\< /p >|  
|Característica:|**Control de contenido no instalado**|  
|Usar:|Elementos de texto (cadenas) usados para la representación de contentnotinstalled.htm|  
|**Element**|**Valor**|  
|ContentNotInstalledTitle|No se encontró ningún contenido en el equipo.|  
|ContentNotInstalledDownloadContentText|\<p > para descargar contenido en el equipo, \<un href = "{0}" {1}> haga clic en la pestaña administrar\</a >.\< /p >|  
|ContentNotInstalledText|\<p > ningún contenido instalado en el equipo. Consulte al administrador para la instalación del contenido de Ayuda local. \</p >|  
|Característica:|**Control de tema no encontrado**|  
|Usar:|Elementos de texto (cadenas) usados para la representación de topicnotfound.htm|  
|**Element**|**Valor**|  
|TopicNotFoundTitle|No se encuentra el tema requerido en el equipo.|  
|TopicNotFoundViewOnlineText|\<p > el tema requerido no se encontró en el equipo, pero puede \<un href = "{0}" {1}> ver el tema en línea\</a >.\< /p >|  
|TopicNotFoundDownloadContentText|\<p > vea el panel de navegación para obtener vínculos a temas similares, o \<un href = "{0}" {1}> haga clic en la pestaña administrar\</a > para descargar contenido en el equipo.\< /p >|  
|TopicNotFoundText|\<p > el tema requerido no se encontró en el equipo. \</p >|  
|Característica:|**Tema dañado Control**|  
|Usar:|Elementos de texto (cadenas) usados para la representación de topiccorrupted.htm|  
|**Element**|**Valor**|  
|TopicCorruptedTitle|No se puede mostrar el tema solicitado.|  
|TopicCorruptedViewOnlineText|\<p > el Visor de ayuda no puede mostrar el tema solicitado. Puede haber un error en el contenido del tema o una dependencia del sistema subyacente. \</p >|  
|Característica:|**Control de la página principal**|  
|Usar:|Texto que admiten la presentación del contenido de nodo de nivel superior del Visor de ayuda.|  
|**Element**|**Valor**|  
|HomePageTitle|Página principal del Visor de ayuda|  
|HomePageIntroduction|\<p > para el Visor de Ayuda de Microsoft, una fuente esencial de la información para todo aquel que use las herramientas, productos, tecnologías y servicios de Microsoft. El Visor de Ayuda proporciona acceso a procedimientos e información de referencia, código de ejemplo, artículos técnicos y mucho más. Para buscar el contenido que necesita, busque en la tabla de contenido, utilice la búsqueda de texto completo o desplazarse por contenido utilizando el índice de la palabra clave. \</p >|  
|HomePageContentInstallText|\<p >\<br / > Use la \<un href = "{0}" {1}> Administrar contenido\</a > pestaña hacer lo siguiente:\<ul >\<li > Agregar contenido al equipo.\< /li >\<li > Buscar actualizaciones a su contenido local.\< /li >\<li > quitar contenido de su equipo.\< /li >\</ul >\</p >|  
|HomePageInstalledBooks|Libros instalados|  
|HomePageNoBooksInstalled|No se encontró ningún contenido en el equipo.|  
|HomePageHelpSettings|Configuración de contenido de ayuda|  
|HomePageHelpSettingsText|\<p > es la configuración actual de la Ayuda local. El Visor de Ayuda muestra contenido que ha instalado en el equipo. \<br / > para cambiar el origen de contenido de ayuda, en la barra de menús de Visual Studio, elija \<span style = "{0}" > Ayuda, establecer preferencias de la Ayuda\</span >.\< br / >\</p >|  
|Megabytes|MB|  
  
**Branding.js**  
  
El archivo branding.js contiene JavaScript que usa los elementos de personalización de marca del Visor de Ayuda de Visual Studio.  A continuación es una lista de los elementos de personalización de marca y la función auxiliar de JavaScript.  Todas las cadenas se localicen para este archivo se definen en la sección "Cadenas localizables" en la parte superior de este archivo.  Tenga en cuenta que se ha creado el archivo ICL loc cadenas dentro del archivo branding.js.  
  
||||  
|-|-|-|  
|**Característica de personalización de marca**|**Función de JavaScript**|**Descripción**|  
|Var...||Definir variables|  
|Obtiene el lenguaje de código de usuario|setUserPreferenceLang|asigna un índice # para el lenguaje de código|  
|Establecer y obtener los valores de cookie|getCookie, setCookie||  
|Miembro heredado|changeMembersLabel|Expandir o contraer miembro heredado|  
|Cuando SelfBranded = False|onLoad|Leer la cadena de consulta para comprobar si es una solicitud de impresión.  Establecer todas las codesnippets para centrarse en la pestaña preferido del usuario.  Si es un proceso de impresión solicitud isPrinterFriendly establecida en true. Compruebe si el modo de contraste alto.|  
|Fragmento de código|addSpecificTextLanguageTagSet||  
||getIndexFromDevLang||  
||Ficha cambiar se||  
||setCodesnippetLang||  
||setCurrentLang||  
||CopyToClipboard||  
|CollapsibleArea|addToCollapsibleControlSet|escribir todos los objetos de control que se pueden contraer en la lista.|  
||CA_Click|según el estado de un área contraíble, define qué imagen y texto que se va a presentar|  
|Compatibilidad de contraste con logotipo|isBlackBackground()|Se llama para determinar si el fondo es negro.  Sólo precisa si en el modo de contraste alto.|  
||isHighContrast()|usar un intervalo de colores para detectar el modo de contraste alto|  
||onHighContrast(black)|Se llama cuando se detecta el contraste alto|  
|Funcionalidad LST|||  
||addToLanSpecTextIdSet(id)||  
||updateLST(currentLang)||  
||getDevLangFromCodeSnippet(lang)||  
|Funcionalidad multiMedia|título (comenzar, final, texto, estilo)||  
||findAllMediaControls(normalizedId)||  
||getActivePlayer(normalizedId)||  
||captionsOnOff(id)||  
||toSeconds(t)||  
||getAllComments(node)||  
||styleRectify (nombre de estilo, styleValue)||  
||showCC(id)||  
||Subtitle(ID)||  
  
**ARCHIVOS HTM**  
  
El paquete de personalización de marca contiene un conjunto de archivos HTM que admiten escenarios para comunicar información de clave a los usuarios de contenido de ayuda, por ejemplo una página principal que contiene una sección que describe qué conjuntos de contenido están instalados y que indica al usuario cuando no los temas de páginas se encuentra en el conjunto de temas local. Tenga en cuenta que se pueden modificar estos archivos HTM por producto.  Los proveedores de ISO Shell son capaces de tomar el paquete de personalización de marca predeterminado y cambiar el comportamiento y el contenido de estas páginas al conjunto de sus necesidades.  Estos archivos, consulte su paquete de personalización de marca correspondiente en el orden de las etiquetas de personalización de marca obtener el contenido correspondiente desde el archivo branding.xml.  
  
||||  
|-|-|-|  
|**Archivo**|**Use**|**Muestra el origen de contenido**|  
|homepage.htm|Se trata de una página que muestra el contenido instalado actualmente y cualquier otro mensaje adecuada para presentar al usuario sobre su contenido.  Este archivo tiene el contenido de "Microsoft.Help.Id" del atributo de datos de metadatos adicional = "-1" que coloca este contenido en la parte superior de la tabla de contenido de contenido local.||  
||&LT; META_HOME_PAGE_TITLE_ADD / &GT;|Branding.XML, etiqueta \<HomePageTitle >|  
||&LT; HOME_PAGE_INTRODUCTION_SECTION_ADD / &GT;|Branding.XML, etiqueta \<HomePageIntroduction >|  
||&LT; HOME_PAGE_CONTENT_INSTALL_SECTION_ADD / &GT;|Branding.XML, etiqueta \<HomePageContentInstallText >|  
||&LT; HOME_PAGE_BOOKS_INSTALLED_SECTION_ADD / &GT;|Encabezado de sección Branding.xml etiqueta\<HomePageInstalledBooks >, los datos generados a partir de la aplicación, \<HomePageNoBooksInstalled > cuando no se instalan los libros en pantalla.|  
||&LT; HOME_PAGE_SETTINGS_SECTION_ADD / &GT;|Encabezado de sección Branding.xml etiqueta \<HomePageHelpSettings >, sección texto \<HomePageHelpSettingsText >.|  
|topiccorrupted.htm|Cuando existe un tema en el conjunto local, pero por alguna razón no se puede mostrar (dañado contenido).||  
||&LT; META_TOPIC_CORRUPTED_TITLE_ADD / &GT;|Branding.XML, etiqueta \<TopicCorruptedTitle >|  
||&LT; TOPIC_CORRUPTED_SECTION_ADD / &GT;|Branding.XML, etiqueta \<TopicCorruptedViewOnlineText >|  
|topicnotfound.htm|Cuando un tema no se encuentra en el contenido local establecida, ni está disponible en línea||  
||&LT; META_TOPIC_NOT_FOUND_TITLE_ADD / &GT;|Branding.XML, etiqueta \<TopicNotFoundTitle >|  
||&LT; META_TOPIC_NOT_FOUND_ID_ADD / &GT;|Branding.XML, etiqueta \<TopicNotFoundViewOnlineText > + \<TopicNotFoundDownloadContentText >|  
||&LT; TOPIC_NOT_FOUND_SECTION_ADD / &GT;|Branding.XML, etiqueta \<TopicNotFoundText >|  
|contentnotinstalled.htm|Cuando no hay ningún contenido local instalado para el producto.||  
||&LT; META_CONTENT_NOT_INSTALLED_TITLE_ADD / &GT;|Branding.XML, etiqueta \<ContentNotInstalledTitle >|  
||&LT; META_CONTENT_NOT_INSTALLED_ID_ADD / &GT;|Branding.XML, etiqueta \<ContentNotInstalledDownloadContentText >|  
||&LT; CONTENT_NOT_INSTALLED_SECTION_ADD / &GT;|Branding.XML, etiqueta \<ContentNotInstalledText >|  
  
**Archivos CSS**  
  
La Ayuda de Visor de personalización de marca paquete de Visual Studio contiene dos archivos css para admitir la presentación del contenido coherente ayuda de Visual Studio:  
  
-   Branding.CSS - contiene elementos de css para representar where SelfBranded = false  
  
-   Printer.CSS - contiene elementos de css para representar where SelfBranded = false  
  
Archivos branding.CSS incluye definiciones para la presentación de tema de Visual Studio (salvedad es que el branding.css contenidos en el Branding_\<configuración regional > puede cambiar MSHC desde el servicio de paquete).  
  
**Archivos de gráficos**  
  
Contenido de Visual Studio muestra un logotipo de Visual Studio, así como otros gráficos.  A continuación, se muestra la lista completa de archivos gráficos en el paquete de personalización de marca del Visor de Ayuda de Visual Studio.  
  
||||  
|-|-|-|  
|**Archivo**|**Use**|**Ejemplos**|  
|Clear.gif|Utilizado para representar un área contraíble||  
|footer_slice.gif|Presentación de pie de página||  
|info_icon.gif|Utilizado para mostrar información|Declinación de responsabilidades|  
|online_icon.gif|Este icono está asociarse con vínculos en línea||  
|tabLeftBD.gif|Utilizado para representar el contenedor del fragmento de código||  
|tabRightBD.gif|Utilizado para representar el contenedor del fragmento de código||  
|vs_logo_bk.gif|Utilizada para referencias de logotipo de contraste normal como se define en la etiqueta Branding.xml \<LogoFileName >.  Productos de Visual Studio, nombre de logotipo es vs_logo_bk.gif.||  
|vs_logo_wh.gif|Utilizada para referencias de logotipo alta normal como se define en la etiqueta Branding.xml \<LogoFileNameHC >.  Productos de Visual Studio, nombre de logotipo es vs_logo_wh.gif.||  
|ccOff.png|Gráfico de subtítulos (CC)||  
|ccOn.png|Gráfico de subtítulos (CC)||  
|ImageSprite.png|Utilizado para representar un área contraíble|Expandir o contraer gráfico|  
  
### <a name="deploying-a-set-of-topics"></a>Implementación de un conjunto de temas  
Este es un tutorial muy sencillo y rápido para crear una implementación de contenido del Visor de ayuda establecer deben constar de un archivo MSHA y el conjunto de archivos .cab o MSHC que contiene los temas. El MSHA es un archivo XML que describe un conjunto de archivos .cab o los archivos MSHC. El Visor de ayuda puede leer el MSHA para obtener una lista de contenido (el. CAB o. Archivos MSHC) disponible para su instalación local.  
  
Esto es sólo un manual que describe el esquema XML muy básico para el Visor de ayuda, MSHA.  Tenga en cuenta que hay una implementación de ejemplo a continuación esta breve introducción y ejemplo HelpContentSetup.msha.  
  
El nombre de la MSHA, para los fines de este manual, es HelpContentSetup.msha (el nombre del archivo puede ser cualquier cosa, con la extensión. MSHA). HelpContentSetup.msha (el ejemplo siguiente) debe contener una lista de los archivos CAB o MSHCs disponibles.  Tenga en cuenta que el tipo de archivo debe ser coherente dentro de la MSHA (no es compatible con una combinación de tipos de archivo MSHA y CAB). Para cada archivo CAB o MSHC, debe haber un \<div clase = "paquetes" >... \</div > (consulte el ejemplo siguiente).  
  
Nota: en el siguiente ejemplo de implementación, hemos incluido el paquete de personalización de marca. Esto es importante incluir con el fin de obtener los elementos necesarios de representación de contenido de Visual Studio y los comportamientos del contenido.  
  
Ejemplo de archivo HelpContentSetup.msha: (reemplace "1 nombre de conjunto de contenido" y "contenido de conjunto de nombre 2", etc. con los nombres de archivo.)  
  
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
  
1.  Cree una carpeta local, algo parecido a "C:\SampleContent"  
  
2.  En este ejemplo, usaremos archivos MSHC para contener los temas.  Un MSHC es un archivo zip con la extensión de archivo ha cambiado de .zip a. MSHC.  
  
3.  Cree la siguiente HelpContentSetup.msha como un archivo de texto (el Bloc de notas se usó para crear el archivo) y guárdelo en la carpeta se indicó anteriormente (vea el paso 1).  
  
Tenga en cuenta que la clase "Personalización de marca" existe y es único. El uso de la marca mshc se incluye en este manual para que el contenido instalado tendrá la personalización de marca y los comportamientos de contenido que se encuentran en el MSHCs tendrá los elementos de soporte técnico adecuado contenidos en el paquete de personalización de marca. Sin esto, se producirán errores cuando el sistema busca soporte técnico de los elementos que no forman parte de copiados (instalado) contenido.  
  
Para obtener el paquete de personalización de marca de Visual Studio, copie el archivo Branding_en US.mshc en C:\Program Files (x86) \Microsoft Help Viewer\v2.3\ a la carpeta de trabajo.  
  
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
  
Usar y ampliar los pasos anteriores le permitirá VSPs implementar sus conjuntos de contenido para el Visor de Ayuda de Visual Studio.  
  
### <a name="adding-help-to-the-visual-studio-shell-integrated-and-isolated"></a>Agregar ayuda a Visual Studio Shell (integrado y aislado)  
**Introducción**  
  
Este tutorial muestra cómo incorporar contenido de ayuda en una aplicación de Shell de Visual Studio y, a continuación, implementarlo.  
  
**Requisitos**  
  
1.  [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)]  
  
2.  [Aislado de Visual Studio 2013 Shell Redist](http://www.microsoft.com/visualstudio/11/downloads#vs-shell)  
  
**Información general**  
  
El [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] Shell es una versión de la [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] IDE en el que se puede basar una aplicación. Estas aplicaciones contienen el Shell aislado junto con las extensiones que cree. Use plantillas de proyecto de Shell aislado, que se incluyen en el [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] SDK para crear extensiones.  
  
Los pasos básicos para crear una aplicación basada en Shell aislado y su ayuda:  
  
1.  Obtener el [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] ISO Shell redistributable (descarga de Microsoft).  
  
2.  En Visual Studio, cree una extensión de ayuda que se basa en el Shell aislado, por ejemplo, la extensión de la Ayuda de Contoso que se describe más adelante en este tutorial.  
  
3.  Ajustar la extensión y el Shell de ISO redistribuible en una implementación de MSI (una instalación de la aplicación). En este tutorial no incluye un paso de instalación.  
  
Crear un almacén de contenido de Visual Studio. Para el escenario de Shell integrado, cambie Studio12 Visual para el nombre del catálogo de productos de la manera siguiente:  
  
-   Crear carpeta C:\ProgramData\Microsoft\HelpLibrary2\Catalogs\VisualStudio15.  
  
-   Cree un archivo denominado CatalogType.xml y agréguelo a la carpeta. El archivo debe contener las siguientes líneas de código:  
  
    ```xml
    <?xml version="1.0" encoding="UTF-8"?>  
    <catalogType>UserManaged</catalogType>  
    ```  
  
Definir el almacén de contenido en el registro. Para el Shell integrado, cambie VisualStudio15 al nombre de catálogo del producto:  
  
-   HKLM\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Catalogs\VisualStudio15  
  
     Clave: Valor de cadena LocationPath: C:\ProgramData\Microsoft\HelpLibrary2\Catalogs\VisualStudio15\  
  
-   HKLM\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Catalogs\VisualStudio15\en-US  
  
     Clave: Valor de cadena CatalogName: [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] documentación  
  
**Crear el proyecto**  
  
Para crear una extensión de Shell aislado:  
  
1.  En Visual Studio, en **archivo**, elija **nuevo proyecto**, en **otros tipos de proyectos** elija **extensibilidad**y, a continuación, elija  **Visual Studio Shell aislado**. Denomine el proyecto `ContosoHelpShell`) para crear un proyecto de extensibilidad basado en la plantilla de Visual Studio Shell aislado.  
  
2.  En el Explorador de soluciones, en el proyecto ContosoHelpShellUI, en la carpeta archivos de recursos, abra ApplicationCommands.vsct. Asegúrese de que esta línea está comentada (busque "No_Help"): `<!-- <define name="No_HelpMenuCommands"/> -->`  
  
3.  Elija la tecla F5 para compilar y ejecutar **depurar**. En la instancia experimental del IDE de Shell aislado, elija el **ayuda** menú. Asegúrese de que el **ver Ayuda**, **agregar y quitar contenido de Ayuda**, y **establecer preferencias de la Ayuda** comandos aparecen.  
  
4.  En el Explorador de soluciones, en el proyecto ContosHelpShell, en la carpeta de personalización del Shell, abra ContosoHelpShell.pkgdef. Para definir el catálogo de Ayuda de Contoso, agregue las siguientes líneas:  
  
    ```  
     [$RootKey$\Help]  
    "Product"="Contoso"  
    "Catalog"="Contoso"  
    "Version"="100"  
    "BrandingPackage"="ContosoBrandingPackage.mshc"  
    ```  
  
5.  En el Explorador de soluciones, en el proyecto ContosHelpShell, en la carpeta de personalización del Shell, abra ContosoHelpShell.Application.pkgdef. Para habilitar la Ayuda F1, agregue las siguientes líneas:  
  
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
  
6.  En el Explorador de soluciones, en el menú contextual de la solución ContosoHelpShell, elija el **propiedades** elemento de menú. En **propiedades de configuración**, seleccione **Configuration Manager**. En el **configuración** columna, cambiar todos los valores "Debug" a "Release".  
  
7.  Compile la solución. Esto crea un conjunto de archivos en una carpeta de versión, que se usará en la sección siguiente.  
  
Para probar esto como si implementan:  
  
1.  En el equipo está implementando Contoso para instalar el Shell de ISO (antes) descargado.  
  
2.  Cree una carpeta en \\archivos \Program (x86)\\y asígnele el nombre `Contoso`.  
  
3.  Copie el contenido de la versión ContosoHelpShell a \\\Program (x86) \Contoso\ en disco.  
  
4.  Inicie el Editor del registro eligiendo **ejecutar** en el **iniciar** menú y escriba `Regedit`. En el editor del registro, elija **archivo**y, a continuación, **importación**. Vaya a la carpeta del proyecto ContosoHelpShell. En la subcarpeta ContosoHelpShell, elija ContosoHelpShell.reg.  
  
5.  Crear un almacén de contenido:  
  
     Para el Shell ISO - crear un almacén de contenido de Contoso C:\ProgramData\Microsoft\HelpLibrary2\Catalogs\ContosoDev12  
  
     Para [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] Shell integrado, cree la carpeta C:\ProgramData\Microsoft\HelpLibrary2\Catalogs\VisualStudio15  
  
6.  Crear CatalogType.xml y agregar al almacén de contenido (paso anterior) que contiene:  
  
    ```  
    <?xml version="1.0" encoding="UTF-8"?>  
    <catalogType>UserManaged</catalogType>  
    ```  
  
7.  Agregue las siguientes claves del registro:  
  
     HKLM\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Catalogs\VisualStudio15Key: Valor de cadena LocationPath:  
  
     Para el Shell ISO:  
  
     C:ProgramDataMicrosoftHelpLibrary2CatalogsVisualStudio15  
  
     [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] Shell integrado:  
  
     C:ProgramDataMicrosoftHelpLibrary2CatalogsVisualStudio15en-EE. UU.  
  
     Clave: Valor de cadena CatalogName: [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] documentación. Para el Shell de ISO, este es el nombre del catálogo.  
  
8.  Copie el contenido (MSHA y MSHC o .cab) en una carpeta local.  
  
9. Línea de comandos de Shell integrado de ejemplo para probar el almacén de contenido. Para el Shell de ISO, cambie los valores de catálogo y launchingApp según corresponda para que coincida con el producto.  
  
     "C:\Program archivos (x86) \Microsoft Help Viewer\v2.3\HlpViewer.exe" /catalogName VisualStudio15 /helpQuery método = "página & id = ContosoTopic0" /launchingApp Microsoft, Visual Studio, 12.0  
  
10. Iniciar la aplicación de Contoso (desde la raíz de la aplicación Contoso). Dentro del Shell de ISO, elija el **ayuda** elemento de menú y cambie el **establecer preferencias de la Ayuda** a **usar la Ayuda Local**.  
  
11. Dentro del shell, elija el **ayuda** elemento de menú, **ver Ayuda**. Debe iniciar el Visor de Ayuda local. Pulse la pestaña **Administrar contenido**. En **origen de instalación**, elija el **disco** botón de opción. Elija la **...**  botón y vaya a la carpeta local que contiene el contenido de Contoso (copiado en la carpeta local en el paso anterior). Elija el HelpContentSetup.msha. Contoso debería aparecer ahora como un libro en las selecciones del libro. Elija **agregar**y, a continuación, elija el **actualización** botón (esquina inferior derecha).  
  
12. En el IDE de Contoso, elija la tecla F1 para probar la funcionalidad de F1.  
  
### <a name="additional-resources"></a>Recursos adicionales  
Para la API de tiempo de ejecución, consulte [API de Ayuda de Windows](http://msdn.microsoft.com/library/windows/desktop/hh447318\(v=vs.85\).aspx).  
  
Para obtener más información sobre cómo aprovechar la API de ayuda, consulte [Visor de Ayuda de los ejemplos de código](http://visualstudiogallery.msdn.microsoft.com/f08f296f-7076-4aec-8da3-8f0fbe04461e)  
  
Para proporcionar comentarios acerca de estos componentes, use [Microsoft Connect](http://connect.microsoft.com/).  
  
Envíe las sugerencias de características para [Microsoft User Voice](http://visualstudio.uservoice.com/forums/121579-visual-studio)  
  
Para obtener ayuda adicional, pruebe el [foros de sistema de ayuda y documentación para desarrolladores de MSDN](http://social.msdn.microsoft.com/Forums/devdocs/threads)  
  
Las actualizaciones sobre importantes problema, consulte el [Léame del Visor de ayuda](http://go.microsoft.com/fwlink/?LinkID=231397&clcid=0x409)  
  
Para ponerse en contacto directamente con el equipo de PM del Visor de ayuda, envíe el correo electrónico a hlpfdbk@microsoft.com