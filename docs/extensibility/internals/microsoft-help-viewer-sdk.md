---
title: Visor de Ayuda de Microsoft SDK | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 620d7dcd-d462-475e-a449-fbfa06ff12c5
caps.latest.revision: "33"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c4c676c28b955fac29db5a961f3b566600bcf318
ms.sourcegitcommit: ec1c7e7e3349d2f3a4dc027e7cfca840c029367d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/07/2017
---
# <a name="microsoft-help-viewer-sdk"></a>SDK del Visor de Ayuda de Microsoft
Este artículo contiene las siguientes tareas para que los integradores de Visor de Ayuda de Visual Studio:  
  
-   Crear un tema (soporte de F1)  
  
-   Crear un paquete de personalización de marca de contenido del Visor de ayuda  
  
-   Implementación de un conjunto de artículos  
  
-   Agregar ayuda para el shell de Visual Studio (integrada o aislado)  
  
-   Recursos adicionales  
  
### <a name="creating-a-topic-f1-support"></a>Crear un tema (soporte de F1)  
Esta sección proporciona información general de los componentes de un tema presentado, requisitos del tema, una breve descripción de cómo crear un tema (incluidos los requisitos de compatibilidad de F1) y, finalmente, un tema de ejemplo con el resultado representado.  
  
**Introducción al Visor de tema de ayuda**  
  
Cuando se llama a un tema para la representación, el Visor de ayuda obtiene los elementos del paquete de personalización de marca que están asociados con el tema en el momento de instalar o última actualización, junto con el tema XHTML y combina los dos que dan como resultado en la vista de contenido presentada (personalización de marca de datos + datos de tema).  El paquete de personalización de marca contiene los logotipos, compatibilidad con comportamientos del contenido y el texto de personalización de marca (copyright, etcetera.).  Para obtener más información acerca de los elementos de paquete de personalización de marca, vea "Crear el paquete de personalización de marca" a continuación.  En caso de que no hay ningún paquete de personalización de marca asociado al tema, el Visor de ayuda usará el paquete de personalización de marca reserva ubicado en la raíz de la aplicación de Visor de ayuda (Branding_en US.mshc).  
  
**Requisitos de tema del Visor de ayuda**  
  
Para representar correctamente en el Visor de ayuda, contenido de los temas sin formato debe ser XHTML 1.1 básica de W3C.  
  
Normalmente, un tema contiene dos secciones:  
  
-   Metadatos (consulte la referencia de metadatos de contenido): datos sobre el tema, por ejemplo, el Id. único del tema, el valor de palabra clave, el Id. de tabla de contenido, tema primario Id. de nodo, etcetera.  
  
-   Contenido del cuerpo: compatibles con XHTML 1.1 básica de W3C que incluye admite comportamientos del contenido (área contraíble, fragmento de código, etcetera. A continuación se muestra una lista completa).  
  
El paquete de personalización de marca de Visual Studio admite controles:  
  
-   Vínculos  
  
-   CodeSnippet  
  
-   CollapsibleArea  
  
-   Miembro heredado  
  
-   LanguageSpecificText  
  
Cadenas de idioma admitidos (no entre mayúsculas y minúsculas):  
  
-   JavaScript  
  
-   CSharp o c#  
  
-   cplusplus o Visual c++ o c ++  
  
-   JScript  
  
-   VisualBasic o vb  
  
-   f # o fsharp o fs  
  
-   otros: una cadena que representa un nombre de idioma  
  
**Crear un tema del Visor de ayuda**  
  
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
  
A continuación, agregar datos para definir cómo se mostrará (self marca o no), el tema Cómo para hacer referencia a este tema de F1, donde existe en este tema dentro de la tabla de contenido, su identificador (como referencia de vínculo por otros temas), etcetera.  Vea la tabla "Metadatos de contenido" a continuación para obtener una lista completa de metadatos compatibles.  
  
-   En este caso, usaremos nuestro propio paquete de personalización de marca, una variante del paquete de personalización de marca en el Visor de Ayuda de Visual Studio.  
  
-   Agregue el nombre de metadatos de F1 y valor (contenido de "Microsoft.Help.F1" = "ContosoTopic4") que coincidirá con el valor de F1 proporcionado en la bolsa de propiedades IDE.  (Vea la sección de soporte técnico de F1 para obtener más información).   Este es el valor que coincida con la tecla F1 llamar desde el IDE para mostrar en este tema cuando se elige la tecla F1 en el IDE.  
  
-   Agregue el identificador del tema. Ésta es la cadena que se utiliza en otros temas para vincular a este tema.  Es el identificador de Visor de Ayuda de este tema.  
  
-   Para la tabla de contenido, agregue el nodo de elemento primario de este tema para definir dónde aparecerá este nodo de tabla de contenido del tema.  
  
-   Para la tabla de contenido, agregue el orden de los nodos de este tema. Cuando el nodo primario tiene n número de nodos secundarios, defina en el orden de los nodos secundarios ubicación de este tema. Por ejemplo, en este tema es el número 4 de 4 temas secundarios.)  
  
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
  
El cuerpo (sin incluir el encabezado y pie de página) del tema contendrá vínculos de página, una sección de la nota, un área contraíble, un fragmento de código y una sección de texto específico del idioma.  Vea la sección personalización de marca para obtener información acerca de esas áreas del tema presentado.  
  
1.  Agregar una etiqueta de título de tema:`<div class="title">Contoso Topic 4</div>`  
  
2.  Agregue una sección de notas:`<div class="alert"> add your table tag and text </div>`  
  
3.  Agregar un área contraíble:`<CollapsibleArea Expanded="1" Title="Collapsible Area Test Heading"> add text  </CollapsibleArea>`  
  
4.  Agregue un fragmento de código:`<CodeSnippet EnableCopyCode="true" Language="CSharp" ContainsMarkup="false" DisplayLanguage="C#" > a block of code </CodeSnippet>`  
  
5.  Agregar texto específico del lenguaje de código: `<LanguageSpecificText devLangcs="CS" devLangvb="VB" devLangcpp="C++" devLangnu="F#" />` tenga en cuenta que devLangnu = permite especificar otros lenguajes. Por ejemplo, devLangnu = "Fortran" mostrará Fortran cuando el fragmento de código DisplayLanguage = Fortran  
  
6.  Agregar vínculos de página:`<a href="ms-xhelp://?Id=ContosoTopic1">Main Topic</a>`  
  
