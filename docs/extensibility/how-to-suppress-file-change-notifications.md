---
title: Procedimiento Suprimir notificaciones de cambio de archivo | Documentos de Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - suppress file change notification
ms.assetid: 891c1eb4-f6d0-4073-8df0-2859dbd417ca
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2d7acfb4a5a680aa4be6e93187560cd66b68fa3b
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66324923"
---
# <a name="how-to-suppress-file-change-notifications"></a>Procedimiento Suprimir notificaciones de cambio de archivo
Cuando se ha cambiado el archivo físico que representa el búfer de texto, muestra un cuadro de diálogo con el mensaje **¿desea guardar los cambios en los siguientes elementos?** Esto se conoce como notificación de cambio de archivo. Si muchos cambios se van a estar en el archivo, sin embargo, este cuadro de diálogo muestra una y otra vez puede volverse rápidamente molesto.

 Mediante programación, puede suprimir este cuadro de diálogo con el siguiente procedimiento. Mediante la supresión del cuadro de diálogo, puede volver a cargar un archivo inmediatamente sin tener que solicitar al usuario que guarde los cambios cada vez.

## <a name="to-suppress-file-change-notification"></a>Para suprimir la notificación de cambio de archivo

1. Llame a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A> método para determinar qué objeto de búfer de texto está asociado con el archivo abierto.

2. Directo el <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> objeto que está en la memoria para pasar por alto supervisando los cambios del archivo mediante la obtención de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl> de la interfaz de la <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> objeto (datos del documento) y, a continuación, implementar el <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl.IgnoreFileChanges%2A> método con el `fIgnore` parámetro establecido en `true`.

3. Llamar a los métodos en el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> y <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> interfaces para actualizar la memoria <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> objeto con los cambios del archivo (por ejemplo, cuando se agrega un campo a su componente).

4. Actualice el archivo en el disco con los cambios sin tener en cuenta cualquiera podría tener el usuario en curso de las ediciones pendientes.

     De este modo, cuando se dirigen el <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> notificaciones de cambio de objeto que se va a reanudar la supervisión de archivos, el búfer de texto en la memoria refleja los cambios que ha generado. También refleja en el búfer de texto en la memoria todas las demás ediciones pendientes. El archivo en disco refleja el código más reciente generado por el usuario y cualquier previamente guardado los cambios realizados por el usuario en el código editado por el usuario.

5. Llamar a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl.IgnoreFileChanges%2A> método para notificar el <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> objeto que se va a reanudar la supervisión para las notificaciones de cambio estableciendo el `fIgnore` parámetro `false`.

6. Si tiene previsto realizar varios cambios en el archivo, como en el caso del control de código fuente (SCC), a continuación, debe indicar el servicio de cambio de archivo global para suspender temporalmente las notificaciones de cambio.

     Por ejemplo, si se vuelva a escribir el archivo y, a continuación, cambie la marca de tiempo, debe suspender las notificaciones de cambio de archivo porque las operaciones de reescritura y la marca de tiempo se consideran un evento de cambio de archivo independiente. Para habilitar la notificación de cambio de archivo global, debe llamar en su lugar el <xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEx.IgnoreFile%2A> método.

## <a name="example"></a>Ejemplo
 En el ejemplo de código siguiente se muestra cómo suprimir la notificación de cambio de archivo.

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
 Si su caso implica varios cambios en el archivo, como en el caso de SCC, es importante reanudar las notificaciones de cambio global antes de alertar de los datos del documento para reanudar la supervisión de los cambios del archivo.