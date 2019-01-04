---
title: Procedimiento Localizar el marcado ASPX | Documentos de Microsoft
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- localizing XML [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, localizing
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 0a646c84df5f6da318e8c21f6a55ac7a852a1af0
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53959878"
---
# <a name="how-to-localize-aspx-markup"></a>Procedimiento Localizar el marcado ASPX
  [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] páginas (.aspx) suelen usan los valores de cadena codificados de forma rígida. Para localizar estas cadenas, reemplácelas por expresiones que hacen referencia a los recursos localizados.  
  
## <a name="localize-aspx-markup"></a>Localizar el marcado ASPX  
  
#### <a name="to-localize-aspx-markup"></a>Para localizar el marcado ASPX  
  
1.  Agregar archivos de recursos independientes: uno para el idioma predeterminado y otro para cada idioma localizado.  
  
     Si va a adaptar solo marcado y no código, agregue un elemento de proyecto del archivo de recursos globales. Si va a adaptar el código y marcado, agregue un elemento de proyecto del archivo de recursos.  
  
    1.  Para agregar un archivo de recursos globales en **el Explorador de soluciones**, abra el menú contextual de un elemento de proyecto de SharePoint y, a continuación, elija **agregar** > **nuevo elemento**. En el SharePoint **2010** nodo, elija el **archivo de recursos globales** plantilla.  
  
    2.  Para agregar un archivo de recursos de **el Explorador de soluciones**, abra el menú contextual de un elemento de proyecto de SharePoint y, a continuación, elija **agregar** > **nuevo elemento**. Bajo el **Visual Basic** o **Visual C#** nodo, elija el **archivo de recursos** plantilla.  
  
    > [!NOTE]  
    >  No olvide agregar los archivos de recursos a un elemento de proyecto de SharePoint para habilitar la propiedad de tipo de implementación. Esta propiedad es necesaria más adelante en este procedimiento. Si la solución no tiene un elemento de proyecto de SharePoint, puede agregar un proyecto de SharePoint vacío y su valor predeterminado de quitar *Elements.xml* archivo.  
  
2.  Asigne el archivo de recursos de idioma predeterminado un nombre de su elección y anéxelo con un *.resx* extensión, por ejemplo, MyAppResources.resx. Use el mismo nombre base para cada archivo de recursos localizado, pero agregue la referencia cultural [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)]. Por ejemplo, de recursos localizado en alemán nombre *MyAppResources.de-DE.resx*.  
  
3.  Cambie el valor de la **tipo de implementación** propiedad de cada archivo de recursos para **AppGlobalResource** hacer que implemente en la carpeta App_GlobalResources del servidor.  
  
4.  Si usa los recursos para localizar código además del marcado ASPX, deje el valor de la **acción de compilación** propiedad de cada archivo como **recurso incrustado**. Si está usando los archivos de recursos para localizar el marcado, también puede cambiar el valor de propiedad de los archivos para **contenido**. Para obtener más información, consulte [soluciones de SharePoint localizar](../sharepoint/localizing-sharepoint-solutions.md).  
  
5.  Abra cada archivo de recursos y agregue las cadenas localizadas, utilizando los mismos identificadores de cadena en cada archivo.  
  
6.  En el [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] marcado de la página ASPX o control, reemplace las cadenas codificadas de forma rígida con los valores que utilizan el formato siguiente:  
  
    ```aspx-csharp  
    <%$Resources:Resource File Name, String ID%>  
    ```  
  
     Por ejemplo, para localizar el texto de un control de etiqueta en una página de aplicación, cambie:  
  
    ```aspx-csharp  
    <asp:Content ID="Main" ContentPlaceHolderID="PlaceHolderMain" runat="server">  
    <asp:Label ID="lbl" runat="server" Text="Label text"></asp:Label>  
    </asp:Content>  
    ```  
  
     por  
  
    ```aspx-csharp  
    <asp:Content ID="Main" ContentPlaceHolderID="PlaceHolderMain" runat="server">  
    <asp:Label ID="lbl" runat="server" Text="<%$Resources:MyAppResources,String1%>"></asp:Label>  
    </asp:Content>  
    ```  
  
7.  Elija la **F5** clave para compilar y ejecutar la aplicación.  
  
8.  En SharePoint, cambie el idioma de presentación predeterminado.  
  
     Las cadenas localizadas aparecen en la aplicación. Para mostrar los recursos localizados, el servidor de SharePoint debe tener instalado el paquete de idioma que coincide con la referencia cultural del archivo de recursos.  
  
## <a name="see-also"></a>Vea también
 [Localizar soluciones de SharePoint](../sharepoint/localizing-sharepoint-solutions.md)   
 [Cómo: Localizar una característica](../sharepoint/how-to-localize-a-feature.md)   
 [Cómo: Agregar un archivo de recursos](../sharepoint/how-to-add-a-resource-file.md)   
 [Cómo: Localizar código](../sharepoint/how-to-localize-code.md)  
