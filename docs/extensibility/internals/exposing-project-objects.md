---
title: Exponiendo objetos de proyecto | Microsoft Docs
description: Obtenga información sobre cómo exponer objetos para tipos de proyecto personalizados en Visual Studio proporcionando objetos de automatización que permiten el acceso al proyecto mediante interfaces de automatización.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project objects, exposing
- extensibility, project objects
ms.assetid: 5bb24967-434a-4ef4-87a0-2f3250c9e22d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c0ad045cb2cc46577c06d65e3ac1236228c870a9
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105069691"
---
# <a name="expose-project-objects"></a>Exponer objetos de proyecto

Los tipos de proyecto personalizados pueden proporcionar objetos de automatización para permitir el acceso al proyecto mediante interfaces de automatización. Se espera que cada tipo de proyecto proporcione el <xref:EnvDTE.Project> objeto de automatización estándar al que se tiene acceso desde <xref:EnvDTE.Solution> , que contiene una colección de todos los proyectos que están abiertos en el IDE. Un <xref:EnvDTE.ProjectItem> objeto al que se obtiene acceso con se espera que exponga cada elemento del proyecto `Project.ProjectItems` . Además de estos objetos de automatización estándar, los proyectos pueden elegir ofrecer objetos de automatización específicos del proyecto.

Puede crear objetos de automatización de nivel de raíz personalizados a los que puede tener acceso enlazados en tiempo de ejecución desde el objeto DTE raíz mediante `DTE.<customObjectName>` o `DTE.GetObject("<customObjectName>")` . Por ejemplo, Visual C++ crea una colección de proyectos específica del proyecto de C++ denominada *VCProjects* a la que se puede tener acceso mediante `DTE.VCProjects` o `DTE.GetObject("VCProjects")` . También puede crear un `Project.Object` , que es único para el tipo de proyecto, un `Project.CodeModel` , que se puede consultar para su objeto más derivado y `ProjectItem` , que expone `ProjectItem.Object` y `ProjectItem.FileCodeModel` .

Es una Convención común para que los proyectos expongan una colección de proyectos personalizada específica del proyecto. Por ejemplo, [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] crea una colección de proyectos específica de C++ a la que se puede tener acceso mediante `DTE.VCProjects` o `DTE.GetObject("VCProjects")` . También puede crear un `Project.Object` , que es único para el tipo de proyecto, un `Project.CodeModel` , que se puede consultar para su objeto más derivado, un `ProjectItem` , que expone `ProjectItem.Object` y `ProjectItem.FileCodeModel` .

## <a name="to-contribute-a-vspackage-specific-object-for-a-project"></a>Para aportar un objeto específico de VSPackage para un proyecto

1. Agregue las claves apropiadas al archivo *. pkgdef* del VSPackage.

     Por ejemplo, a continuación se muestra la configuración de *. pkgdef* para el proyecto del lenguaje C++:

    ```
    [$RootKey$\Packages\{F1C25864-3097-11D2-A5C5-00C04F7968B4}\Automation]
    "VCProjects"=""
    [$RootKey$\Packages\{F1C25864-3097-11D2-A5C5-00C04F7968B4}\AutomationEvents]
    "VCProjectEngineEventsObject"=""
    ```

2. Implemente el código en el <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> método, como en el ejemplo siguiente.

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

     En el código, `g_wszAutomationProjects` es el nombre de la colección de proyectos. El `GetAutomationProjects` método crea un objeto que implementa la `Projects` interfaz y devuelve un `IDispatch` puntero al objeto que realiza la llamada, como se muestra en el ejemplo de código siguiente.

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

     Elija un nombre único para el objeto de automatización. Los conflictos de nombres son imprevisibles y las colisiones provocan que un nombre de objeto conflictivo se inicie arbitrariamente si varios tipos de proyecto usan el mismo nombre. Debe incluir el nombre corporativo o algún aspecto único de su nombre de producto en el nombre del objeto de automatización.

     El `Projects` objeto de colección personalizada es un punto de entrada útil para la parte restante del modelo de automatización del proyecto. También se puede tener acceso al objeto de proyecto desde la <xref:EnvDTE.Solution> colección de proyectos. Una vez que haya creado el código adecuado y las entradas del registro que proporcionan a los consumidores `Projects` objetos de colección, su implementación debe proporcionar objetos estándar restantes para el modelo de proyecto. Para obtener más información, vea [modelado del proyecto](../../extensibility/internals/project-modeling.md).

## <a name="see-also"></a>Consulte también

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>
