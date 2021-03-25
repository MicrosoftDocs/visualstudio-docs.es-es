---
title: Secuencia de inicialización de subtipos de proyecto | Microsoft Docs
description: Obtenga información sobre la secuencia de inicialización en el entorno de Visual Studio para un sistema de proyectos agregado por varios subtipos de proyecto.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project subtypes, initialization sequence
ms.assetid: f657f8c3-5e68-4308-9971-e81e3099ba29
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 88a8aa39c513ed6317a6b57509810e16a58f192b
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105069548"
---
# <a name="initialization-sequence-of-project-subtypes"></a>Secuencia de inicialización de subtipos de proyecto
El entorno crea un proyecto mediante una llamada a la implementación del generador de proyectos base de <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A> . La construcción de un subtipo de proyecto se inicia cuando el entorno determina que la lista de GUID de tipo de proyecto para la extensión de un archivo de proyecto no está vacía. La extensión de archivo de proyecto y el GUID de proyecto especifican si el proyecto es un [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] tipo de proyecto de o [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] . Por ejemplo, la extensión. vbproj y {F184B08F-C81C-45F6-A57F-5ABD9991F28F} identifican un [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] proyecto.

## <a name="environments-initialization-of-project-subtypes"></a>Inicialización del entorno de subtipos de proyecto
 En el procedimiento siguiente se detalla la secuencia de inicialización de un sistema de proyectos agregado por varios subtipos de proyecto.

1. El entorno llama al del proyecto base <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A> y, mientras el proyecto analiza su archivo de proyecto, detecta que la lista de GUID de tipo de proyecto agregado no es `null` . El proyecto deja de crear directamente su proyecto.

2. El proyecto llama a `QueryService` en el <xref:Microsoft.VisualStudio.Shell.Interop.SVsCreateAggregateProject> servicio para crear un subtipo de proyecto utilizando la implementación del entorno del <xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A> método. Dentro de este método, el entorno realiza llamadas a funciones recursivas a las implementaciones de <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject%2A> y <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.InitializeForOuter%2A> métodos mientras está recorriendo la lista de GUID de tipo de proyecto, empezando por el subtipo de proyecto más externo.

     A continuación se detallan los pasos de inicialización.

    1. La implementación del entorno del <xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A> método llama al `HrCreateInnerProj` método con la siguiente declaración de función:

         \<CodeContentPlaceHolder>0</CodeContentPlaceHolder>

         Cuando se llama a esta función por primera vez, es decir, para el subtipo de proyecto más externo, los parámetros `pOuter` y `pOwner` se pasan como `null` y la función establece el subtipo de proyecto más externo `IUnknown` en `pOuter` .

    2. Después, el entorno llama a `HrCreateInnerProj` la función con el segundo GUID de tipo de proyecto en la lista. Este GUID corresponde al segundo subtipo de proyecto interno que se recorre hacia el proyecto base en la secuencia de agregación.

    3. `pOuter`Ahora apunta al `IUnknown` del subtipo de proyecto más externo y `HrCreateInnerProj` llama a la implementación de seguida de <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A> una llamada a la implementación de <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject%2A> . En <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A> el método, se pasa el control `IUnknown` del subtipo de proyecto más externo, `pOuter` . El proyecto de propiedad (subtipo de proyecto interno) debe crear aquí su objeto de proyecto agregado. En la <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject%2A> implementación del método, se pasa un puntero al `IUnknown` del proyecto interno que se va a agregar. Estos dos métodos crean el objeto de agregación y las implementaciones deben seguir las reglas de agregación COM para asegurarse de que un subtipo de proyecto no acabe manteniendo un recuento de referencias a sí mismo.

    4. `HrCreateInnerProj` llama a la implementación de <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A> . En este método, el subtipo de proyecto hace que su inicialización funcione. Por ejemplo, puede registrar eventos de la solución en <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.InitializeForOuter%2A> .

    5. `HrCreateInnerProj` se llama a de forma recursiva hasta que se alcanza el último GUID (el proyecto base) de la lista. Para cada una de estas llamadas, se repiten los pasos de c a d. `pOuter` apunta al subtipo `IUnknown` de proyecto más externo para cada nivel de agregación.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se detalla el proceso de programación en una representación aproximada del <xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A> método tal como se implementa en el entorno. El código es solo un ejemplo; no se ha diseñado para su compilación y se ha quitado toda la comprobación de errores para mayor claridad.

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

## <a name="see-also"></a>Consulte también

- <xref:Microsoft.VisualStudio.Shell.Flavor>
- [Subtipos de proyecto](../../extensibility/internals/project-subtypes.md)
