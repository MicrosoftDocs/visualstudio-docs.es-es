---
title: "&#218;nicas y ficha m&#250;ltiples vistas | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "editores [Visual Studio SDK] personalizados - únicos y ficha múltiples vistas"
ms.assetid: e3611704-349f-4323-b03c-f2b0a445d781
caps.latest.revision: 22
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 22
---
# &#218;nicas y ficha m&#250;ltiples vistas
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Un editor puede crear tipos diferentes de vistas.  Un ejemplo es una ventana del editor de código, otra es diseñador de formularios.  
  
 Una vista multi\-tabulada es una vista que tiene varias fichas.  Por ejemplo, el editor HTML tiene dos fichas en la parte inferior: **Diseño** y **código fuente**, cada una vista lógica.  La vista de diseño muestra una página Web generado, mientras que la otra muestra HTML que contiene la página Web.  
  
## Vistas de acceso de comprobación  
 La comprobación ver los objetos de vista del documento de host, cada uno de los cuales representa una vista de datos en el búfer, como código o un formulario.  Por consiguiente, cada objeto de vista del documento tiene una vista física \(identificada por algo conocido como cadena física de la vista\), y normalmente una única vista lógica.  
  
 En algunos casos, sin embargo, una vista física puede tener vistas dos o más lógicos.  Algunos ejemplos son un editor que tiene una ventana dividida con en paralelo vistas, o un diseñador de formularios que tiene una vista de GUI\/Design y una vista de código subyacente \-\- formulario.  
  
 Para permitir que el editor para tener acceso a todas las vistas disponibles de comprobación, debe crear una cadena física única de vista para cada tipo de objeto de vista del documento que el generador del editor puede crear.  Por ejemplo, el generador del editor de [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] pueden crear objetos de vista del documento para una ventana de código y una ventana del diseñador de formularios.  
  
## Crear vistas Multi\-Tabuladas  
 Aunque un objeto de vista del documento debe estar asociado a una vista física a través de una cadena física única de la vista, puede colocar las pestañas múltiples dentro de la vista física para habilitar la presentación de los datos de maneras diferentes.  En esta configuración multi\-tabulada, todas las fichas son asociado con la misma cadena física de la vista, pero cada pestaña se proporciona una vista diferente lógica GUID.  
  
 Para crear una vista multi\-tabulada para un editor, implemente la interfaz de <xref:Microsoft.VisualStudio.Shell.Interop.IVsMultiViewDocumentView> y y asocie una vista diferente lógica GUID \(<xref:Microsoft.VisualStudio.Shell.Interop.LogicalViewID>\) con cada ficha que cree.  
  
 El editor HTML de Visual Studio es un ejemplo de un editor con una vista de multi\-TAB.  tiene **Diseño** y fichas de **código fuente** .  Para habilitar esto, otra vista lógica es asociado a cada pestaña, `LOGICALVIEWID_TextView` para la ficha de **Diseño** y `LOGICALVIEWID_Code` para la ficha de **código fuente** .  
  
 Especificando la vista lógica adecuada, un Paquete puede tener acceso a la vista correspondiente a un propósito determinado, como diseño de un formulario, editar código, o depurar código.  Sin embargo, una de las ventanas debe identificarse por la cadena nula y ésta debe corresponder a la vista lógica primaria \(`LOGVIEWID_Primary`\).  
  
 La tabla siguiente se enumeran los valores lógicos disponibles de vista y su uso.  
  
|LOGVIEWID GUID|uso recomendado|  
|--------------------|---------------------|  
|`LOGVIEWID_Primary`|Valor predeterminado\/vista primaria del generador del editor.<br /><br /> Todos los generadores de editor deben admitir este valor.  Esta vista debe utilizar la cadena nula como su cadena física de la vista.  Al menos una vista lógica se debe establecer este valor.|  
|`LOGVIEWID_Debugging`|Depurar la vista.  Normalmente, los mapas de `LOGVIEWID_Debugging` igual ven como `LOGVIEWID_Code`.|  
|`LOGVIEWID_Code`|Vea iniciará mediante el comando de **Ver código** .|  
|`LOGVIEWID_Designer`|Vista iniciada por el comando de **Formulario de vista** .|  
|`LOGVIEWID_TextView`|Vista de editor de texto.  Esta es la vista que devuelve <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>, de las que puede tener acceso a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>.|  
|`LOGVIEWID_UserChooseView`|Solicita al usuario elegir que consultan para utilizar.|  
|`LOGVIEWID_ProjectSpecificEditor`|pasado por el cuadro de diálogo de **Abrir con** a<br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.OpenItem%2A><br /><br /> cuando el usuario elige “\(editor predeterminado del proyecto\)” entrada.|  
  
 Aunque la vista lógica GUID es extensible, puede usar la vista lógica GUID definido en el Paquete.  
  
 Al cerrar, Visual Studio conserva el GUID del generador del editor y de las cadenas físicas de vista asociado con la ventana de documento para que se pueda utilizar para abrir de nuevo las ventanas de documento cuando se vuelve a abrir la solución.  Sólo las ventanas que estén abiertos cuando se cierra una solución se conservan en el archivo de solución \(.suo\).  Estos valores corresponden a los valores de `VSFPROPID_guidEditorType` y de `VSFPROPID_pszPhysicalView` pasados al parámetro de `propid` en el método de <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> .  
  
## Ejemplo  
 Este fragmento de código muestra cómo el objeto de <xref:Microsoft.VisualStudio.Shell.Interop.LogicalViewID.TextView> se utiliza para tener acceso a una vista que implemente `IVsCodeWindow`.  En este caso, el servicio de <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShellOpenDocument> se utiliza para llamar a <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenDocumentViaProject%2A> y solicitar `LOGVIEWID_TextView`, que obtiene un puntero a un marco de la ventana.  Un puntero al objeto de vista del documento se obtiene llamando a <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> y especificando un valor de `VSFPROPID_DocView`.  El objeto de vista del documento, `QueryInterface` se llama para `IVsCodeWindow`.  La expectativa en este caso es que un editor de texto está devuelto, por lo que el objeto de vista del documento devuelto en el método de <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> es una ventana de código.  
  
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
  
## Vea también  
 [Admitir varias vistas del documento](../extensibility/supporting-multiple-document-views.md)   
 [Cómo: adjuntar vistas de datos de documentos](../extensibility/how-to-attach-views-to-document-data.md)   
 [Creación de diseñadores y editores personalizados](../extensibility/creating-custom-editors-and-designers.md)