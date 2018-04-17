---
title: Adaptar el código heredado al Editor | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - adapters
ms.assetid: a208d38e-9bea-41c9-9fe2-38bd86a359cb
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2e90a0f8ba27199e3837c59cd7980f027d0485a8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="adapting-legacy-code-to-the-editor"></a>Adaptar el código heredado en el Editor
El editor de Visual Studio tiene muchas características que se pueden acceder desde los componentes de código existentes. Las instrucciones siguientes muestran cómo adaptar un componente MEF no, por ejemplo, un VSPackage, para utilizar la funcionalidad del editor. Las instrucciones también muestran cómo utilizar los adaptadores para obtener los servicios del editor de código no administrado y no administrado.  
  
## <a name="editor-adapters"></a>Adaptadores de editor  
 Adaptadores de editor o correcciones de compatibilidad, son contenedores para objetos de editor que también se muestran las clases e interfaces en el <xref:Microsoft.VisualStudio.TextManager.Interop> API. Puede usar los adaptadores que se va a mover entre los servicios no sean del editor, por ejemplo, comandos de shell de Visual Studio y servicios del editor. (Esto es cómo el editor actualmente se hospeda en Visual Studio). Adaptadores también habilitar extensiones de servicio heredadas de editor y el idioma para que funcione correctamente en Visual Studio.  
  
## <a name="using-editor-adapters"></a>Uso de adaptadores de Editor  
 El <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> proporciona métodos que cambian entre las nuevas interfaces de editor y las interfaces heredadas y también hay métodos que crean adaptadores.  
  
 Si está utilizando este servicio en un componente MEF, puede importar el servicio como se indica a continuación.  
  
```  
[Import(typeof(IVsEditorAdaptersFactoryService))]  
internal IVsEditorAdaptersFactoryService editorFactory;  
```  
  
 Si desea utilizar este servicio en un componente MEF no, siga las instrucciones que aparecen en la sección "Usando Visual Studio Editor servicios en una no-componente MEF" más adelante en este tema.  
  
## <a name="switching-between-the-new-editor-api-and-the-legacy-api"></a>Cambiar entre la nueva API de Editor y la API heredado  
 Utilice los métodos siguientes para cambiar entre un objeto de editor y una interfaz heredada.  
  
|Método|Conversión|  
|------------|----------------|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetBufferAdapter%2A>|Convierte una interfaz <xref:Microsoft.VisualStudio.Text.ITextBuffer> en <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetDataBuffer%2A>|Convierte una interfaz <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> en <xref:Microsoft.VisualStudio.Text.ITextBuffer>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetDocumentBuffer%2A>|Convierte una interfaz <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> en <xref:Microsoft.VisualStudio.Text.ITextBuffer>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetViewAdapter%2A>|Convierte una interfaz <xref:Microsoft.VisualStudio.Text.Editor.ITextView> en <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetWpfTextView%2A>|Convierte una interfaz <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> en <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView>.|  
  
## <a name="creating-adapters"></a>Creación de adaptadores  
 Utilice los métodos siguientes para crear adaptadores para las interfaces heredadas.  
  
|Método|Conversión|  
|------------|----------------|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsCodeWindowAdapter%2A>|Crea una interfaz <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextBufferAdapter%2A>|Crea un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> para un determinado <xref:Microsoft.VisualStudio.Utilities.IContentType>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextBufferAdapter%2A>|Crea una interfaz <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextBufferCoordinatorAdapter%2A>|Crea una interfaz <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextViewAdapter%2A>|Crea un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> para un <xref:Microsoft.VisualStudio.Text.Editor.ITextViewRoleSet>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextViewAdapter%2A>|Crea una interfaz <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>.|  
  
## <a name="creating-adapters-in-unmanaged-code"></a>Creación de adaptadores en código no administrado  
 Todas las clases de adaptador están registradas para ser local puede co-crear y se pueden crear instancias mediante el uso de la `VsLocalCreateInstance()` (función).  
  
 Todos los adaptadores se crean mediante el GUID que están definidos en el archivo vsshlids.h en los... Carpeta \VisualStudioIntegration\Common\Inc\ de la instalación del SDK de Visual Studio. Para crear una instancia de VsTextBufferAdapter, utilice el código siguiente.  
  