> [!NOTE]
>  Nota: para no admite nuevas "idioma para mostrar" (ejemplo, F #, Cobol, Fortran) código en colores en el fragmento de código será monocromo.  
  
**Tema del Visor de Ayuda de ejemplo** el código muestra cómo definir los metadatos, un fragmento de código, un área contraíble y texto específico del idioma.  
  
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
  
En Visual Studio, seleccione F1, genera valores suministrados desde la posición del cursor desde el IDE y rellena un "contenedor de propiedades" con los valores proporcionados (que se basa en la ubicación del cursor. Cuando el cursor está sobre la característica x, característica x está activo o en el foco y rellena la bolsa de propiedades con valores.  Cuando se selecciona F1 se rellena la bolsa de propiedades y código de F1 de Visual Studio, se comprueba si el origen de la Ayuda de los clientes de forma predeterminada es local o en línea (en línea es el valor predeterminado), a continuación, crea la cadena adecuada en función de los usuarios establecer (en línea es el valor predeterminado) - ejecutar el shell (vea los parámetros de inicio de la Guía del administrador ayuda para exe) con parámetros para el Visor de Ayuda local + palabras clave de la bolsa de propiedades si la Ayuda local es el valor predeterminado o la dirección URL de MSDN con la palabra clave en la lista de parámetros.  
  
Si se devuelven tres cadenas de F1, conoce como una cadena multivalor, tardan del primer término, busque un acierto, y si se encuentra, que finalicemos; Si no es así, vaya a la cadena siguiente.  Orden es importante. Presentación de las palabras clave multivalor debe ser una cadena más larga en la cadena más corta.  Para comprobarlo en el caso de palabras clave de varios valores, mire la cadena de dirección URL de F1 en línea, que incluye la palabra clave elegida.  
  
En Visual Studio 2012, intencionadamente hicimos una división más fuerte entre en línea y sin conexión, por lo que si la configuración del usuario era en Online, a continuación, se pasa simplemente la solicitud de F1 directamente a nuestro servicio de consulta en línea en MSDN, en lugar de enrutamiento mediante el agente de bibliotecas de ayuda que ha surgido en Visual Studio 2010. A continuación, confiamos en un estado de "contenido de proveedor instalado = true" para determinar si se debe hacer algo diferente en ese contexto. Si es true, a continuación, realizamos esta lógica de análisis y enrutamiento según lo que desea prestar asistencia a sus clientes. Si es false, a continuación, se vaya a MSDN. Si la configuración del usuario es Local, todas las llamadas vaya simplemente al motor de Ayuda local.  
  
F1 diagrama de flujo:  
  
![Flujo de F1](../../extensibility/internals/media/f1flow.png "F1flow")  
  
Cuando el origen de contenido de Ayuda de Visor de Ayuda predeterminado se establece en línea (lanzamiento en el explorador):  
  
-   Las características de Visual Studio asociado (VSP) emiten un valor a la bolsa de propiedades de F1 (prefix.keyword de bolsa de propiedades y la dirección URL en línea para el prefijo que se encuentran en el registro): F1 envía una dirección URL de VSP + parámetros en el explorador.  
  
-   Las características de Visual Studio (editor de idiomas, los elementos de menú específicos de Visual Studio, etc.): F1 envía una dirección URL de Visual Studio en el explorador.  
  
Cuando el origen de contenido de Ayuda de Visor de Ayuda predeterminado se establece en la Ayuda local (lanzamiento en el Visor de Ayuda):  
  
-   Características VSP donde coinciden con la palabra clave entre F1 bolsa de propiedades y los índices de almacén local (es decir, el prefix.keyword de la bolsa de propiedades = el valor se encuentra en el índice de almacén local): F1 representa el tema en el Visor de ayuda.  
  
-   Características de Visual Studio (ninguna opción para el VSP invalidar la bolsa de propiedades emitida desde las características de Visual Studio): F1 representa un tema de Visual Studio en el Visor de ayuda.  
  
Establezca los siguientes valores del registro para habilitar la reserva de F1 para el contenido de Ayuda de proveedor. Reserva de F1 significa que el Visor de ayuda se establece en línea para buscar contenido de Ayuda de F1, y el contenido de proveedor se instala localmente en el disco duro. El Visor de ayuda debe mirar la Ayuda local para el contenido, aunque el valor predeterminado es para obtener ayuda en línea.  
  
1.  Establecer el **VendorContent** valor en la clave de registro 2.3 ayuda:  
  
    -   Para sistemas operativos de 32 bits:  
  
         HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Help\v2.3\Catalogs\VisualStudio15  
  
         "VendorContent" = dword: 00000001  
  
    -   Para los sistemas operativos de 64 bits:  
  
         HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Catalogs\VisualStudio15  
  
         "VendorContent" = dword: 00000001  
  
2.  Registrar el espacio de nombres asociado en la clave del registro 2.3 ayuda:  
  
    -   Para sistemas operativos de 32 bits:  
  
         HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Help\v2.3\Partner*\\< espacio de nombres\>*  
  
         "ubicación"="sin conexión"  
  
    -   Para los sistemas operativos de 64 bits:  
  
         HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Partner*\\< espacio de nombres\>*  
  
         "ubicación"="sin conexión"  
  
**Base Namespace nativo de análisis**  
  
Para activar el análisis de espacio de nombres base nativo, en el registro de agregar un nuevo valor DWORD con el nombre de: BaseNativeNamespaces y establezca su valor en 1 (bajo la clave de catálogo que desea admitir).  Por ejemplo, si desea usar el catálogo de Visual Studio, puede agregar la clave para la ruta de acceso:  
  
HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Catalogs\VisualStudio15
  
Cuando una palabra clave de F1 en el formato que se encuentra el encabezado o un método, el carácter '/' se va a analizar, lo que produce la construcción siguiente:  
  
-   ENCABEZADO: será el espacio de nombres que puede usarse para registrar en el registro  
  
-   MÉTODO: Esto se convertirá en la palabra clave que se pasa a través de.  
  
Por ejemplo, dada una biblioteca personalizada denominada CustomLibrary y un método denominado MyTestMethod, cuando una solicitud entra en ella de F1 se formatearán como `CustomLibrary/MyTestMethod`.  
  
Un usuario, a continuación, puede registrar CustomLibrary como el espacio de nombres en el subárbol de socios y proporcionar cualquier clave de ubicación que deseen, y la palabra clave que se pasan a la consulta será MyTestMethod.  
  
**Habilitar depuración de la herramienta en el IDE de la Ayuda**  
  
Agregue la siguiente clave del registro y el valor:  
  
Tecla de ayuda HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\15.0\Dynamic: Display Debug Output en el valor de venta directa: Sí  
  
En el IDE, en el elemento de menú Ayuda, seleccione "Depurar el contexto de ayuda"  
  
**Metadatos de contenido**  
  
En la siguiente tabla, cualquier cadena que aparece entre corchetes es un marcador de posición que debe ser reemplazado por un valor reconocido. Por ejemplo, en \<meta name="Microsoft.Help.Locale" contenido = "[código de idioma]" / >, "[código de idioma]" debe reemplazarse por un valor como "en-us".  
  
|Propiedad (representación HTML)|Descripción|  
|--------------------------------------|-----------------|  
|\<contenido de meta name="Microsoft.Help.Locale" = "[lenguaje de código]" / >|Establece una configuración regional de este tema. Si esta etiqueta se utiliza en un tema, se debe usar solo una vez y debe insertarse por encima de las otras etiquetas de Microsoft Help. Si no se usa esta etiqueta, el texto del cuerpo del tema está indizado mediante el uso de separador de palabras está asociado a la configuración regional del producto, si se especifica; en caso contrario, la en-us se utiliza el separador de palabras. Esta etiqueta se ajusta al ISOC RFC 4646. Para asegurarse de que Microsoft Help funciona correctamente, utilice esta propiedad en lugar del atributo de idioma general.|  
|\<contenido de meta name="Microsoft.Help.TopicLocale" = "[lenguaje de código]" / >|Establece una configuración regional de este tema cuando también se usan otras configuraciones regionales. Si esta etiqueta se utiliza en un tema, se debe usar solo una vez. Use esta etiqueta cuando el catálogo de contenido en más de un idioma. Varios temas en un catálogo pueden tener el mismo Id., pero cada una debe especificar un TopicLocale único. El tema que especifica un TopicLocale que coincida con la configuración regional del catálogo es el tema que se muestra en la tabla de contenido. Sin embargo, todas las versiones de idioma del tema se muestran en los resultados de búsqueda.|  
|\<Título > [Title] \< /title >|Especifica el título de este tema. Esta etiqueta es necesaria y debe utilizarse solo una vez en un tema. Si el cuerpo del tema no contiene un título \<div > sección, este título se muestra en el tema y en la tabla de contenido.|  
|\<nombre de metadatos = "Microsoft.Help.Keywords" contenido = "[aKeywordPhrase]" / >|Especifica el texto de un vínculo que se muestra en el panel del índice del Visor de ayuda. Cuando se hace clic en el vínculo, se muestra el tema. Puede especificar varias palabras clave de índice para un tema, o si no desea que los vínculos a este tema para que aparezca en el índice, puede omitir esta etiqueta. Palabras clave "K" de versiones anteriores de ayuda se puede convertir a esta propiedad.|  
|\<contenido de meta name="Microsoft.Help.Id" = "[TopicID]" / >|Establece el identificador de este tema. Esta etiqueta es necesaria y debe utilizarse solo una vez en un tema. El identificador debe ser único entre los temas en el catálogo que tienen la misma configuración regional. En otro tema, puede crear un vínculo a este tema mediante el uso de este identificador.|  
|\<meta name="Microsoft.Help.F1" content="[System.Windows.Controls.Primitives.IRecyclingItemContainerGenerator]"/ >|Especifica la palabra clave de F1 de este tema. Puede especificar varias palabras clave de F1 para un tema o puede omitir esta etiqueta si no desea que este tema se mostrará al usuario de una aplicación presiona la tecla F1. Normalmente, se especifica una sola palabra clave de F1 para un tema. Palabras clave de "F" de versiones anteriores de ayuda se puede convertir a esta propiedad.|  
|\<nombre de metadatos = "Descripción" content = "[descripción del tema]" / >|Proporciona un breve resumen del contenido de este tema. Si esta etiqueta se utiliza en un tema, se debe usar solo una vez. Se tiene acceso a esta propiedad directamente en la biblioteca de consulta; no se almacena en el archivo de índice.|  
 contenido de meta name="Microsoft.Help.TocParent" = "[parent_Id]" / >|Especifica el tema primario de este tema en la tabla de contenido. Esta etiqueta es necesaria y debe utilizarse solo una vez en un tema. El valor es el Microsoft.Help.Id del elemento primario. Un tema puede tener una sola ubicación en la tabla de contenido. "-1" se considera que el Id. del tema de la raíz de la tabla de contenido. En [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)], que la página es la página inicial del Visor de ayuda. Se trata de la misma razón que agregamos específicamente TocParent =-1 para algunos de los temas para asegurarse de que aparecen en la parte superior nivel. La página de inicio del Visor de ayuda es una página del sistema y por lo que no son reemplazables. Si un VSP intenta agregar una página con un Id. de -1, puede obtener agregado para el conjunto de contenido, pero el Visor de ayuda siempre tendrá que utilizar la página del sistema - página principal del Visor de ayuda|  
|\<contenido de meta name="Microsoft.Help.TocOrder" = "[entero]" / >|Especifica que en la tabla de contenido en este tema aparece como relativo para sus temas del mismo nivel. Esta etiqueta es necesaria y debe utilizarse solo una vez en un tema. El valor es un entero. Un tema que especifica un valor menor entero aparece por encima de un tema que especifica un número entero mayor importancia.|  
|\<contenido de meta name="Microsoft.Help.Product" = "[product code]" / >|Especifica el producto que se describen en este tema. Si esta etiqueta se utiliza en un tema, se debe usar solo una vez. Esta información también se puede proporcionar como un parámetro que se pasa al indizador de ayuda.|  
|\<contenido de meta name="Microsoft.Help.ProductVersion" = "[número de versión]" / >|Especifica la versión del producto que se describen en este tema. Si esta etiqueta se utiliza en un tema, se debe usar solo una vez. Esta información también se puede proporcionar como un parámetro que se pasa al indizador de ayuda.|  
|\<contenido de meta name="Microsoft.Help.Category" = "[cadena]" / >|Se utiliza con los productos para identificar subsecciones de contenido. Puede identificar varias subsecciones para un tema, o si no desea que los vínculos para identificar cualquier subsecciones, puede omitir esta etiqueta. Esta etiqueta se utiliza para almacenar los atributos de TargetOS y TargetFrameworkMoniker cuando se convierte un tema desde una versión anterior de la Ayuda. El formato del contenido es AttributeName:AttributeValue.|  
|\<el contenido de meta name="Microsoft.Help.TopicVersion ="[número de versión de tema]"/ >|Especifica esta versión del tema cuando existen varias versiones de un catálogo. Porque Microsoft.Help.Id no se garantiza que sea único, esta etiqueta es necesaria cuando más de una versión de un tema existe en un catálogo, por ejemplo, cuando un catálogo contiene un tema de .NET Framework 3.5 y un tema para .NET Framework 4 y ambos tienen el mismo Micro software. Help.Id.|  
|\<nombre de metadatos = "SelfBranded" content = "[TRUE o FALSE]" / >|Especifica si este tema usa el paquete de personalización de marca de inicio de administrador de bibliotecas de ayuda o un paquete de personalización de marca específica para el tema. Esta etiqueta debe ser verdadero o falso. Si es TRUE, el paquete de personalización de marca para el tema asociado reemplaza el paquete de personalización de marca que se establece cuando se inicia el Administrador de bibliotecas de ayuda para que se represente el tema según lo previsto incluso si es diferente de la representación de otro tipo de contenido. Si es FALSE, se representa en el tema actual según el paquete de personalización de marca que se establece cuando se inicia el Administrador de bibliotecas de ayuda. De forma predeterminada, se supone una personalización de marca automáticamente como false a menos que se declara la variable SelfBranded como TRUE; Administrador de bibliotecas de ayuda por lo tanto, no es necesario declarar \<nombre meta = "SelfBranded" content = "FALSE" / >.|  
  
### <a name="creating-a-branding-package"></a>Crear un paquete de personalización de marca  
La versión de Visual Studio incluye a una serie de diferentes productos de Visual Studio, incluido el aislamiento y shells integrados para Partners de Visual Studio.  Cada uno de estos productos requiere cierto grado de personalización de marca de soporte técnico, único para el producto contenido de ayuda basado en el tema.  Por ejemplo, temas de Visual Studio necesitan tener una presentación marca coherente, mientras que SQL Studio, que ajusta el Shell de ISO, requiere su propio único ayuda contenido personalización de marca de cada tema.  Un asociado de Shell integrado puede sus temas de ayuda para estar dentro del elemento primario contenido de Ayuda del producto de Visual Studio mientras se mantiene su propio tema de la personalización de marca.  
  
Personalización de marca de paquetes se instalan con el producto que contiene el Visor de ayuda.  Para los productos de Visual Studio:  
  
-   Un paquete de personalización de marca de reserva (Branding_\<configuración regional > MSHC) se instala en la raíz de la aplicación 2.3 del Visor de ayuda (ejemplo: C:\Program Files (x86) \Microsoft Help Viewer\v2.3) por el paquete de idioma del Visor de ayuda.  Se utiliza para los casos donde no está instalado ya sea el paquete de personalización de marca del producto (no se ha instalado ningún contenido) o daños en el paquete de personalización de marca instalado.  Tenga en cuenta que los elementos de Visual Studio (logotipo y comentarios) se omiten cuando se utiliza el paquete de personalización de marca de reserva de raíz de aplicación.  
  
-   Cuando se instala el contenido de Visual Studio desde el servicio de contenido del paquete, también se instala un paquete de personalización de marca (para el primer escenario de instalación del contenido de tiempo).  Si hay una actualización para el paquete de personalización de marca, la actualización se instala cuando se produce la siguiente actualización de contenido o la acción de instalación de paquete adicional.  
  
El Visor de Ayuda de Microsoft admite la personalización de marca de temas basadas en los metadatos de tema.  
  
-   Donde los metadatos de tema definen self marca = true, representar el tema tal cual, no hacer nada (en la medida de personalización de marca).  
  
-   Donde los metadatos de tema definen self marca = false, utilice el paquete de personalización de marca asociado con el valor de metadatos de TopicVendor.  
  
-   Contenido donde los metadatos de tema definen name="Microsoft.Help.TopicVendor" =\< nombre de paquete de personalización de marca en proveedor MSHA >, use el paquete de personalización de marca definido en el valor de contenido.  
  
-   Tenga en cuenta que en el catálogo de Visual Studio, hay una aplicación de prioridad de los paquetes de personalización de marca.  Se aplica la primera marca de predeterminada Visual Studio y, a continuación, si definidos en los metadatos de tema y compatible con la personalización de marca asociado del paquete (como se define en el msha de instalación), se aplica la definida por el proveedor marca como una invalidación.  
  
Elementos de personalización de marca normalmente se dividen en tres categorías principales:  
  
-   Elementos de encabezado (algunos ejemplos son el vínculo de comentarios, texto de aviso condicional, logotipo)  
  
-   Contenido comportamientos (algunos ejemplos son elementos de texto del control de expandir o contraer y los elementos del fragmento de código)  
  
-   Elementos del pie de página (ejemplo Copyright)  
  
Elementos que se consideran como incluyen elementos con marca (que se detallan en esta especificación):  
  
-   Logotipo de producto del catálogo (por ejemplo, Visual Studio)  
  
-   Elementos de correo electrónico y el vínculo de comentarios  
  
-   Texto de aviso  
  
-   Texto de copyright  
  
Se incluyen los archivos auxiliares en el paquete de personalización de marca del Visor de Ayuda de Visual Studio:  
  
-   Gráficos (logotipos, iconos, etcetera.)  
  
-   Branding.js - auxiliares comportamientos del contenido de los archivos de script  
  
-   Branding.XML - cadenas que se usa de manera coherente a través de contenido del catálogo.  Nota: para elementos de texto de localización de Visual Studio en el branding.xml incluyen _locID = "\<valor único >"  
  
-   Branding.CSS - definiciones de estilo para la coherencia de presentación  
  
-   Printing.CSS - definiciones de estilos de presentación impresa coherente  
  
Como se mencionó anteriormente, paquetes de personalización de marca están asociados con el tema:  
  
-   Cuando SelfBranded = false se define en los metadatos, el tema hereda el catálogo de paquete de personalización de marca  
  
-   O cuando SelfBranded = false y hay un paquete de personalización de marca única definido en el MSHA y disponible cuando se instala el contenido  
  
Para VSPs implementar paquetes de personalización de marca personalizados (contenido VSP, SelfBranded = True), una manera de continuar es empezar con el paquete de personalización de marca de reserva (que se instala con el Visor de Ayuda) y cambie el nombre del archivo según corresponda.  El Branding_\<configuración regional > MSHC archivo es un archivo zip con la extensión de archivo cambiado a MSHC, por lo que simplemente cambie la extensión de MSHC a .zip y extraiga el contenido.  Vea a continuación para elementos de un paquete de personalización de marca y modificar según corresponda (por ejemplo, cambiar el logotipo del logotipo VSP y la referencia para el logotipo en el archivo Branding.xml, se actualizan Branding.xml por características específicas VSP, etcetera).  
  
Cuando se realizan todas las modificaciones, crear un archivo zip que contiene los elementos de personalización de marca deseados y cambie la extensión a MSHC.  
  
Para asociar el paquete de personalización de marca personalizado, cree el MSHA que contiene la referencia al archivo mshc marca junto con el contenido mshc (que contiene los temas).  Vea a continuación "MSHA" cómo crear un MSHA básica.  
  
El archivo Branding.xml contiene un elementos de lista que se usa para representar constantemente los elementos específicos de un tema cuando el tema contiene \<meta name="Microsoft.Help.SelfBranded" contenido = "false" / >.  La lista de Visual Studio de elementos en el archivo Branding.xml se menciona a continuación.  Tenga en cuenta que esta lista está diseñada para utilizarse como una plantilla para implantaciones de ISO Shell, que modifican estos elementos (por ejemplo, logotipo, comentarios y Copyright) para satisfacer su propias necesidades de personalización de marca de producto.  
  
Nota: las variables que se indican mediante "{n}" tienen dependencias del código, quitar o cambiar estos valores provocará errores y, posiblemente, bloqueo de aplicación. Identificadores de localización (ejemplo _locID="codesnippet.n") se incluyen en el paquete de personalización de marca de Visual Studio.  
  
**Branding.Xml**  
  
|||  
|-|-|  
|Característica:|**CollapsibleArea**|  
|Usar:|Expandir el texto del control de contenido de contrae|  
|**Element**|**Valor**|  
|ExpandText|Expand|  
|CollapseText|Contraer|  
|Característica:|**CodeSnippet**|  
|Usar:|Texto del control de fragmento de código.  Nota: Se cambiará el contenido del fragmento de código con "Poco problemático" espacio al espacio.|  
|**Element**|**Valor**|  
|CopyToClipboard|Copiar en el Portapapeles|  
|ViewColorizedText|Vista aparece con un color|  
|CombinedVBTabDisplayLanguage|Visual Basic (ejemplo)|  
|VBDeclaration|Declaración|  
|VBUsage|Uso|  
|Característica:|**Comentarios, el pie de página y el logotipo de**|  
|Usar:|Proporciona un control de comentarios de cliente proporcionar comentarios sobre el tema actual a través de correo electrónico.  Texto de copyright para el contenido.  Definición de logotipo.|  
|**Element**|**Valor (estas cadenas pueden modificarse para satisfacer la necesidad de adopción de contenido).**|  
|CopyRight|© 2013 Microsoft Corporation. Todos los derechos reservados.|  
|SendFeedback|\<un href = "{0}" {1} > Enviar comentarios\</a > en este tema a Microsoft.|  
|FeedbackLink||  
|LogoTitle|[!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)]|  
|LogoFileName|vs_logo_bk.gif|  
|LogoFileNameHC|vs_logo_wh.gif|  
|Característica:|**Declinación de responsabilidades**|  
|Usar:|Un conjunto de casos declinaciones de responsabilidades específicas para la máquina contenido traducido.|  
|**Element**|**Valor**|  
|MT_Editable|En este artículo es una traducción automática. Si tiene una conexión a Internet, seleccione "Ver este tema en línea" para ver esta página en modo editable con el contenido original en inglés al mismo tiempo.|  
|MT_NonEditable|En este artículo es una traducción automática. Si tiene una conexión a Internet, seleccione "Ver este tema en línea" para ver esta página en modo editable con el contenido original en inglés al mismo tiempo.|  
|MT_QualityEditable|En este artículo se tradujo manualmente. Si tiene una conexión a Internet, seleccione "Ver este tema en línea" para ver esta página en modo editable con el contenido original en inglés al mismo tiempo.|  
|MT_QualityNonEditable|En este artículo se tradujo manualmente. Si tiene una conexión a Internet, seleccione "Ver este tema en línea" para ver esta página en modo editable con el contenido original en inglés al mismo tiempo.|  
|MT_BetaContents|En este artículo es una traducción para una versión preliminar automática. Si tiene una conexión a Internet, seleccione "Ver este tema en línea" para ver esta página en modo editable con el contenido original en inglés al mismo tiempo.|  
|MT_BetaRecycledContents|En este artículo se tradujo manualmente para una versión preliminar. Si tiene una conexión a Internet, seleccione "Ver este tema en línea" para ver esta página en modo editable con el contenido original en inglés al mismo tiempo.|  
|Característica:|**Vinculación**|  
|Usar:|Compatibilidad con vínculos a los temas en línea|  
|**Element**|**Valor**|  
|LinkTableTitle|Tabla de vínculos|  
|TopicEnuLinkText|Ver la versión en inglés\</a > de este tema que está disponible en el equipo.|  
|TopicOnlineLinkText|Ver este tema \<un href = "{0}" {1} > en línea\</a >|  
|OnlineText|En línea|  
|Característica:|**Control de Audio de vídeo**|  
|Usar:|Mostrar elementos y el texto para el contenido de vídeo|  
|**Element**|**Valor**|  
|MultiMediaNotSupported|Internet Explorer 9 o posterior debe instalarse para admitir contenido de {0}.|  
|VideoText|Mostrar vídeo|  
|AudioText|audio de transmisión por secuencias|  
|OnlineVideoLinkText|\<p > para ver el vídeo asociado a este tema, haga clic en {0}\<un href = "\ {1\\}" > {2}here\</a >.\< /p >|  
|OnlineAudioLinkText|\<p > para escuchar el audio asociado a este tema, haga clic en {0}\<un href = "\ {1\\}" > {2}here\</a >.\< /p >|  
|Característica:|**Control contenido no instalado**|  
|Usar:|Elementos de texto (cadenas) que se usan para la representación de contentnotinstalled.htm|  
|**Element**|**Valor**|  
|ContentNotInstalledTitle|No se encontró ningún contenido en el equipo.|  
|ContentNotInstalledDownloadContentText|\<p > para descargar contenido en el equipo, \<un href = "{0}" {1} > haga clic en la pestaña administrar\</a >.\< /p >|  
|ContentNotInstalledText|\<p > contenido no está instalado en el equipo. Consulte al administrador para la instalación del contenido de Ayuda local. \</p >|  
|Característica:|**Control de tema no encontrado**|  
|Usar:|Elementos de texto (cadenas) que se usan para la representación de topicnotfound.htm|  
|**Element**|**Valor**|  
|TopicNotFoundTitle|No se encuentra el tema solicitado en el equipo.|  
|TopicNotFoundViewOnlineText|\<p > el tema solicitado no se encontró en el equipo, pero puede \<un href = "{0}" {1} > ver el tema en línea\</a >.\< /p >|  
|TopicNotFoundDownloadContentText|\<p > ve el panel de navegación para obtener vínculos a temas similares, o \<un href = "{0}" {1} > haga clic en la pestaña administrar\</a > para descargar contenido en el equipo.\< /p >|  
|TopicNotFoundText|\<p > el tema solicitado no se encontró en el equipo. \</p >|  
|Característica:|**Tema dañado Control**|  
|Usar:|Elementos de texto (cadenas) que se usan para la representación de topiccorrupted.htm|  
|**Element**|**Valor**|  
|TopicCorruptedTitle|No se puede mostrar el tema solicitado.|  
|TopicCorruptedViewOnlineText|\<p > Visor de ayuda es no se puede mostrar el tema solicitado. Puede haber un error en el contenido del tema o una dependencia del sistema subyacente. \</p >|  
|Característica:|**Control de la página principal**|  
|Usar:|Texto que admiten la presentación del contenido de nodo de nivel superior del Visor de ayuda.|  
|**Element**|**Valor**|  
|HomePageTitle|Página principal del Visor de ayuda|  
|HomePageIntroduction|\<p > Asistente para el Visor de Ayuda de Microsoft, una fuente fundamental de información para todos los que usan herramientas, productos, tecnologías y servicios de Microsoft. El Visor de Ayuda proporciona acceso a información de referencia y "Cómo...", código de ejemplo, artículos técnicos y mucho más. Para buscar el contenido que necesita, busque en la tabla de contenido, utilice la búsqueda de texto completo o navegar por el contenido mediante el índice de palabras clave. \</p >|  
|HomePageContentInstallText|\<p >\<br / > Use la \<un href = "{0}" {1} > Administrar contenido\</a > pestaña para hacer lo siguiente:\<ul >\<li > Agregar contenido al equipo.\< /li >\<li > Buscar actualizaciones para el contenido local.\< /li >\<li > quitar contenido de su equipo.\< /li >\</ul >\</p >|  
|HomePageInstalledBooks|Libros instalados|  
|HomePageNoBooksInstalled|No se encontró ningún contenido en el equipo.|  
|HomePageHelpSettings|Configuración de contenido de ayuda|  
|HomePageHelpSettingsText|\<p > la configuración actual es la Ayuda local. El Visor de Ayuda muestra el contenido que ha instalado en el equipo. \<br / > para cambiar el origen de contenido de la Ayuda, en la barra de menús de Visual Studio, elija \<span style = "{0}" > Ayuda, establecer preferencias de la Ayuda\</span >.\< br / >\</p >|  
|Megabytes|MB|  
  
