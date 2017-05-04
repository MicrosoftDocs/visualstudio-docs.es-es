---
title: "Windows Script (Interfaces) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4c750627-6797-4857-9f5e-e5f54371f83c
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# Windows Script (Interfaces)
Las interfaces de script de Microsoft Windows proporcionan una manera de que una aplicación agregue script y la automatización OLE.  Hosts de script que confían en el script de Windows pueden usar los motores de scripts de varios orígenes y proveedores para administrar script entre los componentes.  La implementación de sí mismo\- lenguaje de script, sintaxis, formato persistente, modelo de ejecución, y en\- se permite en el proveedor del script.  
  
 La documentación de Windows scripting se divide en las siguientes secciones:  
  
 [Windows Script \(Hosts\)](../winscript/windows-script-hosts.md)  
  
 [Motores Windows Script](../winscript/windows-script-engines.md)  
  
 [Información general acerca de la depuración de Active Script](../winscript/active-script-debugging-overview.md)  
  
 [Información general acerca de la generación de perfiles de Active Script](../winscript/active-script-profiling-overview.md)  
  
 [Referencia de interfaces de Windows Script](../winscript/reference/windows-script-interfaces-reference.md)  
  
## Fondo de script de Windows  
 Las interfaces de script de Windows pertenecen a dos categorías: Host de script de Windows y motores de scripts de Windows.  Un host crea un motor y llamadas de script en el motor para ejecutar scripts.  Ejemplos de los hosts de script de Windows:  
  
-   Microsoft Internet Explorer  
  
-   Herramientas de creación de internet  
  
-   Shell  
  
 Los motores de scripts de Windows se pueden desarrollar para cualquier lenguaje o entorno en tiempo de ejecución, como:  
  
-   Microsoft Visual Basic Scripting Edition \(VBScript\)  
  
-   Perl  
  
-   Lisp  
  
 Para crear la implementación del host en flexible como sea posible, un contenedor de automatización OLE para crear scripts de Windows se proporciona.  Sin embargo, un host que utiliza este objeto de contenedor para crear instancias del motor de script no tiene el grado de control sobre el espacio de nombres en tiempo de ejecución, el modelo de persistencia, etc., que si utilizó el script de Windows directamente.  
  
 El diseño de Windows scripting aísla los elementos de la interfaz necesarios únicamente en un entorno de creación de modo que hospeda nonauthoring \(como exploradores y visores\) y motores de script \(por ejemplo, VBScript\) se pueden mantener ligeros.  
  
## Arquitectura básica de script de Windows  
 La ilustración siguiente se muestra la interacción entre un host de script de Windows y un motor de script de Windows.  
  
 Los pasos implicados en la interacción entre el host y el motor se indican en la siguiente lista.  
  
1.  Cree un proyecto.  El host carga un proyecto o un documento.  \(Este paso no determina el script de Windows, pero se incluye aquí para mayor precisión\).  
  
2.  Cree el motor de scripts de Windows.  El host llama a `CoCreateInstance` para crear un motor de script de Windows, especificando el identificador de clase \(CLSID\) de motor específico de script para utilizar.  Por ejemplo, el explorador HTML de Internet Explorer recibe el identificador de clase del motor de script con el atributo de CLSID\= HTML label \<OBJECT\>.  
  
3.  Cargue el script.  Si se han conservado el contenido del script, el host llama al método de `IPersist*::Load` del motor de scripts para alimentarle el almacenamiento, la secuencia, o el contenedor de propiedades del script.  Si no, el host utiliza `IPersist*::InitNew` o el método de [IActiveScriptParse::InitNew](../winscript/reference/iactivescriptparse-initnew.md) para crear un script null.  Un host que mantiene un script como texto puede utilizar [IActiveScriptParse::ParseScriptText](../winscript/reference/iactivescriptparse-parsescripttext.md) para alimentar a motor de scripting el texto del script, después de llamar a `IActiveScriptParse::InitNew`.  
  
