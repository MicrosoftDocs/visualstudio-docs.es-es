---
title: "Exponer objetos de proyecto | Microsoft Docs"
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
  - "objetos de proyectos de exposición"
  - "objetos de proyectos de extensibilidad"
ms.assetid: 5bb24967-434a-4ef4-87a0-2f3250c9e22d
caps.latest.revision: 17
caps.handback.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
---
# Exponer objetos de proyecto
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Tipos de proyecto personalizadas pueden proporcionar objetos de automatización con el fin de permitir el acceso al proyecto mediante las interfaces de automatización. Se espera que cada tipo de proyecto proporcionan el estándar <xref:EnvDTE.Project> objeto de automatización que se accede desde <xref:EnvDTE.Solution>, que contiene una colección de todos los proyectos que están abiertos en el IDE. Cada elemento en el proyecto debe exponer una <xref:EnvDTE.ProjectItem> acceso a él con el objeto <xref:Project.ProjectItems>. Además de estos objetos de automatización estándar, pueden elegir proyectos proporcionan objetos de automatización específicos del proyecto.  
  
 Puede crear objetos de automatización personalizada de nivel de raíz que puede tener acceso en tiempo de ejecución desde el objeto DTE de raíz mediante `DTE.<customeObjectName>` o `DTE.GetObject(“<customObjectName>”)`. Por ejemplo, Visual C\+\+ crea la colección de proyectos de específicas del proyecto de C\+\+ llamado "VCProjects" que puede tener acceso mediante DTE. VCProjects o DTE. GetObject\("VCProjects"\). También puede crear un Project.Object, que es único para el tipo de proyecto, un Project.CodeModel, que puede consultarse para su objeto más derivado, un objeto ProjectItem, que expone ProjectItem.Object y un ProjectItem.FileCodeModel.  
  
 Es una convención común para los proyectos exponer una colección de proyectos personalizados, específicos del proyecto. Por ejemplo, [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] crea una colección de proyectos específicos de C\+\+ que permite el acceso mediante `DTE.VCProjects` o `DTE.GetObject("VCProjects")`. También puede crear un `Project.Object`, que es único para el tipo de proyecto, un `Project.CodeModel`, que se puede consultar para su objeto más derivado, un `ProjectItem`, que expone `ProjectItem.Object`, y un `ProjectItem.FileCodeModel`.  
  
### Para contribuir a un objeto específico de VSPackage para un proyecto  
  
1.  Agregue las claves apropiadas para el archivo .pkgdef de su paquete VSPackage.  
  
     Por ejemplo, aquí son los valores de .pkgdef para el proyecto de lenguaje C\+\+:  
  
    ```  
    [$RootKey$\Packages\{F1C25864-3097-11D2-A5C5-00C04F7968B4}\Automation] "VCProjects"="" [$RootKey$\Packages\{F1C25864-3097-11D2-A5C5-00C04F7968B4}\AutomationEvents] "VCProjectEngineEventsObject"=""  
    ```  
  
2.  Implementar el código en el <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> método, como en el ejemplo siguiente.  
  
    ```cpp  
    STDMETHODIMP CVsPackage::GetAutomationObject( /* [in]  */ LPCOLESTR       pszPropName, /* [out] */ IDispatch **    ppIDispatch) { ExpectedPtrRet(pszPropName); ExpectedPtrRet(ppIDispatch); *ppIDispatch = NULL; if (m_fZombie) return E_UNEXPECTED; if (_wcsicmp(pszPropName, g_wszAutomationProjects) == 0) { return GetAutomationProjects(ppIDispatch); } else if (_wcsicmp(pszPropName, g_wszAutomationProjectsEvents) == 0) { return CAutomationEvents::GetAutomationEvents(ppIDispatch); } else if (_wcsicmp(pszPropName, g_wszAutomationProjectItemsEvents) == 0) { return CAutomationEvents::GetAutomationEvents(ppIDispatch); } return E_INVALIDARG; }   
    ```  
  
     En el código, `g_wszAutomationProjects` es el nombre de la colección de proyectos. El `GetAutomationProjects` método crea un objeto que implementa el `Projects` interfaz y devuelve un `IDispatch` puntero al objeto que realiza la llamada, como se muestra en el ejemplo de código siguiente.  
  
    ```cpp  
    HRESULT CVsPackage::GetAutomationProjects(/* [out] */ IDispatch ** ppIDispatch) { ExpectedPtrRet(ppIDispatch); *ppIDispatch = NULL; if (!m_srpAutomationProjects) { HRESULT hr = CACProjects::CreateInstance(&m_srpAutomationProjects); IfFailRet(hr); ExpectedExprRet(m_srpAutomationProjects != NULL); } return m_srpAutomationProjects.CopyTo(ppIDispatch); }  
    ```  
  
     Debe elegir un nombre único para el objeto de automatización. Conflictos de nombre están imprevisibles y colisiones hace que un nombre de objeto en conflicto se arbitrariamente producirá si varios tipos de proyectos utilizan el mismo nombre. Debe incluir el nombre corporativo o algún aspecto único de su nombre de producto, el nombre del objeto de automatización.  
  
     Personalizado `Projects` objeto de colección es un punto de entrada de la comodidad de la parte restante del modelo de automatización de proyecto. El objeto de proyecto también es accesible desde el <xref:EnvDTE.Solution> colección de proyectos. Después de haber creado el correspondientes código y entradas del registro que proporcionan a los consumidores con `Projects` objetos de colección, debe proporcionar la implementación quedan objetos estándar para el modelo de proyecto. Para obtener más información, consulta [Modelo de proyecto](../../extensibility/internals/project-modeling.md).  
  
## Vea también  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>