---
title: Localizar soluciones de SharePoint | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.Project.GlobalAndFeatureResource
- VS.SharePoint.Project.AddResourceDialog
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- globalizing [SharePoint development in Visual Studio]
- localizing [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, localizing
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 7bcd11d7860e1d191479d4a2ea5f9fac78dcdfe2
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2019
ms.locfileid: "73189223"
---
# <a name="localize-sharepoint-solutions"></a>Localizar soluciones de SharePoint

  El proceso de preparación de las aplicaciones para que se puedan usar en todo el mundo se conoce como localización. La localización consiste en traducir recursos a una referencia cultural específica. Para obtener más información, vea [globalizar y localizar aplicaciones](../ide/globalizing-and-localizing-applications.md). En este tema se proporciona información general sobre cómo localizar una solución de SharePoint.

 Para localizar una solución, se quitan las cadenas codificadas de forma rígida del código y se abstraen en archivos de recursos. Un archivo de recursos es un archivo basado en [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]con una extensión *. resx* . El archivo de recursos contiene las versiones traducidas de las cadenas usadas en la solución. Para obtener más información, consulte [recursos en aplicaciones](/previous-versions/dotnet/netframework-4.0/f45fce5x(v=vs.100)).

> [!NOTE]
> Agregue solo recursos de cadena a los archivos de recursos de la solución de SharePoint. Aunque el editor de recursos le permite agregar recursos que no son de cadena, los recursos que no son de cadena no se implementan en SharePoint.

## <a name="resource-files"></a>Archivos de recursos
 Hay tres tipos de archivos de recursos: valores predeterminados, independientes del idioma y específicos del idioma.

|Tipo de archivo de recursos|Descripción|
|------------------------|-----------------|
|Predeterminado|También conocido como recurso de reserva, los archivos de recursos predeterminados contienen cadenas localizadas para la referencia cultural predeterminada, como inglés. Se usan si no se pueden encontrar archivos de recursos localizados para el idioma especificado. Los recursos predeterminados no tienen archivos independientes, sino que se almacenan en el ensamblado de la aplicación principal.|
|Independiente del idioma|Un archivo de recursos que contiene cadenas localizadas para un idioma, pero no una referencia cultural específica. Por ejemplo, "fr" para francés.|
|Específico del idioma|Un archivo de recursos que contiene cadenas localizadas para un idioma y una referencia cultural. Por ejemplo, "FR-CA" para francés canadiense.|

 Para obtener más información, consulte [organización jerárquica de recursos para la localización](../ide/globalizing-and-localizing-applications.md).

 Para especificar los archivos de recursos predeterminados en los proyectos de SharePoint que desarrolle en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], elija **idioma invariable (país invariable)** en la lista referencia cultural del cuadro de diálogo **Agregar recurso** cuando agregue un archivo de recursos.

