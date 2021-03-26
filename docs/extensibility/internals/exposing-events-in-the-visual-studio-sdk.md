---
title: Exponer eventos en el SDK de Visual Studio | Microsoft Docs
description: Obtenga información sobre los métodos del SDK de Visual Studio y las entradas del registro que exponen eventos para proyectos y elementos de proyecto.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- events [Visual Studio], exposing
- automation [Visual Studio SDK], exposing events
ms.assetid: 70bbc258-c221-44f8-b0d7-94087d83b8fe
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 019efb11d7a31af875425888a1f70423bca76ca9
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105069808"
---
# <a name="expose-events-in-the-visual-studio-sdk"></a>Exponer eventos en el SDK de Visual Studio
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] permite el origen de eventos mediante la automatización. Se recomienda el origen de eventos para proyectos y elementos de proyecto.

 Los consumidores de automatización recuperan los eventos del <xref:EnvDTE.DTEClass.Events%2A> objeto o <xref:EnvDTE.DTEClass.GetObject%2A> (por ejemplo, `GetObject("EventObjectName")` ). El entorno llama a mediante `IDispatch::Invoke` las `DISPATCH_METHOD` `DISPATCH_PROPERTYGET` marcas o para devolver un evento.

 En el siguiente proceso se explica cómo se devuelven los eventos específicos de VSPackage.

1. Se inicia el entorno.

2. Lee del registro todos los nombres de valor de las claves **Automation**, **AutomationEvents** y **AutomationProperties** de todos los VSPackages y almacena esos nombres en una tabla.

3. Un consumidor de automatización llama a, en este ejemplo `DTE.Events.AutomationProjectsEvents` o `DTE.Events.AutomationProjectItemsEvents` .

4. El entorno busca el parámetro de cadena en la tabla y carga el VSPackage correspondiente.

5. El entorno llama al <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> método utilizando el nombre pasado en la llamada; en este ejemplo, `AutomationProjectsEvents` o `AutomationProjectItemsEvents` .

6. El VSPackage crea un objeto raíz que tiene métodos como `get_AutomationProjectsEvents` y `get_AutomationProjectItemEvents` y, a continuación, devuelve un puntero IDispatch al objeto.

7. El entorno llama al método adecuado en función del nombre pasado a la llamada de automatización.

8. El `get_` método crea otro objeto de evento basado en IDispatch que implementa la `IConnectionPointContainer` interfaz y la `IConnectionPoint` interfaz y devuelve `IDispatchpointer` al objeto.

   Para exponer un evento mediante la automatización, debe responder a <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> las cadenas que agregue al registro y inspeccionarlas. En el ejemplo de proyecto básico, las cadenas son *BscProjectsEvents* y *BscProjectItemsEvents*.

## <a name="registry-entries-from-the-basic-project-sample"></a>Entradas del registro del ejemplo Basic Project
 En esta sección se muestra dónde agregar valores de eventos de automatización al registro.

 **[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0\Packages\\<PkgGUID \> \AutomationEvents]**

 **AutomationProjectEvents** = devuelve el `AutomationProjectEvents` objeto.

 **AutomationProjectItemEvents** = devuelve el `AutomationProjectItemsEvents` objeto.

|Nombre|Tipo|Intervalo|Descripción|
|----------|----------|-----------|-----------------|
|Predeterminado (@)|REG_SZ|No utilizado|Sin usar. Puede usar el campo de datos de la documentación de.|
|*AutomationProjectsEvents*|REG_SZ|Nombre del objeto de evento.|Solo el nombre de la clave es relevante. Puede usar el campo de datos de la documentación de.<br /><br /> Este ejemplo procede del proyecto Basic sample.|
|*AutomationProjectItemEvents*|REG_SZ|Nombre del objeto de evento|Solo el nombre de la clave es relevante. Puede usar el campo de datos de la documentación de.<br /><br /> Este ejemplo procede del proyecto Basic sample.|

 Cuando un consumidor de automatización solicite cualquiera de los objetos de evento, cree un objeto raíz que tenga métodos para cualquier evento que admita el VSPackage. El entorno llama al `get_` método adecuado en este objeto. Por ejemplo, si `DTE.Events.AutomationProjectsEvents` se llama a, `get_AutomationProjectsEvents` se invoca el método en el objeto raíz.

 ![Eventos de proyecto de Visual Studio](../../extensibility/internals/media/projectevents.gif "ProjectEvents") Modelo de automatización para eventos

 La clase `CProjectEventsContainer` representa el objeto de origen para *BscProjectsEvents* y `CProjectItemsEventsContainer` representa el objeto de origen para *BscProjectItemsEvents*.

 En la mayoría de los casos, debe devolver un nuevo objeto para cada solicitud de evento, ya que la mayoría de los objetos de evento toman un objeto de filtro. Cuando desencadene el evento, compruebe este filtro para comprobar que se llama al controlador de eventos.

 *AutomationEvents. h* y *AutomationEvents. cpp* contienen declaraciones e implementaciones de las clases de la tabla siguiente.

|Clase|Descripción|
|-----------|-----------------|
|`CAutomationEvents`|Implementa un objeto raíz del evento, recuperado del `DTE.Events` objeto.|
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

 En el código anterior, `g_wszAutomationProjects` es el nombre de la colección de proyectos (*FigProjects*), `g_wszAutomationProjectsEvents` (*FigProjectsEvents*) y `g_wszAutomationProjectItemsEvents` (*FigProjectItemEvents*) son los nombres de los eventos de proyecto y de elementos de proyecto que se incluyen en la implementación de VSPackage.

 Los objetos de evento se recuperan de la misma ubicación central, el `DTE.Events` objeto. De esta manera, todos los objetos de evento se agrupan para que un usuario final no tenga que examinar todo el modelo de objetos para encontrar un evento específico. Esto también le permite proporcionar objetos VSPackage específicos, en lugar de requerir que implemente su propio código para eventos para todo el sistema. Sin embargo, para el usuario final, que debe encontrar un evento para la `ProjectItem` interfaz, no se borra inmediatamente de donde se recupera ese objeto de evento.

## <a name="see-also"></a>Consulte también
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>
