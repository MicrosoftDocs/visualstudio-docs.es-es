---
title: Exposición de eventos en la Visual Studio SDK | Microsoft Docs
description: Obtenga información sobre los métodos Visual Studio SDK y las entradas del Registro que exponen eventos para proyectos y elementos de proyecto.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- events [Visual Studio], exposing
- automation [Visual Studio SDK], exposing events
ms.assetid: 70bbc258-c221-44f8-b0d7-94087d83b8fe
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 99298329b969df3b9d7dbb46a3f4b9e7d4ed7091
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898336"
---
# <a name="expose-events-in-the-visual-studio-sdk"></a>Exposición de eventos en el SDK Visual Studio
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] le permite crear eventos de origen mediante la automatización. Se recomienda que los eventos de origen para proyectos y elementos de proyecto.

 Los consumidores de automatización recuperan los eventos del <xref:EnvDTE.DTEClass.Events%2A> objeto o <xref:EnvDTE.DTEClass.GetObject%2A> (por ejemplo, `GetObject("EventObjectName")` ). El entorno llama `IDispatch::Invoke` mediante las marcas o para devolver un `DISPATCH_METHOD` `DISPATCH_PROPERTYGET` evento.

 En el siguiente proceso se explica cómo se devuelven los eventos específicos de VSPackage.

1. Se inicia el entorno.

2. Lee del Registro todos los nombres de valor en las claves **Automation**, **AutomationEvents** y **AutomationProperties** de todos los VSPackages y almacena esos nombres en una tabla.

3. En este ejemplo, un consumidor de automatización llama `DTE.Events.AutomationProjectsEvents` a o `DTE.Events.AutomationProjectItemsEvents` .

4. El entorno busca el parámetro string en la tabla y carga el VSPackage correspondiente.

5. El entorno llama al <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> método mediante el nombre pasado en la llamada; en este ejemplo, o `AutomationProjectsEvents` `AutomationProjectItemsEvents` .

6. El VSPackage crea un objeto raíz que tiene métodos como y y, a `get_AutomationProjectsEvents` continuación, devuelve un puntero `get_AutomationProjectItemEvents` IDispatch al objeto .

7. El entorno llama al método adecuado en función del nombre pasado a la llamada de automatización.

8. El método crea otro objeto de evento basado en IDispatch que implementa la interfaz y la `get_` interfaz y devuelve un al objeto `IConnectionPointContainer` `IConnectionPoint` `IDispatchpointer` .

   Para exponer un evento mediante automatización, debe responder y observar <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> las cadenas que agregue al Registro. En el ejemplo de proyecto básico, las cadenas son *BscProjectsEvents* y *BscProjectItemsEvents*.

## <a name="registry-entries-from-the-basic-project-sample"></a>Entradas del Registro del ejemplo de proyecto básico
 En esta sección se muestra dónde agregar valores de eventos de automatización al Registro.

 **[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0\Packages\\<PkgGUID \> \AutomationEvents]**

 **AutomationProjectEvents** = Devuelve el `AutomationProjectEvents` objeto .

 **AutomationProjectItemEvents** = Devuelve el `AutomationProjectItemsEvents` objeto .

|Nombre|Tipo|Intervalo|Descripción|
|----------|----------|-----------|-----------------|
|Valor predeterminado (@)|REG_SZ|No utilizado|Sin usar. Puede usar el campo de datos para la documentación.|
|*AutomationProjectsEvents*|REG_SZ|Nombre del objeto de evento.|Solo el nombre de clave es relevante. Puede usar el campo de datos para la documentación.<br /><br /> Este ejemplo procede del ejemplo de proyecto básico.|
|*AutomationProjectItemEvents*|REG_SZ|Nombre del objeto de evento|Solo el nombre de clave es relevante. Puede usar el campo de datos para la documentación.<br /><br /> Este ejemplo procede del ejemplo de proyecto básico.|

 Cuando un consumidor de automatización solicite cualquiera de los objetos de evento, cree un objeto raíz que tenga métodos para cualquier evento compatible con VSPackage. El entorno llama al método `get_` adecuado en este objeto . Por ejemplo, si `DTE.Events.AutomationProjectsEvents` se llama a , se invoca el método en el objeto `get_AutomationProjectsEvents` raíz.

 ![Visual Studio eventos de proyecto](../../extensibility/internals/media/projectevents.gif "ProjectEvents") Modelo de Automatización para eventos

 La clase `CProjectEventsContainer` representa el objeto de origen para *BscProjectsEvents* y representa el objeto `CProjectItemsEventsContainer` de origen para *BscProjectItemsEvents*.

 En la mayoría de los casos, debe devolver un nuevo objeto para cada solicitud de evento porque la mayoría de los objetos de evento toman un objeto de filtro. Cuando active el evento, compruebe este filtro para comprobar que se llama al controlador de eventos.

 *AutomationEvents.h* y *AutomationEvents.cpp* contienen declaraciones e implementaciones de las clases de la tabla siguiente.

|Clase|Descripción|
|-----------|-----------------|
|`CAutomationEvents`|Implementa un objeto raíz de evento, recuperado del `DTE.Events` objeto .|
|`CProjectsEventsContainer` y `CProjectItemsEventsContainer`|Implemente los objetos de origen del evento que desenlazen los eventos correspondientes.|

 En el ejemplo de código siguiente se muestra cómo responder a una solicitud de un objeto de evento.

```cpp
STDMETHODIMP CVsPackage::GetAutomationObject(
    /* [in]  */ LPCOLESTR       pszPropName,
    /* [out] */ IDispatch **    ppIDispatch)
{
    ExpectedPtrRet(ppIDispatch);
    *ppIDispatch = NULL;

    if (_wcsicmp(pszPropName, g_wszAutomationProjects) == 0)
        //Is the requested name our Projects object?
    {
        return GetAutomationProjects(ppIDispatch);
        // Gets our Projects object.
    }
    else if (_wcsicmp(pszPropName, g_wszAutomationProjectsEvents) == 0)
        //Is the requested name our ProjectsEvents object?
    {
        return CAutomationEvents::GetAutomationEvents(ppIDispatch);
          // Gets our ProjectEvents object.
    }
    else if (_wcsicmp(pszPropName, g_wszAutomationProjectItemsEvents) == 0)  //Is the requested name our ProjectsItemsEvents object?
    {
        return CAutomationEvents::GetAutomationEvents(ppIDispatch);
          // Gets our ProjectItemsEvents object.
    }
    return E_INVALIDARG;
}
```

 En el código anterior, es el nombre de la colección de proyectos `g_wszAutomationProjects` (*FigProjects*), `g_wszAutomationProjectsEvents` (*FigProjectsEvents*) y `g_wszAutomationProjectItemsEvents` (*FigProjectItemEvents*) son los nombres de eventos de proyecto y eventos de elementos de proyecto que se han origen de la implementación de VSPackage.

 Los objetos de evento se recuperan de la misma ubicación central, el `DTE.Events` objeto . De este modo, todos los objetos de evento se agrupan para que un usuario final no tenga que examinar todo el modelo de objetos para encontrar un evento específico. Esto también le permite proporcionar sus objetos de VSPackage específicos, en lugar de requerir que implemente su propio código para eventos de todo el sistema. Sin embargo, para el usuario final, que debe encontrar un evento para la interfaz, no está inmediatamente claro desde dónde se recupera `ProjectItem` ese objeto de evento.

## <a name="see-also"></a>Consulta también
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>
