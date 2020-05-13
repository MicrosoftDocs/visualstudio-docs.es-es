---
title: Secuencia de inicialización de subtipos de proyecto ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project subtypes, initialization sequence
ms.assetid: f657f8c3-5e68-4308-9971-e81e3099ba29
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 05a3c312f61dd2b2c63c3f38ef8bac2203b326db
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707628"
---
# <a name="initialization-sequence-of-project-subtypes"></a>Secuencia de inicialización de subtipos de proyecto
El entorno construye un proyecto llamando a <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>la implementación de la fábrica del proyecto base de . La construcción de un subtipo de proyecto se inicia cuando el entorno determina que la lista GUID de tipo de proyecto para la extensión de un archivo de proyecto no está vacía. La extensión de archivo de proyecto y [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] el GUID del proyecto especifican si el proyecto es un tipo o un tipo de proyecto. Por ejemplo, la extensión .vbproj y el valor de .F184B08F-C81C-45F6-A57F-5ABD9991F28F identifican un [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] proyecto.

## <a name="environments-initialization-of-project-subtypes"></a>La inicialización del entorno de los subtipos de proyecto
 El siguiente procedimiento detalla la secuencia de inicialización de un sistema de proyectos agregado por varios subtipos de proyecto.

1. El entorno llama al <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>proyecto base y, mientras el proyecto analiza su archivo de proyecto, `null`detecta que la lista de GUID de tipo de proyecto agregado no es . El proyecto deja de crear directamente su proyecto.

2. El proyecto `QueryService` <xref:Microsoft.VisualStudio.Shell.Interop.SVsCreateAggregateProject> llama a service para crear un subtipo <xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A> de proyecto mediante la implementación del entorno del método. Dentro de este método, el entorno realiza <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A>llamadas de función recursivas a las implementaciones de , <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject%2A> y <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.InitializeForOuter%2A> métodos mientras camina por la lista de GUID de tipo de proyecto, empezando por el subtipo de proyecto más externo.

     A continuación se detallan los pasos de inicialización.

    1. La implementación del <xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A> método del `HrCreateInnerProj` entorno llama al método con la siguiente declaración de función:

         \<CodeContentPlaceHolder>0</CodeContentPlaceHolder>

         Cuando se llama a esta función por primera vez, es decir, `pOwner` para el `null` subtipo de proyecto más externo, los parámetros `pOuter` y se pasan como y la función establece el subtipo `IUnknown` de proyecto más externo en `pOuter`.

    2. A continuación, `HrCreateInnerProj` el entorno llama a la función con el segundo GUID de tipo de proyecto en la lista. Este GUID corresponde al segundo subtipo de proyecto interno que interpone paso a paso hacia el proyecto base en la secuencia de agregación.

    3. Ahora `pOuter` apunta al `IUnknown` subtipo de proyecto más `HrCreateInnerProj` externo y <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A> llama a la implementación <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject%2A>de seguida de una llamada a la implementación de . En <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A> el método se `IUnknown` pasa el control del `pOuter`subtipo de proyecto más externo, . El proyecto de propiedad (subtipo de proyecto interno) debe crear su objeto de proyecto agregado aquí. En <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject%2A> la implementación del método `IUnknown` se pasa un puntero al proyecto interno que se está agregando. Estos dos métodos crean el objeto de agregación y las implementaciones deben seguir las reglas de agregación COM para asegurarse de que un subtipo de proyecto no termina manteniendo un recuento de referencias para sí mismo.

    4. `HrCreateInnerProj`llama a <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A>su implementación de . En este método, el subtipo de proyecto realiza su trabajo de inicialización. Por ejemplo, puede registrar eventos <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.InitializeForOuter%2A>de solución en .

    5. `HrCreateInnerProj`se llama recursivamente hasta que se alcanza el último GUID (el proyecto base) de la lista. Para cada una de estas llamadas, se repiten los pasos, c a d. `pOuter`apunta al subtipo `IUnknown` de proyecto más externo para cada nivel de agregación.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se detalla <xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A> el proceso de programación en una representación aproximada del método a medida que lo implementa el entorno. El código es solo un ejemplo; no está destinado a ser compilado, y toda la comprobación de errores se eliminó para mayor claridad.

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
