---
title: 'Cómo: localizar el marcado ASPX | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- localizing XML [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, localizing
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 63bd8ee614a78752069002820689a2cc6c0be783
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: es-ES
ms.lasthandoff: 07/06/2020
ms.locfileid: "86016291"
---
# <a name="how-to-localize-aspx-markup"></a>Cómo: localizar el marcado ASPX
  [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)]las páginas de (. aspx) suelen usar valores de cadena codificados de forma rígida. Para localizar estas cadenas, reemplácelas por expresiones que hagan referencia a recursos localizados.

## <a name="localize-aspx-markup"></a>Localizar el marcado ASPX

#### <a name="to-localize-aspx-markup"></a>Para localizar el marcado ASPX

1. Agregue archivos de recursos independientes: uno para el idioma predeterminado y otro para cada idioma localizado.

     Si solo va a localizar el marcado y no el código, agregue un elemento de proyecto archivo de recursos globales. Si va a localizar código y marcado, agregue un elemento de proyecto de archivo de recursos.

    1. Para agregar un archivo de recursos global, en **Explorador de soluciones**, abra el menú contextual de un elemento de proyecto de SharePoint y, a continuación, elija **Agregar**  >  **nuevo elemento**. En el nodo SharePoint **2010** , elija la plantilla **archivo de recursos globales** .

    2. Para agregar un archivo de recursos, en **Explorador de soluciones**, abra el menú contextual de un elemento de proyecto de SharePoint y, a continuación, elija **Agregar**  >  **nuevo elemento**. En el nodo **Visual Basic** o **Visual C#** , elija la plantilla de **archivo de recursos** .

    > [!NOTE]
    > Asegúrese de agregar los archivos de recursos a un elemento de proyecto de SharePoint para habilitar la propiedad tipo de implementación. Esta propiedad es necesaria más adelante en este procedimiento. Si la solución no tiene un elemento de proyecto de SharePoint, puede Agregar un proyecto de SharePoint vacío y quitar su archivo de *Elements.xml* predeterminado.

2. Asigne al archivo de recursos de idioma predeterminado el nombre que prefiera anexado con una extensión *. resx* , como MyAppResources. resx. Use el mismo nombre base para cada archivo de recursos localizado, pero agregue la referencia cultural [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)] . Por ejemplo, asigne un nombre a un recurso localizado en Alemán *MyAppResources.de-de. resx*.

3. Cambie el valor de la propiedad **tipo de implementación** de cada archivo de recursos a **AppGlobalResource** para que se implementen en la carpeta App_GlobalResources del servidor.

4. Si usa los recursos para localizar el código además del marcado ASPX, deje el valor de la propiedad acción de **compilación** de cada archivo como **recurso incrustado**. Si usa los archivos de recursos solo para localizar el marcado, puede cambiar opcionalmente el valor de la propiedad de los archivos a **contenido**. Para obtener más información, vea [localizar soluciones de SharePoint](../sharepoint/localizing-sharepoint-solutions.md).

5. Abra cada archivo de recursos y agregue cadenas localizadas, usando los mismos identificadores de cadena en cada archivo.

6. En el [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] marcado de la página o el control aspx, reemplace las cadenas codificadas de forma rígida por valores que utilicen el formato siguiente:

    ```aspx-csharp
    <%$Resources:Resource File Name, String ID%>
    ```

     Por ejemplo, para localizar el texto de un control etiqueta en una página de aplicación, cambiaría:

    ```aspx-csharp
    <asp:Content ID="Main" ContentPlaceHolderID="PlaceHolderMain" runat="server">
    <asp:Label ID="lbl" runat="server" Text="Label text"></asp:Label>
    </asp:Content>
    ```

     to

    ```aspx-csharp
    <asp:Content ID="Main" ContentPlaceHolderID="PlaceHolderMain" runat="server">
    <asp:Label ID="lbl" runat="server" Text="<%$Resources:MyAppResources,String1%>"></asp:Label>
    </asp:Content>
    ```

7. Elija la tecla **F5** para compilar y ejecutar la aplicación.

8. En SharePoint, cambie el idioma de presentación predeterminado.

     Las cadenas localizadas aparecen en la aplicación. Para mostrar los recursos localizados, el servidor de SharePoint debe tener instalado el paquete de idioma que coincide con la referencia cultural del archivo de recursos.

## <a name="see-also"></a>Consulte también
- [Localizar soluciones de SharePoint](../sharepoint/localizing-sharepoint-solutions.md)
- [Cómo: localizar una característica](../sharepoint/how-to-localize-a-feature.md)
- [Cómo: agregar un archivo de recursos](../sharepoint/how-to-add-a-resource-file.md)
- [Cómo: localizar código](../sharepoint/how-to-localize-code.md)
