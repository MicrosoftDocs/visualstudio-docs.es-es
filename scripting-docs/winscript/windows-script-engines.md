---
title: Motores de Windows Script | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Windows script engines
ms.assetid: e576853d-7252-4eb9-81eb-9d5bb7626ab4
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3434e9baaeb483e60087aec1b8536108c8af4471
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2019
ms.locfileid: "58157768"
---
# <a name="windows-script-engines"></a>Motores Windows Script
Para implementar un motor de Microsoft Windows Script, cree un objeto OLE COM que admita las siguientes interfaces.  
  
|||  
|-|-|  
|Interfaz|Descripción|  
|[IActiveScript](../winscript/reference/iactivescript.md)|Proporciona la capacidad básica de scripts. La implementación de esta interfaz es obligatoria.|  
|[IActiveScriptParse](../winscript/reference/iactivescriptparse.md)|Ofrece la posibilidad de agregar texto de script, evaluar expresiones, etc. La implementación de esta interfaz es opcional; sin embargo, si no se implementa, el motor de scripts debe implementar una de las interfaces IPersist* para cargar un script.|  
|IPersist *|Proporciona compatibilidad con la persistencia. Se requiere la implementación de al menos una de las siguientes interfaces si no se implementa [IActiveScriptParse](../winscript/reference/iactivescriptparse.md).<br /><br /> IPersistStorage: proporciona compatibilidad con el atributo DATA={url} de la etiqueta OBJECT.<br /><br /> IPersistStreamInit: proporciona la misma compatibilidad que `IPersistStorage`, y además con el atributo DATA="secuencia de bytes codificados con cadena" de la etiqueta OBJECT.<br /><br /> IPersistPropertyBag: proporciona compatibilidad con el atributo PARAM= de la etiqueta OBJECT.|  
  
> [!NOTE]
>  Es posible que el motor de scripting nunca se invoque para guardar o restaurar un estado de script mediante `IPersist*`. En su lugar, se usa [IActiveScriptParse](../winscript/reference/iactivescriptparse.md) mediante la llamada a [IActiveScriptParse::InitNew](../winscript/reference/iactivescriptparse-initnew.md) para crear un script en blanco, luego se agregan scriptlets y se conectan a eventos con [IActiveScriptParse::AddScriptlet](../winscript/reference/iactivescriptparse-addscriptlet.md) y se agrega código general con [IActiveScriptParse::ParseScriptText](../winscript/reference/iactivescriptparse-parsescripttext.md). No obstante, un motor de scripting debería implementar completamente al menos una interfaz `IPersist*` (preferiblemente `IPersistStreamInit`), porque otras aplicaciones host podrían intentar usarlas.  
  
 En las secciones siguientes se describe con más detalle la implementación de un motor de Windows Script.  
  
 Consulte la [referencia de las interfaces de Windows Script](../winscript/reference/windows-script-interfaces-reference.md) para más información.  
  
## <a name="registry-standard"></a>Estándar de Registro  
 Un motor de Windows Script puede identificarse a sí mismo mediante identificadores de categoría. Windows Script define actualmente dos identificadores de categoría.  
  
|||  
|-|-|  
|Categoría|Descripción|  
|CATID_ActiveScript|Indica que los identificadores de clase (CLSID) son motores de Windows Script que admiten, como mínimo, la interfaz [IActiveScript](../winscript/reference/iactivescript.md) y un mecanismo de persistencia (la interfaz `IPersistStorage`, `IPersistStreamInit` o IPersistPropertyBag).|  
|CATID_ActiveScriptParse|Indica que los CLSID son motores de Windows Script que admiten, como mínimo, las interfaces [IActiveScript](../winscript/reference/iactivescript.md) y [IActiveScriptParse](../winscript/reference/iactivescriptparse.md).|  
  
 Aunque [IActiveScriptParse](../winscript/reference/iactivescriptparse.md) no es un mecanismo de persistencia verdadero, admite el método [IActiveScriptParse::InitNew](../winscript/reference/iactivescriptparse-initnew.md) que es equivalente funcionalmente a `IPersist*::InitNew`.  
  
## <a name="script-engine-states"></a>Estados del motor de scripts  
 En un momento dado, un motor de Windows Script puede estar en uno de varios estados.  
  
