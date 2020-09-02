---
title: 'Cómo: suprimir notificaciones de cambio de archivo | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - suppress file change notification
ms.assetid: 891c1eb4-f6d0-4073-8df0-2859dbd417ca
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3f045175eae165b75a887ada2716b19f34fc228b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204078"
---
# <a name="how-to-suppress-file-change-notifications"></a>Cómo: Suprimir las notificaciones de cambios de archivos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cuando se ha cambiado el archivo físico que representa el búfer de texto, se muestra un cuadro de diálogo con el mensaje **¿desea guardar los cambios realizados en los elementos siguientes?** Esto se conoce como notificación de cambios de archivo. Sin embargo, si hay muchos cambios que van a ser el archivo, este cuadro de diálogo que se muestra una y otra vez puede resultar molesto.  
  
 Puede suprimir este cuadro de diálogo mediante programación mediante el procedimiento siguiente. Al hacerlo, puede volver a cargar un archivo inmediatamente sin tener que preguntar al usuario si desea guardar los cambios cada vez.  
  
### <a name="to-suppress-file-change-notification"></a>Para suprimir la notificación de cambio de archivo  
  
1. Llame al <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A> método para determinar qué objeto de búfer de texto está asociado con el archivo abierto.  
  
2. Dirija el <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> objeto que se encuentra en memoria para omitir los cambios de los archivos de supervisión obteniendo la <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl> interfaz del <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> objeto (datos del documento) y, a continuación, implementando el <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl.IgnoreFileChanges%2A> método con el `fIgnore` parámetro establecido en `true` .  
  
3. Llame a los métodos de las <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> interfaces y para actualizar el objeto en memoria <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> con los cambios del archivo (por ejemplo, cuando se agrega un campo al componente).  
  
4. Actualice el archivo en disco con los cambios sin tener en cuenta las modificaciones pendientes que el usuario podría tener en curso.  
  
     De esta manera, cuando dirija el <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> objeto para reanudar la supervisión de las notificaciones de cambio de archivo, el búfer de texto en memoria reflejará los cambios que ha generado, así como todas las demás ediciones pendientes. El archivo en disco refleja el código más reciente generado por el usuario y los cambios guardados anteriormente por el usuario en código editado por el usuario.  
  
5. Llame al <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl.IgnoreFileChanges%2A> método para notificar al <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> objeto que reanude la supervisión de notificaciones de cambios de archivo estableciendo el `fIgnore` parámetro en `false` .  
  
6. Si tiene previsto realizar varios cambios en el archivo, como en el caso del control de código fuente (SCC), debe indicar al servicio de cambio global de archivos que suspenda temporalmente las notificaciones de cambio de archivo.  
  
     Por ejemplo, si vuelve a escribir el archivo y, a continuación, cambia la marca de tiempo, debe suspender las notificaciones de cambio del archivo, ya que las operaciones de reescritura y timestample se recuentan como un evento de cambio de archivo independiente. Para habilitar la notificación de cambios de archivo global, debe llamar al <xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEx.IgnoreFile%2A> método.  
  
## <a name="example"></a>Ejemplo  
 A continuación se muestra cómo suprimir la notificación de cambios de archivo.  
  
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
  
## <a name="robust-programming"></a>Programación sólida  
 Si su caso implica varios cambios en el archivo, como en el caso de SCC, es importante reanudar las notificaciones de cambio de archivo global antes de avisar a los datos del documento para reanudar la supervisión de los cambios de archivo.