4.  Agregar denominado elementos.  Para cada elemento denominado de nivel superior \(como páginas y formularios\) importado en el espacio de nombres del motor de script, el host llama al método de [IActiveScript::AddNamedItem](../winscript/reference/iactivescript-addnameditem.md) para crear una entrada en el espacio de nombres del motor.  Este paso no es necesario si los elementos con nombre de nivel superior ya forman parte del estado persistente de script cargado en el paso 3.  Un host no utiliza `IActiveScript::AddNamedItem` para agregar elementos denominados subnivel \(como controles en una página HTML\); en su lugar, el motor obtiene indirectamente elementos de subnivel de elementos de nivel superior mediante las interfaces de `ITypeInfo` y de `IDispatch` host.  
  
5.  Ejecute el script.  El host hace que el motor empiece a ejecuta el script estableciendo la marca de SCRIPTSTATE\_CONNECTED en el método de [IActiveScript::SetScriptState](../winscript/reference/iactivescript-setscriptstate.md).  Esta llamada realizaría probablemente cualquier construcción del motor de scripting, incluido el enlace estático, enlazar a los eventos \(vea a continuación\), y la ejecución del código, de forma similar a una función con scripts de `main()`.  
  
6.  Obtenga información sobre el elemento.  Cada vez que el motor de scripts necesita asociar un símbolo con un elemento de nivel superior, llama al método de [IActiveScriptSite::GetItemInfo](../winscript/reference/iactivescriptsite-getiteminfo.md), que devuelve información sobre el elemento especificado.  
  
7.  Enlazar eventos.  Antes de iniciar el script real, el motor de script se conecta a los eventos de todos los objetos pertinentes a través de la interfaz de `IConnectionPoint`.  
  
8.  Invoca las propiedades y métodos.  Mientras el script se ejecuta, el motor de script realiza referencias a los métodos y propiedades de objetos con nombre a través de `IDispatch::Invoke` u otros mecanismos de enlace de OLE estándar.  
  
## Términos de script de Windows  
 Esta lista contiene definiciones de los términos script\-relacionados utilizados en este documento.  
  
|Término|Definición|  
|-------------|----------------|  
|Objeto de código|Una instancia creada por el motor de scripting que se asocia a un elemento denominado, como el módulo detrás de un formulario en Visual Basic, o a la clase en cuestión. asociada a un elemento con nombre.  Preferiblemente, éste es un objeto de \(COM\) del modelo de objetos componentes OLE que admite la automatización OLE de modo que el host u otra entidad de no script puede manipular el objeto de código.|  
|Elemento denominado|Un objeto COM OLE \(preferiblemente uno que admite la automatización OLE\) que el host juzga interesante al script.  Los ejemplos incluyen la página HTML y el explorador en un explorador web, y el documento y cuadros de Microsoft Word.|  
|Script|Los datos que constituyen el programa que se ejecuta de motor de script.  Un script puede ser cualquier dato ejecutable contiguo, incluidos fragmentos de texto, de bloques de `pcode`, o incluso de códigos ejecutables equipo\- específicos de bytes.  Un host carga un script en el motor de script con una de las interfaces de `IPersist*` o a través de la interfaz de [IActiveScriptParse](../winscript/reference/iactivescriptparse.md).|  
|Motor de script|El objeto OLE que procesa los scripts.  Un motor de scripting implementa las interfaces de [IActiveScript](../winscript/reference/iactivescript.md) y, opcionalmente, de [IActiveScriptParse](../winscript/reference/iactivescriptparse.md).|  
|Host de script|La aplicación o el programa que poseen el motor de scripts de Windows.  El host implementa las interfaces de [IActiveScriptSite](../winscript/reference/iactivescriptsite.md) y, opcionalmente, de [IActiveScriptSiteWindow](../winscript/reference/iactivescriptsitewindow.md).|  
|Scriptlet|Una parte de un script que obtiene asociado a un objeto a través de la interfaz de [IActiveScriptParse](../winscript/reference/iactivescriptparse.md).  La colección global de scriptletes es el script.|  
|Lenguaje de comandos|El lenguaje en el que se escribe un script \(VBScript, por ejemplo\) y la semántica de ese lenguaje.|  
  
## Vea también  
 [Windows Script Interfaces](../winscript/windows-script-interfaces.md)