**Branding.js**  
  
El archivo branding.js contiene código JavaScript utilizado por los elementos de personalización de marca del Visor de Ayuda de Visual Studio.  A continuación se muestra una lista de los elementos de personalización de marca y la función de JavaScript auxiliar.  Todas las cadenas para que se adapten de este archivo se definen en la sección "Cadenas localizables" en la parte superior de este archivo.  Tenga en cuenta que se ha creado el archivo ICL loc cadenas dentro del archivo branding.js.  
  
||||  
|-|-|-|  
|**Característica de personalización de marca**|**Función de JavaScript**|**Descripción**|  
|Var...||Definir variables|  
|Obtiene el lenguaje de código de usuario|setUserPreferenceLang|asigna un índice # para el lenguaje de código|  
|Establecer y obtener valores de cookie|getCookie, setCookie||  
|Miembro heredado|changeMembersLabel|Expandir o contraer miembro heredado|  
|Cuando SelfBranded = False|onLoad|Leer la cadena de consulta para comprobar si es una solicitud de impresión.  Establecer todos los codesnippets para centrarse en la pestaña preferido del usuario.  Si es un proceso de impresión solicitud, a continuación, establezca isPrinterFriendly en true. Compruebe si el modo de contraste alto.|  
|Fragmento de código|addSpecificTextLanguageTagSet||  
||getIndexFromDevLang||  
||Ficha cambiar se||  
||setCodesnippetLang||  
||setCurrentLang||  
||CopyToClipboard||  
|CollapsibleArea|addToCollapsibleControlSet|escribir todos los objetos de control que se puede contraer en la lista.|  
||CA_Click|según el estado del área contraíble, define qué imagen y texto que se va a presentar|  
|Compatibilidad de contraste de logotipo|isBlackBackground()|Se llama para determinar si el fondo es negro.  Solo exactas cuando en modo de contraste alto.|  
||isHighContrast()|utilizar un intervalo de color para detectar el modo de contraste alto|  
||onHighContrast(black)|Se llama cuando se detecta el contraste alto|  
|Funcionalidad LST|||  
||addToLanSpecTextIdSet(id)||  
||updateLST(currentLang)||  
||getDevLangFromCodeSnippet(lang)||  
|Funcionalidad multiMedia|título (begin, end, texto, estilo)||  
||findAllMediaControls(normalizedId)||  
||getActivePlayer(normalizedId)||  
||captionsOnOff(id)||  
||toSeconds(t)||  
||getAllComments(node)||  
||styleRectify (nombre de estilo, styleValue)||  
||showCC(id)||  
||Subtitle(ID)||  
  
