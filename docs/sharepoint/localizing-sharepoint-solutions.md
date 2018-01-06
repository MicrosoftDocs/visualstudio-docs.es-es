---
title: Localizar soluciones de SharePoint | Documentos de Microsoft
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.SharePointTools.Project.GlobalAndFeatureResource
- VS.SharePoint.Project.AddResourceDialog
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- globalizing [SharePoint development in Visual Studio]
- localizing [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, localizing
ms.assetid: 0d4cfa2b-8b48-45c7-bbee-ece9b0baffaf
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 2339ee60e66bca7578c2d5d1e89c7bb649b15b03
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="localizing-sharepoint-solutions"></a>Localizar soluciones de SharePoint
  El proceso de preparar las aplicaciones para que se pueden usar en todo el mundo se conoce como la localización. Localización es traducir los recursos para una referencia cultural concreta. Para obtener más información, consulte [Globalizar y localizar aplicaciones](/visualstudio/ide/globalizing-and-localizing-applications). Este tema proporciona información general sobre cómo localizar una solución de SharePoint.  
  
 Para localizar una solución, quite las cadenas codificadas de forma rígida del código e inclúyalas en archivos de recursos. Un archivo de recursos es un [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]-archivo con la extensión .resx basado en. El archivo de recursos contiene las versiones traducidas de las cadenas usadas en la solución. Para obtener más información, consulte [recursos de aplicaciones](http://go.microsoft.com/fwlink/?LinkID=155844).  
  
> [!NOTE]  
>  Agregue únicamente los recursos de cadena a los archivos de recursos de solución de SharePoint. Aunque el Editor de recursos permite agregar recursos que no son de cadena, no es una cadena recursos no se implementan en SharePoint.  
  
## <a name="resource-files"></a>Archivos de recursos  
 Hay tres tipos de archivos de recursos: predeterminado, independiente del idioma y específico del idioma.  
  
|Tipo de archivo de recursos|Descripción|  
|------------------------|-----------------|  
|Default|También conocido como un recurso de reserva, archivos de recursos predeterminados contienen cadenas localizadas en la referencia cultural predeterminada, como el inglés. Se utilizan si no se encuentra ningún archivo de recursos localizado para el idioma especificado. Recursos predeterminados no tienen archivos independientes, se almacenan en el ensamblado de aplicación principal.|  
|Independiente del idioma|Un archivo de recursos que contiene cadenas localizadas en un idioma, pero no una referencia cultural concreta. Por ejemplo, "fr" para francés.|  
|Específico del idioma|Un archivo de recursos que contiene cadenas localizadas en un idioma y una referencia cultural. Por ejemplo, "fr-CA" para francés canadiense.|  
  
 Para obtener más información, consulte [organización jerárquica de recursos para la localización](http://go.microsoft.com/fwlink/?LinkId=178360).  
  
 Para especificar archivos de recursos predeterminados en los proyectos de SharePoint que se va a desarrollar en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], elija **Idioma invariable (país invariable)** en la lista de referencia cultural de la **Agregar recurso** cuadro de diálogo cuando se Agregue un archivo de recursos.  
  
## <a name="localizing-visual-studio-sharepoint-solutions"></a>Localizar soluciones de SharePoint de Visual Studio  
 Al localizar una solución, debe tener en cuenta toda la información textual que la solución se muestra a los usuarios. Mensajes informativos, mensajes de error, y [!INCLUDE[TLA2#tla_ui](../sharepoint/includes/tla2sharptla-ui-md.md)] se deben traducir cadenas y las traducciones se colocan en los archivos de recursos.  
  
 Cada cadena de un archivo de recursos tiene un identificador único. Utilizar el mismo identificador de la cadena traducida en cada archivo de recursos. Por ejemplo, si "String1" es el identificador de la primera cadena en el archivo de recursos predeterminado, use el mismo identificador de la primera cadena en los archivos de recursos específicos del idioma.  
  
 Hay tres áreas que se suele traducir en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] las aplicaciones de SharePoint: características, el marcado de páginas ASPX y el código. A efectos de ilustración, las siguientes secciones suponga que tiene una solución de SharePoint que desea localizar en alemán y japonés. El idioma predeterminado es el inglés.  
  
### <a name="localizing-features"></a>Localizar las características  
 Para localizar una característica, tiene que reemplazar el título codificado de forma rígida y la descripción de la característica con una expresión que hace referencia el título traducido y la cadena en el archivo de recursos localizados. Para realizar este cambio en el **Diseñador de características** en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Para obtener más información, consulte [Cómo: localizar una característica](../sharepoint/how-to-localize-a-feature.md).  
  
 Para localizar una característica en inglés en alemán y japonés, debe agregar tres elementos de proyecto de archivo de recursos al proyecto: uno para el inglés, uno para el alemán y uno para el japonés. Archivos de recursos de la característica no se puede usar para localizar el marcado ASPX ni el código; archivos de recursos independientes son necesarios para ellos.  
  
 Después de crear la característica archivos de recursos, agregue las cadenas traducidas a ellos. Tener acceso a las cadenas localizadas, use una expresión con el siguiente formato:  
  
```  
$Resources:String ID  
```  
  
 Característica de recursos de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] siempre se denominan recursos. Si selecciona un idioma distinto de todos los idiomas, a continuación, una referencia cultural [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)] se agrega al nombre del archivo de recursos. Por ejemplo, si agrega un archivo de recursos de la característica de todos los idiomas (valor predeterminado), se denomina Resources.resx. Si agrega un recurso específico del idioma característica seleccionando una referencia cultural japonés (Japón), el archivo se denominará Resources.ja-JP.resx. Nombres de archivo de recursos de características se asignan automáticamente y no se puede cambiar.  
  
 El ámbito de recursos de características es local para la característica que se agregan a. Para crear recursos que pueden usarse en cualquier archivo de características o los elementos de la solución, agregue un **archivo de recursos globales** elemento de proyecto en lugar de un archivo de recursos de característica. El **archivo de recursos globales** elemento de proyecto se encuentra en la **2010** carpeta bajo **SharePoint** en el **Agregar nuevo elemento** cuadro de diálogo. Archivos de recursos globales se implementación en la carpeta \Resources de la carpeta raíz de SharePoint.  
  
### <a name="localizing-aspx-page-markup"></a>Localizar el marcado de páginas ASPX  
 Para localizar [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] páginas, agregar tres elementos de proyecto de archivo de recursos al proyecto: uno para el inglés, uno para el alemán y uno para el japonés. Si no tiene que localizar el código además del marcado, en su lugar, puede agregar archivos de recursos globales.  
  
 Proporcione un nombre para el archivo de recursos de idioma predeterminado. Asignar a los archivos de recursos localizados el mismo nombre que se anexa a la referencia cultural específica del lenguaje [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)]. Por ejemplo, será MyAppResources.de-DE.resx para alemán y MyAppResources.ja-JP.resx para japonés.  
  
 Establecer el **tipo de implementación** propiedad de cada archivo de recursos para **AppGlobalResource**. Esto hace que los archivos de recursos implementar en la carpeta App_GlobalResources, donde están disponibles para todas las páginas ASPX y controles en la solución. La carpeta App_GlobalResources se encuentra en C:\inetpub\wwwroot\wss\VirtualDirectories\\< número de puerto\>\App_GlobalResources.  
  
