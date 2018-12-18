---
title: Secuencia de inicialización de subtipos de proyecto | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project subtypes, initialization sequence
ms.assetid: f657f8c3-5e68-4308-9971-e81e3099ba29
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: fe7e7a574d04ec9a49252e32e0fbb8b5685778aa
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31131618"
---
# <a name="initialization-sequence-of-project-subtypes"></a>Secuencia de inicialización de subtipos de proyecto
El entorno crea un proyecto mediante una llamada a la implementación del generador de proyectos de base de <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>. La construcción de un subtipo de proyecto se inicia cuando el entorno determina que la lista GUID de tipo de proyecto de extensión de un archivo de proyecto no está vacía. La extensión de archivo de proyecto y el GUID del proyecto especifican si el proyecto es un [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] o [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] tipo de proyecto. Por ejemplo, la extensión de archivo .vbproj y {F184B08F-C81C-45F6-A57F-5ABD9991F28F} identificar un [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] proyecto.

## <a name="environments-initialization-of-project-subtypes"></a>Inicialización del entorno de subtipos de proyecto
 El siguiente procedimiento detalla la secuencia de inicialización para un sistema de proyecto agregada por varios subtipos de proyecto.

1.  El entorno llama el proyecto de base <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>, y mientras el proyecto analiza el archivo de proyecto detecta que la lista de GUID de tipo de proyecto agregado no es `null`. El proyecto interrumpe la creación directa de su proyecto.

2.  Las llamadas de proyecto `QueryService` en <xref:Microsoft.VisualStudio.Shell.Interop.SVsCreateAggregateProject> servicio para crear un subtipo de proyecto mediante la implementación del entorno de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A> método. Dentro de este método, el entorno realiza llamadas a función recursiva para sus implementaciones del <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A>, <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject%2A> y <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.InitializeForOuter%2A> métodos mientras es recorrer la lista del proyecto de tipo GUID, a partir del subtipo de proyecto más externo.

     A continuación detalla los pasos de inicialización.

    1.  La implementación del entorno de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A> llamadas al método el `HrCreateInnerProj` método con la siguiente declaración de función:

         <CodeContentPlaceHolder>0</CodeContentPlaceHolder>

         Cuando esta función se llama por primera vez, es decir, para el subtipo de proyecto más externo, los parámetros `pOuter` y `pOwner` se pasan como `null` y la función establece el subtipo de proyecto exterior `IUnknown` a `pOuter`.

    2.  A continuación el entorno llama `HrCreateInnerProj` función con el segundo tipo de proyecto GUID en la lista. Este GUID se corresponde con el subtipo de proyecto interna segundo ejecución paso a paso hacia el proyecto de base de la secuencia de agregación.

    3.  El `pOuter` ahora apunta a la `IUnknown` del subtipo de proyecto más externo, y `HrCreateInnerProj` llama a la implementación de <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A> seguido por una llamada a la implementación de <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject%2A>. En <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A> método se pasa el control `IUnknown` del subtipo de proyecto más externo, `pOuter`. El propio proyecto (subtipo de proyecto interna) necesita para crear su objeto de proyecto agregado aquí. En el <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject%2A> implementación del método se pasa un puntero a la `IUnknown` del proyecto interno que se está agregando. Estos dos métodos crean el objeto de agregación y sus implementaciones deben seguir las reglas de agregación de COM para asegurarse de que un subtipo de proyecto no acabar mantiene un recuento de referencias a sí misma.

    4.  `HrCreateInnerProj` llama a la implementación de <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A>. En este método, el subtipo de proyecto realice su trabajo de inicialización. Por ejemplo, puede registrar eventos de la solución en <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.InitializeForOuter%2A>.

    5.  `HrCreateInnerProj` se llama de forma recursiva hasta que se alcance el último GUID (el proyecto de base) en la lista. Para cada una de estas llamadas, los pasos, c y d, se repiten. `pOuter` señala el subtipo de proyecto exterior `IUnknown` para cada nivel de agregación.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se detalla el proceso mediante programación en una representación aproximada de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A> método tal y como se implementa en el entorno. El código es solo un ejemplo; no está pensado para ser compilado y comprobación de todos los errores se ha quitado para mayor claridad.

```cpp
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

## <a name="see-also"></a>Vea también

- <xref:Microsoft.VisualStudio.Shell.Flavor>
- [Subtipos de proyecto](../../extensibility/internals/project-subtypes.md)