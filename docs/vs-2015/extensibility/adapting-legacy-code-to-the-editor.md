---
title: Adaptación del código heredado al editor | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - adapters
ms.assetid: a208d38e-9bea-41c9-9fe2-38bd86a359cb
caps.latest.revision: 26
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0bb90723a72c10dbf6cfda5edd4aa68f71f1c6b9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184914"
---
# <a name="adapting-legacy-code-to-the-editor"></a>Adaptación del código heredado al editor
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

El editor de Visual Studio tiene muchas características a las que puede tener acceso desde componentes de código existentes. Las instrucciones siguientes muestran cómo adaptar un componente que no sea MEF, por ejemplo, un VSPackage, para consumir la funcionalidad del editor. Las instrucciones también muestran cómo usar los adaptadores para obtener los servicios del editor en código administrado y no administrado.  
  
## <a name="editor-adapters"></a>Adaptadores de editor  
 Los adaptadores de editor o las correcciones de compatibilidad (shim) son contenedores para objetos de editor que también exponen las clases e interfaces de la <xref:Microsoft.VisualStudio.TextManager.Interop> API. Puede usar los adaptadores para moverse entre servicios que no son de editor, por ejemplo, comandos de Visual Studio Shell y servicios de editor. (Este es el modo en que el editor se hospeda actualmente en Visual Studio). Los adaptadores también habilitan el editor heredado y las extensiones del servicio de lenguaje para que funcionen correctamente en Visual Studio.  
  
## <a name="using-editor-adapters"></a>Usar adaptadores de editor  
 <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>Proporciona métodos que intercambian entre las nuevas interfaces del editor y las interfaces heredadas, y también los métodos que crean adaptadores.  
  
 Si usa este servicio en una parte del componente de MEF, puede importar el servicio como se indica a continuación.  
  
```  
[Import(typeof(IVsEditorAdaptersFactoryService))]  
internal IVsEditorAdaptersFactoryService editorFactory;  
```  
  
 Si desea usar este servicio en un componente que no sea MEF, siga las instrucciones de la sección "uso de los servicios del editor de Visual Studio en un componente que no sea MEF" más adelante en este tema.  
  
## <a name="switching-between-the-new-editor-api-and-the-legacy-api"></a>Cambiar entre la nueva API del editor y la API heredada  
 Use los métodos siguientes para cambiar entre un objeto de editor y una interfaz heredada.  
  
|Método|Conversión|  
|------------|----------------|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetBufferAdapter%2A>|Convierte una interfaz <xref:Microsoft.VisualStudio.Text.ITextBuffer> en <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetDataBuffer%2A>|Convierte una interfaz <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> en <xref:Microsoft.VisualStudio.Text.ITextBuffer>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetDocumentBuffer%2A>|Convierte una interfaz <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> en <xref:Microsoft.VisualStudio.Text.ITextBuffer>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetViewAdapter%2A>|Convierte una interfaz <xref:Microsoft.VisualStudio.Text.Editor.ITextView> en <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetWpfTextView%2A>|Convierte una interfaz <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> en <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView>.|  
  
## <a name="creating-adapters"></a>Crear adaptadores  
 Use los métodos siguientes para crear adaptadores para interfaces heredadas.  
  
|Método|Conversión|  
|------------|----------------|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsCodeWindowAdapter%2A>|Crea una interfaz <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextBufferAdapter%2A>|Crea un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> para un especificado <xref:Microsoft.VisualStudio.Utilities.IContentType> .|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextBufferAdapter%2A>|Crea una interfaz <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextBufferCoordinatorAdapter%2A>|Crea una interfaz <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextViewAdapter%2A>|Crea un objeto <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> para <xref:Microsoft.VisualStudio.Text.Editor.ITextViewRoleSet>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextViewAdapter%2A>|Crea una interfaz <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>.|  
  
## <a name="creating-adapters-in-unmanaged-code"></a>Crear adaptadores en código no administrado  
 Todas las clases de adaptador se registran para ser coexistentes locales y se pueden crear instancias de ellas mediante la `VsLocalCreateInstance()` función.  
  
 Todos los adaptadores se crean mediante los GUID que se definen en el archivo vsshlids. h en. Carpeta \VisualStudioIntegration\Common\Inc\ de la instalación del SDK de Visual Studio. Para crear una instancia de VsTextBufferAdapter, use el código siguiente.  
  
```  
IVsTextBuffer *pBuf = NULL;  
VsLocalCreateInstance(CLSID_VsTextBuffer, NULL, CLSCTX_INPROC_SERVER, IID_IVsTextBuffer, (void**)&pBuf);  
```  
  
