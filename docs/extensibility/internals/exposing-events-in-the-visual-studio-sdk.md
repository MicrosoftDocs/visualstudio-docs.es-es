---
title: "Exponer eventos en el SDK de Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "eventos [Visual Studio], exponer"
  - "automatización [Visual Studio SDK], exponiendo los eventos"
ms.assetid: 70bbc258-c221-44f8-b0d7-94087d83b8fe
caps.latest.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 16
---
# Exponer eventos en el SDK de Visual Studio
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] permite del origen de eventos mediante la automatización. Se recomienda que origen de eventos para los proyectos y elementos de proyecto.  
  
 Eventos se recuperan mediante los consumidores de automatización de la <xref:EnvDTE.DTEClass.Events%2A> objeto o <xref:EnvDTE.DTEClass.GetObject%2A> ("EventObjectName"). El entorno llama `IDispatch::Invoke` utilizando el `DISPATCH_METHOD` o `DISPATCH_PROPERTYGET` marcas para devolver un evento.  
  
 Este procedimiento explica cómo se devuelven los eventos específicos de VSPackage.  
  
1.  Inicie el nuevo entorno.  
  
2.  Lee desde el registro de todos los nombres de los valores en las claves de automatización, AutomationEvents y AutomationProperties de todos los VSPackages y almacena esos nombres en una tabla.  
  
3.  Llama a un consumidor de automatización, en este ejemplo, `DTE.Events.AutomationProjectsEvents` o `DTE.Events.AutomationProjectItemsEvents`.  
  
4.  El entorno encuentra el parámetro de cadena en la tabla y carga el VSPackage correspondiente.  
  
5.  El entorno llama el <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> pasa al método mediante el nombre de la llamada; en este ejemplo, AutomationProjectsEvents o AutomationProjectItemsEvents.  
  
6.  El VSPackage crea un objeto de raíz que tiene métodos como `get_AutomationProjectsEvents` y `get_AutomationProjectItemEvents` y, a continuación, devuelve un puntero IDispatch al objeto.  
  
7.  El entorno llama al método adecuado en función del nombre que se pasa a la llamada de automatización.  
  
8.  El `get_` método crea otro objeto de evento basada en IDispatch que implementa tanto la `IConnectionPointContainer` interfaz y la `IConnectionPoint` interfaz y devuelve un IDispatchpointer al objeto.  
  
 Para exponer un evento mediante la automatización, debe responder a <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> e inspeccionar las cadenas que agregar al registro. En el ejemplo básico del proyecto, las cadenas son "BscProjectsEvents" y "BscProjectItemsEvents".  
  
## <a name="registry-entries-from-the-basic-project-sample"></a>Entradas del registro desde el proyecto básico de ejemplo  
 En esta sección se muestra dónde agregar valores de eventos de automatización en el registro.  
  
 [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0\Packages\\< PkgGUID\>\AutomationEvents]  
  
 "AutomationProjectEvents"="devuelve el objeto AutomationProjectEvents"  
  
 "AutomationProjectItemEvents"="devuelve el objeto AutomationProjectItemsEvents"  
  
|Nombre|Tipo|Intervalo|Descripción|  
|----------|----------|-----------|-----------------|  
|Valor predeterminado (@)|REG_SZ|No usado|No usado. Puede usar el campo de datos para la documentación.|  
|AutomationProjectsEvents|REG_SZ|Nombre de su objeto de evento.|Solo el nombre de clave es relevante. Puede usar el campo de datos para la documentación.<br /><br /> En este ejemplo proviene el proyecto básico de ejemplo.|  
|AutomationProjectItemEvents|REG_SZ|Nombre de su objeto de evento|Solo el nombre de clave es relevante. Puede usar el campo de datos para la documentación.<br /><br /> En este ejemplo proviene el proyecto básico de ejemplo.|  
  
 Cuando cualquiera de los objetos de evento se solicitan por un consumidor de automatización, cree un objeto de raíz que tiene métodos para cualquier evento que admita el VSPackage. El entorno llama a la correspondiente `get_` método en este objeto. Por ejemplo, si `DTE.Events.AutomationProjectsEvents` se llama, el `get_AutomationProjectsEvents` se invoca el método en el objeto raíz.  
  
 ![Eventos de proyectos de Visual Studio](../../extensibility/internals/media/projectevents.png "ProjectEvents")  
Modelo de automatización de eventos  
  
 La clase `CProjectEventsContainer` representa el objeto de origen para BscProjectsEvents, mientras que `CProjectItemsEventsContainer` representa el objeto de origen para BscProjectItemsEvents.  
  
 En la mayoría de los casos, debe devolver un objeto nuevo para cada solicitud de eventos porque la mayoría de los objetos de eventos toma un objeto de filtro. Cuando se desencadena el evento, compruebe este filtro para comprobar que el controlador de eventos es que se realiza la llamada.  
  
 AutomationEvents.h y AutomationEvents.cpp contienen declaraciones e implementaciones de las clases en la tabla siguiente.  
  
|Clase|Descripción|  
|-----------|-----------------|  
|`CAutomationEvents`|Implementa un objeto de raíz de eventos recuperado de la `DTE.Events` objeto.|  
|`CProjectsEventsContainer` y `CProjectItemsEventsContainer`|Implementar los objetos de origen de eventos que se desencadenan los eventos correspondientes.|  
  
 En el ejemplo de código siguiente se muestra cómo responder a una solicitud de un objeto de evento.  
  
```cpp#  
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
  
 En el código anterior, `g_wszAutomationProjects` es el nombre de la colección de proyectos ("FigProjects"), `g_wszAutomationProjectsEvents` ("FigProjectsEvents") y `g_wszAutomationProjectItemsEvents` ("FigProjectItemEvents") son los nombres de eventos de proyecto y elementos de proyecto de eventos que se obtienen de la implementación de VSPackage.  
  
 Objetos de eventos se recuperan desde la misma ubicación central, el `DTE.Events` objeto. De esta manera, todos los objetos de evento se agrupan juntos para que un usuario final no tiene que examinar el modelo de objetos completo para buscar un evento específico. Esto también le permite proporcionar los objetos de VSPackage específicos, en lugar de requerir que implemente su propio código para los eventos de todo el sistema. Sin embargo, para el usuario final, que debe buscar un evento para su `ProjectItem` interfaz, no está claro inmediatamente desde donde se recupera ese objeto de evento.  
  
## <a name="see-also"></a>Vea también  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>   
 [Muestras de VSSDK](../../misc/vssdk-samples.md)