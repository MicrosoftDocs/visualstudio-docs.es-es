---
title: "Adaptar el c&#243;digo heredado en el Editor | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "editores [Visual Studio SDK] heredados - adaptadores"
ms.assetid: a208d38e-9bea-41c9-9fe2-38bd86a359cb
caps.latest.revision: 25
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 25
---
# Adaptar el c&#243;digo heredado en el Editor
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

El editor de Visual Studio tiene muchas características que puede acceder desde los componentes de código existentes. Las instrucciones siguientes muestran cómo adaptar un componente MEF no, por ejemplo, un VSPackage, para utilizar la funcionalidad del editor. Las instrucciones también muestran cómo usar los adaptadores para obtener los servicios del editor de código administrado y no administrado.  
  
## Adaptadores de editor  
 Adaptadores de editor o correcciones de compatibilidad, son contenedores de objetos del editor que también se exponen las clases e interfaces en el <xref:Microsoft.VisualStudio.TextManager.Interop> API. Puede usar los adaptadores para desplazarse entre los servicios no editor, por ejemplo, los comandos de shell de Visual Studio y editor de servicios. \(Esto es cómo el editor se hospeda actualmente en Visual Studio\). Adaptadores también habilitar heredado editor y el lenguaje de las extensiones de servicio funcione correctamente en Visual Studio.  
  
## Uso de adaptadores de Editor  
 El <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> proporciona métodos que cambiar entre las nuevas interfaces de editor y las interfaces heredadas y también los métodos que crean adaptadores.  
  
 Si utiliza este servicio en un componente MEF, puede importar el servicio como sigue.  
  
```  
[Import(typeof(IVsEditorAdaptersFactoryService))]  
internal IVsEditorAdaptersFactoryService editorFactory;  
```  
  
 Si desea utilizar este servicio en un componente MEF no, siga las instrucciones en la sección "Usando Visual Studio Editor en un MEF no componente de servicios" más adelante en este tema.  
  
## Cambiar entre la nueva API de Editor y la API heredada  
 Utilice los siguientes métodos para pasar un objeto de editor y una interfaz heredada.  
  
|Método|Conversión|  
|------------|----------------|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetBufferAdapter%2A>|Convierte un <xref:Microsoft.VisualStudio.Text.ITextBuffer> para un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetDataBuffer%2A>|Convierte un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> para un <xref:Microsoft.VisualStudio.Text.ITextBuffer>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetDocumentBuffer%2A>|Convierte un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> para un <xref:Microsoft.VisualStudio.Text.ITextBuffer>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetViewAdapter%2A>|Convierte un <xref:Microsoft.VisualStudio.Text.Editor.ITextView> para un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetWpfTextView%2A>|Convierte un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> para un <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView>.|  
  
## Creación de adaptadores  
 Utilice los métodos siguientes para crear adaptadores para las interfaces heredadas.  
  
|Método|Conversión|  
|------------|----------------|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsCodeWindowAdapter%2A>|Crea una interfaz <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextBufferAdapter%2A>|Crea un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> para un elemento <xref:Microsoft.VisualStudio.Utilities.IContentType>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextBufferAdapter%2A>|Crea una interfaz <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextBufferCoordinatorAdapter%2A>|Crea una interfaz <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextViewAdapter%2A>|Crea un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> para un <xref:Microsoft.VisualStudio.Text.Editor.ITextViewRoleSet>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextViewAdapter%2A>|Crea una interfaz <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>.|  
  
## Creación de adaptadores en código no administrado  
 Todas las clases de adaptadores se registran para ser local puede crear conjuntamente y se pueden crear instancias mediante el uso de la `VsLocalCreateInstance()` \(función\).  
  
 Todos los adaptadores se crean mediante el GUID que están definidos en el archivo vsshlids.h en el... Carpeta \\VisualStudioIntegration\\Common\\Inc\\ de la instalación del SDK de Visual Studio. Para crear una instancia de VsTextBufferAdapter, utilice el código siguiente.  
  