**ARCHIVOS HTM**  
  
El paquete de personalización de marca contiene un conjunto de archivos HTM que admiten escenarios para comunicar información de clave para los usuarios de contenido de ayuda, por ejemplo una página principal que contiene una sección que describe qué conjuntos de contenido se instalan y páginas que indica al usuario cuando no pueden temas se encuentra en el conjunto de temas local. Tenga en cuenta que se pueden modificar estos archivos HTM por producto.  Los proveedores de ISO Shell son capaces de tomar predeterminado del paquete de personalización de marca y cambiar el comportamiento y el contenido de estas páginas para el conjunto de sus necesidades.  Estos archivos hacen referencia a su paquete de personalización de marca correspondiente en orden para que las etiquetas de personalización de marca obtener el contenido correspondiente del archivo branding.xml.  
  
||||  
|-|-|-|  
|**Archivo**|**Uso**|**Muestra el origen de contenido**|  
|homepage.htm|Se trata de una página que muestra contenido instalado actualmente y cualquier otro mensaje adecuado para presentar al usuario acerca de su contenido.  Este archivo tiene el contenido de "Microsoft.Help.Id" del atributo de datos de metadatos adicional = "-1" que coloca este contenido en la parte superior de la tabla de contenido de contenido local.||  
||< META_HOME_PAGE_TITLE_ADD / >|Branding.XML, etiqueta \<HomePageTitle >|  
||< HOME_PAGE_INTRODUCTION_SECTION_ADD / >|Branding.XML, etiqueta \<HomePageIntroduction >|  
||< HOME_PAGE_CONTENT_INSTALL_SECTION_ADD / >|Branding.XML, etiqueta \<HomePageContentInstallText >|  
||< HOME_PAGE_BOOKS_INSTALLED_SECTION_ADD / >|Encabezado de sección Branding.xml etiqueta\<HomePageInstalledBooks >, los datos generados a partir de la aplicación, \<HomePageNoBooksInstalled > cuando no se instalan ningún libros.|  
||< HOME_PAGE_SETTINGS_SECTION_ADD / >|Encabezado de sección Branding.xml etiqueta \<HomePageHelpSettings >, sección texto \<HomePageHelpSettingsText >.|  
|topiccorrupted.htm|Cuando no existe un tema en la configuración local, pero por alguna razón no se puede mostrar (dañado contenido).||  
||< META_TOPIC_CORRUPTED_TITLE_ADD / >|Branding.XML, etiqueta \<TopicCorruptedTitle >|  
||< TOPIC_CORRUPTED_SECTION_ADD / >|Branding.XML, etiqueta \<TopicCorruptedViewOnlineText >|  
|topicnotfound.htm|Cuando un tema no se encuentra en el contenido local establecido ni está disponible en línea||  
||< META_TOPIC_NOT_FOUND_TITLE_ADD / >|Branding.XML, etiqueta \<TopicNotFoundTitle >|  
||< META_TOPIC_NOT_FOUND_ID_ADD / >|Branding.XML, etiqueta \<TopicNotFoundViewOnlineText > + \<TopicNotFoundDownloadContentText >|  
||< TOPIC_NOT_FOUND_SECTION_ADD / >|Branding.XML, etiqueta \<TopicNotFoundText >|  
|contentnotinstalled.htm|Cuando no hay contenido local instalado para el producto.||  
||< META_CONTENT_NOT_INSTALLED_TITLE_ADD / >|Branding.XML, etiqueta \<ContentNotInstalledTitle >|  
||< META_CONTENT_NOT_INSTALLED_ID_ADD / >|Branding.XML, etiqueta \<ContentNotInstalledDownloadContentText >|  
||< CONTENT_NOT_INSTALLED_SECTION_ADD / >|Branding.XML, etiqueta \<ContentNotInstalledText >|  
  
