---
title: "Localizar soluciones de SharePoint"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.SharePointTools.Project.GlobalAndFeatureResource"
  - "VS.SharePoint.Project.AddResourceDialog"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "globalizar [desarrollo de SharePoint en Visual Studio]"
  - "localizar [desarrollo de SharePoint en Visual Studio]"
  - "Desarrollo de SharePoint en Visual Studio, localizar"
ms.assetid: 0d4cfa2b-8b48-45c7-bbee-ece9b0baffaf
caps.latest.revision: 18
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 17
---
# Localizar soluciones de SharePoint
  El proceso de preparar las aplicaciones para que puedan usarse en todo el mundo se conoce como "localización".  La localización consiste en la traducción de los recursos a una referencia cultural concreta.  Para obtener más información, vea [Globalizar y localizar aplicaciones](../ide/globalizing-and-localizing-applications.md).  En este tema se proporciona información general acerca de cómo se localiza una solución de SharePoint.  
  
 Para localizar una solución, quite del código las cadenas codificadas de forma rígida e inclúyalas en archivos de recursos.  Un archivo de recursos es un archivo basado en [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] con la extensión .resx.  El archivo de recursos contiene las versiones traducidas de las cadenas que se usan en la solución.  Para obtener más información, vea [Recursos en aplicaciones](http://go.microsoft.com/fwlink/?LinkID=155844).  
  
> [!NOTE]  
>  Solo debe agregar recursos de cadena a los archivos de recursos de la solución de SharePoint.  Aunque el Editor de recursos permite agregar recursos que no son de cadena, este tipo de recursos no se implementan en SharePoint.  
  
## Archivos de recursos  
 Existen tres tipos de archivos de recursos: predeterminado, independiente del idioma y específico del idioma.  
  
|Tipo de archivo de recursos|Descripción|  
|---------------------------------|-----------------|  
|Valor|Los archivos de recursos predeterminados \(también denominados recursos de reserva\) contienen cadenas localizadas en la referencia cultural predeterminada, como por ejemplo, inglés.  Se usan si no se encuentran los archivos de recursos localizados en el idioma especificado.  Los recursos predeterminados no tienen archivos independientes y se almacenan en el ensamblado de la aplicación principal.|  
|Independiente del idioma|Archivo de recursos que contiene cadenas localizadas en un idioma, pero no una referencia cultural concreta.  Por ejemplo, "fr" para francés.|  
|Específicos del idioma|Archivo de recursos que contiene las cadenas localizadas de un idioma y una referencia cultural.  Por ejemplo, "fr\-CA" para francés canadiense.|  
  
 Para obtener más información, vea [Organización jerárquica de recursos para la localización](http://go.microsoft.com/fwlink/?LinkId=178360).  
  
 Para especificar los archivos de recursos predeterminados de los proyectos de SharePoint que desarrolle en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], elija **Todos los idiomas \(todos los países\)** en la lista de referencias culturales del cuadro de diálogo **Agregar recurso** cuando agregue un archivo de recursos.  
  
## Localizar soluciones de SharePoint de Visual Studio  
 Al localizar una solución, debe tener en cuenta toda la información textual que la solución muestra a los usuarios.  Los mensajes informativos, los mensajes de error y las cadenas de [!INCLUDE[TLA2#tla_ui](../sharepoint/includes/tla2sharptla-ui-md.md)] deben traducirse y estas traducciones deben incluirse en los archivos de recursos.  
  
 Todas las cadena de un archivo de recursos tienen un identificador único.  Use el mismo identificador de la cadena traducida en cada archivo de recursos.  Por ejemplo, si "String1" es el identificador de la primera cadena del archivo de recursos predeterminado, use el mismo identificador para la primera cadena de los archivos de recursos específicos del idioma.  
  
 Normalmente, son tres los componentes de las aplicaciones de SharePoint de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] que se traducen: las características, el marcado de páginas ASPX y el código.  A efectos ilustrativos, en las secciones siguientes se va a presuponer que tiene una solución de SharePoint que desea traducir al alemán y el japonés.  El idioma predeterminado es el inglés.  
  
### Localizar las características  
 Para localizar una característica, es necesario sustituir el título y la descripción de la característica codificados de forma rígida por una expresión que haga referencia al título y la cadena traducidos del archivo de recursos localizado.  Esta modificación se lleva a cabo en el **Diseñador de características** de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  Para obtener más información, vea [Cómo: Localizar una característica](../sharepoint/how-to-localize-a-feature.md).  
  
 Para localizar una característica en inglés al alemán y al japonés, debe agregar al proyecto tres elementos de proyecto del archivo de recursos: uno para el inglés, uno para el alemán y uno para el japonés.  Los archivos de recursos de características no pueden usarse para localizar el marcado ASPX ni el código; deben usarse otros archivos de recursos independientes.  
  
 Después de crear los archivos de recursos de características, agregue las cadenas traducidas.  Para obtener acceso a las cadenas localizadas, use una expresión con el siguiente formato:  
  
```  
$Resources:String ID  
```  
  
 Los recursos de características de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] se denominan siempre Resources.  Si selecciona un idioma que no sea Todos los idiomas \(todos los países\), una referencia cultural [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)] se agrega al archivo de recursos.  Por ejemplo, si agrega un archivo de recursos de características de idioma \(predeterminado\) invariable, se denomina Resources.resx.  Si agrega un recurso de características específico del idioma y selecciona la referencia cultural Japonés \(Japón\), el archivo se denominará Resources.ja\-JP.resx.  Los nombres de archivo de recursos de características se asignan automáticamente y no se pueden modificar.  
  
 El ámbito de los recursos de características es local y se limita a la característica a la que estos recursos se agregan.  Para crear recursos que cualquier archivo de elementos o características de la solución pueda usar, agregue un elemento de proyecto **Archivo de recursos globales** en lugar de un archivo de recursos de características.  El elemento de proyecto **Archivo de recursos globales** se encuentra en la carpeta **2010** del cuadro de diálogo **Agregar nuevo elemento** bajo **SharePoint**.  Los archivos de recursos globales se implementan en la carpeta \\Resources de la carpeta raíz de SharePoint.  
  