|||  
|-|-|  
|Estado|Descripción|  
|no inicializado|El script no se ha inicializado ni cargado mediante una interfaz IPersist*, o no tiene definida una interfaz [IActiveScriptSite](../winscript/reference/iactivescriptsite.md). El motor de scripting no se puede usar por lo general con este estado hasta que se carga el script.|  
|inicializado|El script se ha inicializado con una interfaz `IPersist*` y tiene definida una interfaz [IActiveScriptSite](../winscript/reference/iactivescriptsite.md), pero no está conectada a objetos de host y eventos de recepción. Tenga en cuenta que este estado simplemente quiere decir que se ha completado el método `IPersist*::Load`, `IPersist*::InitNew` o [IActiveScriptParse::InitNew](../winscript/reference/iactivescriptparse-initnew.md) y que se ha llamado al método [IActiveScript::SetScriptSite](../winscript/reference/iactivescript-setscriptsite.md). El motor no puede ejecutar código en este modo. El motor pone en cola el código que el host le pasa mediante el método [IActiveScriptParse::ParseScriptText](../winscript/reference/iactivescriptparse-parsescripttext.md) y lo ejecuta después de realizar la transición al estado iniciado.<br /><br /> Como los lenguajes pueden variar ampliamente en la semántica, no se necesitan motores de scripting para admitir esta transición de estado. No obstante, los motores que admiten el método [IActiveScript::Clone](../winscript/reference/iactivescript-clone.md) deben admitir esta transición de estado. Los hosts se deben preparar para esta transición y emprender la acción adecuada: liberar el motor de scripting actual, crear un nuevo motor de scripting y llamar a `IPersist*::Load`, `IPersist*::InitNew` o [IActiveScriptParse::InitNew](../winscript/reference/iactivescriptparse-initnew.md) (y posiblemente también a [IActiveScriptParse::ParseScriptText](../winscript/reference/iactivescriptparse-parsescripttext.md)). El uso de esta transición se debe considerar una optimización de los pasos anteriores. Tenga en cuenta que toda la información que el motor de scripting ha obtenido sobre los nombres de los elementos con nombre y la información de tipos que describen los elementos con nombre sigue siendo válida.<br /><br /> Como los lenguajes pueden variar ampliamente, resulta difícil definir la semántica exacta de esta transición. Como mínimo, se debe desconectar el motor de scripting de todos los eventos y se deben liberar todos los punteros SCRIPTINFO_IUNKNOWN obtenidos con la llamada al método [IActiveScriptSite::GetItemInfo](../winscript/reference/iactivescriptsite-getiteminfo.md). El motor debe volver a obtener estos punteros después de que el script se ejecute de nuevo. El motor de scripting también debe restablecer el script a un estado inicial que sea adecuado para el lenguaje. Por ejemplo, VBScript restablece todas las variables y conserva solo el código agregado dinámicamente mediante la llamada a [IActiveScriptParse::ParseScriptText](../winscript/reference/iactivescriptparse-parsescripttext.md) con el indicador SCRIPTTEXT_ISPERSISTENT establecido. Puede que otros lenguajes deban conservar los valores actuales (como Lisp, ya que no hay separación de código/datos) o restablecerlos a un estado conocido (esto incluye los lenguajes con variables iniciadas de manera estática).<br /><br /> Tenga en cuenta que la transición al estado iniciado debe tener la misma semántica (es decir, debe dejar el motor de scripting en el mismo estado) que la llamada a `IPersist*::Save` para guardar el motor de scripting y que la posterior llamada a `IPersist*::Load` para cargar un nuevo motor de scripting; estas acciones deben tener la misma semántica que [IActiveScript::Clone](../winscript/reference/iactivescript-clone.md). Los motores de scripting que aún no admiten `IActiveScript::Clone` o `IPersist*` deben considerar cuidadosamente cómo se debe comportar la transición al estado iniciado, de modo que esa transición no infrinja las condiciones anteriores si más adelante se agrega compatibilidad con `IActiveScript::Clone` o `IPersist*`.<br /><br /> Durante esta transición al estado iniciado, el motor de scripting se desconectará de los receptores de eventos después de que se ejecuten los destructores adecuados, etc., en el script. Para evitar que estos destructores se ejecuten, el host puede mover primero el script al estado desconectado antes de moverlo al estado iniciado.<br /><br /> Use [IActiveScript::InterruptScriptThread](../winscript/reference/iactivescript-interruptscriptthread.md) para cancelar un subproceso de script en ejecución sin esperar a que eventos actuales, etc., terminen de ejecutarse.|  
|iniciado|La transición del estado inicializado al estado iniciado provoca que el motor ejecute cualquier código que se puso en cola en el estado inicializado. El motor puede ejecutar código mientras se encuentra en estado iniciado, pero no está conectado a ningún evento agregado mediante el método [IActiveScript::AddNamedItem](../winscript/reference/iactivescript-addnameditem.md). El motor puede ejecutar código mediante la llamada a la interfaz IDispatch obtenida por el método [IActiveScript::GetScriptDispatch](../winscript/reference/iactivescript-getscriptdispatch.md), o mediante la llamada a [IActiveScriptParse::ParseScriptText](../winscript/reference/iactivescriptparse-parsescripttext.md). Es posible que siga en curso la inicialización en segundo plano adicional (carga progresiva) y que la llamada al método [IActiveScript::SetScriptState](../winscript/reference/iactivescript-setscriptstate.md) con el indicador SCRIPTSTATE_CONNECTED establecido haga que el script se bloquee hasta finalizar la inicialización.|  
|conectado|El script está cargado y conectado para eventos de recepción desde objetos host. Si se trata de una transición desde el estado inicializado, el motor de scripting debe realizar la transición a través del estado iniciado y realizar las acciones necesarias antes de pasar al estado conectado y conectarse a los eventos.|  
|desconectado|El script está cargado y tiene un estado de tiempo de ejecución, pero está temporalmente desconectado de los eventos de recepción de los objetos host. Esto se puede realizar de manera lógica (ignorando los eventos recibidos) o física (llamando a IConnectionPoint::Unadvise en los puntos de conexión adecuados). Si se trata de una transición desde el estado inicializado, el motor de scripting debe realizar la transición a través del estado iniciado y realizar las acciones necesarias antes de pasar al estado desconectado. Los receptores de eventos que están en curso se completan antes de que cambie el estado (use [IActiveScript::InterruptScriptThread](../winscript/reference/iactivescript-interruptscriptthread.md) para cancelar un subproceso de script en ejecución). Este estado se distingue del estado inicializado en que la transición a este estado no provoca que se restablezca el script, el estado de tiempo de ejecución del script no se restablece y no se ejecuta un procedimiento de inicialización del script.|  
|cerrado|El script se ha cerrado. El motor de scripting ya no funciona y devuelve errores con la mayoría de los métodos.|  
  
 En la siguiente ilustración se muestran las relaciones entre los distintos estados del motor de scripting, junto con los métodos que provocan las transiciones de un estado a otro.  
  
 En la siguiente ilustración muestran las acciones que realiza el motor de scripting durante las diversas transiciones de estado.  
  