**Archivos CSS**  
  
La Ayuda de Visor de personalización de marca paquete de Visual Studio contiene dos archivos de css para admitir la presentación del contenido coherente ayuda de Visual Studio:  
  
-   Branding.CSS - contiene elementos de css para representar where SelfBranded = false  
  
-   Printer.CSS - contiene elementos de css para representar where SelfBranded = false  
  
Archivos de branding.CSS incluye definiciones para la presentación de tema de Visual Studio (salvedad es que la branding.css contenidos en el Branding_\<configuración regional > puede cambiar MSHC desde el servicio de paquete).  
  
**Archivos de gráficos**  
  
Contenido de Visual Studio muestra un logotipo de Visual Studio, así como otros gráficos.  A continuación, se muestra la lista completa de archivos de gráficos en el paquete de personalización de marca del Visor de Ayuda de Visual Studio.  
  
||||  
|-|-|-|  
|**Archivo**|**Uso**|**Ejemplos**|  
|Clear.gif|Usa para representar un área contraíble||  
|footer_slice.gif|Presentación de pie de página||  
|info_icon.gif|Utilizado para mostrar información|Declinación de responsabilidades|  
|online_icon.gif|Este icono es que se asociará con vínculos en línea||  
|tabLeftBD.gif|Usa para representar el contenedor de fragmento de código||  
|tabRightBD.gif|Usa para representar el contenedor de fragmento de código||  
|vs_logo_bk.gif|Utilizado para las referencias del logotipo de contraste normal como se define en la etiqueta de Branding.xml \<LogoFileName >.  Para los productos de Visual Studio, nombre del logotipo es vs_logo_bk.gif.||  
|vs_logo_wh.gif|Utilizada para referencias de logotipo alta normal, tal como se define en la etiqueta de Branding.xml \<LogoFileNameHC >.  Para los productos de Visual Studio, nombre del logotipo es vs_logo_wh.gif.||  
|ccOff.png|Gráfico de subtítulos (CC)||  
|ccOn.png|Gráfico de subtítulos (CC)||  
|ImageSprite.png|Usa para representar un área contraíble|Expandir o contraer el gráfico|  
  
