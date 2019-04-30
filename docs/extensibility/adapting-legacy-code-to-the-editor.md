---
title: Adaptar código heredado en el Editor | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - adapters
ms.assetid: a208d38e-9bea-41c9-9fe2-38bd86a359cb
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4d0e9bcd9943dafc9dcbe9beb62433a62b55dc8e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62844004"
---
# <a name="adapt-legacy-code-to-the-editor"></a>Adaptar código heredado en el editor
El editor de Visual Studio tiene muchas características que puede acceder desde los componentes de código existente. Las instrucciones siguientes muestran cómo adaptar un componente que no son de MEF, por ejemplo, un VSPackage para consumir la funcionalidad del editor. Las instrucciones también muestran cómo utilizar los adaptadores para obtener los servicios del editor de código administrado y no administrado.

## <a name="editor-adapters"></a>Adaptadores de editor
Adaptadores de editor o correcciones de compatibilidad, son contenedores para los objetos de editor que también se exponen las clases e interfaces en el <xref:Microsoft.VisualStudio.TextManager.Interop> API. Puede usar los adaptadores que se va a mover entre los servicios que no sean del editor, por ejemplo, los comandos de shell de Visual Studio y servicios del editor. (Esto es cómo el editor actualmente se hospeda en Visual Studio). Los adaptadores también permiten extensiones heredadas de servicio de editor y lenguaje funcione correctamente en Visual Studio.

## <a name="use-editor-adapters"></a>Usar adaptadores de editor
El <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> proporciona métodos que cambian entre las nuevas interfaces de editor y las interfaces heredadas y también los métodos que crean los adaptadores.

Si usa este servicio en un elemento de componente MEF, puede importar el servicio como se indica a continuación.

```
[Import(typeof(IVsEditorAdaptersFactoryService))]
internal IVsEditorAdaptersFactoryService editorFactory;
```

Si desea utilizar este servicio en un componente que no son de MEF, siga las instrucciones en la sección "Uso de Editor servicios en una que no son de MEF componente de Visual Studio" más adelante en este tema.

## <a name="switch-between-the-new-editor-api-and-the-legacy-api"></a>Cambiar entre la nueva API de editor y la API heredada
Utilice los métodos siguientes para cambiar entre un objeto de editor y una interfaz heredada.

|Método|Conversión|
|------------|----------------|
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetBufferAdapter%2A>|Convierte una interfaz <xref:Microsoft.VisualStudio.Text.ITextBuffer> en <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>.|
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetDataBuffer%2A>|Convierte una interfaz <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> en <xref:Microsoft.VisualStudio.Text.ITextBuffer>.|
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetDocumentBuffer%2A>|Convierte una interfaz <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> en <xref:Microsoft.VisualStudio.Text.ITextBuffer>.|
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetViewAdapter%2A>|Convierte una interfaz <xref:Microsoft.VisualStudio.Text.Editor.ITextView> en <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>.|
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetWpfTextView%2A>|Convierte una interfaz <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> en <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView>.|

## <a name="create-adapters"></a>Crear adaptadores
Utilice los métodos siguientes para crear adaptadores para las interfaces heredadas.

|Método|Conversión|
|------------|----------------|
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsCodeWindowAdapter%2A>|Crea una interfaz <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>.|
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextBufferAdapter%2A>|Crea un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> para un elemento <xref:Microsoft.VisualStudio.Utilities.IContentType>.|
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextBufferAdapter%2A>|Crea una interfaz <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>.|
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextBufferCoordinatorAdapter%2A>|Crea una interfaz <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator>.|
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextViewAdapter%2A>|Crea un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> para un <xref:Microsoft.VisualStudio.Text.Editor.ITextViewRoleSet>.|
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextViewAdapter%2A>|Crea una interfaz <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>.|

## <a name="creating-adapters-in-unmanaged-code"></a>Creación de adaptadores en código no administrado
Se registran todas las clases de adaptador para que sea local compartida que se pueden crear y se pueden crear instancias mediante el uso de la `VsLocalCreateInstance()` función.

Todos los adaptadores se crean mediante el GUID que se definen en el *vsshlids.h* de archivos en el *\..\VisualStudioIntegration\Common\Inc\\* carpeta del SDK de Visual Studio instalación. Para crear una instancia de VsTextBufferAdapter, use el código siguiente.

