---
title: Exposición de objetos de proyecto Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project objects, exposing
- extensibility, project objects
ms.assetid: 5bb24967-434a-4ef4-87a0-2f3250c9e22d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 81446fa582524872b03199ae707f658776787961
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708472"
---
# <a name="expose-project-objects"></a>Exponer objetos de proyecto

Los tipos de proyecto personalizados pueden proporcionar objetos de automatización para permitir el acceso al proyecto mediante interfaces de automatización. Se espera que cada tipo <xref:EnvDTE.Project> de proyecto proporcione <xref:EnvDTE.Solution>el objeto de automatización estándar desde el que se tiene acceso , que contiene una colección de todos los proyectos que están abiertos en el IDE. Se espera que cada elemento del <xref:EnvDTE.ProjectItem> proyecto se `Project.ProjectItems`exponga mediante un objeto al que se accede con . Además de estos objetos de automatización estándar, los proyectos pueden optar por ofrecer objetos de automatización específicos del proyecto.

Puede crear objetos de automatización de nivel raíz personalizados a `DTE.<customObjectName>` los `DTE.GetObject("<customObjectName>")`que pueda tener acceso a enlaces en tiempo de enlace desde el objeto DTE raíz mediante o . Por ejemplo, Visual C++ crea una colección de proyectos específica del `DTE.VCProjects` `DTE.GetObject("VCProjects")`proyecto C++ denominada *VCProjects* a los que puede tener acceso mediante o . También puede crear `Project.Object`un , que es único `Project.CodeModel`para el tipo de proyecto, un , `ProjectItem`que se `ProjectItem.Object` puede `ProjectItem.FileCodeModel`consultar para su objeto más derivado, y un , que expone y un archivo .

Es una convención común para que los proyectos expongan una colección de proyectos personalizada específica del proyecto. Por ejemplo, [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] crea una colección de proyectos específica `DTE.VCProjects` `DTE.GetObject("VCProjects")`de C++ a la que puede acceder mediante o . También puede crear `Project.Object`un , que es único `Project.CodeModel`para el tipo de proyecto, un , `ProjectItem`que se `ProjectItem.Object`puede `ProjectItem.FileCodeModel`consultar para su objeto más derivado, un , que expone y un archivo .

## <a name="to-contribute-a-vspackage-specific-object-for-a-project"></a>Para contribuir con un objeto específico de VSPackage para un proyecto

1. Agregue las claves adecuadas al archivo *.pkgdef* del VSPackage.

     Por ejemplo, aquí está la configuración *.pkgdef* para el proyecto de lenguaje C++:

    ```
    [$RootKey$\Packages\{F1C25864-3097-11D2-A5C5-00C04F7968B4}\Automation]
    "VCProjects"=""
    [$RootKey$\Packages\{F1C25864-3097-11D2-A5C5-00C04F7968B4}\AutomationEvents]
    "VCProjectEngineEventsObject"=""
    ```

2. Implemente el código <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> en el método, como en el ejemplo siguiente.

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

     En el `g_wszAutomationProjects` código, es el nombre de la colección de proyectos. El `GetAutomationProjects` método crea un objeto `Projects` que implementa `IDispatch` la interfaz y devuelve un puntero al objeto que realiza la llamada, como se muestra en el ejemplo de código siguiente.

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

     Elija un nombre único para el objeto de automatización. Los conflictos de nombres son impredecibles y las colisiones hacen que un nombre de objeto en conflicto se descarte arbitrariamente si varios tipos de proyecto usan el mismo nombre. Debe incluir su nombre corporativo o algún aspecto único de su nombre de producto en el nombre del objeto de automatización.

     El `Projects` objeto de colección personalizado es un punto de entrada de conveniencia para la parte restante del modelo de automatización de proyectos. El objeto de proyecto <xref:EnvDTE.Solution> también es accesible desde la colección de proyectos. Después de crear el código adecuado y las `Projects` entradas del Registro que proporcionan a los consumidores objetos de colección, la implementación debe proporcionar los objetos estándar restantes para el modelo de proyecto. Para obtener más información, consulte [Modelado de](../../extensibility/internals/project-modeling.md)proyectos .

## <a name="see-also"></a>Vea también

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>
