---
title: "C&#243;mo: Proporcionar elementos de Cuadro de herramientas personalizados mediante ensamblados de interoperabilidad | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Cuadro de herramientas [SDK de Visual Studio], agregar elementos mediante ensamblados de interoperabilidad"
ms.assetid: c3e8b404-7086-4e08-9d07-ab9c509963ca
caps.latest.revision: 33
caps.handback.revision: 33
manager: "douge"
---
# C&#243;mo: Proporcionar elementos de Cuadro de herramientas personalizados mediante ensamblados de interoperabilidad
> [!NOTE]
>  La forma recomendada de agregar controles personalizados al cuadro de herramientas es usar las plantillas del control de cuadro de herramientas que vienen con Visual Studio 10 SDK. Este tema se conserva únicamente para fines de compatibilidad con versiones anteriores y para agregar los controles existentes al cuadro de herramientas.  
>   
>  Para obtener más información sobre cómo crear controles de cuadro de herramientas mediante plantillas, consulte [Cómo: Crear un control Toolbox que use formularios Windows Forms](../misc/how-to-create-a-toolbox-control-that-uses-windows-forms.md) y [Crear un Control de cuadro de herramientas WPF](../extensibility/creating-a-wpf-toolbox-control.md).  
  
 Un VSPackage basado en un ensamblado de interoperabilidad puede ampliar la funcionalidad del [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] **cuadro de herramientas** agregando controles ActiveX.  
  
 Para obtener una lista de los formatos estándar de Portapapeles del cuadro de herramientas de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], consulte [Extensión del Cuadro de herramientas](../misc/extending-the-toolbox.md).  
  
 Para obtener información sobre cómo un VSPackage administra el **cuadro de herramientas** mediante [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)], consulte [Administración del cuadro de herramientas](../misc/managing-the-toolbox.md).  
  
 Para más información sobre la administración del **cuadro de herramientas** mediante automatización, vea [Cómo: Controlar el Cuadro de herramientas](../Topic/How%20to:%20Control%20the%20Toolbox.md).  
  
## Procedimientos  
 Los elementos agregados al **cuadro de herramientas** deben implementar los formatos estándar de Portapapeles del **cuadro de herramientas**, a menos que el VSPackage que agrega los elementos actúe como un proveedor de elementos del **cuadro de herramientas** y proporcione soporte de implementación para el nuevo formato.  
  
#### Para implementar el control de cuadro de herramientas  
  
-   Un elemento de **cuadro de herramientas** proporcionado por el VSPackage implementado en código no administrado debe implementar un objeto `IDataObject` o ser un control ActiveX, desde el cual el entorno pueda obtener un objeto `IDataObject`.  
  
     Para obtener más información acerca de cómo implementar el objeto `IDataObject` para admitir el **cuadro de herramientas**, consulte <xref:System.Runtime.InteropServices.ComTypes.IDataObject>, <xref:Microsoft.VisualStudio.Shell.Interop.TBXITEMINFO> y <xref:System.Runtime.InteropServices.ComTypes.FORMATETC>.  
  
#### Para agregar controles basados en ensamblados de interoperabilidad al cuadro de herramientas  
  
1.  Obtenga instancias de:  
  
    1.  <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2>, que admite la adición de controles y secciones \(pestañas\) al **cuadro de herramientas** y el control de otros aspectos de la configuración del **cuadro de herramientas**.  
  
    2.  <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3>, que proporciona compatibilidad para la localización y la conservación de la configuración de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
    > [!NOTE]
    >  La interfaz <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> hereda de la interfaz <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox>.<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3> no se deriva de <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> y no implementa sus métodos.  
  
     <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3> y <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> se obtienen llamando al método <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> en el servicio <xref:Microsoft.VisualStudio.Shell.Interop.SVsToolbox> mediante el identificador de servicio de `SID_SVsToolbox`.  
  
     El identificador de interfaz `IID_IVSToolbox2` se usa para obtener <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2>, mientras que el identificador de interfaz `IID_IVSToolbox3` devuelve <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3>.  
  
     En el ejemplo siguiente, la interfaz <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> se obtiene con un `QueryService` y la interfaz <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3> llamando a `QueryInterface` en la interfaz <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2>.  
  
    ```cpp  
    extern CComModule _Module;  
    CComPtr<IVsToolbox2> srpTbx2;  
    CComPtr<IVsToolbox3> srpTbx3;  
    hr = _Module.QueryService(SID_SVsToolbox, IID_IVsToolbox2, (void**) &srpTbx2));  
    hr = srpTbx2->QueryInterface( IID_IVsToolbox3, (void **)&srpTbx3)  
    ```  
  
