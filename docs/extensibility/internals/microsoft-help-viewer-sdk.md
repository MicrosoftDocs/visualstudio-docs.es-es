---
title: "SDK del Visor de Ayuda de Microsoft | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 620d7dcd-d462-475e-a449-fbfa06ff12c5
caps.latest.revision: 33
caps.handback.revision: 33
ms.author: "gregvanl"
manager: "ghogen"
---
# SDK del Visor de Ayuda de Microsoft
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Este artículo contiene las siguientes tareas para que los integradores de Visor de Ayuda de Visual Studio:  
  
-   Crear un tema \(soporte de F1\)  
  
-   Crear un paquete de personalización de marca de contenido del Visor de ayuda  
  
-   Implementación de un conjunto de artículos  
  
-   Agregar ayuda al shell de Visual Studio \(integrada o aislado\)  
  
-   Recursos adicionales  
  
### Crear un tema \(soporte de F1\)  
 Esta sección proporciona información general de los componentes de un tema presentado, requisitos de tema, una breve descripción de cómo crear un tema \(incluidos los requisitos de compatibilidad de F1\) y, finalmente, un tema de ejemplo con el resultado representado.  
  
 **Introducción al Visor de tema de ayuda**  
  
 Cuando se llama a un tema para la representación, el Visor de ayuda obtiene los elementos de paquete de personalización de marca que están asociados con el tema en el momento de la instalación o última actualización, junto con el tema XHTML y combina los dos que dan como resultado en la vista de contenido presentada \(datos de personalización de marca \+ datos tema\).  El paquete de personalización de marca contiene logotipos, compatibilidad con comportamientos de contenido y texto de personalización de marca \(derechos de autor, etc.\).  Para obtener más información acerca de los elementos de paquete de personalización de marca, vea "Crear el paquete de personalización de marca" a continuación.  En caso de que no hay ningún paquete de personalización de marca asociado al tema, el Visor de ayuda usará el paquete de personalización de marca reserva ubicado en la raíz de la aplicación Visor de ayuda \(Branding\_en US.mshc\).  
  
 **Requisitos de tema del Visor de ayuda**  
  
 Para procesarse correctamente en el Visor de ayuda, contenido sin procesar del tema debe ser XHTML 1.1 básica de W3C.  
  
 Normalmente, un tema contiene dos secciones:  
  
-   Metadatos \(consulte la referencia de metadatos de contenido\): datos sobre el tema, por ejemplo, el identificador único del tema, valor de palabra clave, el Id. de tabla de contenido del tema primario Id. de nodo, etc..  
  
-   Contenido del cuerpo: compatible con XHTML 1.1 básica de W3C que incluye admite comportamientos del contenido \(área contraíble, fragmento de código, etc. A continuación se muestra una lista completa\).  
  
 Paquete de personalización de marca de Visual Studio admiten controles:  
  
-   Vínculos  
  
-   CodeSnippet  
  
-   CollapsibleArea  
  
-   Miembro heredado  
  
-   LanguageSpecificText  
  
 Cadenas de idioma admitidos \(no entre mayúsculas y minúsculas\):  
  
-   JavaScript  
  
-   CSharp o c\#  
  
-   cplusplus o visualc \+\+ o c \+\+  
  
-   JScript  
  
-   VisualBasic o vb  
  
-   f \# o fsharp o fs  
  
-   otra cadena que representa un nombre de idioma  
  
 **Creación de un tema del Visor de ayuda**  
  
 Crear un nuevo documento XHTML denominado ContosoTopic4.htm y la etiqueta de título \(abajo\).  
  
```html  
<html> <head> <title>Contoso Topic 4</title> </head> <body> </body> </html>  
  
```  
  
 A continuación, agregar datos para definir cómo se presentará \(self marca o no\), el tema de cómo hacer referencia en este tema para F1, donde existe este tema dentro de la tabla de contenido, su identificador \(para la referencia de vínculo por otros temas\), etc..  Consulte la tabla "Metadatos de contenido" a continuación para obtener una lista completa de metadatos admitidos.  
  
-   En este caso, usaremos nuestro propio paquete de personalización de marca, una variante del paquete de personalización de marca en el Visor de Ayuda de Visual Studio.  
  
-   Agregue el nombre de la meta de F1 y valor \(contenido de "Microsoft.Help.F1" \= "ContosoTopic4"\) que coincidirá con el valor de F1 proporcionado en la bolsa de propiedades IDE.  \(Consulte la sección de soporte técnico de F1 para obtener más información\).   Este es el valor que coincide con la tecla F1 llamar desde el IDE para mostrar este tema cuando se elige la tecla F1 en el IDE.  
  
-   Agregue el identificador de tema. Esta es la cadena que se utiliza en otros temas para vincular a este tema.  Es el identificador de Visor de ayuda para este tema.  
  
-   Para la tabla de contenido, agregue el nodo de elemento primario de este tema para definir dónde aparecerá este nodo de tabla de contenido del tema.  
  
-   La tabla de contenido, agregue el orden de los nodos de este tema. Cuando el nodo primario tiene n número de nodos secundarios, defina en el orden de los nodos secundarios ubicación de este tema. Por ejemplo, este tema es el número 4 de 4 temas secundarios.\)  
  
 Sección de metadatos de ejemplo:  
  
```html  
<html> <head> <title>Contoso Topic 4</title> <meta name="SelfBranded" content="false" /> <meta http-equiv="Content-Type" content="text/html; charset=UTF-8" /> <meta name="Microsoft.Help.Id" content="ContosoTopic4" /> <meta name="Microsoft.Help.F1" content=" ContosoTopic4" /> <meta name="Language" content="en-us" /> <meta name="Microsoft.Help.TocParent" content="ContosoTopic0" /> <meta name="Microsoft.Help.TocOrder" content="4" /> </head> <body> </body> </html>  
  
```  
  
 **El cuerpo del tema**  
  
 El cuerpo \(sin incluir el encabezado y pie de página\) del tema contendrá vínculos de página, una sección de la nota, un área contraíble, un fragmento de código y una sección de texto específico del idioma.  Consulte la sección personalización de marca para obtener información acerca de las áreas del tema presentado.  
  
1.  Agregar una etiqueta de título de tema:  `<div class="title">Contoso Topic 4</div>`  
  
2.  Agregue una sección de Nota: `<div class="alert"> add your table tag and text </div>`  
  
3.  Agregar un área contraíble:  `<CollapsibleArea Expanded="1" Title="Collapsible Area Test Heading"> add text  </CollapsibleArea>`  
  
4.  Agregar un fragmento de código:  `<CodeSnippet EnableCopyCode="true" Language="CSharp" ContainsMarkup="false" DisplayLanguage="C#" > a block of code </CodeSnippet>`  
  
5.  Agregar texto específico del lenguaje de código:  `<LanguageSpecificText devLangcs="CS" devLangvb="VB" devLangcpp="C++" devLangnu="F#" />` tenga en cuenta que devLangnu \= permite introducir otros idiomas. Por ejemplo, devLangnu \= "Fortran" mostrará Fortran cuando el fragmento de código DisplayLanguage \= Fortran  
  
6.  Agregar vínculos de página: `<a href="ms-xhelp://?Id=ContosoTopic1">Main Topic</a>`  
  
