---
title: Exponer eventos en el SDK de Visual Studio | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- events [Visual Studio], exposing
- automation [Visual Studio SDK], exposing events
ms.assetid: 70bbc258-c221-44f8-b0d7-94087d83b8fe
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3cc905e359d7bcb2946d627ebcb3c28067233fa0
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/21/2019
ms.locfileid: "56603162"
---
# <a name="expose-events-in-the-visual-studio-sdk"></a>Exponer eventos en el SDK de Visual Studio
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] permite obtener eventos mediante la automatización. Se recomienda que origen de eventos para los proyectos y elementos de proyecto.

 Los eventos se recuperan los consumidores de automatización de la <xref:EnvDTE.DTEClass.Events%2A> objeto o <xref:EnvDTE.DTEClass.GetObject%2A> (por ejemplo, `GetObject("EventObjectName")`). El entorno llama a `IDispatch::Invoke` utilizando el `DISPATCH_METHOD` o `DISPATCH_PROPERTYGET` marcas para devolver un evento.

 El siguiente proceso explica cómo se devuelven los eventos específicos de VSPackage.

1. Se inicia el entorno.

2. Lee desde el registro de todos los nombres de valor la **automatización**, **AutomationEvents**, y **AutomationProperties** las claves de todos los VSPackages y almacena esos nombres en un tabla.

3. Llama un consumidor de automatización, en este ejemplo, `DTE.Events.AutomationProjectsEvents` o `DTE.Events.AutomationProjectItemsEvents`.

4. El entorno busca el parámetro de cadena en la tabla y carga el VSPackage correspondiente.

5. El entorno llama a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> método con el nombre pasado en la llamada; en este ejemplo, `AutomationProjectsEvents` o `AutomationProjectItemsEvents`.

6. El VSPackage crea un objeto de raíz que incorpora métodos como `get_AutomationProjectsEvents` y `get_AutomationProjectItemEvents` y, a continuación, devuelve un puntero IDispatch para el objeto.

7. El entorno llama el método adecuado según el nombre pasado a la llamada de automatización.

8. El `get_` método crea otro objeto de eventos basado en IDispatch que implementa tanto la `IConnectionPointContainer` interfaz y la `IConnectionPoint` interfaz y devuelve un `IDispatchpointer` al objeto.

   Para exponer un evento mediante la automatización, debe responder a <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> e inspeccionar las cadenas que agregue en el registro. En el proyecto básico de ejemplo, las cadenas son *BscProjectsEvents* y *BscProjectItemsEvents*.

## <a name="registry-entries-from-the-basic-project-sample"></a>Entradas del registro desde el proyecto básico de ejemplo
 En esta sección se muestra dónde agregar valores de evento de automatización en el registro.

 **[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0\Packages\\<PkgGUID\>\AutomationEvents]**

 **AutomationProjectEvents** = devuelve el `AutomationProjectEvents` objeto.

 **AutomationProjectItemEvents** = devuelve el `AutomationProjectItemsEvents` objeto.

|nombre|Tipo|Intervalo|Descripción|
|----------|----------|-----------|-----------------|
|Predeterminado (@)|REG_SZ|sin usar|Sin usar. Puede usar el campo de datos para la documentación.|
|*AutomationProjectsEvents*|REG_SZ|Nombre de su objeto de evento.|Solo el nombre de clave es relevante. Puede usar el campo de datos para la documentación.<br /><br /> Este ejemplo se incluye en el proyecto básico de ejemplo.|
|*AutomationProjectItemEvents*|REG_SZ|Nombre de su objeto de evento|Solo el nombre de clave es relevante. Puede usar el campo de datos para la documentación.<br /><br /> Este ejemplo se incluye en el proyecto básico de ejemplo.|

 Cuando cualquiera de los objetos de evento se solicita un consumidor de automatización, cree un objeto de raíz que tiene métodos para cualquier evento que admita el VSPackage. El entorno llama a la correspondiente `get_` método en este objeto. Por ejemplo, si `DTE.Events.AutomationProjectsEvents` se llama, el `get_AutomationProjectsEvents` se invoca el método en el objeto raíz.

 ![Eventos de proyecto de Visual Studio](../../extensibility/internals/media/projectevents.gif "ProjectEvents") modelo de automatización de eventos

 La clase `CProjectEventsContainer` representa el objeto de origen para *BscProjectsEvents*, y `CProjectItemsEventsContainer` representa el objeto de origen para *BscProjectItemsEvents*.

 En la mayoría de los casos, debe devolver un nuevo objeto para cada solicitud de eventos porque la mayoría de los objetos de eventos toma un objeto de filtro. Cuando se desencadena el evento, compruebe este filtro para comprobar que el controlador de eventos es que se llama.

 *AutomationEvents.h* y *AutomationEvents.cpp* contener declaraciones e implementaciones de las clases en la tabla siguiente.

|Clase|Descripción|
|-----------|-----------------|
|`CAutomationEvents`|Implementa un objeto de raíz de evento recuperado de la `DTE.Events` objeto.|
|`CProjectsEventsContainer` y `CProjectItemsEventsContainer`|Implementar los objetos de origen de eventos que se activan los eventos correspondientes.|

 El ejemplo de código siguiente muestra cómo responder a una solicitud para un objeto de evento.

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

 En el código anterior, `g_wszAutomationProjects` es el nombre de la colección de proyectos (*FigProjects*), `g_wszAutomationProjectsEvents` (*FigProjectsEvents*) y `g_wszAutomationProjectItemsEvents` (*FigProjectItemEvents* ) son los nombres de los eventos de proyecto y elementos de proyecto de los eventos que se obtienen de la implementación de VSPackage.

 Objetos de eventos se recuperan de la misma ubicación central, el `DTE.Events` objeto. De este modo, todos los objetos de eventos se agrupan para que un usuario final no tenga que examinar el modelo de objetos completo para buscar un evento específico. Esto también le permite proporcionar los objetos de VSPackage específicos, en lugar de requerir que implemente su propio código para los eventos de todo el sistema. Sin embargo, para el usuario final, que debe buscar un evento para su `ProjectItem` interfaz, no queda inmediatamente claro desde donde se recupera el objeto de ese evento.

## <a name="see-also"></a>Vea también
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>