## <a name="localize-visual-studio-sharepoint-solutions"></a>Localizar soluciones de SharePoint de Visual Studio
 Al localizar una solución, debe tener en cuenta toda la información textual que la solución muestra a los usuarios. Los mensajes informativos, los mensajes de error y las cadenas de [!INCLUDE[TLA2#tla_ui](../sharepoint/includes/tla2sharptla-ui-md.md)] deben traducirse y las traducciones colocadas en los archivos de recursos.

 Cada cadena de un archivo de recursos tiene un identificador único. Use el mismo identificador para la cadena traducida en cada archivo de recursos. Por ejemplo, si "string1" es el identificador de la primera cadena del archivo de recursos predeterminado, utilice el mismo identificador para la primera cadena en los archivos de recursos específicos del lenguaje.

 Normalmente, hay tres áreas que se pueden localizar en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] aplicaciones de SharePoint: características, marcado de páginas ASPX y código. A efectos de Ilustración, en las secciones siguientes se supone que tiene una solución de SharePoint que desea localizar en alemán y japonés. El idioma predeterminado es el inglés.

### <a name="localize-features"></a>Localizar características
 Para localizar una característica, tiene que reemplazar el título y la descripción de la característica codificados de forma rígida por una expresión que haga referencia al título y la cadena traducidos en el archivo de recursos adaptado. Este cambio se realiza en el **Diseñador de características** de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Para obtener más información, vea [Cómo: localizar una característica](../sharepoint/how-to-localize-a-feature.md).

 Para localizar la característica en inglés en alemán y japonés, agregue tres elementos de proyecto de archivo de recursos al proyecto: uno para inglés, otro para alemán y otro para japonés. Los archivos de recursos de características no se pueden usar para localizar el marcado ASPX o el código; los archivos de recursos independientes son necesarios para ellos.

 Después de crear los archivos de recursos de características, agregue cadenas traducidas. Acceda a las cadenas traducidas con una expresión con el siguiente formato:

```aspx-csharp
$Resources:String ID
```

 Los recursos de características de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] siempre son recursos denominados. Si selecciona un idioma que no sea el idioma invariable, se agregará una referencia cultural [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)] al nombre del archivo de recursos. Por ejemplo, si agrega un archivo de recursos de características de lenguaje invariable (predeterminado), se denomina *Resources. resx*. Si agrega un recurso de característica específico del idioma seleccionando una referencia cultural japonés (Japón), el archivo se denomina *Resources. ja-JP. resx*. Los nombres de archivo de recursos de características se asignan automáticamente y no se pueden cambiar.

 El ámbito de los recursos de características es local a la característica a la que se agregan. Para crear recursos que se puedan usar en cualquier característica o archivo de elemento de la solución, agregue un elemento de proyecto de **archivo de recursos globales** en lugar de un archivo de recursos de características. El elemento de proyecto de **archivo de recursos globales** se encuentra en la carpeta **2010** bajo **SharePoint** en el cuadro de diálogo **Agregar nuevo elemento** . Los archivos de recursos globales se implementan en la carpeta \Resources de la carpeta raíz de SharePoint.

### <a name="localize-aspx-page-markup"></a>Localizar el marcado de página ASPX
 Para localizar páginas [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)], agregue tres elementos de proyecto de archivo de recursos al proyecto: uno para inglés, otro para alemán y otro para japonés. Si no tiene que localizar el código además del marcado, puede Agregar archivos de recursos globales en su lugar.

 Proporcione un nombre para el archivo de recursos de idioma predeterminado. Asigne a los archivos de recursos localizados el mismo nombre anexado a la referencia cultural específica del idioma [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)]. Por ejemplo, *MyAppResources.de-de. resx* para alemán y *MyAppResources. ja-JP. resx* para japonés.

 Establezca la propiedad **tipo de implementación** de cada archivo de recursos en **AppGlobalResource**. Esto hace que los archivos de recursos se implementen en la carpeta App_GlobalResources, donde están disponibles para todos los controles y páginas ASPX de la solución. La carpeta App_GlobalResources se encuentra en C:\inetpub\wwwroot\wss\VirtualDirectories\\< número de Puerto\>\App_GlobalResources.

> [!NOTE]
> Si usa archivos de recursos no globales, muévalos a la carpeta de elementos de proyecto para habilitar la propiedad tipo de implementación y otras propiedades específicas de SharePoint.

 Los archivos de recursos de marcado ASPX también se pueden usar para localizar código. Si usa los recursos para localizar el código además del marcado ASPX, deje la configuración de la propiedad acción de compilación de cada archivo como recurso incrustado para que el recurso se compile en un ensamblado satélite. Sin embargo, si usa los archivos de recursos para localizar el marcado, opcionalmente puede cambiar la acción de compilación a contenido para evitar que el archivo se compile en el ensamblado de la aplicación principal.

 Reemplace todas las cadenas de propiedades codificadas de forma rígida en las páginas ASPX y el marcado de controles por una expresión con el siguiente formato:

```aspx-csharp
<asp:<class> runat="server" Text="<%$Resources:<Resource File Name>, <String ID>%>" />
```

 Por ejemplo:

```aspx-csharp
<asp:Button ID="btn1" runat="server" onclick="btn1_Click" Text="<%$Resources:Resource1,String7%>"></asp:Button>
```

 Para ASPX como texto, use una expresión con el siguiente formato:

```aspx-csharp
<asp:literal ID="<ID>" runat="server" Text="<%$Resources:<Resource File Name>, <String ID>%>" />
```

 Por ejemplo:

```aspx-csharp
<asp:literal ID="Literal1" runat="server" Text="<%$Resources:Resource1, String9%>" />
```

 Para obtener más información, vea [Cómo: localizar el marcado aspx](../sharepoint/how-to-localize-aspx-markup.md).

