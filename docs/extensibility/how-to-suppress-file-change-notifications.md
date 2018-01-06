---
title: "Cómo: suprimir las notificaciones de cambio de archivo | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], legacy - suppress file change notification
ms.assetid: 891c1eb4-f6d0-4073-8df0-2859dbd417ca
caps.latest.revision: "18"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 209006129bcb2cfaaf88233768df1d9597cd09a5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-suppress-file-change-notifications"></a>Cómo: suprimir las notificaciones de cambio de archivo
Cuando ha cambiado el archivo físico que representa el búfer de texto, aparece un cuadro de diálogo con el mensaje **¿desea guardar los cambios en los siguientes elementos?** Esto se conoce como la notificación de cambio de archivo. Si muchos cambios van a estar en el archivo, sin embargo, este cuadro de diálogo con una y otra vez puede volverse rápidamente molesto.  
  
 Mediante programación, puede suprimir este cuadro de diálogo con el siguiente procedimiento. Al hacerlo, se puede volver a cargar un archivo inmediatamente sin tener que solicitar al usuario que guarde los cambios cada vez.  
  
### <a name="to-suppress-file-change-notification"></a>Para eliminar la notificación de cambio de archivo  
  
1.  Llame a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A> método para determinar qué objeto de búfer de texto está asociado con el archivo abierto.  
  
2.  Directa el <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> objeto que en la memoria para pasar por alto supervisa los cambios de archivo mediante la obtención de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl> de la interfaz de la <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> objeto (datos del documento) y, a continuación, implementar la <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl.IgnoreFileChanges%2A> método con el `fIgnore` parámetro establecido en `true`.  
  
3.  Llamar a los métodos en el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> y <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> interfaces para actualizar la memoria <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> objeto con los cambios de archivo (por ejemplo, cuando se agrega un campo a su componente).  
  
4.  Actualizar el archivo en disco con los cambios sin tener en cuenta los pendientes modificaciones que el usuario pueda tener en curso.  
  
     De este modo, cuando se dirigen el <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> las notificaciones de cambio de objeto que se va a reanudar la supervisión de archivos, el búfer de texto en la memoria refleja los cambios que ha generado, así como todas las demás ediciones pendientes. El archivo en disco refleja el código más reciente generado por el usuario y cualquier guardado previamente cambios realizados por el usuario en el código de usuario se ha editado.  
  
5.  Llame a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl.IgnoreFileChanges%2A> método para informar a la <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> objeto que se va a reanudar la supervisión de las notificaciones de cambio de archivo estableciendo el `fIgnore` parámetro `false`.  
  
6.  Si tiene previsto realizar varios cambios en el archivo, como en el caso de control de código fuente (SCC), a continuación, debe indicar el servicio de cambio de archivo global para suspender temporalmente las notificaciones de cambio de archivo.  
  
     Por ejemplo, si se vuelva a escribir el archivo y, a continuación, cambie la marca de tiempo, es necesario suspender las notificaciones de cambio de archivo, como las operaciones de reescritura y timestample cada consideran como evento de cambio de un archivo independiente. Para habilitar la notificación de cambio de archivo global en su lugar, debe llamar a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEx.IgnoreFile%2A> método.  
  
## <a name="example"></a>Ejemplo  
 A continuación muestra cómo eliminar la notificación de cambio de archivo.  
  
```cpp  
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
  
## <a name="robust-programming"></a>Programación sólida  
 Si su caso implica varios cambios en el archivo, como en el caso de SCC, es importante reanudar las notificaciones de cambio de archivo global antes de alertar de los datos del documento para reanudar la supervisión de los cambios de archivo.