### Localizar el marcado de páginas ASPX  
 Para localizar páginas de [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)], agregue tres elementos de proyecto Archivo de recursos al proyecto: uno para inglés, uno para alemán y otro para japonés.  Si no es necesario localizar el código además del marcado, puede agregar archivos de recursos globales en su lugar.  
  
 Especifique un nombre para el archivo de recursos del idioma predeterminado.  Asigne a los archivos de recursos localizados el mismo nombre y use como anexo el [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)] de la referencia cultural específica del idioma.  Por ejemplo, MyAppResources.de\-DE.resx para alemán y MyAppResources.ja\-JP.resx para japonés.  
  
 Establezca la propiedad **Deployment Type** de cada archivo de recursos en **AppGlobalResource**.  De este modo, los archivos de recursos se implementarán en la carpeta App\_GlobalResources, donde estarán disponibles para todos los controles y páginas ASPX de la solución.  La carpeta App\_GlobalResources se encuentra en C:\\inetpub\\wwwroot\\wss\\VirtualDirectories\\\<número de puerto\>\\App\_GlobalResources.  
  
> [!NOTE]  
>  Si usa archivos de recursos que no son globales, muévalos a la carpeta de elementos del proyecto para habilitar la propiedad Deployment Type y otras propiedades específicas de SharePoint.  
  
 Los archivos de recursos de marcado ASPX también se pueden usar para localizar código.  Si está usando los recursos para localizar código además del marcado ASPX, deje el valor de la propiedad Build Action de cada archivo como Embedded Resource para que el recurso se compile en un ensamblado satélite.  En cambio, si está usando los archivos de recursos únicamente para localizar el marcado, puede cambiar la propiedad Build Action a Content para evitar que el archivo se compile en el ensamblado de la aplicación principal.  
  
 Sustituya todas las cadenas de propiedad codificadas de forma rígida del marcado de los controles y páginas ASPX por una expresión con el siguiente formato:  
  
```  
<asp:<class> runat="server" Text="<%$Resources:<Resource File Name>, <String ID>%>" />  
```  
  
 Por ejemplo:  
  
```  
<asp:Button ID="btn1" runat="server" onclick="btn1_Click" Text="<%$Resources:Resource1,String7%>"></asp:Button>  
```  
  
 Para ASPX como texto, use una expresión en el formato siguiente:  
  
```  
<asp:literal ID="<ID>" runat="server" Text="<%$Resources:<Resource File Name>, <String ID>%>" />  
```  
  
 Por ejemplo:  
  
