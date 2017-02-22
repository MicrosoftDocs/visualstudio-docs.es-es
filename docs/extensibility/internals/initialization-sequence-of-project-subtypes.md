---
title: "Secuencia de inicializaci&#243;n de subtipos de proyecto | Microsoft Docs"
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
  - "subtipos de proyecto, la secuencia de inicialización"
ms.assetid: f657f8c3-5e68-4308-9971-e81e3099ba29
caps.latest.revision: 15
caps.handback.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
---
# Secuencia de inicializaci&#243;n de subtipos de proyecto
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

El entorno construye un proyecto llamando a la implementación base de generador de proyecto de <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>.  La construcción de un subtipo del proyecto se inicia cuando el entorno determina que la lista de GUID del tipo de proyecto para una extensión de archivo de proyecto no está vacía.  La extensión de archivo y el proyecto GUID del proyecto especifican si el proyecto es un tipo de proyecto de [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] o de[!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] .  Por ejemplo, la extensión .vbproj y {F184B08F\- C81 C\-45F6\-A57F\-5ABD9991F28F} identifica un proyecto de [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] .  
  
## La inicialización del entorno del proyecto Subtypes  
 Los siguientes del procedimiento que la secuencia de inicialización para un sistema de proyectos agregadas por subtipos varios del proyecto.  
  
1.  El entorno llama al <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>base del proyecto, y mientras el proyecto analiza el archivo de proyecto se detecta que la lista global de GUID del tipo de proyecto no es `null`.  El proyecto interrumpe directamente la creación del proyecto.  
  
2.  El proyecto llama `QueryService` en el servicio de <xref:Microsoft.VisualStudio.Shell.Interop.SVsCreateAggregateProject> para crear un subtipo del proyecto mediante la implementación del entorno del método de <xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A> .  En este método el entorno realiza llamadas de función recursiva a las implementaciones de <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A>, de `M:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject(System.Object)` y métodos de <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.InitializeForOuter%2A> mientras está recorriendo la lista de tipos de proyecto GUID, empezando por el subtipo fuera del proyecto.  
  
     Los siguientes pasos de inicialización.  
  
    1.  La implementación del entorno del método de `HrCreateInnerProj```de las llamadas al método de <xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A> con la siguiente declaración de función:  
  
<CodeContentPlaceHolder>0</CodeContentPlaceHolder>  
         Cuando esta función se denomina por primera vez, es decir, para el subtipo fuera del proyecto, los parámetros `pOuter` y `pOwner` se pasan en como `null` y la función establece el subtipo fuera `IUnknown` a `pOuter`.  
  
    2.  El Siguiente el entorno llama a la función de `HrCreateInnerProj` con el segundo tipo de proyecto GUID en la lista.  Este GUID corresponde al segundo subtipo interno de proyecto que entra en hacia el proyecto basado en la secuencia de agregación.  
  
    3.  `pOuter` ahora apunta al `IUnknown` de subtipo fuera del proyecto, y las llamadas de `HrCreateInnerProj` que la implementación de <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A> seguido por una llamada a la implementación de <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject%2A>.  En el método de <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A> se pasa `IUnknown` controladora de subtipo fuera del proyecto, `pOuter`.  El proyecto propiedad \(subtipo interno de proyecto\) es necesario crear un objeto global del proyecto aquí.  En la implementación del método de <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject%2A> se pasa un puntero a `IUnknown` de proyecto interno se suma que.  Estos dos métodos crean el objeto de agregación, y las implementaciones deben seguir reglas COM de agregación para garantizar que un subtipo del proyecto no termina hacia arriba mantener un recuento de referencia a sí mismo.  
  
    4.  `HrCreateInnerProj` llama a la implementación de <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A>.  En este método, subtipo de proyecto realiza su trabajo de inicialización.  Puede, por ejemplo, registrar eventos de la solución en <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.InitializeForOuter%2A>.  
  
    5.  `HrCreateInnerProj` se llama de forma recursiva hasta que GUID pasado \(el proyecto base\) en la lista se alcance.  Para cada una de estas llamadas, se repiten los pasos, c a d.  puntos de`pOuter` el subtipo fuera `IUnknown` de cada nivel de agregación.  
  
 Los detalles de ejemplo siguientes el proceso de programación en una representación aproximada del método de <xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A> como es implementado por el entorno.  El código es simplemente un ejemplo; no pretende ser compilado y toda la comprobación de errores se quitó para mayor claridad.  
  
