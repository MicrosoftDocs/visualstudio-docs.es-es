---
title: Interfaces de Windows Script | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4c750627-6797-4857-9f5e-e5f54371f83c
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: acb62f3dc5774ef8574fded3c0537e97611049c2
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2019
ms.locfileid: "58154431"
---
# <a name="windows-script-interfaces"></a>Windows Script (Interfaces)

Las Interfaces de Microsoft Windows Script permiten que una aplicación agregue scripts y automatización OLE. Los hosts de scripting que se basan en Windows Script pueden usar los motores de scripting de varios orígenes y proveedores para administrar scripts entre los componentes. La implementación del script en sí mismo (el lenguaje, la sintaxis, el formato persistente, el modelo de ejecución, etc.) le corresponde al proveedor del script.

La documentación de Windows Script se divide en las secciones siguientes:

[Windows Script (Hosts)](../winscript/windows-script-hosts.md)

[Windows Script (Motores)](../winscript/windows-script-engines.md)

[Información general acerca de la depuración de Active Script](../winscript/active-script-debugging-overview.md)

[Información general acerca de la generación de perfiles de Active Script](../winscript/active-script-profiling-overview.md)

[Referencia de interfaces de Windows Script](../winscript/reference/windows-script-interfaces-reference.md)

## <a name="windows-script-background"></a>Información previa sobre Windows Script

Las interfaces de Windows Script se dividen en dos categorías: Hosts de Windows Script y motores de Windows Script. Un host crea un motor de scripting y llama al motor para ejecutar los scripts. Algunos ejemplos de hosts de Windows Script son los siguientes:

- Microsoft Internet Explorer

- Herramientas de creación de Internet

- Shell

Los motores de Windows Script se pueden desarrollar para cualquier lenguaje o entorno de tiempo de ejecución, incluidos los siguientes:

- Microsoft Visual Basic Scripting (VBScript)

- Perl

- Lisp

Para que la implementación del host sea lo más flexible posible, se proporciona un contenedor de automatización OLE para Windows Script. Con todo, un host que use este objeto contenedor para crear una instancia del motor de scripting no tiene el mismo grado de control sobre el espacio de nombres del tiempo de ejecución, el modelo de persistencia, etc. que tendría si usara Windows Script directamente.

El diseño de Windows Script aísla los elementos de interfaz necesarios únicamente en un entorno de creación, de modo que los hosts que no son de creación (por ejemplo, exploradores y visores) y los motores de scripting (por ejemplo, VBScript) puedan seguir siendo ligeros.

## <a name="windows-script-basic-architecture"></a>Arquitectura básica de Windows Script

En la siguiente ilustración se muestra la interacción entre un host de Windows Script y un motor de Windows Script.

Los pasos que implica la interacción entre el host y el motor se indican en la lista siguiente.

1.  Cree un proyecto. El host carga un proyecto o documento. (Este paso no es específico de Windows Script, pero se incluye aquí para proporcionar información completa).

2.  Cree el motor de Windows Script. El host llama a `CoCreateInstance` para crear un motor de Windows Script. Para ello, especifica el identificador de clase (CLSID) del motor de scripting específico que se va a usar. Por ejemplo, el explorador HTML de Internet Explorer recibe el identificador de clase del motor de scripting mediante el atributo CLSID= de la etiqueta HTML \<OBJECT>.

3.  Cargue el script. Si se ha guardado el contenido del script, el host llama al método `IPersist*::Load` del motor de scripting para introducir en él el almacenamiento de scripts, la secuencia o el contenedor de propiedades. En caso contrario, el host usa el método `IPersist*::InitNew` o [IActiveScriptParse::InitNew](../winscript/reference/iactivescriptparse-initnew.md) para crear un script null. Un host que guarde un script como texto puede usar [IActiveScriptParse::ParseScriptText](../winscript/reference/iactivescriptparse-parsescripttext.md) para introducir en el motor de scripting el texto del script, después de llamar a `IActiveScriptParse::InitNew`.

