---
title: Exponer objetos del proyecto | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project objects, exposing
- extensibility, project objects
ms.assetid: 5bb24967-434a-4ef4-87a0-2f3250c9e22d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 16a9c34d06cc94e3c9fb41fa3cc09b12b7349849
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54992898"
---
# <a name="expose-project-objects"></a>Exponer objetos del proyecto

Tipos de proyecto personalizado pueden proporcionar objetos de automatización con el fin de permitir el acceso al proyecto mediante interfaces de automatización. Cada tipo de proyecto se espera que proporcione el estándar <xref:EnvDTE.Project> objeto de automatización que se accede desde <xref:EnvDTE.Solution>, que contiene una colección de todos los proyectos que están abiertos en el IDE. Cada elemento en el proyecto debe exponerse mediante un <xref:EnvDTE.ProjectItem> objeto obtiene acceso con `Project.ProjectItems`. Además de estos objetos de automatización estándar, pueden elegir los proyectos ofrecer a los objetos de automatización específicos del proyecto.

Puede crear objetos de automatización de nivel de raíz personalizada que puede tener acceso en tiempo de ejecución desde el objeto DTE de raíz mediante `DTE.<customObjectName>` o `DTE.GetObject("<customObjectName>")`. Por ejemplo, Visual C++ crea una colección de proyectos específicos del proyecto de C++ denominada *VCProjects* que puede tener acceso mediante `DTE.VCProjects` o `DTE.GetObject("VCProjects")`. También puede crear un `Project.Object`, que es único para el tipo de proyecto, un `Project.CodeModel`, que se puede consultar para su objeto más derivado y un `ProjectItem`, que expone `ProjectItem.Object` y un `ProjectItem.FileCodeModel`.

Es una convención común para los proyectos exponer una colección de proyectos personalizados, específicos del proyecto. Por ejemplo, [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] crea una colección de proyectos específicos de C++ que, a continuación, se puede acceder mediante `DTE.VCProjects` o `DTE.GetObject("VCProjects")`. También puede crear un `Project.Object`, que es único para el tipo de proyecto, un `Project.CodeModel`, que se puede consultar para su objeto más derivado, un `ProjectItem`, que expone `ProjectItem.Object`y un `ProjectItem.FileCodeModel`.  
  
## <a name="to-contribute-a-vspackage-specific-object-for-a-project"></a>Para contribuir a un objeto específico de VSPackage para un proyecto  
  
1.  Agregar las claves apropiadas para la *.pkgdef* archivo del paquete VSPackage.  
  
     Por ejemplo, estos son los *.pkgdef* configuración para el proyecto de lenguaje C++:  
  
    ```  
    [$RootKey$\Packages\{F1C25864-3097-11D2-A5C5-00C04F7968B4}\Automation]  
    "VCProjects"=""  
    [$RootKey$\Packages\{F1C25864-3097-11D2-A5C5-00C04F7968B4}\AutomationEvents]  
    "VCProjectEngineEventsObject"=""  
    ```  
  
2.  Implemente el código en el <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> método, como en el ejemplo siguiente.  
  
    ```cpp  
    STDMETHODIMP CVsPackage::GetAutomationObject(  
    /* [in]  */ LPCOLESTR       pszPropName,   
    /* [out] */ IDispatch **    ppIDispatch)  
    {  
    ExpectedPtrRet(pszPropName);  
    ExpectedPtrRet(ppIDispatch);  
    *ppIDispatch = NULL;  
  
        if (m_fZombie)  
            return E_UNEXPECTED;  
  
        if (_wcsicmp(pszPropName, g_wszAutomationProjects) == 0)  
        {  
            return GetAutomationProjects(ppIDispatch);  
        }  
        else if (_wcsicmp(pszPropName, g_wszAutomationProjectsEvents) == 0)  
        {  
            return CAutomationEvents::GetAutomationEvents(ppIDispatch);  
        }  
        else if (_wcsicmp(pszPropName, g_wszAutomationProjectItemsEvents) == 0)  
        {  
            return CAutomationEvents::GetAutomationEvents(ppIDispatch);  
        }  
        return E_INVALIDARG;  
    }   
    ```  
  
     En el código, `g_wszAutomationProjects` es el nombre de la colección de proyectos. El `GetAutomationProjects` método crea un objeto que implementa el `Projects` interfaz y devuelve un `IDispatch` puntero al objeto que realiza la llamada, como se muestra en el siguiente ejemplo de código.  
  
    ```cpp  
    HRESULT CVsPackage::GetAutomationProjects(/* [out] */ IDispatch ** ppIDispatch)  
    {  
        ExpectedPtrRet(ppIDispatch);  
        *ppIDispatch = NULL;  
  
        if (!m_srpAutomationProjects)  
        {  
            HRESULT hr = CACProjects::CreateInstance(&m_srpAutomationProjects);  
            IfFailRet(hr);  
            ExpectedExprRet(m_srpAutomationProjects != NULL);  
        }  
        return m_srpAutomationProjects.CopyTo(ppIDispatch);  
    }  
    ```  
  
     Elija un nombre único para el objeto de automatización. Conflictos de nombres están imprevisibles y colisiones causar un nombre de objeto en conflicto que se produzca arbitrariamente si varios tipos de proyectos utilizan el mismo nombre. Debe incluir el nombre corporativo o algunos aspectos únicos de su nombre de producto, el nombre del objeto de automatización.  
  
     Personalizado `Projects` objeto de colección es un punto de entrada de la comodidad de la parte restante de su modelo de automatización de proyecto. El objeto de proyecto también es accesible desde el <xref:EnvDTE.Solution> la colección de proyectos. Después de haber creado las entradas apropiadas de código y del registro que proporcionan los consumidores con `Projects` colección de objetos, debe proporcionar su implementación quedan objetos estándar para el modelo de proyecto. Para obtener más información, consulte [modelado proyecto](../../extensibility/internals/project-modeling.md).  
  
## <a name="see-also"></a>Vea también

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>