## Ejemplo  
  
### Código  
  
```  
HRESULT CreateAggregateProject  
(  
    LPCOLESTR lpstrGuids,   
    LPCOLESTR pszFilename,   
    LPCOLESTR pszLocation,  
    LPCOLESTR pszName,   
    VSCREATEPROJFLAGS grfCreateFlags,   
    REFIID iidProject,   
    void **ppvProject)  
{  
    HRESULT hr = NOERROR;  
    CComPtr<IUnknown> srpunkProj;  
    CComPtr<IVsAggregatableProject> srpAggProject;  
    CComBSTR bstrGuids = lpstrGuids;  
    BOOL fCanceled = FALSE;  
    *ppvProject = NULL;  
  
    HrCreateInnerProj(  
         bstrGuids, NULL, NULL, pszFilename, pszLocation,   
         pszName, grfCreateFlags, &srpunkProj, &fCanceled);  
    srpunkProj->QueryInterface(  
        IID_IVsAggregatableProject, (void **)&srpAggProject));  
    srpAggProject->OnAggregationComplete();  
    srpunkProj->QueryInterface(iidProject, ppvProject);  
}  
  
HRESULT HrCreateInnerProj  
(  
    WCHAR *pwszGuids,   
    IUnknown *pOuter,   
    IVsAggregatableProject *pOwner,   
    LPCOLESTR pszFilename,   
    LPCOLESTR pszLocation,  
    LPCOLESTR pszName,   
    VSCREATEPROJFLAGS grfCreateFlags,   
    IUnknown **ppInner,   
    BOOL *pfCanceled  
)  
{  
    HRESULT hr = NOERROR;  
    CComPtr<IUnknown> srpInner;  
    CComPtr<IVsAggregatableProject> srpAggInner;  
    CComPtr<IVsProjectFactory> srpProjectFactory;  
    CComPtr<IVsAggregatableProjectFactory> srpAggPF;  
    GUID guid = GUID_NULL;  
    WCHAR *pwszNextGuids = wcschr(pwszGuids, L';');  
    WCHAR wszText[_MAX_PATH+150] = L"";  
  
    if (pwszNextGuids)  
    {  
        *pwszNextGuids++ = 0;  
    }  
  
    CLSIDFromString(pwszGuids, &guid);  
    GetProjectTypeMgr()->HrGetProjectFactoryOfGuid(  
        guid, &srpProjectFactory);  
    srpProjectFactory->QueryInterface(  
        IID_IVsAggregatableProjectFactory,   
        (void **)&srpAggPF);  
    srpAggPF->PreCreateForOuter(pOuter, &srpInner);  
    srpInner->QueryInterface(  
        IID_IVsAggregatableProject, (void **)&srpAggInner);  
  
    if (pOwner)  
    {  
        IfFailGo(pOwner->SetInnerProject(srpInner));  
    }  
  
    if (pwszNextGuids)  
    {  
        CComPtr<IUnknown> srpNextInner;  
        HrCreateInnerProj(  
            pwszNextGuids, pOuter ? pOuter : srpInner,   
            srpAggInner, pszFilename, pszLocation, pszName,   
            grfCreateFlags, &srpNextInner, pfCanceled);  
    }  
  
    return srpAggInner->InitializeForOuter(  
        pszFilename, pszLocation, pszName, grfCreateFlags,   
        IID_IUnknown, (void **)ppInner, pfCanceled);  
}  
```  
  
## Vea también  
 <xref:Microsoft.VisualStudio.Shell.Flavor>   
 [Subtipos de proyecto](../../extensibility/internals/project-subtypes.md)