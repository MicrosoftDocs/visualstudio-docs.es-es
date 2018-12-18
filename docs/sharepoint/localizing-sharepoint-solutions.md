---
title: Localizar soluciones de SharePoint | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: ba02d8811fc6633a55e06ae63c9399c70f59634f
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/29/2018
ms.locfileid: "37119850"
---
# <a name="localize-sharepoint-solutions"></a>Localizar soluciones de SharePoint

  El proceso de preparar las aplicaciones para que se pueden usar en todo el mundo se conoce como la localización. Localización es traducir los recursos para una referencia cultural concreta. Para obtener más información, consulte [Globalizar y localizar aplicaciones](/visualstudio/ide/globalizing-and-localizing-applications). En este tema se proporciona información general sobre cómo localizar una solución de SharePoint.  
  
 Para localizar una solución, quite del código las cadenas codificadas de forma rígida e inclúyalas en archivos de recursos. Un archivo de recursos es un [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]-basado en archivo con un *.resx* extensión. El archivo de recursos contiene las versiones traducidas de las cadenas usadas en la solución. Para obtener más información, consulte [recursos en aplicaciones](http://go.microsoft.com/fwlink/?LinkID=155844).  
  
> [!NOTE]  
>  Agregar recursos de cadena solo a los archivos de recursos de solución de SharePoint. Aunque el Editor de recursos permite agregar recursos que no son de cadena, los recursos que no son de cadena no se implementan en SharePoint.  
  
## <a name="resource-files"></a>Archivos de recursos
 Hay tres tipos de archivos de recursos: predeterminado, independiente del idioma y específico del idioma.  
  
|Tipo de archivo de recursos|Descripción|  
|------------------------|-----------------|  
|Default|También conocido como un recurso de reserva, archivos de recursos predeterminados contienen cadenas localizadas en la referencia cultural predeterminada, como el inglés. Se usan si no se encuentra ningún archivo de recursos localizados para el idioma especificado. Los recursos predeterminados no tienen archivos independientes y se almacenan en el ensamblado principal de la aplicación.|  
|Idioma neutro|Un archivo de recursos que contiene cadenas localizadas en un idioma, pero no una referencia cultural concreta. Por ejemplo, "fr" para francés.|  
|Específico del lenguaje|Un archivo de recursos que contiene cadenas localizadas en un idioma y una referencia cultural. Por ejemplo, "fr-CA" para francés canadiense.|  
  
 Para obtener más información, consulte [organización jerárquica de recursos para la localización](http://go.microsoft.com/fwlink/?LinkId=178360).  
  
 Para especificar archivos de recursos predeterminados en los proyectos de SharePoint que desarrolle en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], elija **todos los idiomas (todos los países)** en la lista de referencia cultural de la **Agregar recurso** cuadro de diálogo cuando se Agregue un archivo de recursos.  
  
## <a name="localize-visual-studio-sharepoint-solutions"></a>Localizar soluciones de SharePoint de Visual Studio
 Al localizar una solución, debe considerar toda la información textual que la solución se muestra a los usuarios. Los mensajes informativos, mensajes de error, y [!INCLUDE[TLA2#tla_ui](../sharepoint/includes/tla2sharptla-ui-md.md)] cadenas deben traducirse y estas traducciones se colocan en los archivos de recursos.  
  
 Todas las cadenas en un archivo de recursos tienen un identificador único. Use el mismo identificador de la cadena traducida en cada archivo de recursos. Por ejemplo, si "String1" es el identificador de la primera cadena en el archivo de recursos predeterminado, use el mismo identificador de la primera cadena en los archivos de recursos específicos del idioma.  
  
 Hay tres áreas que normalmente se localiza en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] las aplicaciones de SharePoint: características, el marcado de páginas ASPX y el código. Con fines ilustrativos, en las secciones siguientes se suponen que tiene una solución de SharePoint que desea traducir al alemán y japonés. El idioma predeterminado es inglés.  
  
### <a name="localize-features"></a>Localizar las características
 Para localizar una característica, tiene que reemplazar el codificado de forma rígida título y descripción de la característica con una expresión que hace referencia al título traducido y la cadena en el archivo de recursos localizados. Para realizar este cambio en el **característica Diseñador** en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Para obtener más información, consulte [Cómo: localizar una característica](../sharepoint/how-to-localize-a-feature.md).  
  
 Para localizar una característica en inglés al alemán y japonés, agregue tres elementos de proyecto del archivo de recursos al proyecto: uno para el inglés, uno para el alemán y otro para japonés. Archivos de recursos de la característica no se puede usar para localizar el marcado ASPX ni el código; archivos de recursos independientes son necesarios para ellos.  
  
 Después de crear la función de los archivos de recursos, agregue las cadenas traducidas a ellos. Obtener acceso a las cadenas localizadas con una expresión en el formato siguiente:  
  
```aspx-csharp  
$Resources:String ID  
```  
  
 Características de los recursos de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] se denominan siempre Resources. Si selecciona un idioma distinto del idioma invariable, a continuación, una referencia cultural [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)] se agrega al nombre del archivo de recursos. Por ejemplo, si agrega un archivo de recursos de la característica de todos los idiomas (valor predeterminado), se denomina *Resources.resx*. Si agrega un recurso de características específico del idioma seleccionando una referencia cultural japonés (Japón), el archivo se denomina *Resources.ja-JP.resx*. Nombres de archivo de recursos de características se asignan automáticamente y no se puede cambiar.  
  
 El ámbito de recursos de características es local para la característica que se agregan a. Para crear los recursos que se pueden usar cualquier archivo de características o los elementos de la solución, agregue un **archivo de recursos globales** elemento de proyecto en lugar de un archivo de recursos de característica. El **archivo de recursos globales** se encuentra el elemento de proyecto en el **2010** carpeta bajo **SharePoint** en el **Agregar nuevo elemento** cuadro de diálogo. Archivos de recursos globales se implementación en la carpeta \Resources de la carpeta raíz de SharePoint.  
  