2.  Utilice las instancias de las interfaces <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> y <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3> para agregar pestañas \(secciones\) y controles al **cuadro de herramientas**.  
  
     En el ejemplo siguiente, se agrega una nueva pestaña con un nombre localizado mediante el método <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2.AddTab%2A>.  
  
     Dado que este nombre localizado no es invariable, un nombre invariable no localizado \(en este caso `L"HTML"`\) se establece mediante una llamada al método <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3.SetIDOfTab%2A>.  
  
     Si la pestaña del cuadro de herramientas ya existe, `AddTab2` devuelve E\_FAIL, en cuyo caso se supone que la pestaña se agregó correctamente antes de intentar recuperar el nombre invariable.  
  
     Si una pestaña se agregó correctamente, se agrega un control basado en <xref:System.Runtime.InteropServices.ComTypes.IDataObject> al **cuadro de herramientas**; de lo contrario, se devuelve un error.  
  
    ```cpp  
    CComBSTR sbstrID;  
    hr = srpTbx2->AddTab2((WCHAR*)szwDisplayTabName, *pclsidPackage);  
    if ( hr == S_OK) {  
        sbstrID =L"HTML";  
        hr = srpTbx3->SetIDOfTab( (WCHAR*)szwDisplayTabName, sbstrID);  
    }else{  
        hr = S_OK;  
        hr = srpTbx3->GetIDOfTab( (WCHAR*)szwDisplayTabName, &sbstrID );  
  
    }  
    if ( hr = S_OK){  
        hr=srpTbx2->AddItem(tbxItem, &tinfo, bstrLabel);  
    }  
    return hr;  
    ```  
  
 Además de agregarse al propio **cuadro de herramientas**, un VSPackage se puede configurar como un proveedor de datos de **cuadro de herramientas** y usarse para ampliar la compatibilidad de arrastrar y colocar para el IDE de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Esto permite que los formatos arbitrarios de Portapapeles se expongan en el **cuadro de herramientas** y los editores.  
  
#### Para configurar el VSPackage como un proveedor de elementos de cuadro de herramientas  
  
1.  Registre el VSPackage basado en interoperabilidad como un proveedor de elementos de **cuadro de herramientas**.  
  
     Para obtener más información sobre cómo registrar un proveedor de **cuadro de herramientas**, vea [Registrar características de compatibilidad del Cuadro de herramientas](../misc/registering-toolbox-support-features.md).  
  
2.  Regístrelo como compatible con los formatos personalizados de Portapapeles del **cuadro de herramientas**.  
  
     Los controles compatibles con paquetes VSPackage basados en interoperabilidad que admitan controles que no implementan todos los formatos estándar de Portapapeles del **cuadro de herramientas** o que implementan un formato personalizado de Portapapeles del **cuadro de herramientas** deben:  
  
    1.  Registrar los formatos de Portapapeles del cuadro de herramientas que admiten. Para obtener más información, consulta [Registrar características de compatibilidad del Cuadro de herramientas](../misc/registering-toolbox-support-features.md).  
  
    2.  Cree una clase que implemente las interfaces <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxDataProvider> y <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxDataProvider2>.  
  
        > [!NOTE]
        >  Las interfaces <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxDataProvider> y <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxDataProvider2> no se deben implementar interfaces en la misma clase que implementa la interfaz <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>.  
  
    3.  Informe mediante programación al cuadro de herramientas que una implementación específica de las interfaces <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxDataProvider> y <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxDataProvider2> proporciona compatibilidad para los formatos de datos personalizados con cualquiera de los métodos equivalentes: <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxDataProviderRegistry.RegisterDataProvider%2A> o <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox.RegisterDataProvider%2A>.  
  
         La llamada al método <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox.RegisterDataProvider%2A> se suele realizar en la implementación del método <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> o en el método de controlador <xref:Microsoft.VisualStudio.Shell.WindowPane.OnCreate%2A> cuando el VSPackage se activa.  
  
        ```cpp  
        CComPtr<IVsToolboxDataProviderRegistry> pTB;  
        if (SUCCEEDED (hr = pServiceProvider->QueryService(SID_SVsToolboxDataProviderRegistry, IID_IVsToolboxDataProviderRegistry, (PVOID*)&pTB)) && pTB != NULL)  
        {  
            CustToolboxDataProvider* pDP = new CustToolboxDataProvider;  
            if (pDP)  
            {  
                pDP->AddRef();  
                VSCOOKIE dwDPCookie; //UNDONE: pass NULL instead of ptr to the cookie when RegisterDataProvider allows it.  
                pTB->RegisterDataProvider((IVsToolboxDataProvider*)pDP, &dwDPCookie);  
                pDP->Release();  
            }  
            else  
            {  
                hr = E_OUTOFMEMORY;  
            }  
        }  
        ```  
  
 Para obtener una lista de los formatos estándar de Portapapeles del [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] **cuadro de herramientas** , consulte [Extensión del Cuadro de herramientas](../misc/extending-the-toolbox.md).  
  
## Vea también  
 [Extensión del Cuadro de herramientas](../misc/extending-the-toolbox.md)   
 [Tutoriales del cuadro de herramientas](../misc/toolbox-walkthroughs.md)   
 [Registrar características de compatibilidad del Cuadro de herramientas](../misc/registering-toolbox-support-features.md)   
 [Desarrollo avanzado de controles del cuadro de herramientas](../misc/advanced-toolbox-control-development.md)   
 [Administración del cuadro de herramientas](../misc/managing-the-toolbox.md)   
 [Cómo: Controlar el Cuadro de herramientas](../Topic/How%20to:%20Control%20the%20Toolbox.md)