> [!NOTE]  
>  Si usa archivos de recursos no son globales, muévalos a la carpeta de elementos de proyecto para habilitar la propiedad Deployment Type y otras propiedades específicas de SharePoint.  
  
 Archivos de recursos de marcado ASPX también se pueden utilizar para localizar el código. Si está utilizando los recursos para localizar el código además del marcado ASPX, deje la acción de compilación configuración de la propiedad de cada archivo como un recurso incrustado para hacer que el recurso para compilar en un ensamblado satélite. Sin embargo, si está utilizando los archivos de recursos para localizar el marcado, también puede cambiar acción de compilación al contenido para impedir que el archivo que se compila en el ensamblado de aplicación principal.  
  
 Reemplace todas las cadenas de propiedad codificadas de forma rígida en el marcado de páginas y controles ASPX por una expresión con el siguiente formato:  
  
```  
<asp:<class> runat="server" Text="<%$Resources:<Resource File Name>, <String ID>%>" />  
```  
  
 Por ejemplo:  
  
```  
<asp:Button ID="btn1" runat="server" onclick="btn1_Click" Text="<%$Resources:Resource1,String7%>"></asp:Button>  
```  
  
 Para ASPX como texto, utilice una expresión con el formato siguiente:  
  
```  
<asp:literal ID="<ID>" runat="server" Text="<%$Resources:<Resource File Name>, <String ID>%>" />  
```  
  
 Por ejemplo:  
  