4.  Agregue elementos con nombre. Para cada elemento con nombre de nivel superior (por ejemplo, páginas y formularios) importado en el espacio de nombres del motor de scripting, el host llama al método [IActiveScript::AddNamedItem](../winscript/reference/iactivescript-addnameditem.md) para crear una entrada en el espacio de nombres del motor. Este paso no es necesario si los elementos con nombre de nivel superior ya forman parte del estado persistente del script cargado en el paso 3. Un host no usa `IActiveScript::AddNamedItem` para agregar elementos con nombre de subnivel (por ejemplo, controles en una página HTML); en su lugar, el motor obtiene indirectamente elementos de subnivel a partir de elementos de nivel superior mediante las interfaces `ITypeInfo` y `IDispatch` del host.

5.  Ejecute el script. El host hace que el motor empiece a ejecutar el script mediante el establecimiento de la marca SCRIPTSTATE_CONNECTED en el método [IActiveScript::SetScriptState](../winscript/reference/iactivescript-setscriptstate.md). Esta llamada probablemente hará que funcionen todas las construcciones del motor de scripting, incluidos el enlace estático, el enlace a eventos (vea más adelante) y la ejecución de código, de forma similar a la función `main()` generada por script.

6.  Obtenga información del elemento. Cada vez que el motor de scripting necesita asociar un símbolo con un elemento de nivel superior, llama al método [IActiveScriptSite::GetItemInfo](../winscript/reference/iactivescriptsite-getiteminfo.md), que devuelve información sobre el elemento especificado.

7.  Enlace eventos. Antes de iniciar el script real, el motor de scripting se conecta a los eventos de todos los objetos relevantes a través de la interfaz `IConnectionPoint`.

8.  Invoque propiedades y métodos. A medida que se ejecuta el script, el motor de scripting realiza referencias a métodos y propiedades en objetos con nombre a través de `IDispatch::Invoke` u otros mecanismos estándares de enlace de OLE.

## <a name="windows-script-terms"></a>Términos de Windows Script

Esta lista contiene las definiciones de los términos relacionados con los scripts usados en este documento.

|Término|de esquema JSON|
|----------|----------------|
|Objeto de código|Instancia creada por el motor de scripting que está asociada a un elemento con nombre, como el módulo subyacente a un formulario en Visual Basic o una clase de C++ asociada con un elemento con nombre. Preferiblemente, se trata de un objeto OLE COM (Modelo de objetos componentes) que es compatible con la automatización OLE, por lo que el host u otra entidad que no sea un script pueden manipular el objeto de código.|
|Elemento con nombre|Objeto OLE COM (preferiblemente uno que admita la automatización OLE) que el host considera interesante para el script. Algunos ejemplos son HTML Page y Browser en un explorador web, así como Document y Dialogs en Microsoft Word.|
|Script|Datos que constituyen el programa que el motor de scripting ejecuta. Un script puede ser cualquier dato ejecutable contiguo, incluidos fragmentos de texto, bloques de `pcode` o incluso códigos de byte ejecutables específicos del equipo. Un host carga un script en el motor de scripting a través de una de las interfaces `IPersist*` o a través de la interfaz [IActiveScriptParse](../winscript/reference/iactivescriptparse.md).|
|Motor de scripting|Objeto OLE que procesa scripts. Un motor de scripting implementa la interfaz [IActiveScript](../winscript/reference/iactivescript.md) y, opcionalmente, la interfaz [IActiveScriptParse](../winscript/reference/iactivescriptparse.md).|
|Host de scripting|Aplicación o programa que posee el motor de Windows Script. El host implementa la interfaz [IActiveScriptSite](../winscript/reference/iactivescriptsite.md) y, opcionalmente, la interfaz [IActiveScriptSiteWindow](../winscript/reference/iactivescriptsitewindow.md).|
|Scriptlet|Parte de un script que se asocia a un objeto a través de la interfaz [IActiveScriptParse](../winscript/reference/iactivescriptparse.md). La colección agregada de scriptlets es el script.|
|Lenguaje de script|Lenguaje en el que se escribe un script (por ejemplo, VBScript) y la semántica de dicho lenguaje.|