## <a name="scripting-engine-threading"></a>Subprocesos del motor de scripting  
 Dado que un motor de Windows Script se puede usar en muchos entornos, es importante mantener su modelo de ejecución lo más flexible posible. Por ejemplo, un host basado en servidor puede necesitar conservar un diseño multiproceso haciendo uso de Windows Script de una manera eficiente. Al mismo tiempo, un host que no use subprocesos, como una aplicación típica, no se debe sobrecargar con administración de subprocesos. Windows Script consigue este equilibrio al restringir las formas en que un motor de scripting sin subprocesos puede devolver la llamada al host y así liberar a los hosts de esta carga.  
  
 Los motores de scripting usados en los servidores se implementan normalmente como objetos COM sin subprocesos. Esto significa que se puede llamar a los métodos de la interfaz [IActiveScript](../winscript/reference/iactivescript.md) y sus interfaces asociadas desde cualquier subproceso del proceso, sin serialización. (Por desgracia, esto también significa que el motor de scripting debe implementarse como un servidor en proceso, porque OLE no admite actualmente la serialización entre procesos de objetos sin subprocesos). La sincronización es responsabilidad del motor de scripting. En el caso de motores de scripting que no son internamente reentrantes, o modelos de lenguaje que no son multiproceso, la sincronización podría ser tan simple como serializar el acceso al motor de scripting con una exclusión mutua. Por supuesto, ciertos métodos como [IActiveScript::InterruptScriptThread](../winscript/reference/iactivescript-interruptscriptthread.md), no se deben serializar de esta forma para que un script detenido pueda finalizarse desde otro subproceso.  
  
 El hecho de que [IActiveScript](../winscript/reference/iactivescript.md) esté, por lo general, libre de subprocesos implica que la interfaz [IActiveScriptSite](../winscript/reference/iactivescriptsite.md) y el modelo de objetos del host deben estar también libres de subprocesos. Como consecuencia, la implementación del host sería bastante difícil, en especial, en el caso común donde el host es una aplicación basada en Windows de un único subproceso con controles ActiveX de un único subproceso o de modelo apartamento en su modelo de objetos. Por este motivo, se colocan las siguientes restricciones sobre el uso de [IActiveScriptSite](../winscript/reference/iactivescriptsite.md) del motor de scripting:  
  
 El sitio de script siempre se llama en el contexto de un subproceso de host. Es decir, el motor de scripting nunca llama al sitio de script en el contexto de un subproceso que creó el motor de scripting, sino solo desde un método del motor de scripting al que se llamó desde el host mediante [IActiveScript](../winscript/reference/iactivescript.md) y sus derivados, mediante el objeto de distribución del motor de scripting expuesto, mediante un mensaje de Windows o desde un origen de evento en el modelo de objetos del host.  
  
 Nunca se llama al sitio de script desde el contexto de un simple método de control del estado de los subprocesos (por ejemplo, el método [IActiveScript::InterruptScriptThread](../winscript/reference/iactivescript-interruptscriptthread.md)) o desde el método [IActiveScript::Clone](../winscript/reference/iactivescript-clone.md).  
  
## <a name="see-also"></a>Vea también  
 [Windows Script (Interfaces)](../winscript/windows-script-interfaces.md)
