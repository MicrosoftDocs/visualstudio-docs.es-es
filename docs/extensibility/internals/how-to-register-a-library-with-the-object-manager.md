---
title: 'Cómo: registrar una biblioteca con el administrador de objetos | Microsoft Docs'
description: Obtenga información sobre cómo registrar una biblioteca con el administrador de objetos de Visual Studio para que pueda ver símbolos en herramientas de exploración, como Vista de clases y Examinador de objetos.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- libraries, registering with object manager
- IVsLibrary2 interface, registering library with object manager
- IVsSimpleLibrary2 interface, registering library with object manager
- IVsObjectManager2 interface, registering library with object manager
- libraries, symbol-browsing tools
ms.assetid: f124dd05-cb0f-44ad-bb2a-7c0b34ef4038
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a5f4e9805eec8fd5d0089f1b8348253523d9056f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99925012"
---
# <a name="how-to-register-a-library-with-the-object-manager"></a>Cómo: registrar una biblioteca con el administrador de objetos
Las herramientas de exploración de símbolos, como **vista de clases**, **Examinador de objetos**, **Explorador de llamadas** y **Buscar los resultados** de los símbolos, permiten ver los símbolos del proyecto o de los componentes externos. Los símbolos incluyen espacios de nombres, clases, interfaces, métodos y otros elementos del lenguaje. Las bibliotecas realizan el seguimiento de estos símbolos y los exponen al [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Administrador de objetos que rellena las herramientas con los datos.

 El administrador de objetos realiza un seguimiento de todas las bibliotecas disponibles. Cada biblioteca se debe registrar con el administrador de objetos antes de proporcionar símbolos para las herramientas de exploración de símbolos.

 Normalmente, se registra una biblioteca cuando se carga un VSPackage. Sin embargo, se puede realizar en otro momento según sea necesario. Se anula el registro de la biblioteca cuando se cierra el VSPackage.

 Para registrar una biblioteca, use el <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterLibrary%2A> método. En el caso de una biblioteca de código administrado, utilice el <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> método.

 Para anular el registro de una biblioteca, use el <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.UnregisterLibrary%2A> método.

 Para obtener una referencia al administrador de objetos, <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2> , pase el <xref:Microsoft.VisualStudio.Shell.Interop.SVsObjectManager> identificador de servicio al `GetService` método.

## <a name="register-and-unregister-a-library-with-the-object-manager"></a>Registro y anulación del registro de una biblioteca con el administrador de objetos

### <a name="to-register-a-library-with-the-object-manager"></a>Para registrar una biblioteca con el administrador de objetos

1. Cree una biblioteca.

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

2. Obtenga una referencia a un objeto del <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2> tipo y llame al <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> método.

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

### <a name="to-unregister-a-library-with-the-object-manager"></a>Para anular el registro de una biblioteca con el administrador de objetos

1. Obtenga una referencia a un objeto del <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2> tipo y llame al <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.UnregisterLibrary%2A> método.

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
- [Extensibilidad del servicio de lenguaje heredado](../../extensibility/internals/legacy-language-service-extensibility.md)
- [Compatibilidad con herramientas de exploración de símbolos](../../extensibility/internals/supporting-symbol-browsing-tools.md)
- [Cómo: exponer listas de símbolos proporcionados por la biblioteca al administrador de objetos](../../extensibility/internals/how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager.md)