### <a name="localize-code"></a>Localizar código
 Además de localizar cadenas de características y [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] marcado, también tiene que localizar las cadenas de mensajes y las cadenas de error que aparecen en el código de la solución. Los mensajes informativos y de error localizados se encuentran en ensamblados satélite. Los ensamblados satélite contienen cadenas que son visibles para los usuarios, como [!INCLUDE[TLA2#tla_ui](../sharepoint/includes/tla2sharptla-ui-md.md)] mensajes de texto y de salida, como las excepciones.

 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] usa el modelo estándar de concentrador y radio de .NET Framework. El concentrador, o ensamblado del programa principal, contiene los recursos de idioma predeterminados. Los radios, o ensamblados satélite, contienen los recursos específicos del lenguaje. Para obtener más información, vea [Packaging and Deploying Resources](/previous-versions/dotnet/netframework-4.0/sb6a8618(v=vs.100)) (Empaquetar e implementar recursos). Los ensamblados satélite se compilan a partir de archivos de recursos ( *. resx*). Al agregar archivos de recursos específicos del lenguaje al proyecto y al paquete de solución, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] compila los archivos de recursos en ensamblados satélite denominados *{nombre del proyecto}. Resources. dll*.

 Como con el marcado ASPX, localizar el código de aplicación de SharePoint agregando elementos de proyecto de archivo de recursos independientes al proyecto; uno para el idioma predeterminado y otro para cada idioma localizado. Sin embargo, como se mencionó anteriormente, si ya tiene archivos de recursos para localizar el marcado ASPX, puede volver a usarlos para localizar el código. Si tiene que crear archivos de recursos, asigne al archivo de recursos de idioma predeterminado el nombre que prefiera anexado con la extensión *. resx* . Asigne a los archivos de recursos localizados el mismo nombre anexado a la referencia cultural específica del idioma [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)]. Establezca la propiedad acción de compilación de cada archivo de recursos en recurso incrustado para habilitar la creación de ensamblados de recursos satélite.

 Para crear los ensamblados satélite, compile el proyecto y, a continuación, agregue los archivos como ensamblados adicionales a través de la pestaña **Opciones avanzadas** del **Diseñador de paquetes**. Al agregar los ensamblados, anteponga una referencia cultural [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)] carpeta a la ruta de acceso de ubicación, como, por ejemplo, *de-de\\{nombre del elemento de proyecto}. Resources. dll*. Esto permite que el paquete contenga archivos con el mismo nombre.

 En el código, reemplace las cadenas codificadas de forma rígida por llamadas al método <xref:System.Web.HttpContext.GetGlobalResourceObject%2A> con la siguiente sintaxis:

```aspx-csharp
HttpContext.GetGlobalResourceObject("<Resource File Name>", "<String ID>")
```

 Para obtener más información, consulte [How to: Localize Code](../sharepoint/how-to-localize-code.md).

#### <a name="web-part-code-localization"></a>Localización del código del elemento Web
 Los elementos Web incluyen una característica del editor de propiedades personalizadas que incluye atributos de código que usan cadenas codificadas de forma rígida, como WebDisplayName, Category y Description. Para reemplazar los valores de cadena de estos atributos, cree una clase independiente que derive de la clase del atributo. En esas clases, establezca la propiedad del atributo. La propiedad del atributo depende de la clase base. Por ejemplo, la propiedad de atributo WebDisplayName es DisplayNameValue y la propiedad de atributo Description es DescriptionValue.

 En la clase derivada, haga referencia al identificador de cadena del archivo de recursos y al objeto ResourceManager para obtener el valor localizado del identificador de cadena. Devuelva este valor al atributo Editor de propiedades.

## <a name="see-also"></a>Vea también
- [Cómo: localizar una característica](../sharepoint/how-to-localize-a-feature.md)
- [Cómo: localizar el marcado ASPX](../sharepoint/how-to-localize-aspx-markup.md)
- [Cómo: localizar código](../sharepoint/how-to-localize-code.md)
- [Cómo: agregar un archivo de recursos](../sharepoint/how-to-add-a-resource-file.md)
- [Cómo: usar un archivo de recursos para especificar nombres, propiedades y permisos localizados](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)