```  
<asp:literal ID="Literal1" runat="server" Text="<%$Resources:Resource1, String9%>" />  
```  
  
 Para obtener más información, consulte [Cómo: localizar marcado ASPX](../sharepoint/how-to-localize-aspx-markup.md).  
  
### <a name="localizing-code"></a>Adaptar código  
 Además de localizar cadenas de características y [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] marcado, también tiene que localizar las cadenas de mensaje y las cadenas de error que aparecen en el código de la solución. Adaptado informativos y mensajes de error están incluidos en los ensamblados satélite. Los ensamblados satélite contienen cadenas que son visibles para los usuarios, como [!INCLUDE[TLA2#tla_ui](../sharepoint/includes/tla2sharptla-ui-md.md)] mensajes de texto y de salida como excepciones.  
  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]usa el modelo de concentrador y radio estándar de .NET Framework. El concentrador o el ensamblado principal del programa, contiene los recursos de idioma predeterminado. Los radios o ensamblados satélite contienen los recursos específicos del idioma. Para obtener más información, vea [Packaging and Deploying Resources](http://go.microsoft.com/fwlink/?LinkId=179280) (Empaquetar e implementar recursos). Ensamblados satélite se compilan a partir de archivos de recursos (.resx). Cuando se agregan archivos de recursos específicos del idioma para el proyecto y el paquete de solución, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] compila los archivos de recursos en ensamblados satélite denominados *nombre del proyecto*. resources.dll.  
  
 Al igual que con el marcado ASPX, localizar el código de aplicación de SharePoint mediante la adición de elementos de proyecto de archivo de recursos independientes al proyecto; uno para el idioma predeterminado y otro para cada uno de los idiomas localizados. Sin embargo, como se mencionó anteriormente, si ya tiene archivos de recursos para localizar el marcado ASPX, se puede reutilizar para localizar el código. Si necesita crear archivos de recursos, asigne un nombre de su elección y anéxelo con la extensión .resx al archivo de recursos de idioma predeterminado. Asigne el mismo nombre que se anexa a la referencia cultural específica del lenguaje de los archivos de recursos adaptados [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)]. Establezca la propiedad acción de compilación de cada archivo de recursos en recurso incrustado para habilitar la creación de ensamblados de recursos satélite.  
  
 Para crear los ensamblados satélite, compile el proyecto y, a continuación, agregue los archivos como ensamblados adicionales a través de la **avanzadas** pestaña de la **Diseñador de paquetes**. Al agregar los ensamblados, anteponga una referencia cultural [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)] carpeta a la ruta de acceso de ubicación, por ejemplo de-DE\\*el nombre del elemento de proyecto*. resources.dll. Esto permite que el paquete contenga los archivos que tienen el mismo nombre.  
  
 En el código, reemplace las cadenas codificadas de forma rígida con llamadas a la <xref:System.Web.HttpContext.GetGlobalResourceObject%2A> método utilizando la sintaxis siguiente:  
  
```  
HttpContext.GetGlobalResourceObject("<Resource File Name>", "<String ID>")  
```  
  
 Para obtener más información, consulte [Cómo: localizar código](../sharepoint/how-to-localize-code.md).  
  
#### <a name="web-part-code-localization"></a>Localización del código de elemento Web  
 Los elementos Web incluyen una característica del editor de propiedades personalizadas que incluye los atributos de código que usan cadenas codificadas de forma rígida, como WebDisplayName, Category y WebDescription. Para reemplazar los valores de cadena para estos atributos, cree una clase independiente que se deriva de la clase de atributo. En esas clases, establezca la propiedad del atributo. La propiedad del atributo depende de la clase base. Por ejemplo, la propiedad del atributo WebDisplayName es DisplayNameValue y la propiedad del atributo WebDescription es DescriptionValue.  
  
 En la clase derivada, puede hacer referencia al identificador de cadena desde el archivo de recursos y el objeto ResourceManager para obtener el valor localizado para el identificador de cadena. Devuelve este valor para el atributo de editor de propiedades.  
  
## <a name="see-also"></a>Vea también  
 [Cómo: localizar una característica](../sharepoint/how-to-localize-a-feature.md)   
 [Cómo: localizar el marcado ASPX](../sharepoint/how-to-localize-aspx-markup.md)   
 [Cómo: localizar código](../sharepoint/how-to-localize-code.md)   
 [Cómo: agregar un archivo de recursos](../sharepoint/how-to-add-a-resource-file.md)   
 [Cómo: Usar un archivo de recursos para especificar nombres, propiedades y permisos localizados](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)  
  
  