---
title: Exponer objetos del proyecto | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project objects, exposing
- extensibility, project objects
ms.assetid: 5bb24967-434a-4ef4-87a0-2f3250c9e22d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4eaa2a5e8c5c153698069084b9f0cfe406cad7db
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="exposing-project-objects"></a>Exponer objetos del proyecto
Tipos de proyecto personalizadas pueden proporcionar objetos de automatización con el fin de permitir el acceso al proyecto mediante interfaces de automatización. Cada tipo de proyecto se espera que proporcione el estándar <xref:EnvDTE.Project> el objeto de automatización que se accede desde <xref:EnvDTE.Solution>, que contiene una colección de todos los proyectos que están abiertos en el IDE. Se espera que cada elemento en el proyecto que va a exponer un <xref:EnvDTE.ProjectItem> objeto obtiene acceso con `Project.ProjectItems`. Además de estos objetos de automatización estándar, pueden elegir proyectos ofrecer los objetos de automatización específicos del proyecto.  
  
 Puede crear objetos de automatización personalizada de nivel de raíz que puede tener acceso en tiempo de ejecución desde el objeto DTE de raíz utilizando `DTE.<customeObjectName>` o `DTE.GetObject("<customObjectName>")`. Por ejemplo, Visual C++ crea la colección de proyectos de específica del proyecto de C++ denominado "VCProjects" que se puede tener acceso mediante DTE. VCProjects o DTE. GetObject("VCProjects"). También puede crear un Project.Object, que es único para el tipo de proyecto, un Project.CodeModel, que se puede consultar para su objeto más derivado, que es un objeto ProjectItem, que expone ProjectItem.Object y un ProjectItem.FileCodeModel.  
  
 Es una convención común para los proyectos exponer una colección de proyectos personalizados, específicos del proyecto. Por ejemplo, [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] crea una colección de proyectos específicos de C++ que, a continuación, se puede tener acceso mediante `DTE.VCProjects` o `DTE.GetObject("VCProjects")`. También puede crear un `Project.Object`, que es único para el tipo de proyecto, un `Project.CodeModel`, que se puede consultar para su objeto más derivado, un `ProjectItem`, que expone `ProjectItem.Object`y un `ProjectItem.FileCodeModel`.  
  
### <a name="to-contribute-a-vspackage-specific-object-for-a-project"></a>Para contribuir a un objeto específico de VSPackage para un proyecto  
  
1.  Agregar las claves apropiadas para el archivo .pkgdef del paquete de VS.  
  
     Por ejemplo, esta es la configuración de .pkgdef para el proyecto de lenguaje C++:  
  
    ```  
    [$RootKey$\Packages\{F1C25864-3097-11D2-A5C5-00C04F7968B4}\Automation]  
    "VCProjects"=""  
    [$RootKey$\Packages\{F1C25864-3097-11D2-A5C5-00C04F7968B4}\AutomationEvents]  
    "VCProjectEngineEventsObject"=""  
    ```  
  
2.  Implementar el código en el <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> método, como en el ejemplo siguiente.  
  
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
  
     En el código, `g_wszAutomationProjects` es el nombre de la colección de proyectos. El `GetAutomationProjects` método crea un objeto que implementa el `Projects` interfaz y devuelve un `IDispatch` puntero al objeto que realiza la llamada, tal como se muestra en el ejemplo de código siguiente.  
  
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
  
     Debe elegir un nombre único para el objeto de automatización. Conflictos de nombres son impredecibles y las colisiones provocar un nombre de objeto en conflicto que se produce arbitrariamente si varios tipos de proyecto usan el mismo nombre. Debe incluir el nombre corporativo o algún aspecto único de su nombre de producto, el nombre del objeto de automatización.  
  
     Personalizado `Projects` objeto de colección es un punto de entrada de comodidad para la parte restante del modelo de automatización de proyecto. El objeto de proyecto también es accesible desde el <xref:EnvDTE.Solution> colección de proyectos. Una vez haya creado las entradas apropiadas de código y del registro que proporcionan los consumidores con `Projects` objetos de colección, debe proporcionar la implementación restantes objetos estándar para el modelo de proyecto. Para obtener más información, consulte [proyecto de modelado](../../extensibility/internals/project-modeling.md).  
  
## <a name="see-also"></a>Vea también  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>