## <a name="creating-adapters-in-managed-code"></a>Crear adaptadores en código administrado  
 En código administrado, puede crear coautoría de los adaptadores de la misma manera que se describe en el código no administrado. También puede usar un servicio de MEF que le permita crear y interactuar con adaptadores. Esta manera de obtener un adaptador permite un control más específico de lo que tiene al crearlo de forma conjunta.  
  
#### <a name="to-create-an-adapter-for-ivstextview"></a>Para crear un adaptador para IVsTextView  
  
1. Agregue una referencia a Microsoft.VisualStudio.Editor.dll. Asegúrese de que `CopyLocal` está establecido en `false`.  
  
2. Cree una instancia de <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> , como se indica a continuación.  
  
    ```  
    using Microsoft.VisualStudio.Editor;  
    ...  
    IVsEditorAdaptersFactoryService adapterFactoryService = ComponentModel.GetService<IVsEditorAdaptersFactoryService>();  
    ```  
  
3. Llame al método `CreateX()` .  
  
    ```  
    adapterFactoryService.CreateTextViewAdapter(textView);  
    ```  
  
## <a name="using-the-visual-studio-editor-directly-from-unmanaged-code"></a>Usar el editor de Visual Studio directamente desde el código no administrado  
 El espacio de nombres Microsoft. VisualStudio. Platform. VSEditor y el espacio de nombres Microsoft. VisualStudio. Platform. VSEditor. Interop exponen interfaces COM Invocables como interfaces IVx *. Por ejemplo, la interfaz Microsoft. VisualStudio. Platform. VSEditor. Interop. IVxTextBuffer es la versión COM de la <xref:Microsoft.VisualStudio.Text.ITextBuffer> interfaz. En `IVxTextBuffer` , puede obtener acceso a las instantáneas de búfer, modificar el búfer, escuchar los eventos de cambio de texto en el búfer y crear puntos de seguimiento y intervalos. En los pasos siguientes se muestra cómo obtener acceso a `IVxTextBuffer` desde un `IVsTextBuffer` .  
  
#### <a name="to-get-an-ivxtextbuffer"></a>Para obtener una IVxTextBuffer  
  
1. Las definiciones de las interfaces IVx * se encuentran en el archivo VSEditor. h en. Carpeta \VisualStudioIntegration\Common\Inc\ de la instalación del SDK de Visual Studio.  
  
2. El código siguiente crea una instancia de un búfer de texto mediante el `IVsUserData->GetData()` método. En el código siguiente, `pData` es un puntero a un `IVsUserData` objeto.  
  
    ```  
    #include <textmgr.h>  
    #include <VSEditor.h>  
    #include <vsshlids.h>  
  
    CComPtr<IVsTextBuffer> pVsTextBuffer;  
    CComPtr<IVsUserData> pData;  
    CComPtr<IVxTextBuffer> pVxBuffer;  
    ...  
    if (SUCCEEDED(pVsTextBuffer->QueryInterface(IID_IVsUserData, &pData))  
    {  
        CComVariant vt;  
        if (SUCCEEDED(pData->GetData(GUID_VxTextBuffer, &vt)) &&  
        (vt.Type == VT_UNKNOWN) && (vt.punkVal != NULL))  
        {  
            vt.punkVal->QueryInterface(IID_IVxTextBuffer, (void**)&pVxBuffer);  
        }  
    }  
    ```  
  
## <a name="using-visual-studio-editor-services-in-a-non-mef-component"></a>Usar los servicios de editor de Visual Studio en un componente que no sea MEF  
 Si tiene un componente de código administrado existente que no usa MEF y desea utilizar los servicios del editor de Visual Studio, debe agregar una referencia al ensamblado que contiene el VSPackage ComponentModelHost y obtener su servicio SComponentModel.  
  
#### <a name="to-consume-visual-studio-editor-components-from-a-non-mef-component"></a>Para consumir componentes del editor de Visual Studio desde un componente que no sea MEF  
  
1. Agregue una referencia al ensamblado Microsoft.VisualStudio.ComponentModelHost.dll en. Carpeta \Common7\IDE\ de la instalación de Visual Studio. Asegúrese de que `CopyLocal` está establecido en `false`.  
  
2. Agregue un `IComponentModel` miembro privado a la clase en la que desea utilizar los servicios de editor de Visual Studio, como se indica a continuación.  
  
    ```  
    using Microsoft.VisualStudio.ComponentModelHost;  
    ....  
    private IComponentModel componentModel;  
    ```  
  
3. Cree una instancia del modelo de componentes en el método de inicialización del componente.  
  
    ```  
    componentModel =  
     (IComponentModel)Package.GetGlobalService(typeof(SComponentModel));  
    ```  
  
4. Después, puede obtener cualquiera de los servicios del editor de Visual Studio llamando al método del `IComponentModel.GetService<T>()` servicio que desee.  
  
    ```  
    textBufferFactoryService =  
         componentModel.GetService<ITextBufferFactoryService>();     
    ```
