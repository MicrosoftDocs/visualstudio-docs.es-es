---
title: Exponer objetos de proyecto | Microsoft Docs
description: Obtenga información sobre cómo exponer objetos para tipos de proyecto personalizados en Visual Studio proporcionando objetos de automatización que permiten el acceso al proyecto mediante interfaces de automatización.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- project objects, exposing
- extensibility, project objects
ms.assetid: 5bb24967-434a-4ef4-87a0-2f3250c9e22d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c3e89b4c80d64bedb77e68c648ba993794f8b658
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898297"
---
# <a name="expose-project-objects"></a>Exposición de objetos de proyecto

Los tipos de proyecto personalizados pueden proporcionar objetos de automatización para permitir el acceso al proyecto mediante interfaces de automatización. Se espera que cada tipo de proyecto proporcione el objeto de automatización estándar al que se tiene acceso desde , que contiene una colección de todos los proyectos que están <xref:EnvDTE.Project> <xref:EnvDTE.Solution> abiertos en el IDE. Se espera que un objeto al que se tiene acceso con exponga cada <xref:EnvDTE.ProjectItem> elemento del `Project.ProjectItems` proyecto. Además de estos objetos de automatización estándar, los proyectos pueden optar por ofrecer objetos de automatización específicos del proyecto.

Puede crear objetos de automatización de nivel raíz personalizados a los que puede acceder enlazados en tiempo de tiempo desde el objeto DTE raíz mediante `DTE.<customObjectName>` o `DTE.GetObject("<customObjectName>")` . Por ejemplo, Visual C++ crea una colección de proyectos específica del proyecto de C++ denominada *VCProjects* a la que se puede acceder mediante `DTE.VCProjects` o `DTE.GetObject("VCProjects")` . También puede crear un , que es único para el tipo de proyecto, , que se puede consultar para su objeto más derivado, y , que expone y `Project.Object` `Project.CodeModel` `ProjectItem` `ProjectItem.Object` `ProjectItem.FileCodeModel` .

Es una convención común para que los proyectos exponán una colección de proyectos personalizada específica del proyecto. Por ejemplo, crea una colección de proyectos específica de C++ a [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] la que puede acceder mediante o `DTE.VCProjects` `DTE.GetObject("VCProjects")` . También puede crear un , que es único para el tipo de proyecto, , que se puede consultar para su objeto más derivado, , que expone `Project.Object` `Project.CodeModel` `ProjectItem` y `ProjectItem.Object` `ProjectItem.FileCodeModel` .

## <a name="to-contribute-a-vspackage-specific-object-for-a-project"></a>Para contribuir a un objeto específico de VSPackage para un proyecto

1. Agregue las claves adecuadas al *archivo .pkgdef* del VSPackage.

     Por ejemplo, esta es la *configuración de .pkgdef* para el proyecto de lenguaje C++:

    ```
    [$RootKey$\Packages\{F1C25864-3097-11D2-A5C5-00C04F7968B4}\Automation]
    "VCProjects"=""
    [$RootKey$\Packages\{F1C25864-3097-11D2-A5C5-00C04F7968B4}\AutomationEvents]
    "VCProjectEngineEventsObject"=""
    ```

2. Implemente el código en <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> el método , como en el ejemplo siguiente.

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

     En el código, `g_wszAutomationProjects` es el nombre de la colección de proyectos. El método crea un objeto que implementa la interfaz y devuelve un puntero al objeto que realiza la llamada, como se `GetAutomationProjects` muestra en el ejemplo de código `Projects` `IDispatch` siguiente.

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

     Elija un nombre único para el objeto de automatización. Los conflictos de nombres son impredecibles y las colisiones hacen que un nombre de objeto en conflicto se deseche arbitrariamente si varios tipos de proyecto usan el mismo nombre. Debe incluir el nombre corporativo o algún aspecto único de su nombre de producto en el nombre del objeto de automatización.

     El objeto `Projects` de colección personalizado es un punto de entrada conveniente para la parte restante del modelo de automatización de proyectos. El objeto de proyecto también es accesible desde la colección <xref:EnvDTE.Solution> de proyectos. Después de crear el código y las entradas del Registro adecuados que proporcionan a los consumidores objetos de colección, la implementación debe proporcionar los objetos estándar restantes `Projects` para el modelo de proyecto. Para obtener más información, vea [Modelado de proyectos.](../../extensibility/internals/project-modeling.md)

## <a name="see-also"></a>Consulte también

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>
