---
title: Vistas de una y varias pestañas ( Single y Multi-tab Views) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - single and multi-tab views
ms.assetid: e3611704-349f-4323-b03c-f2b0a445d781
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c308b4d6c7b90456255019ef57c6b9d544aefc77
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699987"
---
# <a name="single-and-multi-tab-views"></a>Vistas de una sola pestaña y varias pestañas
Un editor puede crear diferentes tipos de vistas. Un ejemplo es una ventana del editor de código, otro es un diseñador de formularios.

 Una vista con varias pestañas es una vista que tiene varias fichas. Por ejemplo, el editor HTML tiene dos pestañas en la parte inferior: **Diseño** y **Origen,** cada una una de las dos una vista lógica. La vista de diseño muestra una página web representada, mientras que la otra muestra el código HTML que comprende la página web.

## <a name="accessing-physical-views"></a>Acceso a vistas físicas
 Las vistas físicas alojan objetos de vista de documento, cada uno de los cuales representa una vista de datos en el búfer, como código o un formulario. En consecuencia, cada objeto de vista de documento tiene una vista física (identificada por algo conocido como una cadena de vista física) y, por lo general, una única vista lógica.

 En algunos casos, sin embargo, una vista física puede tener dos o más vistas lógicas. Algunos ejemplos son un editor que tiene una ventana dividida con vistas en paralelo, o un diseñador de formularios que tiene una vista de gui/diseño y una vista de código subyacente al formulario.

 Para permitir que el editor tenga acceso a todas las vistas físicas disponibles, debe crear una cadena de vista física única para cada tipo de objeto de vista de documento que el generador del editor pueda crear. Por ejemplo, [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] el generador de editores puede crear objetos de vista de documento para una ventana de código y una ventana del diseñador de formularios.

## <a name="creating-multi-tabbed-views"></a>Creación de vistas con varias pestañas
 Aunque un objeto de vista de documento debe estar asociado a una vista física a través de una cadena de vista física única, puede colocar varias pestañas dentro de la vista física para habilitar la visualización de datos de diferentes maneras. En esta configuración con varias pestañas, todas las pestañas están asociadas a la misma cadena de vista física, pero a cada pestaña se le da un GUID de vista lógica diferente.

 Para crear una vista con varias pestañas para un editor, implemente la <xref:Microsoft.VisualStudio.Shell.Interop.IVsMultiViewDocumentView> interfaz y, a continuación, asocie un GUID de vista lógica diferente (<xref:Microsoft.VisualStudio.Shell.Interop.LogicalViewID>) a cada pestaña que cree.

 El editor HTML de Visual Studio es un ejemplo de un editor con una vista de varias pestañas. Tiene pestañas **Diseño** y **Origen.** Para habilitar esto, se asocia una vista `LOGICALVIEWID_TextView` lógica diferente `LOGICALVIEWID_Code` a cada ficha, para la pestaña **Diseño** y para la pestaña **Origen.**

 Al especificar la vista lógica adecuada, un VSPackage puede tener acceso a la vista que corresponde a un propósito determinado, como diseñar un formulario, editar código o depurar código. Sin embargo, una de las ventanas debe identificarse mediante la`LOGVIEWID_Primary`cadena NULL y esto debe corresponder a la vista lógica principal ( ).

 En la tabla siguiente se enumeran los valores de vista lógica disponibles y su uso.

|LOGVIEWID GUID|Uso Recomendado|
|--------------------|---------------------|
|`LOGVIEWID_Primary`|Vista predeterminada/primaria de la fábrica del editor.<br /><br /> Todas las fábricas de editores deben admitir este valor. Esta vista debe usar la cadena NULL como su cadena de vista física. Se debe establecer al menos una vista lógica en este valor.|
|`LOGVIEWID_Debugging`|Vista de depuración. Normalmente, `LOGVIEWID_Debugging` se asigna a `LOGVIEWID_Code`la misma vista que .|
|`LOGVIEWID_Code`|Vista iniciada por el comando **Ver código.**|
|`LOGVIEWID_Designer`|Vista iniciada por el comando **Ver formulario.**|
|`LOGVIEWID_TextView`|Vista del editor de texto. Esta es la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>vista que devuelve, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>desde la que se puede acceder.|
|`LOGVIEWID_UserChooseView`|Solicita al usuario que elija qué vista utilizar.|
|`LOGVIEWID_ProjectSpecificEditor`|Pasado por el cuadro de diálogo **Abrir con** a<br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.OpenItem%2A><br /><br /> cuando el usuario elige la entrada "(Editor predeterminado del proyecto)".|

 Aunque los GUID de vista lógica son extensibles, solo puede usar los GUID de vista lógica definidos en el VSPackage.

 Al apagarse, Visual Studio conserva el GUID del generador del editor y las cadenas de vista física asociadas a la ventana del documento para que se pueda usar para volver a abrir las ventanas de documento cuando se vuelva a abrir la solución. Solo las ventanas que están abiertas cuando se cierra una solución se conservan en el archivo de solución (.suo). Estos valores corresponden `VSFPROPID_guidEditorType` `VSFPROPID_pszPhysicalView` a los `propid` valores pasados en el parámetro en el <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> método.

## <a name="example"></a>Ejemplo
 Este fragmento de <xref:Microsoft.VisualStudio.Shell.Interop.LogicalViewID.TextView> código ilustra cómo se usa `IVsCodeWindow`el objeto para tener acceso a una vista que implementa . En este caso, el <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShellOpenDocument> servicio <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenDocumentViaProject%2A> se `LOGVIEWID_TextView`utiliza para llamar y solicitar , que obtiene un puntero a un marco de ventana. Un puntero al objeto de vista <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> de documento se `VSFPROPID_DocView`obtiene llamando y especificando un valor de . Desde el objeto `QueryInterface` de vista `IVsCodeWindow`de documento, se llama para . La expectativa en este caso es que se devuelve un editor <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> de texto, por lo que el objeto de vista de documento devuelto en el método es una ventana de código.

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