```
IVsTextBuffer *pBuf = NULL;
VsLocalCreateInstance(CLSID_VsTextBuffer, NULL, CLSCTX_INPROC_SERVER, IID_IVsTextBuffer, (void**)&pBuf);
```

## <a name="create-adapters-in-managed-code"></a>Crear adaptadores en código administrado
En código administrado, puede crear conjuntamente los adaptadores de la misma manera que se ha descrito para código no administrado. También puede usar un servicio MEF que le permite crear e interactuar con los adaptadores. Esta forma de obtener un adaptador permite un control más minucioso que tiene cuando creas conjuntamente.

### <a name="to-create-an-adapter-for-ivstextview"></a>Para crear un adaptador para IVsTextView

1. Agregue una referencia a *Microsoft.VisualStudio.Editor.dll*. Asegúrese de que `CopyLocal` está establecido en `false`.

2. Crear una instancia de la <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>, como se indica a continuación.

    ```
    using Microsoft.VisualStudio.Editor;
    ...
    IVsEditorAdaptersFactoryService adapterFactoryService = ComponentModel.GetService<IVsEditorAdaptersFactoryService>();
    ```

3. Llame al método `CreateX()`.

    ```
    adapterFactoryService.CreateTextViewAdapter(textView);
    ```

## <a name="use-the-visual-studio-editor-directly-from-unmanaged-code"></a>Usar el editor de Visual Studio directamente desde código no administrado
El espacio de nombres Microsoft.VisualStudio.Platform.VSEditor y el espacio de nombres Microsoft.VisualStudio.Platform.VSEditor.Interop exponen interfaces COM que se puede llamar como interfaces de IVx. Por ejemplo, la interfaz Microsoft.VisualStudio.Platform.VSEditor.Interop.IVxTextBuffer es la versión COM de la <xref:Microsoft.VisualStudio.Text.ITextBuffer> interfaz. Desde el `IVxTextBuffer`, puede obtener acceso a las instantáneas de búfer, modifican el búfer, escuchar eventos de cambio de texto en el búfer y crear puntos de seguimiento y los intervalos. Los pasos siguientes muestran cómo obtener acceso a un `IVxTextBuffer` desde un `IVsTextBuffer`.

### <a name="to-get-an-ivxtextbuffer"></a>Para obtener un IVxTextBuffer

1. Las definiciones para el IVx\* interfaces se encuentran en el *VSEditor.h* de archivos en el *\..\VisualStudioIntegration\Common\Inc\\* carpeta de Visual Studio Instalación del SDK.

2. El código siguiente crea una instancia de un búfer de texto mediante el uso de la `IVsUserData->GetData()` método. En el código siguiente, `pData` es un puntero a un `IVsUserData` objeto.

    ```cpp
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

## <a name="use-visual-studio-editor-services-in-a-non-mef-component"></a>Usar servicios del editor de Visual Studio en un componente que no son de MEF
Si tiene un componente de código administrado existente que no use MEF y desea usar los servicios del editor de Visual Studio, debe agregar una referencia al ensamblado que contiene el ComponentModelHost VSPackage y obtener su servicio de manera que SComponentModel.

### <a name="to-consume-visual-studio-editor-components-from-a-non-mef-component"></a>Para consumir los componentes del editor de Visual Studio desde un componente que no son de MEF

1. Agregue una referencia a la *Microsoft.VisualStudio.ComponentModelHost.dll* ensamblado en el *\..\Common7\IDE\\* carpeta de la instalación de Visual Studio. Asegúrese de que `CopyLocal` está establecido en `false`.

2. Agregar una privada `IComponentModel` miembro a la clase en el que desea usar servicios del editor de Visual Studio, como se indica a continuación.

    ```
    using Microsoft.VisualStudio.ComponentModelHost;
    ....
    private IComponentModel componentModel;
    ```

3. Cree una instancia del modelo del componente en el método de inicialización para el componente.

    ```
    componentModel =
        (IComponentModel)Package.GetGlobalService(typeof(SComponentModel));
    ```

4. Una vez hecho esto, puede obtener uno de los servicios del editor de Visual Studio mediante una llamada a la `IComponentModel.GetService<T>()` método para el servicio que desee.

    ```
    textBufferFactoryService =
        componentModel.GetService<ITextBufferFactoryService>();
    ```
