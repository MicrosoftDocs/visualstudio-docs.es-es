---
title: Obtener una lista de fragmentos de código instalados (heredados) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- snippets, retrieving list
- code snippets, retrieving list
- GetSnippets method
ms.assetid: 7d142f8b-35b1-44c4-a13e-f89f6460c906
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 072827bbb9676ba49df5ccd69f329ea9b04c78b2
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72721655"
---
# <a name="walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation"></a>Tutorial: Obtención de una lista de fragmentos de código instalados (implementación heredada)
Un fragmento de código es un fragmento de código que se puede insertar en el búfer de origen con un comando de menú (que permite elegir entre una lista de fragmentos de código instalados) o mediante la selección de un acceso directo a un fragmento de código de una lista de finalización de IntelliSense.

 El método <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionManager.EnumerateExpansions%2A> obtiene todos los fragmentos de código para un GUID de lenguaje específico. Los métodos abreviados de los fragmentos de código se pueden insertar en una lista de finalización de IntelliSense.

 Consulte [compatibilidad con fragmentos de código en un servicio de lenguaje heredado](../../extensibility/internals/support-for-code-snippets-in-a-legacy-language-service.md) para obtener más información sobre la implementación de fragmentos de código en un servicio de lenguaje MPF (Managed Package Framework).

### <a name="to-retrieve-a-list-of-code-snippets"></a>Para recuperar una lista de fragmentos de código

1. En el código siguiente se muestra cómo obtener una lista de fragmentos de código para un lenguaje determinado. Los resultados se almacenan en una matriz de estructuras <xref:Microsoft.VisualStudio.TextManager.Interop.VsExpansion>. Este método usa el método estático de <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> para obtener la interfaz de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager> del servicio de <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>. Sin embargo, también puede usar el proveedor de servicios dado a su VSPackage y llamar al método <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A>.

    ```csharp
    using System;
    using System.Collections;
    using System.Runtime.InteropServices;
    using Microsoft.VisualStudio.Package;
    using Microsoft.VisualStudio.Shell;
    using Microsoft.VisualStudio.TextManager.Interop;

    [Guid("00000000-0000-0000-0000-000000000000")] //create a new GUID for the language service
    namespace TestLanguage
    {
        class TestLanguageService : LanguageService
        {
            private void GetSnippets(Guid languageGuid,
                                     ref ArrayList expansionsList)
            {
                IVsTextManager textManager = (IVsTextManager)Package.GetGlobalService(typeof(SVsTextManager));
                if (textManager != null)
                {
                    IVsTextManager2 textManager2 = (IVsTextManager2)textManager;
                    if (textManager2 != null)
                    {
                        IVsExpansionManager expansionManager = null;
                        textManager2.GetExpansionManager(out expansionManager);
                        if (expansionManager != null)
                        {
                            // Tell the environment to fetch all of our snippets.
                            IVsExpansionEnumeration expansionEnumerator = null;
                            expansionManager.EnumerateExpansions(languageGuid,
                            0,     // return all info
                            null,    // return all types
                            0,     // return all types
                            1,     // include snippets without types
                            0,     // do not include duplicates
                            out expansionEnumerator);
                            if (expansionEnumerator != null)
                            {
                                // Cache our expansions in a VsExpansion array
                                uint count   = 0;
                                uint fetched = 0;
                                VsExpansion expansionInfo = new VsExpansion();
                                IntPtr[] pExpansionInfo   = new IntPtr[1];

                                // Allocate enough memory for one VSExpansion structure. This memory is filled in by the Next method.
                                pExpansionInfo[0] = Marshal.AllocCoTaskMem(Marshal.SizeOf(expansionInfo));

                                expansionEnumerator.GetCount(out count);
                                for (uint i = 0; i < count; i++)
                                {
                                    expansionEnumerator.Next(1, pExpansionInfo, out fetched);
                                    if (fetched > 0)
                                    {
                                        // Convert the returned blob of data into a structure that can be read in managed code.
                                        expansionInfo = (VsExpansion)Marshal.PtrToStructure(pExpansionInfo[0], typeof(VsExpansion));

                                        if (!String.IsNullOrEmpty(expansionInfo.shortcut))
                                        {
                                            expansionsList.Add(expansionInfo);
                                        }
                                    }
                                }
                                Marshal.FreeCoTaskMem(pExpansionInfo[0]);
                            }
                        }
                    }
                }
            }
        }
    }
    ```

### <a name="to-call-the-getsnippets-method"></a>Para llamar al método GetSnippets

1. El método siguiente muestra cómo llamar al método `GetSnippets` al finalizar una operación de análisis. Se llama al método <xref:Microsoft.VisualStudio.Package.LanguageService.OnParseComplete%2A> después de una operación de análisis que se inició con la razón <xref:Microsoft.VisualStudio.Package.ParseReason>.

> [!NOTE]
> La lista de matrices de `expansionsList` se almacena en caché por motivos de rendimiento. Los cambios en los fragmentos de código no se reflejan en la lista hasta que el servicio de lenguaje se detenga y se vuelva a cargar (por ejemplo, al detener y reiniciar [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]).

```csharp
class TestLanguageService : LanguageService
{
    private ArrayList expansionsList;

    public override void OnParseComplete(ParseRequest req)
    {
        if (this.expansionsList == null)
        {
            this.expansionsList = new ArrayList();
            GetSnippets(this.GetLanguageServiceGuid(),
                ref this.expansionsList);
        }
    }
}
```

### <a name="to-use-the-snippet-information"></a>Para usar la información del fragmento de código

1. En el código siguiente se muestra cómo utilizar la información del fragmento de código devuelta por el método `GetSnippets`. Se llama al método `AddSnippets` desde el analizador en respuesta a cualquier motivo de análisis que se usa para rellenar una lista de fragmentos de código. Esto debe realizarse después de que se haya realizado el análisis completo por primera vez.

     El método `AddDeclaration` crea una lista de declaraciones que se muestra más adelante en una lista de finalización.

     La clase `TestDeclaration` contiene toda la información que se puede mostrar en una lista de finalización, así como el tipo de declaración.

    ```csharp
    class TestAuthoringScope : AuthoringScope
    {
        public void AddDeclarations(TestDeclaration declaration)
        {
            if (m_declarations == null)
                m_declarations = new List<TestDeclaration>();
            m_declarations.Add(declaration);
         }
    }
    class TestDeclaration
    {
        private string m_name;
        private string m_description;
        private string m_type;

        public TestDeclaration(string name, string desc, string type)
        {
            m_name = name;
            m_description = desc;
            m_type = type;
        }

    class TestLanguageService : LanguageService
    {
        internal void AddSnippets(ref TestAuthoringScope scope)
        {
            if (this.expansionsList != null && this.expansionsList.Count > 0)
            {
                int count = this.expansionsList.Count;
                for (int i = 0; i < count; i++)
                {
                    VsExpansion expansionInfo = (VsExpansion)this.expansionsList[i];
                    scope.AddDeclaration(new TestDeclaration(expansionInfo.title,
                         expansionInfo.description,
                         "snippet"));
                }
            }
        }
    }

    ```

## <a name="see-also"></a>Vea también
- [Compatibilidad con fragmentos de código en un servicio de lenguaje heredado](../../extensibility/internals/support-for-code-snippets-in-a-legacy-language-service.md)