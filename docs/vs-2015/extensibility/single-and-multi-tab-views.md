---
title: Vistas únicas y varias pestañas | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], custom - single and multi-tab views
ms.assetid: e3611704-349f-4323-b03c-f2b0a445d781
caps.latest.revision: 23
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8231581761199be4df9c368494fb27bdc7926c51
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51748996"
---
# <a name="single-and-multi-tab-views"></a>Vistas de una sola pestaña y varias pestañas
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Un editor puede crear diferentes tipos de vistas. Un ejemplo es una ventana del editor de código, el otro es un diseñador de formularios.  
  
 Una vista con múltiples fichas es una vista que tiene varias pestañas. Por ejemplo, el editor HTML tiene dos pestañas en la parte inferior: **diseño** y **origen**, cada una vista lógica. La vista de diseño muestra una página web representada, mientras que la otra muestra el código HTML que incluye la página web.  
  
## <a name="accessing-physical-views"></a>Obtener acceso a vistas físicas  
 Vistas físicas hospedan objetos de vista de documento, que representa una vista de datos en el búfer, por ejemplo, código o un formulario. En consecuencia, cada objeto de vista de documento tiene una vista física (identificado por algo conocido como una cadena de la vista física) y, por lo general una sola vista lógica.  
  
 Sin embargo, en algunos casos, una vista física puede tener dos o más vistas lógicas. Algunos ejemplos son un editor que tenga una ventana dividida con vistas en paralelo o un diseñador de formularios que tiene una vista de diseño de interfaz gráfica de usuario y una vista de código subyacente: el formulario.  
  
 Para habilitar el editor tener acceso a todas las vistas físicas disponibles, debe crear una cadena de la vista física único para cada tipo de objeto de vista de documento que puede crear el generador de editores. Por ejemplo, el [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] generador de editores puede crear documento objetos de vista para una ventana de código y una ventana del Diseñador de formularios.  
  
## <a name="creating-multi-tabbed-views"></a>Creación de vistas con múltiples fichas  
 Aunque un objeto de vista de documento debe estar asociado a una vista física a través de una cadena única vista física, puede colocar varias fichas dentro de la vista física para permitir la visualización de datos de maneras diferentes. En esta configuración con múltiples fichas, todas las fichas están asociadas con la misma cadena de la vista física, pero cada pestaña se proporciona un GUID de la vista lógica diferente.  
  
 Para crear una vista con múltiples fichas para un editor, implemente el <xref:Microsoft.VisualStudio.Shell.Interop.IVsMultiViewDocumentView> interfaz y, a continuación, asocie un GUID de la vista lógica diferente (<xref:Microsoft.VisualStudio.Shell.Interop.LogicalViewID>) con cada pestaña cree.  
  
 El editor HTML de Visual Studio es un ejemplo de un editor con una vista de varias pestaña. Tiene **diseño** y **origen** pestañas. Para habilitar esta opción, se asocia con cada pestaña, una vista lógica diferente `LOGICALVIEWID_TextView` para el **diseño** pestaña y `LOGICALVIEWID_Code` para el **origen** ficha.  
  
 Mediante la especificación de la vista lógica apropiada, un VSPackage puede tener acceso a la vista que corresponde a un propósito específico, como diseñar un formulario, edición de código o depurar el código. Sin embargo, una de las ventanas debe identificarse por la cadena es NULL y se debe corresponder a la vista lógica principal (`LOGVIEWID_Primary`).  
  
 En la tabla siguiente se enumera los valores de la vista lógica disponibles y su uso.  
  
|GUID DE LOGVIEWID|Uso recomendado|  
|--------------------|---------------------|  
|`LOGVIEWID_Primary`|Vista predeterminada/primaria del generador del editor.<br /><br /> Todos los generadores de editores deben admitir este valor. Esta vista debe utilizar la cadena NULL como su cadena de la vista física. Este valor debe establecerse al menos una vista lógica.|  
|`LOGVIEWID_Debugging`|Vista de depuración. Por lo general, `LOGVIEWID_Debugging` se asigna a la misma vista que `LOGVIEWID_Code`.|  
|`LOGVIEWID_Code`|Vista iniciados por el **ver código** comando.|  
|`LOGVIEWID_Designer`|Vista iniciados por el **Ver formulario** comando.|  
|`LOGVIEWID_TextView`|Vista de editor de texto. Esta es la vista que devuelve <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>, desde que puede tener acceso a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>.|  
|`LOGVIEWID_UserChooseView`|Pide al usuario elegir qué vista se debe para usar.|  
|`LOGVIEWID_ProjectSpecificEditor`|Pasa por el **abrir con** cuadro de diálogo<br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.OpenItem%2A><br /><br /> Cuando el usuario selecciona la entrada "(editor de proyectos predeterminado)".|  
  
 Aunque los GUID de vista lógica son extensibles, puede usar solo los GUID de vista lógica definidos en el VSPackage.  
  
 En el apagado, Visual Studio conserva el GUID del generador de editores y las cadenas de la vista física asociadas con la ventana de documento para que se puede usar para volver a abrir ventanas de documento al volver a abrir la solución. Solo las ventanas que están abiertas cuando se cierra una solución se conservan en el archivo de solución (.suo). Estos valores se corresponden con los `VSFPROPID_guidEditorType` y `VSFPROPID_pszPhysicalView` valores pasados en el `propid` parámetro en el <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> método.  
  
