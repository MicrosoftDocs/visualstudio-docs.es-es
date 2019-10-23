---
title: Vistas de una y varias pestañas | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - single and multi-tab views
ms.assetid: e3611704-349f-4323-b03c-f2b0a445d781
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c651bda042524b2ed3188fef880f848bb0087433
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72720058"
---
# <a name="single-and-multi-tab-views"></a>Vistas de una sola pestaña y varias pestañas
Un editor puede crear diferentes tipos de vistas. Un ejemplo es una ventana del editor de código, otra es un diseñador de formularios.

 Una vista con varias pestañas es una vista que tiene varias pestañas. Por ejemplo, el editor HTML tiene dos pestañas en la parte inferior: **diseño** y **origen**, cada una de las cuales es una vista lógica. La vista de diseño muestra una página web representada, mientras que la otra muestra el código HTML que contiene la Página Web.

## <a name="accessing-physical-views"></a>Acceder a vistas físicas
 Las vistas físicas hospedan objetos de vista de documento, cada uno de los cuales representa una vista de los datos en el búfer, como el código o un formulario. En consecuencia, cada objeto de vista de documento tiene una vista física (identificada por algo conocido como cadena de vista física) y, por lo general, una única vista lógica.

 Sin embargo, en algunos casos, una vista física puede tener dos o más vistas lógicas. Algunos ejemplos son un editor que tiene una ventana dividida con vistas en paralelo, o un diseñador de formularios que tiene una vista gráfica o de diseño y una vista de código subyacente.

 Para permitir que el editor tenga acceso a todas las vistas físicas disponibles, debe crear una cadena de vista física única para cada tipo de objeto de vista de documento que pueda crear el generador de editores. Por ejemplo, el generador de editores de [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] puede crear objetos de vista de documento para una ventana de código y una ventana del diseñador de formularios.

## <a name="creating-multi-tabbed-views"></a>Crear vistas con varias pestañas
 Aunque un objeto de vista de documento debe estar asociado a una vista física a través de una cadena de vista física única, se pueden colocar varias pestañas dentro de la vista física para habilitar la visualización de datos de diferentes maneras. En esta configuración con varias pestañas, todas las pestañas están asociadas a la misma cadena de vista física, pero a cada pestaña se le asigna un GUID de vista lógica diferente.

 Para crear una vista con varias fichas para un editor, implemente la interfaz <xref:Microsoft.VisualStudio.Shell.Interop.IVsMultiViewDocumentView> y, a continuación, asocie un GUID de vista lógica diferente (<xref:Microsoft.VisualStudio.Shell.Interop.LogicalViewID>) con cada pestaña que cree.

 El editor HTML de Visual Studio es un ejemplo de un editor con una vista de varias pestañas. Tiene pestañas **diseño** y **código fuente** . Para habilitar esto, se asocia una vista lógica diferente a cada pestaña, `LOGICALVIEWID_TextView` para la pestaña **diseño** y `LOGICALVIEWID_Code` para la pestaña **origen** .

 Al especificar la vista lógica adecuada, un VSPackage puede tener acceso a la vista que corresponde a un propósito determinado, como diseñar un formulario, editar código o depurar código. Sin embargo, una de las ventanas debe identificarse mediante la cadena nula y debe corresponder a la vista lógica primaria (`LOGVIEWID_Primary`).

 En la tabla siguiente se enumeran los valores de vista lógica disponibles y su uso.

|GUID DE LOGVIEWID|Uso recomendado|
|--------------------|---------------------|
|`LOGVIEWID_Primary`|Vista predeterminada/primaria del generador de editores.<br /><br /> Todos los generadores de editores deben admitir este valor. Esta vista debe usar la cadena NULL como su cadena de vista física. Debe establecerse al menos una vista lógica en este valor.|
|`LOGVIEWID_Debugging`|Vista de depuración. Normalmente, `LOGVIEWID_Debugging` se asigna a la misma vista que `LOGVIEWID_Code`.|
|`LOGVIEWID_Code`|Vista iniciada por el comando **Ver código** .|
|`LOGVIEWID_Designer`|Vista iniciada por el comando **Ver formulario** .|
|`LOGVIEWID_TextView`|Vista del editor de texto. Esta es la vista que devuelve <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>, desde la que puede tener acceso a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>.|
|`LOGVIEWID_UserChooseView`|Solicita al usuario que elija la vista que se va a usar.|
|`LOGVIEWID_ProjectSpecificEditor`|Pasado por el cuadro de diálogo **abrir con**<br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.OpenItem%2A><br /><br /> Cuando el usuario elige la entrada "(editor predeterminado del proyecto)".|

 Aunque los GUID de vista lógica son extensibles, solo se pueden usar los GUID de vista lógica definidos en el VSPackage.

 Al cerrarse, Visual Studio conserva el GUID del generador de editores y las cadenas de vista física asociadas a la ventana de documento para que se pueda usar para volver a abrir las ventanas de documento cuando se vuelva a abrir la solución. Solo las ventanas que están abiertas cuando se cierra una solución se guardan en el archivo de solución (. suo). Estos valores corresponden a los valores `VSFPROPID_guidEditorType` y `VSFPROPID_pszPhysicalView` pasados en el parámetro `propid` en el método <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A>.

## <a name="example"></a>Ejemplo
 Este fragmento de código muestra cómo se utiliza el objeto de <xref:Microsoft.VisualStudio.Shell.Interop.LogicalViewID.TextView> para tener acceso a una vista que implementa `IVsCodeWindow`. En este caso, el servicio <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShellOpenDocument> se usa para llamar a <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenDocumentViaProject%2A> y solicitar `LOGVIEWID_TextView`, que obtiene un puntero a un marco de ventana. Un puntero al objeto de vista de documento se obtiene llamando a <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> y especificando un valor de `VSFPROPID_DocView`. En el objeto de vista de documento, se llama a `QueryInterface` para `IVsCodeWindow`. En este caso, la expectativa es que se devuelva un editor de texto, por lo que el objeto de vista de documento devuelto en el método <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> es una ventana de código.

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
- [Compatibilidad con vistas de varios documentos](../extensibility/supporting-multiple-document-views.md)
- [Anexión de vistas a datos de documentos](../extensibility/how-to-attach-views-to-document-data.md)
- [Creación de diseñadores y editores personalizados](../extensibility/creating-custom-editors-and-designers.md)