### <a name="deploying-a-set-of-topics"></a>Implementación de un conjunto de temas  
Se trata de un tutorial muy rápido y sencillo para crear una implementación de contenido del Visor de ayuda establecer formada por un archivo MSHA y el conjunto de archivos .cab o MSHC del que contiene los temas. El MSHA es un archivo XML que describe un conjunto de archivos .cab o los archivos MSHC. El Visor de ayuda puede leer el MSHA para obtener una lista de contenido (el archivo. CAB o. Archivos MSHC) disponibles para la instalación local.  
  
Esto es sólo un manual que describe el esquema XML muy básico para el Visor de ayuda, MSHA.  Tenga en cuenta que hay una implementación de ejemplo a continuación de esta breve introducción y HelpContentSetup.msha de ejemplo.  
  
El nombre de la MSHA, para los fines de este manual es HelpContentSetup.msha (el nombre del archivo puede ser cualquier cosa, con la extensión. MSHA). HelpContentSetup.msha (ejemplo a continuación) debe contener una lista de los archivos CAB o MSHCs disponibles.  Tenga en cuenta que el tipo de archivo debe ser coherente dentro de la MSHA (no es compatible con una combinación de tipos de archivo MSHA y CAB). Para cada archivo CAB o MSHC, debe haber un \<div clase = "paquete" >... \</div > (vea el ejemplo siguiente).  
  