### <a name="localize-aspx-page-markup"></a>Localizar el marcado de páginas ASPX
 Para localizar [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] páginas, agregue tres elementos de proyecto de archivo de recursos al proyecto: uno para el inglés, uno para el alemán y otro para japonés. Si no tiene que localizar código además del marcado, en su lugar, puede agregar archivos de recursos globales.  
  
 Proporcione un nombre para el archivo de recursos de idioma predeterminado. Asignar a los archivos de recursos localizados el mismo nombre que se anexa a la referencia cultural específica del lenguaje [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)]. Por ejemplo, *MyAppResources.de-DE.resx* para alemán y *MyAppResources.ja-JP.resx* para japonés.  
  
 Establecer el **tipo de implementación** propiedad de cada archivo de recursos para **AppGlobalResource**. Esto hace que los archivos de recursos implementar en la carpeta App_GlobalResources, donde estarán disponibles para todas las páginas ASPX y controles en la solución. La carpeta App_GlobalResources se encuentra en C:\inetpub\wwwroot\wss\VirtualDirectories\\< número de puerto\>\App_GlobalResources.  
  
> [!NOTE]  
>  Si usa archivos de recursos que no son globales, muévalos a la carpeta de elementos de proyecto para habilitar la propiedad Deployment Type y otras propiedades específicas de SharePoint.  
  
 Archivos de recursos de marcado ASPX también se pueden usar para localizar el código. Si usa los recursos para localizar código además del marcado ASPX, deje la acción de compilación configuración de la propiedad de cada archivo como Embedded Resource para que el recurso para compilar en un ensamblado satélite. Sin embargo, si está usando los archivos de recursos para localizar el marcado, también puede cambiar acción de compilación al contenido para impedir que el archivo que se compilan en el ensamblado principal de la aplicación.  
  
 Reemplace todas las cadenas de propiedad codificadas de forma rígida en el marcado de controles y páginas ASPX por una expresión en el siguiente formato:  
  
```aspx-csharp  
<asp:<class> runat="server" Text="<%$Resources:<Resource File Name>, <String ID>%>" />  
```  
  
 Por ejemplo:  
  
```aspx-csharp  
<asp:Button ID="btn1" runat="server" onclick="btn1_Click" Text="<%$Resources:Resource1,String7%>"></asp:Button>  
```  
  
 Para ASPX como texto, use una expresión en el formato siguiente:  
  
```aspx-csharp  
<asp:literal ID="<ID>" runat="server" Text="<%$Resources:<Resource File Name>, <String ID>%>" />  
```  
  
 Por ejemplo:  
  
```aspx-csharp  
<asp:literal ID="Literal1" runat="server" Text="<%$Resources:Resource1, String9%>" />  
```  
  
 Para obtener más información, consulte [Cómo: marcado ASPX localizar](../sharepoint/how-to-localize-aspx-markup.md).  
  
