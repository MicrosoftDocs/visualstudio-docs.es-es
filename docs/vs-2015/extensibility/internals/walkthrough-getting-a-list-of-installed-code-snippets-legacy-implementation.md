---
title: 'Tutorial: Obtener una lista de instalado fragmentos de código (implementación heredada) | Microsoft Docs'
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
- snippets, retrieving list
- code snippets, retrieving list
- GetSnippets method
ms.assetid: 7d142f8b-35b1-44c4-a13e-f89f6460c906
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a8d132de9773614b966b6fe3a7ae84392fba4f35
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51759980"
---
# <a name="walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation"></a>Tutorial: Obtención de una lista de fragmentos de código instalados (implementación heredada)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Un fragmento de código es un fragmento de código que se puede insertar en el búfer de origen con un comando de menú (que permite elegir entre una lista de fragmentos de código instalados) o mediante la selección de un método abreviado de fragmento de código de una lista de finalización de IntelliSense.  
  
 El <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionManager.EnumerateExpansions%2A> método obtiene todos los fragmentos de código para un idioma específico de GUID. Los métodos abreviados para esos fragmentos de código se pueden insertar en una lista de finalización de IntelliSense.  
  
 Consulte [compatibilidad con fragmentos de código en un servicio de lenguaje heredado](../../extensibility/internals/support-for-code-snippets-in-a-legacy-language-service.md) para obtener más información sobre la implementación de fragmentos de código en un servicio de lenguaje de paquetes administrados framework (MPF).  
  
### <a name="to-retrieve-a-list-of-code-snippets"></a>Para recuperar una lista de fragmentos de código  
  
1.  El código siguiente muestra cómo obtener una lista de fragmentos de código para un idioma determinado. Los resultados se almacenan en una matriz de <xref:Microsoft.VisualStudio.TextManager.Interop.VsExpansion> estructuras. Este método usa estático <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> método para obtener el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager> interfaz desde el <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager> service. Sin embargo, también puede usar el proveedor de servicios dado su VSPackage y la llamada la <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> método.  
  
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
  
1.  El método siguiente muestra cómo llamar a la `GetSnippets` método al finalizar una operación de análisis. El <xref:Microsoft.VisualStudio.Package.LanguageService.OnParseComplete%2A> se llama al método después de una operación de análisis que se inició con el motivo <xref:Microsoft.VisualStudio.Package.ParseReason>.  
  
> [!NOTE]
>  El `expansionsList` listis almacenado en caché por motivos de rendimiento de la matriz. No se reflejan los cambios realizados en los fragmentos de código en la lista hasta que se detiene y se vuelve a cargar el servicio de lenguaje (por ejemplo, al detener y reiniciar [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]).  
  
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
  
### <a name="to-use-the-snippet-information"></a>Para usar la información de fragmento de código  
  
1.  El código siguiente muestra cómo usar la información de fragmento de código devuelta por la `GetSnippets` método. El `AddSnippets` se llama al método del analizador en respuesta a alguna razón de análisis que se usa para rellenar una lista de fragmentos de código. Esto debe tener lugar después de que se ha realizado el análisis completo por primera vez.  
  
     El `AddDeclaration` método genera una lista de declaraciones que se muestra más adelante en una lista de finalización.  
  
     La `TestDeclaration` clase contiene toda la información que se puede mostrar en una lista de finalización, así como el tipo de declaración.  
  
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
 [Compatibilidad con fragmentos de código en un servicio de lenguaje heredado](../../extensibility/internals/support-for-code-snippets-in-a-legacy-language-service.md)

