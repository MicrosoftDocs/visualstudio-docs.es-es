---
title: 'Cómo: registrar una biblioteca con el Administrador de objetos | Microsoft Docs'
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
- libraries, registering with object manager
- IVsLibrary2 interface, registering library with object manager
- IVsSimpleLibrary2 interface, registering library with object manager
- IVsObjectManager2 interface, registering library with object manager
- libraries, symbol-browsing tools
ms.assetid: f124dd05-cb0f-44ad-bb2a-7c0b34ef4038
caps.latest.revision: 27
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 204291cae617c704943889b8b88c590145935db3
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49174712"
---
# <a name="how-to-register-a-library-with-the-object-manager"></a>Cómo: registrar una biblioteca con el Administrador de objetos
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Exploración de símbolos de herramientas, como **vista de clases**, **Examinador de objetos**, **Examinador de llamadas** y **resultados de la búsqueda de símbolos**, le permiten ver símbolos en el proyecto o en los componentes externos. Los símbolos incluyen los espacios de nombres, clases, interfaces, métodos y otros elementos de lenguaje. Las bibliotecas de realizar un seguimiento de estos símbolos y exponerlos a la [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Administrador de objetos que rellena las herramientas con los datos.  
  
 El Administrador de objetos realiza un seguimiento de todas las bibliotecas disponibles. Cada biblioteca debe registrar con el Administrador de objetos antes de proporcionar los símbolos para las herramientas de exploración de símbolos.  
  
 Normalmente, registrar una biblioteca cuando se carga un paquete VSPackage. Sin embargo, puede realizarse en otro momento, según sea necesario. Anular el registro de la biblioteca cuando se cierra el VSPackage.  
  
 Para registrar una biblioteca, use el <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterLibrary%2A> método. En el caso de la biblioteca de código administrado, use el <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> método.  
  
 Para anular el registro de una biblioteca, use el <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.UnregisterLibrary%2A> método.  
  
 Para obtener una referencia al administrador de objetos, <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2>, pase el <xref:Microsoft.VisualStudio.Shell.Interop.SVsObjectManager> identificador al servicio `GetService` método.  
  
## <a name="registering-and-unregistering-a-library-with-the-object-manager"></a>Registrar y anular el registro de una biblioteca con el Administrador de objetos  
  
#### <a name="to-register-a-library-with-the-object-manager"></a>Para registrar una biblioteca con el Administrador de objetos  
  
1.  Crear una biblioteca.  
  
    ```vb  
    Private m_CallBrowserLibrary As CallBrowser.Library = Nothing  
    Private m_nLibraryCookie As UInteger = 0  
    ' Create Library.  
    m_CallBrowserLibrary = New CallBrowser.Library()  
    ```  
  
    ```csharp  
    private CallBrowser.Library m_CallBrowserLibrary = null;  
    private uint m_nLibraryCookie = 0;  
    // Create Library.  
    m_CallBrowserLibrary = new CallBrowser.Library();  
  
    ```  
  
2.  Obtener una referencia a un objeto de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2> escriba y llamar a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> método.  
  
    ```vb  
    Private Sub RegisterLibrary()  
        If m_nLibraryCookie <> 0 Then  
            Throw New Exception("Library already registered with Object Manager")  
        End If  
  
        ' Obtain a reference to IVsObjectManager2 type object.  
        Dim objManager As IVsObjectManager2 = TryCast(GetService(GetType(SVsObjectManager)), IVsObjectManager2)  
        If objManager Is Nothing Then  
            Throw New NullReferenceException("GetService failed for SVsObjectManager")  
        End If  
  
        Try  
            Dim hr As Integer = objManager.RegisterSimpleLibrary(m_CallBrowserLibrary, m_nLibraryCookie)  
            Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure(hr)  
        Catch e As Exception  
            ' Code to handle any CLS-compliant exception.  
            Trace.WriteLine(e.Message)  
            Throw  
        End Try  
    End Sub  
    ```  
  
    ```csharp  
    private void RegisterLibrary()  
    {  
        if (m_nLibraryCookie != 0)  
            throw new Exception("Library already registered with Object Manager");  
  
        // Obtain a reference to IVsObjectManager2 type object.  
        IVsObjectManager2 objManager =   
                          GetService(typeof(SVsObjectManager)) as IVsObjectManager2;  
        if (objManager == null)  
            throw new NullReferenceException("GetService failed for SVsObjectManager");  
  
        try  
        {  
            int hr =   
                objManager.RegisterSimpleLibrary(m_CallBrowserLibrary,   
                                                 out m_nLibraryCookie);  
                Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure(hr);  
        }  
        catch (Exception e)  
        {  
            // Code to handle any CLS-compliant exception.  
            Trace.WriteLine(e.Message);  
            throw;  
        }  
    }  
  
    ```  
  
#### <a name="to-unregister-a-library-with-the-object-manager"></a>Para anular el registro de una biblioteca con el Administrador de objetos  
  
1.  Obtener una referencia a un objeto de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2> escriba y llamar a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.UnregisterLibrary%2A> método.  
  
    ```vb  
    Private Sub UnregisterLibrary()  
        If m_nLibraryCookie <> 0 Then  
            ' Obtain a reference to IVsObjectManager2 type object.  
            Dim objManager As IVsObjectManager2 = TryCast(GetService(GetType(SVsObjectManager)), IVsObjectManager2)  
            If objManager Is Nothing Then  
                Throw New NullReferenceException("GetService failed for SVsObjectManager")  
            End If  
  
            Try  
                objManager.UnregisterLibrary(m_nLibraryCookie)  
            Catch e As Exception  
                ' Code to handle any CLS-compliant exception.  
                Trace.WriteLine(e.Message)  
                Throw  
            Finally  
                m_nLibraryCookie = 0  
            End Try  
        End If  
    End Sub  
    ```  
  
    ```csharp  
    private void UnregisterLibrary()  
    {  
        if (m_nLibraryCookie != 0)  
        {  
            // Obtain a reference to IVsObjectManager2 type object.  
            IVsObjectManager2 objManager = GetService(typeof(SVsObjectManager)) as IVsObjectManager2;  
            if (objManager == null)  
                throw new NullReferenceException("GetService failed for SVsObjectManager");  
  
            try  
            {  
                objManager.UnregisterLibrary(m_nLibraryCookie);  
            }  
            catch (Exception e)  
            {  
                // Code to handle any CLS-compliant exception.  
                Trace.WriteLine(e.Message);  
                throw;  
            }  
            finally  
            {  
                m_nLibraryCookie = 0;  
            }  
        }  
    }  
  
    ```  
  
## <a name="see-also"></a>Vea también  
 [Extensibilidad de servicio de lenguaje heredado](../../extensibility/internals/legacy-language-service-extensibility.md)   
 [Herramientas de exploración de símbolos de compatibilidad](../../extensibility/internals/supporting-symbol-browsing-tools.md)   
 [Exposición de listas de símbolos proporcionadas por la biblioteca al Administrador de objetos](../../extensibility/internals/how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager.md)