### <a name="localize-code"></a>Localizar código
 Además de localizar cadenas de características y [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] marcado, también tiene que localizar las cadenas de mensaje y las cadenas de error que aparecen en el código de la solución. Localizado informativos y mensajes de error se encuentran en ensamblados satélite. Los ensamblados satélite contienen cadenas que son visibles para los usuarios, como [!INCLUDE[TLA2#tla_ui](../sharepoint/includes/tla2sharptla-ui-md.md)] mensajes de texto y salida como excepciones.  
  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] usa el modelo de concentrador y radio estándar de .NET Framework. El concentrador o el ensamblado del programa principal contiene los recursos de idioma predeterminado. Los radios, o ensamblados satélite contienen los recursos específicos del idioma. Para obtener más información, vea [Packaging and Deploying Resources](http://go.microsoft.com/fwlink/?LinkId=179280) (Empaquetar e implementar recursos). Los ensamblados satélite se compilan a partir de recursos (*.resx*) los archivos. Cuando se agregan archivos de recursos específicos del idioma al proyecto y el paquete de solución, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] compila los archivos de recursos en los ensamblados satélite denominados *.resources.dll {nombre del proyecto}*.  
  
 El marcado ASPX, localizar el código de aplicación de SharePoint mediante la adición de elementos de proyecto de archivo de recursos independientes al proyecto; uno para el idioma predeterminado y otro para cada idioma localizado. Sin embargo, como se mencionó anteriormente, si ya tiene archivos de recursos para localizar el marcado ASPX, se pueden volver a usarlos para localizar el código. Si necesita crear archivos de recursos, asigne el archivo de recursos de idioma predeterminado un nombre de su elección y anéxelo con un *.resx* extensión. Asigne los archivos de recursos localizados el mismo nombre que se anexa a la referencia cultural específica del lenguaje [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)]. Establezca la propiedad Build Action de cada archivo de recursos en Embedded Resource para permitir la creación de ensamblados de recursos satélite.  
  
 Para crear los ensamblados satélite, compile el proyecto y, a continuación, agregue los archivos como ensamblados adicionales a través de la **avanzadas** pestaña de la **Diseñador de paquetes**. Al agregar los ensamblados, anteponga una referencia cultural [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)] carpeta a la ruta de acceso de ubicación, como *de\\.resources.dll {nombre de elemento de proyecto}*. Esto permite que el paquete podrá contener archivos que tienen el mismo nombre.  
  
 En el código, reemplace las cadenas codificadas de forma rígida con llamadas a la <xref:System.Web.HttpContext.GetGlobalResourceObject%2A> método utilizando la sintaxis siguiente:  
  
```aspx-csharp  
HttpContext.GetGlobalResourceObject("<Resource File Name>", "<String ID>")  
```  
  
 Para obtener más información, consulte [Cómo: localizar código](../sharepoint/how-to-localize-code.md).  
  
#### <a name="web-part-code-localization"></a>Localización del código de elemento Web
 Los elementos Web incluyen una característica del editor de propiedad personalizada que incluye atributos de código que usan cadenas codificadas de forma rígida, como WebDisplayName, Category y WebDescription. Para reemplazar los valores de cadena para estos atributos, cree una clase independiente que se deriva de la clase del atributo. En esas clases, establezca la propiedad del atributo. La propiedad de atributo depende de la clase base. Por ejemplo, la propiedad del atributo WebDisplayName es DisplayNameValue y la propiedad del atributo WebDescription es DescriptionValue.  
  
 En la clase derivada, hacer referencia al identificador de cadena desde el archivo de recursos y el objeto ResourceManager para obtener el valor localizado para el identificador de cadena. Devuelve este valor para el atributo de propiedad del editor.  
  
## <a name="see-also"></a>Vea también
 [Cómo: localizar una característica](../sharepoint/how-to-localize-a-feature.md)   
 [Cómo: localizar el marcado ASPX](../sharepoint/how-to-localize-aspx-markup.md)   
 [Cómo: localizar código](../sharepoint/how-to-localize-code.md)   
 [Cómo: agregar un archivo de recursos](../sharepoint/how-to-add-a-resource-file.md)   
 [Cómo: usar un archivo de recursos para especificar nombres, propiedades y permisos localizados](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)  
  
