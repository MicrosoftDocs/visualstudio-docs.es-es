---
title: Exponer eventos en el SDK de Visual Studio ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- events [Visual Studio], exposing
- automation [Visual Studio SDK], exposing events
ms.assetid: 70bbc258-c221-44f8-b0d7-94087d83b8fe
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 48f1e0ea0dcd07bbc26fc89d5c61a6a5941d4727
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708487"
---
# <a name="expose-events-in-the-visual-studio-sdk"></a>Exponer eventos en el SDK de Visual Studio
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]le permite originar eventos mediante la automatización. Se recomienda obtener eventos para proyectos y elementos de proyecto.

 Los consumidores de automatización <xref:EnvDTE.DTEClass.Events%2A> recuperan <xref:EnvDTE.DTEClass.GetObject%2A> los eventos `GetObject("EventObjectName")`del objeto o (por ejemplo, ). El entorno `IDispatch::Invoke` llama `DISPATCH_METHOD` mediante `DISPATCH_PROPERTYGET` el uso de los indicadores o para devolver un evento.

 El siguiente proceso explica cómo se devuelven los eventos específicos de VSPackage.

1. Se inicia el entorno.

2. Lee del registro todos los nombres de valor en las claves **Automation**, **AutomationEvents**y **AutomationProperties** de todos los VSPackages y almacena esos nombres en una tabla.

3. Un consumidor de automatización `DTE.Events.AutomationProjectsEvents` llama, en este ejemplo, o `DTE.Events.AutomationProjectItemsEvents`.

4. El entorno busca el parámetro de cadena en la tabla y carga el VSPackage correspondiente.

5. El entorno <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> llama al método mediante el nombre pasado en la llamada; en este `AutomationProjectsEvents` ejemplo, o `AutomationProjectItemsEvents`.

6. El VSPackage crea un objeto raíz `get_AutomationProjectsEvents` `get_AutomationProjectItemEvents` que tiene métodos como y, a continuación, devuelve un puntero IDispatch al objeto.

7. El entorno llama al método adecuado en función del nombre pasado a la llamada de automatización.

8. El `get_` método crea otro objeto de evento basado `IConnectionPointContainer` en `IConnectionPoint` IDispatch que `IDispatchpointer` implementa la interfaz y la interfaz y devuelve un al objeto.

   Para exponer un evento mediante la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> automatización, debe responder y observar las cadenas que agregue al registro. En el ejemplo De proyecto básico, las cadenas son *BscProjectsEvents* y *BscProjectItemsEvents*.

## <a name="registry-entries-from-the-basic-project-sample"></a>Entradas de registro del ejemplo de proyecto básico
 En esta sección se muestra dónde agregar valores de eventos de automatización al registro.

 **[HKEY_LOCAL_MACHINE,SOFTWARE, Microsoft, VisualStudio, 8,0,\\ \>Paquetes<PkgGUID, AutomationEvents]**

 **AutomationProjectEvents:** devuelve `AutomationProjectEvents` el objeto.

 **AutomationProjectItemEvents:** devuelve `AutomationProjectItemsEvents` el objeto.

|Nombre|Tipo|Intervalo|Descripción|
|----------|----------|-----------|-----------------|
|Predeterminado (no)|REG_SZ|No utilizado|Sin usar. Puede utilizar el campo de datos para la documentación.|
|*AutomationProjectsEvents*|REG_SZ|Nombre del objeto de evento.|Solo el nombre de clave es relevante. Puede utilizar el campo de datos para la documentación.<br /><br /> Este ejemplo procede del ejemplo de proyecto básico.|
|*AutomationProjectItemEvents*|REG_SZ|Nombre del objeto de evento|Solo el nombre de clave es relevante. Puede utilizar el campo de datos para la documentación.<br /><br /> Este ejemplo procede del ejemplo de proyecto básico.|

 Cuando un consumidor de automatización solicita cualquiera de los objetos de evento, cree un objeto raíz que tenga métodos para cualquier evento que admita el VSPackage. El entorno llama `get_` al método adecuado en este objeto. Por ejemplo, `DTE.Events.AutomationProjectsEvents` si se `get_AutomationProjectsEvents` llama, se invoca el método en el objeto raíz.

 ![Eventos de proyecto de Visual Studio](../../extensibility/internals/media/projectevents.gif "ProjectEvents") Modelo de automatización para eventos

 La `CProjectEventsContainer` clase representa el objeto de origen `CProjectItemsEventsContainer` para *BscProjectsEvents*y el objeto de origen para *BscProjectItemsEvents*.

 En la mayoría de los casos, debe devolver un nuevo objeto para cada solicitud de evento porque la mayoría de los objetos de evento toman un objeto de filtro. Cuando se desencadena el evento, compruebe este filtro para comprobar que se llama al controlador de eventos.

 *AutomationEvents.h* y *AutomationEvents.cpp* contienen declaraciones e implementaciones de las clases de la tabla siguiente.

|Clase|Descripción|
|-----------|-----------------|
|`CAutomationEvents`|Implementa un objeto raíz de evento, recuperado del `DTE.Events` objeto.|
|`CProjectsEventsContainer` y `CProjectItemsEventsContainer`|Implemente los objetos de origen de eventos que desencadenan los eventos correspondientes.|

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

 En el código `g_wszAutomationProjects` anterior, es el nombre de `g_wszAutomationProjectsEvents` la colección de proyectos (*FigProjects*), (*FigProjectsEvents*) y `g_wszAutomationProjectItemsEvents` (*FigProjectItemEvents*) son los nombres de eventos de proyecto y eventos de elementos de proyecto que se originan desde la implementación de VSPackage.

 Los objetos de evento se recuperan de la misma ubicación central, el `DTE.Events` objeto. De esta manera, todos los objetos de evento se agrupan para que un usuario final no tenga que examinar todo el modelo de objetos para buscar un evento específico. Esto también le permite proporcionar sus objetos VSPackage específicos, en lugar de requerir que implemente su propio código para eventos de todo el sistema. Sin embargo, para el usuario final, `ProjectItem` que debe encontrar un evento para la interfaz, no está inmediatamente claro desde dónde se recupera ese objeto de evento.

## <a name="see-also"></a>Vea también
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>