Nota: en el siguiente ejemplo de implementación, hemos incluido el paquete de personalización de marca. Esto es importante incluir con el fin de obtener los elementos necesarios de representación contenido de Visual Studio y los comportamientos de contenido.  
  
Ejemplo de archivo de HelpContentSetup.msha: (reemplazar "nombre 1 del conjunto de contenido" y "contenido el nombre de conjunto 2", etc. con sus nombres de archivo.)  
  
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
  
1.  Cree una carpeta local, algo como "C:\SampleContent"  
  
2.  En este ejemplo, se van a usar archivos MSHC para que contenga los temas.  Un MSHC es un archivo zip con la extensión de archivo cambiado de .zip a. MSHC.  
  
3.  Crear el debajo de HelpContentSetup.msha como un archivo de texto (el Bloc de notas se utilizó para crear el archivo) y guárdelo en la carpeta se indicó anteriormente (vea el paso 1).  
  
Tenga en cuenta que la clase "Branding" existe y es único. La personalización de marca mshc se incluye en este manual para que el contenido instalado tendrá la personalización de marca y los comportamientos del contenido que se encuentran en el MSHCs tendrá los elementos de asistencia adecuado contenidos en el paquete de personalización de marca. Sin esto, se producirán errores cuando el sistema busca elementos de compatibilidad que no forman parte de la (instalado) copiados contenido.  
  
Para obtener el paquete de personalización de marca de Visual Studio, copie el archivo de Branding_en US.mshc en C:\Program Files (x86) \Microsoft Help Viewer\v2.3\ en la carpeta de trabajo.  
  
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
  
Usar y extender los pasos anteriores le permitirá VSPs implementar sus conjuntos de contenido para el Visor de Ayuda de Visual Studio.  
  
### <a name="adding-help-to-the-visual-studio-shell-integrated-and-isolated"></a>Agregar ayuda a Visual Studio Shell (integrado y aislado)  
**Introducción**  
  
Este tutorial muestra cómo incorporar contenido de la Ayuda en una aplicación de Shell de Visual Studio y, a continuación, implementarlo.  
  
**Requisitos**  
  
1.  [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)]  
  
2.  [Aislamiento de Visual Studio 2013 Shell Redist](http://www.microsoft.com/visualstudio/11/downloads#vs-shell)  
  
**Información general**  
  
El [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] Shell es una versión de la [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] IDE en la que se puede basar una aplicación. Estas aplicaciones contienen el Shell aislado junto con las extensiones que cree. Usar plantillas de proyecto de Shell aislado, que se incluyen en el [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] SDK para compilar las extensiones.  
  
Los pasos básicos para crear una aplicación basada en Shell aislado y su ayuda:  
  
1.  Obtener el [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] ISO Shell redistributable (descarga de Microsoft).  
  
2.  En Visual Studio, cree una extensión de ayuda que se basa en el Shell aislado, por ejemplo, la extensión de la Ayuda de Contoso que se describe más adelante en este tutorial.  
  
3.  Ajustar la extensión y el Shell de ISO redistribuible en una implementación de MSI (una instalación de la aplicación). En este tutorial no incluye un paso de instalación.  
  
Crear un almacén de contenido de Visual Studio. Para el escenario de Shell integrado, cambiar Studio12 Visual para el nombre del catálogo de productos de la manera siguiente:  
  
-   Cree la carpeta C:\ProgramData\Microsoft\HelpLibrary2\Catalogs\VisualStudio15.  
  
-   Cree un archivo denominado CatalogType.xml y agréguelo a la carpeta. El archivo debe contener las siguientes líneas de código:  
  
    ```xml
    <?xml version="1.0" encoding="UTF-8"?>  
    <catalogType>UserManaged</catalogType>  
    ```  
  
Definir el almacén de contenido en el registro. Para el Shell integrado, cambiar VisualStudio15 para el nombre del catálogo de productos:  
  
-   HKLM\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Catalogs\VisualStudio15  
  
     Key: Valor de cadena de LocationPath: C:\ProgramData\Microsoft\HelpLibrary2\Catalogs\VisualStudio15\  
  
-   HKLM\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Catalogs\VisualStudio15\en-US  
  
     Clave: Valor cadena CatalogName: [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] documentación  
  
**Crear el proyecto**  
  
Para crear una extensión de Shell aislado:  
  
1.  En Visual Studio, en **archivo**, elija **nuevo proyecto**, en **otros tipos de proyectos** elegir **extensibilidad**y, a continuación, elija  **Visual Studio Shell aislado**. Denomine el proyecto `ContosoHelpShell`) para crear un proyecto de extensibilidad que se basa en la plantilla de Shell aislado de Visual Studio.  
  