```  
<asp:literal ID="Literal1" runat="server" Text="<%$Resources:Resource1, String9%>" />  
```  
  
 Para obtener más información, vea [Cómo: Localizar el marcado ASPX](../sharepoint/how-to-localize-aspx-markup.md).  
  
### Adaptar código  
 Además de localizar cadenas de características y el marcado de [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)], también tiene que localizar las cadenas de mensaje y las cadenas del error que aparecen en el código de la solución.  Los mensajes informativos y de error localizados están en ensamblados satélite.  Los ensamblados satélite contienen cadenas visibles para los usuarios, como los mensajes de texto y salida de [!INCLUDE[TLA2#tla_ui](../sharepoint/includes/tla2sharptla-ui-md.md)] como excepciones.  
  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] usa el modelo de radio y concentrador de .NET Framework estándar.  El concentrador \(o ensamblado del programa principal\) contiene los recursos del idioma predeterminado.  Los radios \(o ensamblados satélite\) contienen los recursos específicos del idioma.  Para obtener más información, vea [Empaquetar e implementar recursos](http://go.microsoft.com/fwlink/?LinkId=179280).  Los ensamblados satélite se compilan a partir de los archivos de recursos \(.resx\).  Cuando se agregan archivos de recursos específicos del idioma al proyecto y al paquete de solución, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] compila los archivos de recursos en los ensamblados satélite denominados *Project Name*.resources.dll.  
  
 Al igual que en el marcado ASPX, debe localizar el código de la aplicación de SharePoint agregando los elementos de proyecto de archivo de recursos independientes al proyecto: uno para el idioma predeterminado y uno para cada idioma localizado.  Sin embargo, tal y como se mencionó anteriormente, si ya tiene archivos de recursos para localizar el marcado ASPX, puede volver a usarlos para localizar el código.  Si necesita crear archivos de recursos, asigne al archivo de recursos del idioma predeterminado un nombre de su elección y anéxelo con la extensión .resx.  Asigne a los archivos de recursos localizados el mismo nombre y use como anexo el [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)] de la referencia cultural específica del idioma.  Establezca la propiedad Build Action de cada archivo de recursos en Embedded Resource para permitir la creación de ensamblados de recursos satélite.  
  
 Para crear los ensamblados satélite, compile el proyecto y, a continuación, agregue los archivos como ensamblados adicionales a través de la pestaña **Opciones avanzadas** del **Diseñador de paquetes**.  Cuando agregue los ensamblados, anteponga una carpeta [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)] de referencia cultural a la ruta de acceso de ubicación, por ejemplo de\-DE\\*Project Item Name*.resources.dll.  De este modo, el paquete podrá contener archivos que tengan el mismo nombre.  
  
 En el código, reemplace las cadenas codificadas de forma rígida con llamadas al método <xref:System.Web.HttpContext.GetGlobalResourceObject%2A> mediante la siguiente sintaxis:  
  
```  
HttpContext.GetGlobalResourceObject("<Resource File Name>", "<String ID>")  
```  
  
 Para obtener más información, vea [Cómo: Localizar código](../sharepoint/how-to-localize-code.md).  
  
#### Localización del código de elementos web  
 Los elementos web incluyen una característica del editor de propiedades personalizadas que contiene atributos de código que usan cadenas codificadas de forma rígida, como WebDisplayName, Category y WebDescription.  Para reemplazar los valores de cadena de estos atributos, cree una clase independiente que se derive de la clase del atributo.  En esas clases, establezca la propiedad del atributo.  La propiedad del atributo depende de la clase base.  Por ejemplo, la propiedad del atributo WebDisplayName es DisplayNameValue y la propiedad del atributo WebDescription es DescriptionValue.  
  
 En la clase derivada, haga referencia al identificador de cadena del archivo de recursos y al objeto ResourceManager para obtener el valor localizado del identificador de cadena.  Devuelva este valor al atributo del editor de propiedades.  
  
## Vea también  
 [Cómo: Localizar una característica](../sharepoint/how-to-localize-a-feature.md)   
 [Cómo: Localizar el marcado ASPX](../sharepoint/how-to-localize-aspx-markup.md)   
 [Cómo: Localizar código](../sharepoint/how-to-localize-code.md)   
 [Cómo: Agregar un archivo de recursos](../sharepoint/how-to-add-a-resource-file.md)   
 [Cómo: Usar un archivo de recursos para especificar nombres, propiedades y permisos localizados](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)  
  
  