```  
IVsTextBuffer *pBuf = NULL;  
VsLocalCreateInstance(CLSID_VsTextBuffer, NULL, CLSCTX_INPROC_SERVER, IID_IVsTextBuffer, (void**)&pBuf);  
```  
  
## Creación de adaptadores en código administrado  
 En código administrado, puede crear comparte los adaptadores de la misma manera que la descrita para código no administrado. También puede utilizar un servicio MEF que permite crear e interactuar con los adaptadores. Esta forma de obtener un adaptador permite un control más fino que tendrá cuando creas conjuntamente.  
  
#### Para crear un adaptador de IVsTextView  
  
1.  Agregue una referencia a Microsoft.VisualStudio.Editor.dll. Asegúrese de que `CopyLocal` está establecido en `false`.  
  
2.  Crear una instancia de la <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>, como sigue.  
  
    ```  
    using Microsoft.VisualStudio.Editor;  
    ...  
    IVsEditorAdaptersFactoryService adapterFactoryService = ComponentModel.GetService<IVsEditorAdaptersFactoryService>();  
    ```  
  
3.  Llame al método `CreateX()`.  
  
    ```  
    adapterFactoryService.CreateTextViewAdapter(textView);  
    ```  
  
## Con el Editor de Visual Studio directamente desde el código no administrado  
 Los espacios de nombres Microsoft.VisualStudio.Platform.VSEditor y Microsoft.VisualStudio.Platform.VSEditor.Interop exponen interfaces COM invocables como interfaces de IVx. Por ejemplo, la interfaz Microsoft.VisualStudio.Platform.VSEditor.Interop.IVxTextBuffer es la versión COM de la <xref:Microsoft.VisualStudio.Text.ITextBuffer> interfaz. Desde el `IVxTextBuffer`, puede obtener acceso a las instantáneas de búfer, modifican el búfer, escuchar eventos de cambio de texto en el búfer y crear puntos de seguimiento y los intervalos. Los pasos siguientes muestran cómo tener acceso a un `IVxTextBuffer` de un `IVsTextBuffer`.  
  
#### Para obtener un objeto IVxTextBuffer  
  
1.  Las definiciones de las interfaces de IVx \* están en el archivo VSEditor.h en el... Carpeta \\VisualStudioIntegration\\Common\\Inc\\ de la instalación del SDK de Visual Studio.  
  
2.  El código siguiente crea una instancia de un búfer de texto utilizando la `IVsUserData->GetData()` \(método\). En el código siguiente, `pData` es un puntero a un `IVsUserData` objeto.  
  
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
  
## Con servicios de Editor de Visual Studio en un componente MEF no  
 Si tiene un componente de código administrado existente que no use MEF y desea usar los servicios del editor de Visual Studio, debe agregar una referencia al ensamblado que contiene el ComponentModelHost VSPackage y obtener su servicio SComponentModel.  
  
#### Utilizar componentes de editor de Visual Studio desde un componente MEF no  
  
1.  Agregue una referencia al ensamblado Microsoft.VisualStudio.ComponentModelHost.dll en el... Carpeta \\Common7\\IDE\\ de la instalación de Visual Studio. Asegúrese de que `CopyLocal` está establecido en `false`.  
  
2.  Agregar una privada `IComponentModel` miembro a la clase en la que desea usar servicios del editor de Visual Studio, como se indica a continuación.  
  
    ```  
    using Microsoft.VisualStudio.ComponentModelHost;  
    ....  
    private IComponentModel componentModel;  
    ```  
  
3.  Crear instancias del modelo de componente en el método de inicialización del componente.  
  
    ```  
    componentModel =  
     (IComponentModel)Package.GetGlobalService(typeof(SComponentModel));  
    ```  
  
4.  Después de esto, puede obtener uno de los servicios del editor de Visual Studio mediante una llamada a la `IComponentModel.GetService<T>()` método para el servicio que desee.  
  
    ```  
    textBufferFactoryService =  
         componentModel.GetService<ITextBufferFactoryService>();     
    ```