2.  En el Explorador de soluciones, en el proyecto ContosoHelpShellUI, en la carpeta archivos de recursos, abra ApplicationCommands.vsct. Asegúrese de que esta línea está comentada (busque "No_Help"):`<!-- <define name="No_HelpMenuCommands"/> -->`  
  
3.  Presione la tecla F5 para compilar y ejecutar **depurar**. En la instancia experimental del IDE de Shell aislado, elija la **ayuda** menú. Asegúrese de que el **ver Ayuda**, **agregar y quitar contenido de la Ayuda**, y **establecer preferencias de la Ayuda** comandos aparecen.  
  
4.  En el Explorador de soluciones, en el proyecto ContosHelpShell, en la carpeta de Shell personalización, abra ContosoHelpShell.pkgdef. Para definir el catálogo de Ayuda de Contoso, agregue las siguientes líneas:  
  
    ```  
     [$RootKey$\Help]  
    "Product"="Contoso"  
    "Catalog"="Contoso"  
    "Version"="100"  
    "BrandingPackage"="ContosoBrandingPackage.mshc"  
    ```  
  
5.  En el Explorador de soluciones, en el proyecto ContosHelpShell, en la carpeta de Shell personalización, abra ContosoHelpShell.Application.pkgdef. Para habilitar la Ayuda F1, agregue las siguientes líneas:  
  
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
  
6.  En el Explorador de soluciones, en el menú contextual de la solución ContosoHelpShell, elija la **propiedades** elemento de menú. En **propiedades de configuración**, seleccione **Configuration Manager**. En el **configuración** columna, cambiar cada valor de "Debug" a "Release".  
  
7.  Compile la solución. Esto crea un conjunto de archivos en una carpeta de versión, que se usará en la sección siguiente.  
  
Para probar esto como si hubieran sido:  
  
1.  En el equipo está implementando Contoso para instalar el Shell de ISO (desde) descargado.  
  
2.  Crear una carpeta en \\archivos \Program (x86)\\y asígnele el nombre `Contoso`.  
  
3.  Copie el contenido de la carpeta de la versión de ContosoHelpShell a \\\Program (x86) \Contoso\ carpeta.  
  
4.  Inicie el Editor del registro seleccionando **ejecutar** en el **iniciar** menú y escriba `Regedit`. En el editor del registro, elija **archivo**y, a continuación, **importación**. Vaya a la carpeta del proyecto ContosoHelpShell. En la subcarpeta ContosoHelpShell, elija ContosoHelpShell.reg.  
  
5.  Crear un almacén de contenido:  
  
     Para el Shell de ISO - crear un almacén de contenido de Contoso C:\ProgramData\Microsoft\HelpLibrary2\Catalogs\ContosoDev12  
  
     Para [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] Shell integrado, cree la carpeta C:\ProgramData\Microsoft\HelpLibrary2\Catalogs\VisualStudio15  
  
6.  Cree CatalogType.xml y agregue en el almacén de contenido (paso anterior) que contiene:  
  
    ```  
    <?xml version="1.0" encoding="UTF-8"?>  
    <catalogType>UserManaged</catalogType>  
    ```  
  
7.  Agregue las siguientes claves del registro:  
  
     HKLM\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Catalogs\VisualStudio15Key: Valor de cadena de LocationPath:  
  
     Para el Shell de ISO:  
  
     C:ProgramDataMicrosoftHelpLibrary2CatalogsVisualStudio15  
  
     [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)]Shell integrado:  
  
     C:ProgramDataMicrosoftHelpLibrary2CatalogsVisualStudio15en-EE. UU.  
  
     Clave: Valor cadena CatalogName: [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] documentación. Para el Shell de ISO, este es el nombre del catálogo.  
  
8.  Copie el contenido (MSHA y MSHC o .cab) en una carpeta local.  
  
9. Línea de comandos de Shell integrado de ejemplo para probar el almacén de contenido. Para el Shell de ISO, cambiar los valores de catálogo y launchingApp según corresponda para que coincida con el producto.  
  
     Método de "C:\Program archivos (x86) \Microsoft Help Viewer\v2.3\HlpViewer.exe" / CatalogName VisualStudio15 /helpQuery = "página & id = ContosoTopic0" /launchingApp Microsoft, VisualStudio, 12.0  
  
10. Inicie la aplicación Contoso (desde la raíz de la aplicación Contoso). Dentro del Shell de ISO, elija la **ayuda** elemento de menú y cambie la **establecer preferencias de la Ayuda** a **usar la Ayuda Local**.  
  
11. Dentro del shell, elija la **ayuda** elemento de menú, a continuación, **ver Ayuda**. Debe iniciar el Visor de Ayuda local. Pulse la pestaña **Administrar contenido**. En **origen de instalación**, elija la **disco** botón de opción. Elija la **...**  botón y vaya a la carpeta local que contiene el contenido de Contoso (copiado en la carpeta local en el paso anterior). Elija el HelpContentSetup.msha. Contoso debería aparecer ahora como un libro en las selecciones del libro. Elija **agregar**y, a continuación, elija la **actualización** botón (esquina inferior derecha).  
  
12. En el IDE de Contoso, presione la tecla F1 para probar la funcionalidad de F1.  
  
### <a name="additional-resources"></a>Recursos adicionales  
Para la API de tiempo de ejecución, consulte [API de Ayuda de Windows](http://msdn.microsoft.com/library/windows/desktop/hh447318\(v=vs.85\).aspx).  
  
Para obtener información adicional sobre cómo aprovechar la API de ayuda, consulte [ejemplos de código de Visor de ayuda](http://visualstudiogallery.msdn.microsoft.com/f08f296f-7076-4aec-8da3-8f0fbe04461e)  
  
Para proporcionar comentarios acerca de estos componentes, use [Microsoft Connect](http://connect.microsoft.com/).  
  
Envíe sugerencias sobre características a [Microsoft User Voice](http://visualstudio.uservoice.com/forums/121579-visual-studio)  
  
Para obtener ayuda adicional, pruebe el [foros de sistema de ayuda y documentación para desarrolladores de MSDN](http://social.msdn.microsoft.com/Forums/devdocs/threads)  
  
Actualizaciones sobre importantes problema, vea el [Léame del Visor de ayuda](http://go.microsoft.com/fwlink/?LinkID=231397&clcid=0x409)  
  
Para ponerse en contacto directamente con el equipo P.M. del Visor de ayuda, enviar correo electrónico ahlpfdbk@microsoft.com