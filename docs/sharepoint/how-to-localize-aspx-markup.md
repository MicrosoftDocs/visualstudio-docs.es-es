---
title: "Cómo: localizar el marcado ASPX | Documentos de Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- localizing XML [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, localizing
ms.assetid: 9559a1d1-6558-4c24-a51e-c6ee79432778
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 39d72d4807f61adcab1321b6471c2bea31f048a8
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-localize-aspx-markup"></a>Cómo: Localizar el marcado ASPX
  [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)]páginas (.aspx) normalmente usan valores de cadena codificados de forma rígida. Para localizar estas cadenas, reemplácelas por expresiones que hacen referencia a los recursos localizados.  
  
## <a name="localizing-aspx-markup"></a>Localizar el marcado ASPX  
  
#### <a name="to-localize-aspx-markup"></a>Para localizar el marcado ASPX  
  
1.  Agregar archivos de recursos independientes: uno para el idioma predeterminado y otro para cada uno de los idiomas localizados.  
  
     Si va a adaptar solo no es código y marcado, agregue un elemento de proyecto de archivo de recursos globales. Si va a adaptar el código y marcado, agregue un elemento de proyecto de archivo de recursos.  
  
    1.  Para agregar un archivo de recursos globales en **el Explorador de soluciones**, abra el menú contextual de un elemento de proyecto de SharePoint y, a continuación, elija **agregar**, **nuevo elemento**. En el SharePoint **2010** nodo, elija la **archivo de recursos globales** plantilla.  
  
    2.  Para agregar un archivo de recursos en **el Explorador de soluciones**, abra el menú contextual de un elemento de proyecto de SharePoint y, a continuación, elija **agregar**, **nuevo elemento**. Bajo el **Visual Basic** o **Visual C#** nodo, elija la **archivo de recursos** plantilla.  
  
    > [!NOTE]  
    >  Asegúrese de agregar los archivos de recursos a un elemento de proyecto de SharePoint para habilitar la propiedad de tipo de implementación. Esta propiedad es necesaria más adelante en este procedimiento. Si la solución no tiene un elemento de proyecto de SharePoint, puede agregar un proyecto de SharePoint vacío y quitar su archivo Elements.xml de forma predeterminada.  
  
2.  Asigne al archivo de recursos del idioma predeterminado el nombre que desee y agréguele la extensión .resx, por ejemplo, MyAppResources.resx. Use el mismo nombre base para cada archivo de recursos localizado, pero agregue la referencia cultural [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)]. Por ejemplo, el nombre del archivo de recursos localizado en alemán será MyAppResources.de-DE.resx.  
  
3.  Cambie el valor de la **tipo de implementación** propiedad de cada archivo de recursos para **AppGlobalResource** hacer que implemente en la carpeta App_GlobalResources del servidor.  
  
4.  Si está utilizando los recursos para localizar el código además del marcado ASPX, deje el valor de la **acción de compilación** propiedad de cada archivo como **recurso incrustado**. Si está utilizando los archivos de recursos para localizar el marcado, también puede cambiar el valor de propiedad de los archivos para **contenido**. Para obtener más información, consulte [localizar soluciones de SharePoint](../sharepoint/localizing-sharepoint-solutions.md).  
  
5.  Abra cada archivo de recursos y agregue las cadenas localizadas usando los mismos identificadores de cadena en cada archivo.  
  
6.  En el [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] marcado para la página ASPX o un control, reemplace las cadenas codificadas de forma rígida con valores que utilice el formato siguiente:  
  
    ```  
    <%$Resources:Resource File Name, String ID%>  
    ```  
  
     Por ejemplo, para localizar el texto de un control de etiqueta en una página de aplicación, cambie:  
  
    ```  
    <asp:Content ID="Main" ContentPlaceHolderID="PlaceHolderMain" runat="server">  
    <asp:Label ID="lbl" runat="server" Text="Label text"></asp:Label>  
    </asp:Content>  
    ```  
  
     por  
  
    ```  
    <asp:Content ID="Main" ContentPlaceHolderID="PlaceHolderMain" runat="server">  
    <asp:Label ID="lbl" runat="server" Text="<%$Resources:MyAppResources,String1%>"></asp:Label>  
    </asp:Content>  
    ```  
  
7.  Elija la tecla F5 para compilar y ejecutar la aplicación.  
  
8.  En SharePoint, cambie el idioma de presentación predeterminado.  
  
     Las cadenas localizadas aparecen en la aplicación. Para mostrar los recursos localizados, el servidor de SharePoint debe tener instalado el paquete de idioma que coincide con la referencia cultural del archivo de recursos.  
  
## <a name="see-also"></a>Vea también  
 [Localizar soluciones de SharePoint](../sharepoint/localizing-sharepoint-solutions.md)   
 [Cómo: localizar una característica](../sharepoint/how-to-localize-a-feature.md)   
 [Cómo: agregar un archivo de recursos](../sharepoint/how-to-add-a-resource-file.md)   
 [Cómo: Localizar código](../sharepoint/how-to-localize-code.md)  
  
  