## <a name="example"></a>Ejemplo  
 Este fragmento de código se muestra cómo el <xref:Microsoft.VisualStudio.Shell.Interop.LogicalViewID.TextView> objeto se usa para tener acceso a una vista que implementa `IVsCodeWindow`. En este caso, el <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShellOpenDocument> servicio se usa para llamar a <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenDocumentViaProject%2A> y solicitud `LOGVIEWID_TextView`, que obtiene un puntero a un marco de ventana. Un puntero al objeto de vista de documento se obtiene mediante una llamada a <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> y especificando un valor de `VSFPROPID_DocView`. Desde el objeto de vista de documento, `QueryInterface` se llama para `IVsCodeWindow`. La expectativa de que en este caso es que se devuelve un editor de texto y, por lo que se devuelve el objeto de vista de documento en el <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> método es una ventana de código.  
  
```cpp#  
HRESULT CFindTool::GotoFileLocation(const WCHAR * szFile, long iLine, long iStart, long iLen)  
{  
  HRESULT hr;  
  if (NULL == szFile || !*szFile)  
    return E_INVALIDARG;  
  
  if (iLine == -1L)  
    return S_FALSE;  
  
  VSITEMID                  itemid;  
  VARIANT                   var;  
  RECT                      rc;  
  IVsUIShellOpenDocument *  pOpenDoc    = NULL;  
  IVsCodeWindow *           pCodeWin    = NULL;  
  IVsTextView *             pTextView   = NULL;  
  IVsUIHierarchy *          pHierarchy  = NULL;  
  IVsWindowFrame *          pFrame      = NULL;  
  IUnknown *                pUnk        = NULL;  
  IVsHighlight *            pHighlight  = NULL;  
  
  IfFailGo(CGlobalServiceProvider::HrQueryService(SID_SVsUIShellOpenDocument, IID_IVsUIShellOpenDocument, (void **)&pOpenDoc));  
  IfFailGo(pOpenDoc->OpenDocumentViaProject(szFile, LOGVIEWID_TextView, NULL, &pHierarchy, &itemid, &pFrame));  
  pFrame->Show();  
  VariantInit(&var);  
  IfFailGo(pFrame->GetProperty(VSFPROPID_DocView, &var));  
  if (VT_UNKNOWN != var.vt) { hr = E_FAIL; goto Error; }  
  pUnk = V_UNKNOWN(&var);  
  if (NULL != pUnk)  
  {  
    IfFailGo(pUnk->QueryInterface(IID_IVsCodeWindow, (void **)&pCodeWin));  
    if (SUCCEEDED(hr = pCodeWin->GetLastActiveView(&pTextView)) ||  
        SUCCEEDED(hr = pCodeWin->GetPrimaryView(&pTextView)) )  
    {  
      pTextView->SetSelection(iLine, iStart, iLine, iStart + iLen);  
      // uncover selection  
      IfFailGo(pTextView->QueryInterface(IID_IVsHighlight, (void**)&pHighlight));  
      IfFailGo(SUCCEEDED(pHighlight->GetHighlightRect(&rc)));  
      UncoverSelectionRect(&rc);  
    }  
  }  
  
Error:  
  CLEARINTERFACE(pHighlight);  
  CLEARINTERFACE(pTextView);  
  CLEARINTERFACE(pCodeWin);  
  CLEARINTERFACE(pUnk);  
  CLEARINTERFACE(pFrame);  
  CLEARINTERFACE(pOpenDoc);  
  CLEARINTERFACE(pHierarchy);  
  RedrawWindow(m_hwndResults, NULL, NULL, RDW_ERASE|RDW_FRAME|RDW_INVALIDATE|RDW_ALLCHILDREN);  
  return hr;  
}  
```  
  
## <a name="see-also"></a>Vea también  
 [Compatibilidad con varias vistas de documento](../extensibility/supporting-multiple-document-views.md)   
 [Cómo: adjuntar las vistas de datos de documentos](../extensibility/how-to-attach-views-to-document-data.md)   
 [Creación de diseñadores y editores personalizados](../extensibility/creating-custom-editors-and-designers.md)

