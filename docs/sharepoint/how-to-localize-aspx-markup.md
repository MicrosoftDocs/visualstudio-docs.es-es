---
title: "C&#243;mo: Localizar el marcado ASPX | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "localizar XML [desarrollo de SharePoint en Visual Studio]"
  - "desarrollo de SharePoint en Visual Studio, adaptar"
ms.assetid: 9559a1d1-6558-4c24-a51e-c6ee79432778
caps.latest.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 15
---
# C&#243;mo: Localizar el marcado ASPX
  Normalmente, las páginas de [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)]\(.aspx\) usan valores de cadena codificados de forma rígida.  Para localizar estas cadenas, reemplácelas por expresiones que hagan referencia a recursos localizados.  
  
## Localizar el marcado ASPX.  
  
#### Para localizar el marcado ASPX  
  
1.  Agregue archivos de recursos distintos: uno para el idioma predeterminado y otro para cada uno de los idiomas localizados.  
  
     Si solamente esta localizando el marcado y no está localizando el código, agregue un elemento de proyecto del archivo de recursos globales.  Si está localizando el código y el marcado, agregue un elemento de proyecto del archivo de recursos.  
  
    1.  Para agregar un archivo de recursos Global, en **Explorador de soluciones**, abra el menú contextual para un elemento de proyecto de SharePoint y, a continuación **Add**, **Nuevo elemento**.  Bajo el nodo de SharePoint **2010** , elija la plantilla de **Archivo de recursos globales** .  
  
    2.  Para agregar un archivo de recursos, en **Explorador de soluciones**, abra el menú contextual para un elemento de proyecto de SharePoint y, a continuación **Add**, **Nuevo elemento**.  En **Visual Basic** o nodo de **Visual C\#** , elija la plantilla de **Archivo de recursos** .  
  
    > [!NOTE]  
    >  Asegúrese de agregar los archivos de recursos a un elemento de proyecto de SharePoint para habilitar la propiedad Tipo de implementación.  Esta propiedad es necesaria más adelante en este procedimiento.  Si su solución no tiene un elemento de proyecto de SharePoint, puede agregar un proyecto de SharePoint vacío y quitar el archivo Elements.xml predeterminado.  
  
2.  Asigne al archivo de recursos del idioma predeterminado el nombre que desee y agréguele la extensión .resx, por ejemplo, MyAppResources.resx.  Use el mismo nombre base para cada archivo de recursos localizado, pero agregue la referencia cultural [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)].  Por ejemplo, el nombre del archivo de recursos localizado en alemán será MyAppResources.de\-DE.resx.  
  
3.  Cambie el valor de la propiedad de **Tipo de implementación** de cada archivo de recursos a **AppGlobalResource** para hacer para implementar en la carpeta App\_GlobalResources del servidor.  
  
4.  Si está utilizando los recursos para localizar el código además del marcado ASPX, deje el valor de la propiedad de **Acción de compilación** de cada archivo como **Recurso incrustado**.  Si solamente está utilizando los archivos de recursos para localizar el marcado, puede cambiar el valor de propiedad de los archivos a **Content**.  Para obtener más información, vea [Localizar soluciones de SharePoint](../sharepoint/localizing-sharepoint-solutions.md).  
  
5.  Abra cada uno de los archivos de recursos y agregue las cadenas localizadas usando los mismos identificadores de cadena en cada archivo.  
  
6.  En el marcado [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] del control o página ASPX, reemplace las cadenas codificadas de forma rígida por valores que tengan el formato siguiente:  
  
    ```  
    <%$Resources:Resource File Name, String ID%>  
    ```  
  
     Por ejemplo, para localizar el texto de un control de etiqueta de una página de aplicación, deberá cambiar:  
  
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
  
     Las cadenas localizadas aparecen en la aplicación.  Para mostrar los recursos localizados, el servidor de SharePoint debe tener instalado el paquete de idioma que coincide con la referencia cultural del archivo de recursos.  
  
## Vea también  
 [Localizar soluciones de SharePoint](../sharepoint/localizing-sharepoint-solutions.md)   
 [Cómo: Localizar una característica](../sharepoint/how-to-localize-a-feature.md)   
 [Cómo: Agregar un archivo de recursos](../sharepoint/how-to-add-a-resource-file.md)   
 [Cómo: Localizar código](../sharepoint/how-to-localize-code.md)  
  
  