```  
IVsTextBuffer *pBuf = NULL;  
VsLocalCreateInstance(CLSID_VsTextBuffer, NULL, CLSCTX_INPROC_SERVER, IID_IVsTextBuffer, (void**)&pBuf);  
```  
  
## <a name="creating-adapters-in-managed-code"></a>Creación de adaptadores en código administrado  
 En código administrado, puede crear comparte los adaptadores de la misma manera que se ha descrito para código no administrado. También puede utilizar un servicio MEF que le permite crear e interactuar con los adaptadores. Esta manera de obtener un adaptador permite un control más minucioso de tener cuando creas conjuntamente.  
  
#### <a name="to-create-an-adapter-for-ivstextview"></a>Para crear un adaptador de IVsTextView  
  
1.  Agregue una referencia a Microsoft.VisualStudio.Editor.dll. Asegúrese de que `CopyLocal` está establecido en `false`.  
  
2.  Crear una instancia de la <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>, como se indica a continuación.  
  
    ```  
    using Microsoft.VisualStudio.Editor;  
    ...  
    IVsEditorAdaptersFactoryService adapterFactoryService = ComponentModel.GetService<IVsEditorAdaptersFactoryService>();  
    ```  
  
3.  Llame al método `CreateX()`.  
  
    ```  
    adapterFactoryService.CreateTextViewAdapter(textView);  
    ```  
  
## <a name="using-the-visual-studio-editor-directly-from-unmanaged-code"></a>Con el Editor de Visual Studio directamente desde el código no administrado  
 El espacio de nombres Microsoft.VisualStudio.Platform.VSEditor y el espacio de nombres Microsoft.VisualStudio.Platform.VSEditor.Interop exponen interfaces COM invocables como interfaces de IVx. Por ejemplo, la interfaz Microsoft.VisualStudio.Platform.VSEditor.Interop.IVxTextBuffer es la versión de COM de la <xref:Microsoft.VisualStudio.Text.ITextBuffer> interfaz. Desde el `IVxTextBuffer`, puede obtener acceso a las instantáneas de búfer, modificar el búfer, realizar escuchas de eventos de cambio de texto en el búfer y crear puntos de seguimiento y los intervalos. Los pasos siguientes muestran cómo obtener acceso a un `IVxTextBuffer` desde un `IVsTextBuffer`.  
  
#### <a name="to-get-an-ivxtextbuffer"></a>Para obtener un objeto IVxTextBuffer  
  
1.  Las definiciones de las interfaces de IVx * están en el archivo VSEditor.h en los... Carpeta \VisualStudioIntegration\Common\Inc\ de la instalación del SDK de Visual Studio.  
  
2.  El código siguiente crea una instancia de un búfer de texto usando el `IVsUserData->GetData()` método. En el código siguiente, `pData` es un puntero a un `IVsUserData` objeto.  
  
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
  
## <a name="using-visual-studio-editor-services-in-a-non-mef-component"></a>Con servicios de Editor de Visual Studio en un componente MEF no  
 Si tiene un componente de código administrado existente que no usa MEF y desea usar los servicios del editor de Visual Studio, debe agregar una referencia al ensamblado que contiene el ComponentModelHost VSPackage y obtener su servicio SComponentModel.  
  
#### <a name="to-consume-visual-studio-editor-components-from-a-non-mef-component"></a>Utilizar componentes de editor de Visual Studio desde un componente MEF no  
  
1.  Agregue una referencia al ensamblado Microsoft.VisualStudio.ComponentModelHost.dll en los... Carpeta \Common7\IDE\ de la instalación de Visual Studio. Asegúrese de que `CopyLocal` está establecido en `false`.  
  
2.  Agregar una privada `IComponentModel` miembro a la clase en la que desea usar servicios de editor de Visual Studio, como se indica a continuación.  
  
    ```  
    using Microsoft.VisualStudio.ComponentModelHost;  
    ....  
    private IComponentModel componentModel;  
    ```  
  
3.  Crear instancias del modelo de componente en el método de inicialización para el componente.  
  
    ```  
    componentModel =  
     (IComponentModel)Package.GetGlobalService(typeof(SComponentModel));  
    ```  
  
4.  Después de esto, puede obtener uno de los servicios del editor de Visual Studio mediante una llamada a la `IComponentModel.GetService<T>()` método para el servicio que desee.  
  
    ```  
    textBufferFactoryService =  
         componentModel.GetService<ITextBufferFactoryService>();     
    ```