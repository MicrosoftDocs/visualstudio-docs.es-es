---
title: "C&#243;mo: registrar una biblioteca con el Administrador de objetos | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "bibliotecas de registro con el Administrador de objetos"
  - "Interfaz IVsLibrary2, registrar la biblioteca con el Administrador de objetos"
  - "Interfaz IVsSimpleLibrary2, registrar la biblioteca con el Administrador de objetos"
  - "Interfaz IVsObjectManager2, registrar la biblioteca con el Administrador de objetos"
  - "bibliotecas de herramientas de exploración de símbolos"
ms.assetid: f124dd05-cb0f-44ad-bb2a-7c0b34ef4038
caps.latest.revision: 26
caps.handback.revision: 26
ms.author: "gregvanl"
manager: "ghogen"
---
# C&#243;mo: registrar una biblioteca con el Administrador de objetos
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Símbolo\-examinando herramientas, como **Vista de clases**, **Examinador de objetos**, **Explorador de llamadas** y **Resultados de la búsqueda de símbolos**, permiten ver símbolos en el proyecto o en componentes externos.  Los símbolos incluyen espacios de nombres, clases, interfaces, métodos, y otros elementos del lenguaje.  Las bibliotecas siga estos símbolos y los exponen el administrador de objetos de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] que rellena las herramientas con los datos.  
  
 El administrador de objetos realiza un seguimiento de todas las bibliotecas disponible.  Cada biblioteca debe registrar con el administrador de objetos antes de proporcionar los símbolos para las herramientas símbolo\-que examinan.  
  
 Normalmente, registra una biblioteca cuando se cargue un paquete VSPackage.  Sin embargo, puede realizarse en otra hora según sea necesario.  Puede anular la biblioteca cuando el Paquete se cierra.  
  
 Para registrar una biblioteca, use el método de <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterLibrary%2A> .  En el caso de la biblioteca de código administrado, utilice el método de <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> .  
  
 Anular el registro de una biblioteca, se utiliza el método de <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.UnregisterLibrary%2A> .  
  
 Para obtener una referencia al administrador de objetos, <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2>, pasa el identificador de servicio de <xref:Microsoft.VisualStudio.Shell.Interop.SVsObjectManager> al método de `GetService` .  
  
## Registrar y anular una biblioteca con el administrador de objetos  
  
#### para registrar una biblioteca con el administrador de objetos  
  
1.  cree una biblioteca.  
  
    ```vb#  
    Private m_CallBrowserLibrary As CallBrowser.Library = Nothing  
    Private m_nLibraryCookie As UInteger = 0  
    ' Create Library.  
    m_CallBrowserLibrary = New CallBrowser.Library()  
    ```  
  
    ```c#  
    private CallBrowser.Library m_CallBrowserLibrary = null;  
    private uint m_nLibraryCookie = 0;  
    // Create Library.  
    m_CallBrowserLibrary = new CallBrowser.Library();  
  
    ```  
  
2.  Obtener una referencia a un objeto de <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2> escrito y llame al método de <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> .  
  
    ```vb#  
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
  
    ```c#  
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
  
#### Al anular una biblioteca con el administrador de objetos  
  
1.  Obtener una referencia a un objeto de <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2> escrito y llame al método de <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.UnregisterLibrary%2A> .  
  
    ```vb#  
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
  
    ```c#  
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
  
## Vea también  
 [Extensibilidad de servicio de lenguaje heredado](../../extensibility/internals/legacy-language-service-extensibility.md)   
 [Compatibilidad con herramientas de exploración de símbolos](../../extensibility/internals/supporting-symbol-browsing-tools.md)   
 [Cómo: exponer listas de símbolos proporcionadas por la biblioteca al administrador de objetos](../../extensibility/internals/how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager.md)