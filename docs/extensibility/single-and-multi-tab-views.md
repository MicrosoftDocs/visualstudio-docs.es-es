---
title: "Vistas simples y múltiples ficha | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], custom - single and multi-tab views
ms.assetid: e3611704-349f-4323-b03c-f2b0a445d781
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: f20e5d251d8d6ef31289fb1b9ee8b9420ff9146a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="single-and-multi-tab-views"></a>Vistas simples y múltiples pestaña
Un editor puede crear diferentes tipos de vistas. Un ejemplo es una ventana del editor de código, el otro es un diseñador de formularios.  
  
 Una vista con múltiples fichas es una vista que tiene varias pestañas. Por ejemplo, el editor HTML tiene dos pestañas en la parte inferior: **diseño** y **origen**, cada una vista lógica. La vista de diseño muestra una página web representada, mientras que la otra muestra el código HTML que incluye la página web.  
  
## <a name="accessing-physical-views"></a>Obtener acceso a vistas físicas  
 Vistas físicas hospedan objetos de vista de documento, que representa una vista de datos en el búfer, por ejemplo, código o un formulario. En consecuencia, cada objeto de vista de documento tiene una vista física (identificadas por un método conocido como una cadena de vista física) y, por lo general en una vista lógica única.  
  
 Sin embargo, en algunos casos, una vista física puede tener dos o más vistas lógicas. Algunos ejemplos son un editor que tenga una ventana dividida con vistas en paralelo o un diseñador de formularios que tiene una vista de diseño/interfaz gráfica de usuario y una vista de código subyacente y el formulario.  
  
 Para habilitar el editor tener acceso a todas las vistas físicas disponibles, debe crear una cadena única vista física para cada tipo de objeto de vista de documento que puede crear el generador de editores. Por ejemplo, el [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] generador de editores puede crear documento objetos de vista de una ventana de código y una ventana del Diseñador de formularios.  
  
## <a name="creating-multi-tabbed-views"></a>Creación de vistas con múltiples fichas  
 Aunque un objeto de vista de documento debe estar asociado a una vista física a través de una cadena única vista física, puede colocar varias pestañas en la vista física para habilitar la visualización de los datos de maneras diferentes. En esta configuración con múltiples fichas, todas las fichas están asociadas con la misma cadena de vista físico, pero cada pestaña se proporciona una vista lógica diferentes GUID.  
  
 Para crear una vista con múltiples fichas para un editor, implemente el <xref:Microsoft.VisualStudio.Shell.Interop.IVsMultiViewDocumentView> de interfaz y, a continuación, asociar una vista lógica diferentes GUID (<xref:Microsoft.VisualStudio.Shell.Interop.LogicalViewID>) con cada pestaña se crea.  
  
 El editor de HTML de Visual Studio es un ejemplo de un editor con una vista de la ficha. Tiene **diseño** y **origen** pestañas. Para habilitar esta opción, está asociada con cada pestaña, una vista lógica diferente `LOGICALVIEWID_TextView` para el **diseño** ficha y `LOGICALVIEWID_Code` para el **origen** ficha.  
  
 Mediante la especificación de la vista lógica adecuada, un VSPackage puede tener acceso a la vista que se corresponde con un propósito específico, como diseñar un formulario, edición de código o depurar el código. Sin embargo, una de las ventanas debe identificarse por la cadena es NULL y se debe corresponder a la vista de la lógica principal (`LOGVIEWID_Primary`).  
  
 En la tabla siguiente se enumera los valores de la vista lógica disponibles y su uso.  
  
|GUID DE LOGVIEWID|Uso recomendado|  
|--------------------|---------------------|  
|`LOGVIEWID_Primary`|Vista principal predeterminada del generador de editores.<br /><br /> Todos los generadores de editores deben admitir este valor. Esta vista debe utilizar la cadena NULL como su cadena de vista física. Al menos una vista lógica debe establecerse en este valor.|  
|`LOGVIEWID_Debugging`|Vista de depuración. Por lo general, `LOGVIEWID_Debugging` se asigna a la misma vista que `LOGVIEWID_Code`.|  
|`LOGVIEWID_Code`|Inicia vista de la **ver código** comando.|  
|`LOGVIEWID_Designer`|Inicia vista de la **Ver formulario** comando.|  
|`LOGVIEWID_TextView`|Vista de editor de texto. Esta es la vista que devuelve <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>, desde que puede tener acceso a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>.|  
|`LOGVIEWID_UserChooseView`|Pide al usuario que elija qué vista se debe para usar.|  
|`LOGVIEWID_ProjectSpecificEditor`|Pasa por el **abrir con** cuadro de diálogo<br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.OpenItem%2A><br /><br /> Cuando el usuario selecciona la entrada "(editor de proyectos predeterminado)".|  
  
 Aunque la vista lógica GUID son extensibles, puede usar solo el GUID de la vista lógica definido en el paquete de VS.  
  
 En el apagado, Visual Studio conserva el GUID del generador de editores y las cadenas de vista física asociadas a la ventana de documento para que se puede utilizar para volver a abrir ventanas de documento al volver a abrir la solución. Sólo las ventanas que estén abiertas cuando se cierra una solución se conservan en el archivo de solución (.suo). Estos valores corresponden a la `VSFPROPID_guidEditorType` y `VSFPROPID_pszPhysicalView` valores que se pasan en el `propid` parámetro en el <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> método.  
  
## <a name="example"></a>Ejemplo  
 Este fragmento de código se muestra cómo el <xref:Microsoft.VisualStudio.Shell.Interop.LogicalViewID.TextView> objeto se usa para tener acceso a una vista que implementa `IVsCodeWindow`. En este caso, el <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShellOpenDocument> servicio se usa para llamar <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenDocumentViaProject%2A> y solicitud `LOGVIEWID_TextView`, que obtiene un puntero a un marco de ventana. Un puntero al objeto de vista de documento se obtiene mediante una llamada a <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> y especificando un valor de `VSFPROPID_DocView`. Desde el objeto de vista de documento, `QueryInterface` llaman a `IVsCodeWindow`. En este caso es la expectativa de que se devuelve un editor de texto y, por lo que devuelve el objeto de vista de documento en el <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> método es una ventana de código.  
  
```cpp  
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
 [Admitir varias vistas del documento](../extensibility/supporting-multiple-document-views.md)   
 [Cómo: adjuntar vistas para datos de documentos](../extensibility/how-to-attach-views-to-document-data.md)   
 [Creación de diseñadores y editores personalizados](../extensibility/creating-custom-editors-and-designers.md)