> [!NOTE]
>  Nota: no admite nuevas "para idioma para mostrar" \(ejemplo, F \#, Cobol, Fortran\) el código en colores en el fragmento de código será monocromo.  
  
 **Tema del Visor de Ayuda de ejemplo** el código muestra cómo definir metadatos, un fragmento de código, un área contraíble y texto específico del idioma.  
  
```  
<?xml version="1.0" encoding="utf-8"?> <html> <head> <title>Contoso Topic 4</title> <meta http-equiv="Content-Type" content="text/html; charset=UTF-8" /> <meta name="Microsoft.Help.Id" content="ContosoTopic4" /> <meta name="Microsoft.Help.F1" content=" ContosoTopic4" /> <meta name="Language" content="en-us" /> <meta name="Microsoft.Help.TocParent" content="ContosoTopic0" /> <meta name="Microsoft.Help.TocOrder" content="4" /> <meta name="SelfBranded" content="false" /> </head> <body> <div class="title">Contoso Topic 4</div> <div id="header"> <table id="bottomTable" cellpadding="0" cellspacing="0"  width="100%"> <tr id="headerTableRow2"><td align="left"> <span id="nsrTitle">Contoso Topic 1</span> </td> <td align="right"> </td></tr> <tr id="headerTableRow1"><td align="left"> <span id="runningHeaderText">Contoso Widgets & Sprockets</span> </td></tr> </table> </div> <h2>Table of Contents</h2> <ul class="toc"> <li class="tocline1"><a href="#introduction" target="_self">1.0 Introduction</a></li> <li class="tocline1"><a href="#seealso" target="_self">2.1 See Also</a></li> </ul> <div class="topic"> <div id="mainSection"> <div id="mainBody"> <a name="introduction"></a> <h2>1.0 Introduction</h2> <p>[This documentation is for sample purposes only.]</p> <p>Contoso Topic 1 contains examples of: <ul> <li>Collapsible Area</li> <li>Bookmark ("See also")</li> <li>Code Snippets from Branding Package</li> </ul> </p> <div class="alert"><table><tr><th> <strong>Note </strong></th></tr> <tr><td> <p>This is an example of a <span class="label">Note </span>section. Call out important items for your reader in this <span class="label">Note </span>box. </p></td></tr> </table> </div> </div> <CollapsibleArea Expanded="1" Title="Collapsible Area Test Heading"> <a id="sectionToggle0"><!----></a> <div> Example of Collapsible Area <br/> Lorem ipsum dolor sit amet... </div> </CollapsibleArea> <div id="snippetGroup" > <CodeSnippet EnableCopyCode="true" Language="VisualBasic" ContainsMarkup="false" DisplayLanguage="Visual Basic" > Private Sub ToolStripRenderer1_RenderGrip(sender as Object, e as ToolStripGripRenderEventArgs) _ Handles ToolStripRenderer1.RenderGrip Dim messageBoxVB as New System.Text.StringBuilder() messageBoxVB.AppendFormat("{0} = {1}", "GripBounds", e.GripBounds) messageBoxVB.AppendLine() ... MessageBox.Show(messageBoxVB.ToString(),"RenderGrip Event") End Sub </CodeSnippet> <CodeSnippet EnableCopyCode="true" Language="CSharp" ContainsMarkup="false" DisplayLanguage="C#" > private void ToolStripRenderer1_RenderGrip(Object sender, ToolStripGripRenderEventArgs e) { System.Text.StringBuilder messageBoxCS = new System.Text.StringBuilder(); messageBoxCS.AppendFormat("{0} = {1}", "GripBounds", e.GripBounds ); messageBoxCS.AppendLine(); ... MessageBox.Show(messageBoxCS.ToString(), "RenderGrip Event" ); } </CodeSnippet> <CodeSnippet EnableCopyCode="true" Language="fsharp" ContainsMarkup="false" DisplayLanguage="F#" > some F# code </CodeSnippet> </div> <h4 class="subHeading">Example of code specific text</h4>Language = <LanguageSpecificText devLangcs="CS" devLangvb="VB" devLangcpp="C++" devLangnu="F#" /> <a name="seealso"></a> <h1 class="heading">See Also</h1> <div id="seeAlsoSection" class="section"> <div class="seeAlsoStyle"> <a href="ms-xhelp://?Id=ContosoTopic1">Main Topic</a> </div> </div> </div> </div> </body> </html>  
  
```  
  
 **Compatibilidad con F1**  
  
 En Visual Studio, seleccione F1 genera valores suministrados desde la posición del cursor en el IDE y rellena una "bolsa de propiedades" con los valores proporcionados \(basada en la ubicación del cursor. Cuando el cursor está sobre la característica x, característica x está activo o en el foco y rellena la bolsa de propiedades con valores.  Cuando se selecciona F1 se rellena la bolsa de propiedades y el código de F1 de Visual Studio, se comprueba si el origen de la Ayuda de los clientes predeterminado es local o en línea \(online es el valor predeterminado\), a continuación, crea la cadena adecuada según la configuración de usuarios \(en línea es el valor predeterminado\): ejecutar el shell \(consulte la Guía del administrador ayuda para exe los parámetros de inicio\) con parámetros para el Visor de Ayuda local \+ palabras clave de la bolsa de propiedades si ayuda local es el valor predeterminado , o la dirección URL de MSDN con la palabra clave en la lista de parámetros.  
  
 Si se devuelven tres cadenas F1, conoce para como una cadena de varios valores, realizar el primer término, busque para un acierto, y si se encuentra, terminemos; Si no es así, mueva a la cadena siguiente.  Orden es importante. Presentación de las palabras clave de varios valores debe ser una cadena más larga en la cadena más corta.  Para comprobar esto en el caso de las palabras clave de varios valores, mire la cadena URL F1 en línea, que incluye la palabra clave seleccionada.  
  
 En Visual Studio 2012, hemos hecho intencionadamente una división más fuerte entre en línea y sin conexión, por lo que si la configuración del usuario ha en línea, a continuación, simplemente pasamos la solicitud de F1 directamente a nuestro servicio de consulta en línea en MSDN, en lugar de enrutamiento mediante el agente de bibliotecas de ayuda que teníamos en Visual Studio 2010. A continuación, confiamos en un estado de "contenido de proveedor instalado \= true" para determinar si se debe hacer algo diferente en ese contexto. Si es true, a continuación, realizamos esta lógica de análisis y enrutamiento según lo que desee para sus clientes. Si es false, a continuación, sólo vamos a MSDN. Si la configuración del usuario es Local, todas las llamadas vaya simplemente al motor de Ayuda local.  
  
 F1 diagrama de flujo:  
  
 ![F1 flow](../../extensibility/internals/media/f1flow.png "F1flow")  
  
 Cuando el origen de contenido de Ayuda de Visor de Ayuda predeterminado se establece en lanzamiento en línea \(en el explorador\):  
  
-   Características de Visual Studio asociado \(VSP\) emiten un valor a la bolsa de propiedades F1 \(prefix.keyword de contenedor de propiedad y la dirección URL en línea para el prefijo que se encuentra en el registro\): F1 envía una dirección URL de VSP \+ parámetros al explorador.  
  
-   Las características de Visual Studio \(editor de idiomas, elementos de menú de Visual Studio, etc.\): F1 envía una URL de Visual Studio en el explorador.  
  
 Cuando el origen de contenido de Ayuda de Visor de Ayuda predeterminado se establece en la Ayuda local \(inicio en Visor de Ayuda\):  
  
-   Características VSP donde coinciden palabra clave entre la bolsa de propiedades de F1 y el índice de almacén local \(es decir, el prefix.keyword de contenedor de propiedad \= el valor que se encuentra en el índice de almacén local\): F1 representa el tema en el Visor de ayuda.  
  
-   Características de Visual Studio \(ninguna opción de VSP invalidar la bolsa de propiedades que se emiten desde características de Visual Studio\): F1 representa un tema en el Visor de Ayuda de Visual Studio.  
  
 Establezca los siguientes valores del registro para habilitar la reserva de F1 para el contenido de Ayuda del proveedor. Reserva de F1 significa que el Visor de ayuda se establece en línea para buscar contenido de Ayuda de F1, y el contenido del proveedor se instala localmente en el disco duro. El Visor de ayuda debe mirar la Ayuda local para el contenido, aunque el valor predeterminado es de ayuda en pantalla.  
  
1.  Establecer el **VendorContent** valor en la clave del registro ayuda 2.1:  
  
    -   Para los sistemas operativos de 32 bits:  
  
         HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\Help\\v2.1\\Catalogs\\VisualStudio12  
  
         "VendorContent" \= dword: 00000001  
  
    -   Para los sistemas operativos de 64 bits:  
  
         HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Wow6432Node\\Microsoft\\Help\\v2.1\\Catalogs\\VisualStudio12  
  
         "VendorContent" \= dword: 00000001  
  
2.  Registrar el espacio de nombres asociado en la clave del registro ayuda 2.1:  
  
    -   Para los sistemas operativos de 32 bits:  
  
         HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\Help\\v2.1\\Partner*\\ \< namespace \>*  
  
         "ubicación"\="sin conexión"  
  
    -   Para los sistemas operativos de 64 bits:  
  
         HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Wow6432Node\\Microsoft\\Help\\v2.1\\Partner*\\ \< namespace \>*  
  
         "ubicación"\="sin conexión"  
  
 **Espacio de nombres base nativa de análisis**  
  
 Para activar el análisis de espacio de nombres base nativa, en el registro de agregar un nuevo valor DWORD con el nombre de: BaseNativeNamespaces y establezca su valor en 1 \(bajo la clave de catálogo que desea admitir\).  Por ejemplo, si desea usar el catálogo de Visual Studio, puede agregar la clave a la ruta de acceso:  
  
 HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Wow6432Node\\Microsoft\\Help\\v2.1\\Catalogs\\VisualStudio12  
  
 Cuando una palabra clave de F1 en el formato que se encuentra el encabezado o el método, el carácter '\/' se analizará, lo que resulta en la construcción siguiente:  
  
-   ENCABEZADO: será el espacio de nombres que puede usar para registrar en el registro  
  
-   MÉTODO: Esto se convertirá en la palabra clave que se pasa a través de.  
  
 Por ejemplo, dada una biblioteca personalizada denominada CustomLibrary y un método denominado MyTestMethod, cuando una solicitud entra de F1 se formatearán como `CustomLibrary/MyTestMethod`.  
  
 Un usuario puede registrar CustomLibrary como el espacio de nombres bajo el subárbol de socios y proporcionar cualquier clave de la ubicación que deseen, y la palabra clave que se pasan a la consulta será MyTestMethod.  
  
 **Habilitar la depuración de la herramienta en el IDE de la Ayuda**  
  
 Agregue la siguiente clave del registro y valor:  
  
 Tecla de ayuda HKEY\_CURRENT\_USER\\Software\\Microsoft\\VisualStudio\\12.0\\Dynamic: mostrar los resultados de depuración en el valor de venta: Sí  
  
 En el IDE, bajo el elemento de menú Ayuda, seleccione "Depurar el contexto de ayuda"  
  
 **Metadatos de contenido**  
  
 En la siguiente tabla, cualquier cadena que aparece entre corchetes es un marcador de posición que se debe reemplazar por un valor reconocido. Por ejemplo, en \< meta name\="Microsoft.Help.Locale" contenido \= "\[código de idioma\]" \/ \>, "\[código de idioma\]" debe sustituirse por un valor como "en\-us".  
  
|Propiedad \(representación HTML\)|Descripción|  
|---------------------------------------|-----------------|  
|\< meta name\="Microsoft.Help.Locale" contenido \= "\[\-Cód.\]" \/ \>|Establece una configuración regional de este tema. Si esta etiqueta se utiliza en un tema, debe utilizarse una sola vez y debe insertarse por encima de otras etiquetas de Microsoft Help. Si no se usa esta etiqueta, el texto del cuerpo del tema se indiza utilizando el separador de palabras está asociado a la configuración regional del producto, si se especifica; de lo contrario, la en\-us utiliza el separador de palabras. Esta etiqueta se ajusta al ISOC RFC 4646. Para asegurarse de que Microsoft Help funciona correctamente, utilice esta propiedad en lugar del atributo de lenguaje general.|  
|\< meta name\="Microsoft.Help.TopicLocale" contenido \= "\[\-Cód.\]" \/ \>|Establece una configuración regional de este tema cuando también se usan otras configuraciones regionales. Si esta etiqueta se utiliza en un tema, debe utilizarse una sola vez. Utilice esta etiqueta cuando el catálogo contiene contenido en varios idiomas. Varios temas en un catálogo pueden tener el mismo identificador, pero cada uno debe especificar un TopicLocale único. El tema que especifica un TopicLocale que coincida con la configuración regional del catálogo es el tema que se muestra en la tabla de contenido. Sin embargo, todas las versiones de idioma del tema se muestran en los resultados de búsqueda.|  
|\< title \> \[Title\] \< \/title \>|Especifica el título de este tema. Esta etiqueta es necesaria y debe usarse sólo una vez en un tema. Si el cuerpo del tema no contiene una sección de título \< div \>, este título se muestra en el tema y en la tabla de contenido.|  
|\< nombre de metadatos \= "Microsoft.Help.Keywords" contenido \= "\[aKeywordPhrase\]" \/ \>|Especifica el texto de un vínculo que se muestra en el panel del índice del Visor de ayuda. Cuando se hace clic en el vínculo, se muestra el tema. Puede especificar varias palabras clave de índice para un tema, o si no desea que los vínculos a este tema para que aparezca en el índice, puede omitir esta etiqueta. Palabras clave "K" desde versiones anteriores de ayuda se puede convertir a esta propiedad.|  
|\< meta name\="Microsoft.Help.Id" contenido \= "\[TopicID\]" \/ \>|Establece el identificador de este tema. Esta etiqueta es necesaria y debe usarse sólo una vez en un tema. El identificador debe ser único entre los temas en el catálogo que tienen la misma configuración regional. En otro tema, puede crear un vínculo a este tema utilizando este Id.|  
|\< meta name\="Microsoft.Help.F1" content\="\[System.Windows.Controls.Primitives.IRecyclingItemContainerGenerator\]"\/ \>|Especifica la palabra clave F1 para este tema. Puede especificar varias palabras clave F1 para un tema, o si no desea que este tema se mostrará al usuario de una aplicación presiona F1, puede omitir esta etiqueta. Normalmente, se especifica una sola tecla F1 para un tema. Palabras clave de "F" de las versiones anteriores de la Ayuda se puede convertir a esta propiedad.|  
|\< nombre de metadatos \= "Descripción" content \= "\[descripción de tema\]" \/ \>|Proporciona un breve resumen del contenido de este tema. Si esta etiqueta se utiliza en un tema, debe utilizarse una sola vez. Se tiene acceso a esta propiedad directamente en la biblioteca de consulta; no se almacena en el archivo de índice.|  
|\< meta name\="Microsoft.Help.TocParent" contenido \= "\[parent\_Id\]" \/ \>|Especifica el tema principal de este tema en la tabla de contenido. Esta etiqueta es necesaria y debe usarse sólo una vez en un tema. El valor es el Microsoft.Help.Id del elemento primario. Un tema puede tener una sola ubicación en la tabla de contenido. "\-1" se considera el identificador de tema de la raíz de la TDC. En [!INCLUDE[vs_dev12](../../data-tools/includes/vs_dev12_md.md)], que la página es la página inicial del Visor de ayuda. Se trata de la misma razón que agregamos específicamente TocParent \=\-1 a algunos temas para asegurarse de que aparecen en la parte superior nivel. La página principal de Visor de ayuda es un sistema y por lo tanto no reemplazables. Si un VSP intenta agregar una página con un Id. de \-1, puede obtener agregado al conjunto de contenido, pero el Visor de ayuda siempre utilizará la página del sistema: página principal del Visor de ayuda|  
|\< meta name\="Microsoft.Help.TocOrder" contenido \= "\[entero\]" \/ \>|Especifica dónde en la tabla de contenido en este tema aparece en relación con los temas del mismo nivel. Esta etiqueta es necesaria y debe usarse sólo una vez en un tema. El valor es un entero. Un tema que especifica un entero menor valor aparece por encima de un tema que especifica un entero de valor superior.|  
|\< meta name\="Microsoft.Help.Product" contenido \= "\[product code\]" \/ \>|Especifica el producto que se describen en este tema. Si esta etiqueta se utiliza en un tema, debe utilizarse una sola vez. Esta información también se puede proporcionar como un parámetro que se pasa al indizador de ayuda.|  
|\< meta name\="Microsoft.Help.ProductVersion" contenido \= "\[version number\]" \/ \>|Especifica la versión del producto que se describen en este tema. Si esta etiqueta se utiliza en un tema, debe utilizarse una sola vez. Esta información también se puede proporcionar como un parámetro que se pasa al indizador de ayuda.|  
|\< meta name\="Microsoft.Help.Category" contenido \= "\[string\]" \/ \>|Utiliza los productos para identificar subsecciones de contenido. Puede identificar varias subsecciones para un tema, o si no desea que los vínculos para identificar cualquier subsecciones, puede omitir esta etiqueta. Esta etiqueta se utiliza para almacenar los atributos de TargetOS y TargetFrameworkMoniker cuando se convierte un tema de una versión anterior de la Ayuda. El formato del contenido es AttributeName:AttributeValue.|  
|\< contenido de meta name\="Microsoft.Help.TopicVersion \="\[número de versión de tema\]"\/ \>|Especifica esta versión del tema cuando existen varias versiones de un catálogo. Porque Microsoft.Help.Id no está garantizado que es único, esta etiqueta se requiere cuando más de una versión de un tema existe en un catálogo, por ejemplo, cuando un catálogo contiene un tema para .NET Framework 3.5 y un tema para .NET Framework 4 y ambos tienen el mismo Microsoft.Help.Id.|  
|\< nombre de metadatos \= "SelfBranded" content \= "\[TRUE o FALSE\]" \/ \>|Especifica si este tema usa el paquete de personalización de marca de inicio de administrador de bibliotecas de ayuda o un paquete de personalización de marca específica para el tema. Esta etiqueta debe ser TRUE o FALSE. Si es TRUE, el paquete de personalización de marca para el tema asociado reemplaza el paquete de personalización de marca se establece cuando se inicia el Administrador de bibliotecas de ayuda para que se represente el tema correctamente incluso si difiere de la representación de otro contenido. Si es FALSE, el tema actual se representa según el paquete de personalización de marca se establece cuando se inicia el Administrador de bibliotecas de ayuda. De forma predeterminada, Administrador de bibliotecas de ayuda supone automática marca sea false a menos que se declara la variable SelfBranded como TRUE; por lo tanto, no es necesario declarar \< nombre meta \= "SelfBranded" content \= "FALSE" \/ \>.|  
  
### Creación de un paquete de personalización de marca  
 La versión de Visual Studio incluye a una serie de diferentes productos de Visual Studio, incluidas las aislado y shells integrados para Partners de Visual Studio.  Cada uno de estos productos requiere cierto grado de personalización de marca única para el producto, soporte contenido de Ayuda basada en temas.  Por ejemplo, temas de Visual Studio necesitan tener una presentación marca coherente, mientras que SQL Studio, que se ajusta a ISO Shell, requiere su propio único ayuda contenido personalización de marca para cada tema.  Un socio de Shell integrado puede sus temas de ayuda que dentro del elemento primario contenido de Ayuda del producto de Visual Studio mientras se mantiene su propia información de marca de tema.  
  
 Personalización de marca los paquetes se instalan por el producto que contiene el Visor de ayuda.  Para los productos de Visual Studio:  
  
-   Un paquete de personalización de marca de reserva \(Branding\_ \< configuración regional \> MSHC\) se instala en la raíz de la aplicación 2.1 del Visor de ayuda \(ejemplo: C:\\Program Files \(x 86\) \\Microsoft Help Viewer\\v2.1\) por el paquete de idioma del Visor de ayuda.  Se utiliza para los casos donde no está instalado el producto cualquier paquete de personalización de marca \(no se ha instalado contenido\) o daños en el paquete de personalización de marca de instalado.  Tenga en cuenta que los elementos de Visual Studio \(logotipo y comentarios\) se omiten cuando se utiliza el paquete de personalización de marca de reserva de aplicación raíz.  
  
-   Cuando se instala el contenido de Visual Studio desde el servicio de contenido del paquete, también se instala un paquete de personalización de marca \(para el primer escenario de instalación del contenido de tiempo\).  Si hay una actualización para el paquete de personalización de marca, la actualización se instala cuando se produzca la siguiente actualización del contenido o la acción de instalación del paquete adicional.  
  
 El Visor de Ayuda de Microsoft admite la personalización de los temas basados en los metadatos del tema.  
  
-   Donde los metadatos de tema definen self marca \= true, representar el tema tal cual, no hacer nada \(en cuanto a la información de marca\).  
  
-   Donde los metadatos de tema definen self marca \= false, usar el paquete de personalización de marca asociado con el valor de metadatos de TopicVendor.  
  
-   Contenido en los metadatos de tema definen name\="Microsoft.Help.TopicVendor" \= \< marca nombre del paquete en el proveedor MSHA \>, utilice el paquete de personalización de marca definido en el valor de contenido.  
  
-   Tenga en cuenta que en el catálogo de Visual Studio, hay una aplicación de prioridad de paquetes de personalización de marca.  Se aplica la marca predeterminada del primer Visual Studio y, a continuación, si definido en los metadatos de tema y compatible con la personalización de marca asociado del paquete \(como se define en la instalación msha\), el proveedor define información de personalización se aplica como una invalidación.  
  
 Normalmente, los elementos de personalización de marca se dividen en tres categorías principales:  
  
-   Elementos de encabezado \(algunos ejemplos son el vínculo de comentarios, texto de renuncia condicional, logotipo\)  
  
-   Contenido comportamientos \(algunos ejemplos son elementos de texto del control de expandir y contraer y elementos de fragmento de código\)  
  
-   Elementos del pie de página \(por ejemplo Copyright\)  
  
 Elementos que se consideran como incluyen elementos con marca \(que se detallan en esta especificación\):  
  
-   Logotipo de producto del catálogo \(por ejemplo, Visual Studio\)  
  
-   Elementos de correo electrónico y el vínculo de comentarios  
  
-   Texto de renuncia  
  
-   Texto de copyright  
  
 Los archivos auxiliares en el paquete de personalización de marca del Visor de Ayuda de Visual Studio se incluyen:  
  
-   Gráficos \(logotipos, iconos, etc.\).  
  
-   Branding.js – auxiliares comportamientos del contenido de los archivos de script  
  
-   Branding.XML: las cadenas que se usa de manera coherente a través de contenido del catálogo.  Nota: para elementos de texto de localización de Visual Studio en el branding.xml incluyen \_locID \= "\< valor único \>"  
  
-   Branding.CSS: las definiciones de estilo para la coherencia de la presentación  
  
-   Printing.CSS: definiciones de estilos de presentación impresa coherente  
  
 Como se mencionó anteriormente, marca paquetes están asociados con el tema:  
  
-   Cuando SelfBranded \= false se define en los metadatos, el tema hereda el catálogo de paquete de personalización de marca  
  
-   O cuando SelfBranded \= false y existe un paquete de personalización de marca única definido en el MSHA y disponible cuando se instala el contenido  
  
 Para VSPs implementar paquetes de personalización de marca personalizados \(contenido VSP, SelfBranded \= True\), una manera de continuar es comenzar con el paquete de personalización de marca de reserva \(instalado con el Visor de Ayuda\), y cambiar el nombre del archivo según corresponda.  El archivo de MSHC Branding\_ \< configuración regional \> es un archivo zip con la extensión de archivo cambiado a MSHC, sólo tendrá que cambiar la extensión de MSHC a .zip y extraiga el contenido.  Consulte a continuación los elementos del paquete de personalización de marca y modificar según sea necesario \(por ejemplo, cambiar el logotipo, el logotipo VSP y la referencia para el logotipo en el archivo Branding.xml, actualizar Branding.xml por particularidades VSP, etc.\).  
  
 Cuando se realizan todas las modificaciones, cree un archivo zip que contiene los elementos de personalización de marca que desee y cambie la extensión a MSHC.  
  
 Para asociar el paquete de personalización de marca personalizado, cree el MSHA que contiene la referencia al archivo mshc marca junto con el contenido mshc \(que contiene los temas\).  Vea a continuación "MSHA" para saber cómo crear un MSHA básica.  
  
 El archivo Branding.xml contiene un elementos de lista que se usa para representar constantemente los elementos específicos de un tema cuando el tema contiene \< meta name\="Microsoft.Help.SelfBranded" contenido \= "false" \/ \>.  A continuación aparece la lista de elementos en el archivo Branding.xml de Visual Studio.  Tenga en cuenta que esta lista está pensada para utilizarse como plantilla para usuarios pioneros de ISO Shell, que modifican estos elementos \(por ejemplo, logotipo, comentarios y Copyright\) para satisfacer su propias necesidades de personalización de marca de producto.  
  
 Nota: las variables que se indica en "{n}" tienen las dependencias del código, quitar o cambiar estos valores provocará errores y, posiblemente, el bloqueo de aplicación. Identificadores de localización \(ejemplo \_locID\="codesnippet.n"\) se incluyen en el paquete de personalización de marca de Visual Studio.  
  
 **Branding.Xml**  
  
|||  
|-|-|  
|Característica:|**CollapsibleArea**|  
|Uso:|Expandir el texto del control de contenido se contrae|  
|**Elemento**|**Valor**|  
|ExpandText|Expandir|  
|CollapseText|Contraer|  
|Característica:|**CodeSnippet**|  
|Uso:|Texto del control de fragmento de código.  Nota: El contenido de fragmento de código con espacio "Indivisible" se cambiará a espacio.|  
|**Elemento**|**Valor**|  
|CopyToClipboard|Copiar en el Portapapeles|  
|ViewColorizedText|Ver texto coloreado|  
|CombinedVBTabDisplayLanguage|Visual Basic \(ejemplo\)|  
|VBDeclaration|Declaración|  
|VBUsage|Uso|  
|Característica:|**Comentarios, el pie de página y el logotipo de**|  
|Uso:|Proporciona un control de comentarios de cliente proporcionar comentarios sobre el tema actual a través de correo electrónico.  Texto de copyright para el contenido.  Definición del logotipo.|  
|**Elemento**|**Valor \(estas cadenas pueden modificarse para satisfacer la necesidad de adopción de contenido\).**|  
|CopyRight|© 2013 Microsoft Corporation. All rights reserved.|  
|SendFeedback|\< una href \= "{0}" \\{1\\} \> Enviar comentarios \< \/a \> en este tema a Microsoft.|  
|FeedbackLink||  
|LogoTitle|[!INCLUDE[vs_dev12](../../data-tools/includes/vs_dev12_md.md)]|  
|LogoFileName|vs\_logo\_bk.gif|  
|LogoFileNameHC|vs\_logo\_wh.gif|  
|Característica:|**Declinación de responsabilidades**|  
|Uso:|Un conjunto de casos renuncias de responsabilidad específicas de máquina contenido traducido.|  
|**Elemento**|**Valor**|  
|MT\_Editable|Este artículo es una traducción automática. Si tiene una conexión a Internet, seleccione "Ver este tema en línea" para ver esta página en modo editable con el contenido original en inglés al mismo tiempo.|  
|MT\_NonEditable|Este artículo es una traducción automática. Si tiene una conexión a Internet, seleccione "Ver este tema en línea" para ver esta página en modo editable con el contenido original en inglés al mismo tiempo.|  
|MT\_QualityEditable|En este artículo se tradujo manualmente. Si tiene una conexión a Internet, seleccione "Ver este tema en línea" para ver esta página en modo editable con el contenido original en inglés al mismo tiempo.|  
|MT\_QualityNonEditable|En este artículo se tradujo manualmente. Si tiene una conexión a Internet, seleccione "Ver este tema en línea" para ver esta página en modo editable con el contenido original en inglés al mismo tiempo.|  
|MT\_BetaContents|Este artículo fue traducidos para una versión preliminar. Si tiene una conexión a Internet, seleccione "Ver este tema en línea" para ver esta página en modo editable con el contenido original en inglés al mismo tiempo.|  
|MT\_BetaRecycledContents|En este artículo se tradujo manualmente para una versión preliminar. Si tiene una conexión a Internet, seleccione "Ver este tema en línea" para ver esta página en modo editable con el contenido original en inglés al mismo tiempo.|  
|Característica:|**Vinculación**|  
|Uso:|Compatibilidad con vínculos a temas en línea|  
|**Elemento**|**Valor**|  
|LinkTableTitle|Tabla de vínculos|  
|TopicEnuLinkText|Ver la versión en inglés \< \/a \> de este tema que está disponible en el equipo.|  
|TopicOnlineLinkText|Ver este tema \< una href \= "{0}" \\{1\\} \> en línea \< \/a \>|  
|OnlineText|En línea|  
|Característica:|**Control de Audio de vídeo**|  
|Uso:|Mostrar elementos y texto para el contenido de vídeo|  
|**Elemento**|**Valor**|  
|MultiMediaNotSupported|Internet Explorer 9 o posterior debe instalarse para admitir contenido de {0}.|  
|VideoText|Mostrar vídeo|  
|AudioText|transmisión de audio|  
|OnlineVideoLinkText|\< p \> para ver el vídeo de este tema, haga clic en {0} \< una href \= "\\\\ {1\\\\}" \> \\{2\\}here \< \/a \>. \< \/p \>|  
|OnlineAudioLinkText|\< p \> para escuchar el audio asociado a este tema, haga clic en {0} \< una href \= "\\\\ {1\\\\}" \> \\{2\\}here \< \/a \>. \< \/p \>|  
|Característica:|**Control de contenido no instalado**|  
|Uso:|Elementos de texto \(cadenas\) que se utiliza para la representación de contentnotinstalled.htm|  
|**Elemento**|**Valor**|  
|ContentNotInstalledTitle|No se encontró ningún contenido en el equipo.|  
|ContentNotInstalledDownloadContentText|\< p \> para descargar contenido en el equipo \< una href \= "{0}" \\{1\\} \> haga clic en la pestaña administrar \< \/a \>. \< \/p \>|  
|ContentNotInstalledText|\< p \> no hay contenido está instalado en el equipo. Consulte al administrador local ayuda contenido instalación. \< \/p \>|  
|Característica:|**Control de tema no encontrado**|  
|Uso:|Elementos de texto \(cadenas\) que se utiliza para la representación de topicnotfound.htm|  
|**Elemento**|**Valor**|  
|TopicNotFoundTitle|No se encuentra el tema solicitado en el equipo.|  
|TopicNotFoundViewOnlineText|\< p \> el tema solicitado no se encontró en el equipo, pero se puede \< una href \= "{0}" \\{1\\} \> ver el tema en línea \< \/a \>. \< \/p \>|  
|TopicNotFoundDownloadContentText|\< p \> consulte el panel de navegación para ver vínculos a temas similares, o \< una href \= "{0}" \\{1\\} \> haga clic en la pestaña administrar \< \/a \> para descargar contenido en el equipo. \< \/p \>|  
|TopicNotFoundText|\< p \> el tema solicitado no se encontró en el equipo. \< \/p \>|  
|Característica:|**Tema dañado Control**|  
|Uso:|Elementos de texto \(cadenas\) que se utiliza para la representación de topiccorrupted.htm|  
|**Elemento**|**Valor**|  
|TopicCorruptedTitle|No se puede mostrar el tema solicitado.|  
|TopicCorruptedViewOnlineText|\< p \> Visor de ayuda no pudo mostrar el tema solicitado. Puede haber un error en el contenido del tema o una dependencia de sistema subyacente. \< \/p \>|  
|Característica:|**Control de la página principal**|  
|Uso:|Texto de admitir la visualización del contenido de nodo de nivel superior del Visor de ayuda.|  
|**Elemento**|**Valor**|  
|HomePageTitle|Página principal del Visor de ayuda|  
|HomePageIntroduction|\< p \> Este es el Visor de Ayuda de Microsoft, una fuente esencial de la información de todos los que usan herramientas, productos, tecnologías y servicios de Microsoft. El Visor de Ayuda proporciona acceso a procedimientos e información de referencia, código de ejemplo, artículos técnicos y mucho más. Para encontrar el contenido que necesita, busque la tabla de contenido, utilice la búsqueda de texto completo o desplazarse por contenido utilizando el índice de palabra clave. \< \/p \>|  
|HomePageContentInstallText|\< p \>\< br \/ \> Utilice el \< una href \= "{0}" \\{1\\} \> pestaña administrar contenido \< \/a \> para hacer lo siguiente: \< ul \>\< li \> Agregar contenido a su equipo. \< \/li \>\< li \> Compruebe las actualizaciones para el contenido local. \< \/li \>\< li \> quitar contenido del equipo. \< \/li \>\< \/ul \>\< \/p \>|  
|HomePageInstalledBooks|Libros instalados|  
|HomePageNoBooksInstalled|No se encontró ningún contenido en el equipo.|  
|HomePageHelpSettings|Configuración de contenido de ayuda|  
|HomePageHelpSettingsText|\< p \> su configuración actual es la Ayuda local. El Visor de Ayuda muestra el contenido que ha instalado en el equipo. \< br \/ \> para cambiar el origen de contenido de ayuda, en la barra de menús de Visual Studio, elija \< span style \= "{0}" \> Ayuda establecer preferencias de la Ayuda \< \/span \>. \< br \/ \>\< \/p \>|  
|Megabytes|MB|  
  
 **Branding.js**  
  
 El archivo branding.js contiene JavaScript utilizado por los elementos de personalización de marca del Visor de Ayuda de Visual Studio.  A continuación se muestra una lista de los elementos de personalización de marca y la función auxiliar de JavaScript.  Todas las cadenas para que se adapten de este archivo se definen en la sección "Cadenas localizables" en la parte superior de este archivo.  Tenga en cuenta que se ha creado el archivo ICL loc cadenas dentro del archivo branding.js.  
  
||||  
|-|-|-|  
|**Característica de personalización de marca**|**Función de JavaScript**|**Descripción**|  
|Var...||Definir variables|  
|Obtiene el lenguaje de código de usuario|setUserPreferenceLang|asigna un índice \# para el lenguaje de código|  
|Establecer y obtener valores de cookies|getCookie, setCookie||  
|Miembro heredado|changeMembersLabel|Expandir o contraer miembro heredado|  
|Cuando SelfBranded \= False|onLoad|Leer la cadena de consulta para comprobar si una solicitud de impresión.  Establecer todos los codesnippets centrarse en la pestaña preferido del usuario.  Si es una impresión solicitud isPrinterFriendly establecida en true. Compruebe si el modo de contraste alto.|  
|Fragmento de código|addSpecificTextLanguageTagSet||  
||getIndexFromDevLang||  
||Ficha cambiar se||  
||setCodesnippetLang||  
||setCurrentLang||  
||CopyToClipboard||  
|CollapsibleArea|addToCollapsibleControlSet|escribir el objeto de control contraíble en la lista.|  
||CA\_Click|en función del estado del área contraíble, define qué imagen y texto para presentar|  
|Compatibilidad de contraste de logotipo|isBlackBackground\(\)|Se llama para determinar si el fondo es negro.  Sólo precisa cuando en modo de contraste alto.|  
||isHighContrast\(\)|utilizar un intervalo de color para detectar el modo de contraste alto|  
||onHighContrast\(black\)|Se llama cuando se detecta el contraste alto|  
|Funcionalidad LST|||  
||addToLanSpecTextIdSet\(id\)||  
||updateLST\(currentLang\)||  
||getDevLangFromCodeSnippet\(lang\)||  
|Funcionalidad multiMedia|título \(comenzar, final, texto, estilo\)||  
||findAllMediaControls\(normalizedId\)||  
||getActivePlayer\(normalizedId\)||  
||captionsOnOff\(id\)||  
||toSeconds\(t\)||  
||getAllComments\(node\)||  
||styleRectify \(nombre de estilo, styleValue\)||  
||showCC\(id\)||  
||Subtitle\(ID\)||  
  
 **ARCHIVOS HTM**  
  
 El paquete de personalización de marca contiene un conjunto de archivos HTM que admiten escenarios para comunicar información de clave a los usuarios de contenido de ayuda, por ejemplo una página principal que contiene una sección que describe qué conjuntos de contenido están instalados y páginas que indica al usuario cuando no se puede encontrar temas en el conjunto de temas local. Tenga en cuenta que se pueden modificar estos archivos HTM por producto.  Proveedores de ISO Shell son capaces de tomar el paquete de personalización de marca predeterminada y cambiar el comportamiento y el contenido de estas páginas al conjunto de sus necesidades.  Estos archivos, consulte su paquete de personalización de marca correspondiente para las etiquetas de personalización de marca obtener el contenido correspondiente del archivo branding.xml.  
  
||||  
|-|-|-|  
|**Archivo**|**Uso**|**Muestra el origen de contenido**|  
|homepage.htm|Se trata de una página que muestra el contenido instalado actualmente y cualquier otro mensaje adecuado para presentar al usuario acerca de su contenido.  Este archivo tiene el contenido de "Microsoft.Help.Id" del atributo de datos de metadatos adicional \= "\-1" que coloca este contenido en la parte superior de la tabla de contenido local.||  
||\< META\_HOME\_PAGE\_TITLE\_ADD \/ \>|Branding.XML, la etiqueta \< HomePageTitle \>|  
||\< HOME\_PAGE\_INTRODUCTION\_SECTION\_ADD \/ \>|Branding.XML, la etiqueta \< HomePageIntroduction \>|  
||\< HOME\_PAGE\_CONTENT\_INSTALL\_SECTION\_ADD \/ \>|Branding.XML, la etiqueta \< HomePageContentInstallText \>|  
||\< HOME\_PAGE\_BOOKS\_INSTALLED\_SECTION\_ADD \/ \>|Encabezado de sección Branding.xml etiqueta \< HomePageInstalledBooks \>, los datos generados a partir de la aplicación, \< HomePageNoBooksInstalled \> cuando no hay ningún libro está instalado.|  
||\< HOME\_PAGE\_SETTINGS\_SECTION\_ADD \/ \>|Encabezado de sección Branding.xml etiqueta \< HomePageHelpSettings \> texto de la sección \< HomePageHelpSettingsText \>.|  
|topiccorrupted.htm|Cuando existe un tema en el conjunto local, pero por alguna razón no se puede mostrar \(dañado el contenido\).||  
||\< META\_TOPIC\_CORRUPTED\_TITLE\_ADD \/ \>|Branding.XML, la etiqueta \< TopicCorruptedTitle \>|  
||\< TOPIC\_CORRUPTED\_SECTION\_ADD \/ \>|Branding.XML, la etiqueta \< TopicCorruptedViewOnlineText \>|  
|topicnotfound.htm|Cuando un tema no se encuentra en el contenido local establecido ni disponible en línea||  
||\< META\_TOPIC\_NOT\_FOUND\_TITLE\_ADD \/ \>|Branding.XML, la etiqueta \< TopicNotFoundTitle \>|  
||\< META\_TOPIC\_NOT\_FOUND\_ID\_ADD \/ \>|Branding.XML, la etiqueta \< TopicNotFoundViewOnlineText \> \+ \< TopicNotFoundDownloadContentText \>|  
||\< TOPIC\_NOT\_FOUND\_SECTION\_ADD \/ \>|Branding.XML, la etiqueta \< TopicNotFoundText \>|  
|contentnotinstalled.htm|Cuando no hay contenido local instalado para el producto.||  
||\< META\_CONTENT\_NOT\_INSTALLED\_TITLE\_ADD \/ \>|Branding.XML, la etiqueta \< ContentNotInstalledTitle \>|  
||\< META\_CONTENT\_NOT\_INSTALLED\_ID\_ADD \/ \>|Branding.XML, la etiqueta \< ContentNotInstalledDownloadContentText \>|  
||\< CONTENT\_NOT\_INSTALLED\_SECTION\_ADD \/ \>|Branding.XML, la etiqueta \< ContentNotInstalledText \>|  
  
 **Archivos CSS**  
  
 La Ayuda de Visor de personalización de marca paquete de Visual Studio contiene dos archivos de css para admitir la presentación de contenido coherente ayuda de Visual Studio:  
  
-   Branding.CSS: contiene los elementos de css para representar where SelfBranded \= false  
  
-   Printer.CSS: contiene los elementos de css para representar where SelfBranded \= false  
  
 Archivos de branding.CSS incluye definiciones para la presentación de Visual Studio tema \(salvedad es que puede cambiar la branding.css contenida en el MSHC Branding\_ \< configuración regional \> desde el servicio de paquete\).  
  
 **Archivos de gráficos**  
  
 Contenido de Visual Studio muestra un logotipo de Visual Studio, así como otros gráficos.  A continuación, se muestra la lista completa de archivos de gráficos en el paquete de personalización de marca del Visor de Ayuda de Visual Studio.  
  
||||  
|-|-|-|  
|**Archivo**|**Uso**|**Ejemplos**|  
|Clear.gif|Utilizado para representar el área contraíble||  
|footer\_slice.gif|Presentación de pie de página||  
|info\_icon.gif|Utilizado para mostrar información|Declinación de responsabilidades|  
|online\_icon.gif|Este icono es asociarse con vínculos en línea||  
|tabLeftBD.gif|Utilizado para representar el contenedor del fragmento de código||  
|tabRightBD.gif|Utilizado para representar el contenedor del fragmento de código||  
|vs\_logo\_bk.gif|Se utiliza para las referencias del logotipo de contraste normal tal como se define en la etiqueta Branding.xml \< LogoFileName \>.  Para los productos de Visual Studio, nombre del logotipo es vs\_logo\_bk.gif.||  
|vs\_logo\_wh.gif|Utilizada para referencias de logotipo alto normal, como se define en la etiqueta Branding.xml \< LogoFileNameHC \>.  Para los productos de Visual Studio, nombre del logotipo es vs\_logo\_wh.gif.||  
|ccOff.png|Gráfico de subtítulos \(CC\)||  
|ccOn.png|Gráfico de subtítulos \(CC\)||  
|ImageSprite.png|Utilizado para representar el área contraíble|Expandir o contraer el gráfico|  
  
### Implementación de un conjunto de temas  
 Se trata de un tutorial muy sencillo y rápido para crear una implementación de contenido del Visor de ayuda conjunto compuesta por un archivo MSHA y el conjunto de archivos .cab o MSHC que contiene los temas. El MSHA es un archivo XML que describe un conjunto de archivos .cab o los archivos MSHC. El Visor de ayuda puede leer el MSHA para obtener una lista de contenido \(el archivo. CAB o. Archivos MSHC\) disponible para su instalación local.  
  
 Esto es sólo una guía que describe el esquema XML muy básico para el Visor de ayuda, MSHA.  Tenga en cuenta que hay una implementación de ejemplo a continuación de esta breve introducción y ejemplo de HelpContentSetup.msha.  
  
 El nombre de la MSHA para los fines de este manual es de HelpContentSetup.msha \(el nombre del archivo puede ser cualquier cosa, con la extensión. MSHA\). \(El ejemplo a continuación\) de HelpContentSetup.msha debe contener una lista de los archivos CAB o MSHCs disponibles.  Tenga en cuenta que el tipo de archivo debe ser coherente dentro de la MSHA \(no admite una combinación de tipos de archivo MSHA y CAB\). Para cada archivo CAB o MSHC, debe haber un \< div clase \= "paquete" \>... \< \/ div \> \(consulte el ejemplo siguiente\).  
  
 Nota: en el siguiente ejemplo de implementación, hemos incluido el paquete de personalización de marca. Esto es importante incluir para obtener los elementos necesarios de representación de contenido de Visual Studio y los comportamientos de contenido.  
  
 Ejemplo de archivo de HelpContentSetup.msha: \(reemplace "contenido conjunto nombre 1" y "contenido conjunto nombre 2", etc. con los nombres de archivo.\)  
  
```  
<html> <head /> <body class="vendor-book"> <div class="details"> <span class="vendor">Your Company</span> <span class="locale">en-us</span> <span class="product">Your Company Help Content</span> <span class="name">Your Company Help Content</span> </div> <div class="package-list"> <div class="package"> <span class="name">Your_Company _Content_Set_1</span> <span class="deployed">True</span> <a class="current-link" href="Your_Company _Content_Set_1.mshc">Your_Company _Content_Set_1.mshc </a> </div> <div class="package"> <span class="name">Your_Company _Content_Set_2</span> <span class="deployed">True</span> <a class="current-link"href=" Your_Company _Content_Set_2.mshc "> Your_Company _Content_Set_2.mshc </a> </div>.  
  
```  
  
1.  Cree una carpeta local, algo parecido a "C:\\SampleContent"  
  
2.  En este ejemplo, usaremos archivos MSHC para que contenga los temas.  Un MSHC es un archivo zip con la extensión de archivo cambiado de .zip a. MSHC.  
  
3.  Crear el debajo de HelpContentSetup.msha como un archivo de texto \(Bloc de notas se usó para crear el archivo\) y guárdelo en la carpeta anotada anterior \(consulte el paso 1\).  
  
 Tenga en cuenta que la clase "Personalización" existe y es único. El uso de la marca mshc se incluye en este manual para que el contenido instalado tendrá la personalización de marca y los comportamientos de contenido que se encuentran en el MSHCs tendrá los elementos de soporte adecuado contenidos en el paquete de personalización de marca. Sin esto, se producirán errores cuando el sistema busca elementos de soporte que no forman parte de copiados \(instalado\) contenido.  
  
 Para obtener el paquete de personalización de marca de Visual Studio, copie el archivo de Branding\_en US.mshc en C:\\Program Files \(x 86\) \\Microsoft Help Viewer\\v2.1\\ a la carpeta de trabajo.  
  
```html  
<html> <head /> <body class="vendor-book"> <div class="details"> <span class="vendor">Your Company</span> <span class="locale">en-us</span> <span class="product">Your Company Help Content</span> <span class="name">Your Company Help Content</span> </div> <div class="package-list"> <div class="package"> <span class="name">Your_Company _Content_Set_1</span> <span class="deployed">True</span> <a class="current-link" href="Your_Company _Content_Set_1.mshc">Your_Company _Content_Set_1.mshc </a> </div> <div class="package"> <span class="name">Your_Company _Content_Set_2</span> <span class="deployed">True</span> <a class="current-link"href=" Your_Company _Content_Set_2.mshc "> Your_Company _Content_Set_2.mshc </a> </div> <div class="package"> <span class="packageType">branding</span> <span class="name">Branding_en-US</span> <span class="deployed">True</span> <a class="current-link" href="Branding_en-US.mshc">Branding_en-US.mshc</a> </div> </div> </body> </html>  
  
```  
  
 **Resumen**  
  
 Usar y extender los pasos anteriores le permitirá VSPs implementar sus conjuntos de contenido para el Visor de Ayuda de Visual Studio.  
  
### Agregar ayuda a Visual Studio Shell \(integrado y aislado\)  
 **Introducción**  
  
 Este tutorial muestra cómo incorporar contenido de ayuda en una aplicación de Shell de Visual Studio y, a continuación, implementarlo.  
  
 **Requisitos**  
  
1.  [!INCLUDE[vs_dev12](../../data-tools/includes/vs_dev12_md.md)]  
  
2.  [Visual Studio 2013 aislada a Redist de Shell](http://www.microsoft.com/visualstudio/11/downloads#vs-shell)  
  
 **Información general**  
  
 El [!INCLUDE[vs_dev12](../../data-tools/includes/vs_dev12_md.md)] Shell es una versión de la [!INCLUDE[vs_dev12](../../data-tools/includes/vs_dev12_md.md)] IDE en el que puede basar una aplicación. Estas aplicaciones contienen el Shell aislado junto con las extensiones que cree. Usar plantillas de proyecto de Shell aislado, que se incluyen en el [!INCLUDE[vs_dev12](../../data-tools/includes/vs_dev12_md.md)] SDK para crear extensiones.  
  
 Los pasos básicos para crear una aplicación basada en Shell aislado y la Ayuda:  
  
1.  Obtener el [!INCLUDE[vs_dev12](../../data-tools/includes/vs_dev12_md.md)] ISO Shell redistributable \(descarga de Microsoft\).  
  
2.  En Visual Studio, cree una extensión de la Ayuda que se basa en el Shell aislado, por ejemplo, la extensión de la Ayuda de Contoso que se describe más adelante en este tutorial.  
  
3.  Ajuste la extensión y el Shell de ISO redistribuible en una implementación de MSI \(una instalación de aplicación\). Este tutorial no incluye un paso de configuración.  
  
 Crear un almacén de contenido de Visual Studio. Para el escenario de Shell integrado, cambie Studio12 Visual para el nombre del catálogo de productos:  
  
-   Cree la carpeta C:\\ProgramData\\Microsoft\\HelpLibrary2\\Catalogs\\VisualStudio12.  
  
-   Cree un archivo denominado CatalogType.xml y agréguelo a la carpeta. El archivo debe contener las siguientes líneas de código:  
  
    ```  
    <?xml version="1.0" encoding="UTF-8"?> <catalogType>UserManaged</catalogType>  
    ```  
  
 Definir el almacén de contenido en el registro. Para el Shell integrado, cambiar VisualStudio12 para el nombre del catálogo de productos:  
  
-   HKLM\\SOFTWARE\\Wow6432Node\\Microsoft\\Help\\v2.1\\Catalogs\\VisualStudio12  
  
     Clave: El valor de cadena de LocationPath: C:\\ProgramData\\Microsoft\\HelpLibrary2\\Catalogs\\VisualStudio12\\  
  
-   HKLM\\SOFTWARE\\Wow6432Node\\Microsoft\\Help\\v2.1\\Catalogs\\VisualStudio12\\en\-US  
  
     Clave: Valor cadena CatalogName: [!INCLUDE[vs_dev12](../../data-tools/includes/vs_dev12_md.md)] documentación  
  
 **Crear el proyecto**  
  
 Para crear una extensión de Shell aislado:  
  
1.  En Visual Studio, en **archivo**, elija **nuevo proyecto**, en **otros tipos de proyectos** elegir **extensibilidad**, y, a continuación, elija  **Visual Studio Shell aislado**. Denomine el proyecto `ContosoHelpShell`\) para crear un proyecto de extensibilidad basado en la plantilla de Shell aislado de Visual Studio.  
  
2.  En el Explorador de soluciones, en el proyecto ContosoHelpShellUI, en la carpeta archivos de recursos, abra ApplicationCommands.vsct. Asegúrese de que esta línea está comentada \(busque "No\_Help"\): `<!-- <define name=“No_HelpMenuCommands”/> -->`  
  
3.  Presione la tecla F5 para compilar y ejecutar **Depurar**. En la instancia experimental de la IDE de Shell aislado, elija la **Ayuda** menú. Asegúrese de que el **Ver Ayuda**, **Agregar y quitar contenido de Ayuda**, y **establecer preferencias de la Ayuda** comandos aparecen.  
  
4.  En el Explorador de soluciones, en el proyecto ContosHelpShell, en la carpeta de la personalización del Shell, abra ContosoHelpShell.pkgdef. Para definir el catálogo de Ayuda de Contoso, agregue las siguientes líneas:  
  
    ```  
    [$RootKey$\Help] "Product"="Contoso" "Catalog"="Contoso" “Version"="100" "BrandingPackage"="ContosoBrandingPackage.mshc"  
    ```  
  
5.  En el Explorador de soluciones, en el proyecto ContosHelpShell, en la carpeta de la personalización del Shell, abra ContosoHelpShell.Application.pkgdef. Para habilitar la Ayuda F1, agregue las siguientes líneas:  
  
    ```  
    // F1 Help Provider [$RootKey$\HelpProviders\{C99BDC23-FF29-46bf-9658-ADD634CCAED8}] "Name"="13407" "Package"="{DA9FB551-C724-11d0-AE1F-00A0C90FFFC3}" @="Help3 Provider" [$RootKey$\HelpProviders] @="{C99BDC23-FF29-46bf-9658-ADD634CCAED8}" [$RootKey$\Services\{C99BDC23-FF29-46bf-9658-ADD634CCAED8}] "Name"="Help3 Provider" @="{4A791146-19E4-11D3-B86B-00C04F79F802}"  
    ```  
  
6.  En el Explorador de soluciones, en el menú contextual de la solución ContosoHelpShell, elija la **propiedades** elemento de menú. Bajo **Propiedades de configuración**, seleccione **Configuration Manager**. En el **configuración** columna, cambiar cada valor de "Debug" a "Release".  
  
7.  Compile la solución. Esto crea un conjunto de archivos en una carpeta de la versión que se utilizará en la sección siguiente.  
  
 Para probar esto como si hubieran sido:  
  
1.  En el equipo de implementación de Contoso para instalar descargado ISO Shell \(desde\).  
  
2.  Cree una carpeta en \\\\Program Files \(x 86\) \\ y asígnele el nombre `Contoso`.  
  
3.  Copie el contenido de la carpeta de la versión ContosoHelpShell a la carpeta \\Contoso\\ de \\\\Program Files \(x 86\).  
  
4.  Inicie el Editor del registro eligiendo  **ejecutar** en el **iniciar** menú y escriba `Regedit`. En el editor del registro, elija **archivo**, y luego **importación**. Vaya a la carpeta del proyecto ContosoHelpShell. En la subcarpeta ContosoHelpShell, elija ContosoHelpShell.reg.  
  
5.  Crear un almacén de contenido:  
  
     Shell de ISO \- crear un almacén de contenido de Contoso C:\\ProgramData\\Microsoft\\HelpLibrary2\\Catalogs\\ContosoDev12  
  
     Para [!INCLUDE[vs_dev12](../../data-tools/includes/vs_dev12_md.md)] Shell integrado, cree la carpeta C:\\ProgramData\\Microsoft\\HelpLibrary2\\Catalogs\\VisualStudio12  
  
6.  Crear CatalogType.xml y agregar al almacén de contenido \(paso anterior\) que contiene:  
  
    ```  
    <?xml version="1.0" encoding="UTF-8"?> <catalogType>UserManaged</catalogType>  
    ```  
  
7.  Agregue las siguientes claves del registro:  
  
     HKLM\\SOFTWARE\\Wow6432Node\\Microsoft\\Help\\v2.1\\Catalogs\\VisualStudio12Key: Valor de cadena de LocationPath:  
  
     Shell de ISO:  
  
     C:\\ProgramData\\Microsoft\\HelpLibrary2\\Catalogs\\VisualStudio12\\  
  
     [!INCLUDE[vs_dev12](../../data-tools/includes/vs_dev12_md.md)] Shell integrado:  
  
     C:\\ProgramData\\Microsoft\\HelpLibrary2\\Catalogs\\VisualStudio12\\\\en\-US  
  
     Clave: Valor cadena CatalogName: [!INCLUDE[vs_dev12](../../data-tools/includes/vs_dev12_md.md)] documentación. Shell de ISO, este es el nombre del catálogo.  
  
8.  Copie el contenido \(MSHA y MSHC o .cab\) en una carpeta local.  
  
9. Línea de comandos de Shell integrado de ejemplo para probar el almacén de contenido. Shell de ISO, cambiar los valores de catálogo y launchingApp para coincidir con el producto.  
  
     Método de \/helpQuery \/catalogName VisualStudio12 "C:\\Program Files \(x 86\) \\Microsoft Help Viewer\\v2.1\\HlpViewer.exe" \= "página & id \= ContosoTopic0" \/launchingApp Microsoft, VisualStudio, 12.0  
  
10. Inicie la aplicación Contoso \(desde la raíz de la aplicación Contoso\). Shell de ISO, elija la **Ayuda** elemento de menú y cambiar la **establecer preferencias de la Ayuda** a **usar la Ayuda Local**.  
  
11. Dentro del shell, elija la **Ayuda** elemento de menú, **Ver Ayuda**. Debe iniciar el Visor de Ayuda local. Elija la pestaña **Administrar contenido**. Bajo **origen de instalación**, elija la **disco** botón de opción. Elija la **...** botón y vaya a la carpeta local que contiene el contenido de Contoso \(que se copia a la carpeta local en el paso anterior\). Elija el HelpContentSetup.msha. Contoso debería aparecer ahora como un libro en las selecciones del libro. Elija **Agregar**, y, a continuación, elija la **actualización** botón \(esquina inferior derecha\).  
  
12. En el IDE de Contoso, elija la tecla F1 para probar la funcionalidad de F1.  
  
### Recursos adicionales  
 Para la API de tiempo de ejecución, consulte [API de Ayuda de Windows](http://msdn.microsoft.com/library/windows/desktop/hh447318\(v=vs.85\).aspx).  
  
 Para obtener información adicional acerca de cómo aprovechar la API de ayuda, consulte [ejemplos de código de Visor de Ayuda](http://visualstudiogallery.msdn.microsoft.com/f08f296f-7076-4aec-8da3-8f0fbe04461e)  
  
 Para proporcionar comentarios acerca de estos componentes, use [Microsoft Connect](http://connect.microsoft.com/).  
  
 Envíe sugerencias de características a [Microsoft User Voice](http://visualstudio.uservoice.com/forums/121579-visual-studio)  
  
 Para obtener ayuda adicional, pruebe la [sistema de ayuda y documentación para desarrolladores de MSDN foros](http://social.msdn.microsoft.com/Forums/devdocs/threads)  
  
 Las actualizaciones de romper el problema, consulte el [Léame del Visor de Ayuda](http://go.microsoft.com/fwlink/?LinkID=231397&clcid=0x409)  
  
 Para ponerse en contacto directamente con el equipo P.M. del Visor de ayuda, enviar correo electrónico a hlpfdbk@microsoft.com