---
title: "C&#243;mo: suprimir las notificaciones de cambio de archivo | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "editores [Visual Studio SDK] heredados - Suprimir notificaciones de cambio de archivo"
ms.assetid: 891c1eb4-f6d0-4073-8df0-2859dbd417ca
caps.latest.revision: 18
caps.handback.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
---
# C&#243;mo: suprimir las notificaciones de cambio de archivo
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Cuando el archivo físico que representa el búfer de texto se ha cambiado, se muestra un cuadro de diálogo con el mensaje **¿Desea guardar los cambios en los elementos siguientes?** Esto se conoce como notificación del archivo.  Si muchos cambios van a estar al archivo, sin embargo, este cuadro de diálogo que muestra una y otra vez puede llegar a ser rápidamente molesto.  
  
 Mediante programación puede suprimir este cuadro de diálogo mediante el procedimiento siguiente.  Haciendo esto, puede volver a cargar un archivo inmediatamente sin tener que pedir al usuario guardar los cambios cada vez.  
  
### Para suprimir la notificación de archivo  
  
1.  Llame al método de <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A> para determinar qué texto en el objeto de búfer son asociado al archivo abierto.  
  
2.  Resuelva el objeto de <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> que está en la memoria para omitir cambios del archivo de supervisión obtener la interfaz de <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl> del objeto de <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> \(datos de documento\), e implementar el método de <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl.IgnoreFileChanges%2A> con el parámetro de `fIgnore` establecido en `true`.  
  
3.  Llame a los métodos en <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> y las interfaces de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> para actualizar el objeto de <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> de memoria con los cambios del archivo \(por ejemplo cuando un campo se agrega el componente\).  
  
4.  Actualice el archivo en el disco con los cambios sin tener de ninguna ediciones pendientes que el usuario puede tener en curso.  
  
     De esta manera, cuando se ejecuta el objeto de <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> a la supervisión resume para las notificaciones del archivo, el búfer de texto en memoria refleja los cambios que generó, junto con el resto de las ediciones pendientes.  el archivo en el disco refleja el último código generado por usted y cualquier cambio previamente guardado por el usuario en código usuario\-editado.  
  
5.  Llame al método de <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl.IgnoreFileChanges%2A> para notificar al objeto de <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> a la supervisión resume para las notificaciones del archivo estableciendo el parámetro de `fIgnore` a `false`.  
  
6.  Si piensa realizar varios cambios en el archivo, como en el caso del control de \(SCC\) código fuente, después de debe indicar al servicio de cambio de archivo global que debe suspender temporalmente las notificaciones del archivo.  
  
     Por ejemplo, si se rescribe el archivo y después cambia la marca de tiempo, debe suspender notificaciones de cambio de archivo, como las operaciones de la reescritura y de timestample cada recuento como un archivo independiente cambian evento.  Para habilitar la notificación del archivo global debe en lugar de llamar al método de <xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEx.IgnoreFile%2A> .  
  
## Ejemplo  
 A continuación se muestra cómo suprimir la notificación del archivo.  
  
```cpp#  
//Misc. helper classes  
  
CSuspendFileChanges::CSuspendFileChanges(  
    /* [in] */ const CString& strMkDocument,   
    /* [in] */ BOOL fSuspendNow /* = TRUE */)   
:  
    m_strMkDocument(strMkDocument),  
    m_fFileChangeSuspended(FALSE)  
{  
    if(fSuspendNow)  
        Suspend();  
}  
CSuspendFileChanges::~CSuspendFileChanges()  
{  
    Resume();  
}  
void CSuspendFileChanges::Suspend()  
{  
    USES_CONVERSION;  
  
    // Prevent suspend from suspending more than once.  
    if(m_fFileChangeSuspended)  
        return;  
  
    IVsRunningDocumentTable* pRDT =   
      _VxModule.GetIVsRunningDocumentTable();  
    ASSERT(pRDT);  
    if (!pRDT)  
        return;  
  
    CComPtr<IUnknown> srpDocData;  
    VSCOOKIE vscookie = VSCOOKIE_NIL;  
    pRDT->FindAndLockDocument(RDT_NoLock, T2COLE(m_strMkDocument),    
      NULL, NULL, &srpDocData, &vscookie);  
    if ( (vscookie == VSCOOKIE_NIL) || !srpDocData)  
        return;  
    CComPtr<IVsFileChangeEx> srpIVsFileChangeEx;  
    HRESULT hr = _VxModule.QueryService(SID_SVsFileChangeEx,   
      IID_IVsFileChangeEx, (void **)&srpIVsFileChangeEx);  
    if (SUCCEEDED(hr) && srpIVsFileChangeEx)  
    {  
        m_fFileChangeSuspended = TRUE;  
        srpIVsFileChangeEx->IgnoreFile(NULL, m_strMkDocument, TRUE);   
        srpDocData->QueryInterface(IID_IVsDocDataFileChangeControl,   
          (void**)&m_srpIVsDocDataFileChangeControl);  
        if(m_srpIVsDocDataFileChangeControl)  
            m_srpIVsDocDataFileChangeControl->IgnoreFileChanges(TRUE);  
    }  
}  
void CSuspendFileChanges::Resume()  
{  
    if(!m_fFileChangeSuspended)  
        return;  
  
    CComPtr<IVsFileChangeEx> srpIVsFileChangeEx;  
    HRESULT hr = _VxModule.QueryService(SID_SVsFileChangeEx,   
      IID_IVsFileChangeEx, (void **)&srpIVsFileChangeEx);  
    if (SUCCEEDED(hr) && srpIVsFileChangeEx)  
  
    srpIVsFileChangeEx->IgnoreFile(NULL, m_strMkDocument, FALSE);   
    if(m_srpIVsDocDataFileChangeControl)  
        m_srpIVsDocDataFileChangeControl->IgnoreFileChanges(FALSE);  
    m_fFileChangeSuspended = FALSE;  
    m_srpIVsDocDataFileChangeControl.Release();  
}  
// Misc. helper classes  
```  
  
## Programación eficaz  
 Si el caso implica varios cambios al archivo, como en el caso de SCC, después de es importante reanudar las notificaciones de archivo global antes de avisar a los datos del documento a la supervisión resume para los cambios del archivo.