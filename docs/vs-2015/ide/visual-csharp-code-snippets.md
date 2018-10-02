---
title: Fragmentos de código de Visual C# | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- snippets [C#], default snippets
- snippets [C#], Code Snippet Inserter
- Code Snippet Inserter [J#]
- Code Snippet Inserter [C#]
- Visual C#, default snippets
ms.assetid: dbea3dd6-e650-4190-b874-c9f097d7de6e
caps.latest.revision: 37
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 2afbadccfc894dd5ba5baba9c58ab43417f44ed5
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/05/2018
ms.locfileid: "47592880"
---
# <a name="visual-c-code-snippets"></a>Fragmentos de código de Visual C#
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [fragmentos de código de Visual C#](https://docs.microsoft.com/visualstudio/ide/visual-csharp-code-snippets).  
  
Los fragmentos de código están listos para usar y puede insertarlos rápidamente en el código. Por ejemplo, el fragmento de código `for` crea un bucle `for` vacío. Algunos fragmentos de código son envolventes, lo que permite seleccionar líneas de código y después elegir un fragmento de código que incorpore las líneas de código seleccionadas. Por ejemplo, al seleccionar líneas de código y activar después el fragmento de código `for`, se creará un bucle `for` que incluirá dichas líneas en su bloque. De este modo, los fragmentos de código hacen de la escritura de código de programación un proceso más rápido, sencillo y fiable.  
  
 Puede insertar un fragmento de código en la posición del cursor o insertar un fragmento de código envolvente alrededor del código seleccionado actualmente. La herramienta de inserción de fragmento de código se invoca a través de los comandos **Insertar fragmento de código** o **Envolver con** del menú **IntelliSense**, o mediante los métodos abreviados de teclado CTRL+K y después X o CTRL+K y después S, respectivamente.  
  
 La herramienta de inserción de fragmento de código muestra el nombre de todos los fragmentos de código disponibles. La herramienta de inserción de fragmento de código también incluye un cuadro de diálogo de entrada en el que puede escribir el nombre del fragmento de código o parte de este. La herramienta de inserción de fragmento de código resalta la coincidencia más cercana a un nombre de fragmento de código. Si se presiona TAB en cualquier momento, se cerrará la herramienta de inserción de fragmento de código y se insertará el fragmento de código seleccionado actualmente. Si se presiona ESC o se hace clic con el mouse en el Editor de código, se cerrará la herramienta de inserción de fragmento de código sin insertar ningún fragmento de código.  
  
## <a name="default-code-snippets"></a>Fragmentos de código predeterminados  
 Los siguientes fragmentos de código se incluyen en Visual Studio de manera predeterminada.  
  
|Nombre (o acceso directo)|Descripción|Ubicaciones válidas donde se puede insertar el fragmento|  
|--------------------------|-----------------|---------------------------------------|  
|#if|Crea una directiva [#if](http://msdn.microsoft.com/library/48cabbff-ca82-491f-a56a-eeccd528c7c2) y una directiva [#endif](http://msdn.microsoft.com/library/6a5fca55-5aee-441f-86f6-1c99fbe9ec05).|En cualquier lugar.|  
|#region|Crea una directiva [#region](http://msdn.microsoft.com/library/672c87d1-9771-4f64-ab3f-0ad3d4ffb2b4) y una directiva [#endregion](http://msdn.microsoft.com/library/16099660-91b2-49e5-9646-77f9ef069526).|En cualquier lugar.|  
|~|Crea un destructor para la clase contenedora.|Dentro de una clase.|  
|Atributo|Crea una declaración para una clase que se deriva de <xref:System.Attribute>.|Dentro de un espacio de nombres (incluido el espacio de nombres global), una clase o un struct.|  
|checked|Crea un bloque [checked](http://msdn.microsoft.com/library/718a1194-988d-48a3-b089-d6ee8bd1608d).|Dentro de un método, un indexador, un descriptor de acceso a propiedad o un descriptor de acceso a evento.|  
|clase|Crea una declaración de clase.|Dentro de un espacio de nombres (incluido el espacio de nombres global), una clase o un struct.|  
|ctor|Crea un constructor para la clase contenedora.|Dentro de una clase.|  
|cw|Crea una llamada a <xref:System.Console.WriteLine%2A>.|Dentro de un método, un indexador, un descriptor de acceso a propiedad o un descriptor de acceso a evento.|  
|do|Crea un [hacer](http://msdn.microsoft.com/library/50725f79-9ba6-4898-aa78-6e331568a1bb) `while` bucle.|Dentro de un método, un indexador, un descriptor de acceso a propiedad o un descriptor de acceso a evento.|  
|else|Crea un bloque [else](http://msdn.microsoft.com/library/d9a1d562-8cf5-4bd4-9ba7-8ad970cd25b2).|Dentro de un método, un indexador, un descriptor de acceso a propiedad o un descriptor de acceso a evento.|  
|enum|Crea una declaración [enum](http://msdn.microsoft.com/library/bbeb9a0f-e9b3-41ab-b0a6-c41b1a08974c).|Dentro de un espacio de nombres (incluido el espacio de nombres global), una clase o un struct.|  
|equals|Crea una declaración de método que invalida el método <xref:System.Object.Equals%2A> que se define en la clase <xref:System.Object>.|Dentro de una clase o un struct.|  
|exception|Crea una declaración de una clase que deriva de una excepción (<xref:System.Exception> de manera predeterminada).|Dentro de un espacio de nombres (incluido el espacio de nombres global), una clase o un struct.|  
|for|Crea un bucle [for](http://msdn.microsoft.com/library/34041a40-2c87-467a-9ffb-a0417d8f67a8).|Dentro de un método, un indexador, un descriptor de acceso a propiedad o un descriptor de acceso a evento.|  
|foreach|Crea un bucle [foreach](http://msdn.microsoft.com/library/5a9c5ddc-5fd3-457a-9bb6-9abffcd874ec).|Dentro de un método, un indexador, un descriptor de acceso a propiedad o un descriptor de acceso a evento.|  
|forr|Crea un bucle [for](http://msdn.microsoft.com/library/34041a40-2c87-467a-9ffb-a0417d8f67a8) que disminuye la variable de bucle después de cada iteración.|Dentro de un método, un indexador, un descriptor de acceso a propiedad o un descriptor de acceso a evento.|  
|if|Crea un bloque [if](http://msdn.microsoft.com/library/d9a1d562-8cf5-4bd4-9ba7-8ad970cd25b2).|Dentro de un método, un indexador, un descriptor de acceso a propiedad o un descriptor de acceso a evento.|  
|indizador|Crea una declaración de indexador.|Dentro de una clase o un struct.|  
|interfaz|Crea una declaración [interface](http://msdn.microsoft.com/library/7da38e81-4f99-4bc5-b07d-c986b687eeba).|Dentro de un espacio de nombres (incluido el espacio de nombres global), una clase o un struct.|  
|invoke|Crea un bloque que invoca un evento de manera segura.|Dentro de un método, un indexador, un descriptor de acceso a propiedad o un descriptor de acceso a evento.|  
|iterator|Crea un iterador.|Dentro de una clase o un struct.|  
|iterindex|Crea un par de iterador e indexador "con nombre" mediante una clase anidada.|Dentro de una clase o un struct.|  
|bloquear|Crea un bloque [lock](http://msdn.microsoft.com/library/656da1a4-707e-4ef6-9c6e-6d13b646af42).|Dentro de un método, un indexador, un descriptor de acceso a propiedad o un descriptor de acceso a evento.|  
|mbox|Crea una llamada a <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=fullName>. Puede que tenga que agregar una referencia a System.Windows.Forms.dll.|Dentro de un método, un indexador, un descriptor de acceso a propiedad o un descriptor de acceso a evento.|  
|namespace|Crea una declaración [namespace](http://msdn.microsoft.com/library/0a788423-9110-42e0-97d9-bda41ca4870f).|Dentro de un espacio de nombres (incluido el espacio de nombres global).|  
|prop|Crea una declaración de [propiedad autoimplementada](http://msdn.microsoft.com/library/aa55fa97-ccec-431f-b5e9-5ac789fd32b7).|Dentro de una clase o un struct.|  
|propfull|Crea una declaración de propiedad con descriptores de acceso get y set.|Dentro de una clase o un struct.|  
|propg|Crea una [propiedad autoimplementada](http://msdn.microsoft.com/library/aa55fa97-ccec-431f-b5e9-5ac789fd32b7) de solo lectura con un descriptor de acceso "set" privado.|Dentro de una clase o un struct.|  
|sim|Crea una declaración de método Main [static](http://msdn.microsoft.com/library/5509e215-2183-4da3-bab4-6b7e607a4fdf)[int](http://msdn.microsoft.com/library/212447b4-5d2a-41aa-88ab-84fe710bdb52).|Dentro de una clase o un struct.|  
|struct|Crea una declaración [struct](http://msdn.microsoft.com/library/ff3dd9b7-dc93-4720-8855-ef5558f65c7c).|Dentro de un espacio de nombres (incluido el espacio de nombres global), una clase o un struct.|  
|svm|Crea una declaración de método Main [static](http://msdn.microsoft.com/library/5509e215-2183-4da3-bab4-6b7e607a4fdf)[void](http://msdn.microsoft.com/library/0d2d8a95-fe20-4fbd-bf5d-c1e54bce71d4).|Dentro de una clase o un struct.|  
|switch|Crea un bloque [switch](http://msdn.microsoft.com/library/44bae8b8-8841-4d85-826b-8a94277daecb).|Dentro de un método, un indexador, un descriptor de acceso a propiedad o un descriptor de acceso a evento.|  
|try|Crea un bloque [try-catch](http://msdn.microsoft.com/library/cb5503c7-bfa1-4610-8fc2-ddcd2e84c438).|Dentro de un método, un indexador, un descriptor de acceso a propiedad o un descriptor de acceso a evento.|  
|tryf|Crea un bloque [try-finally](http://msdn.microsoft.com/library/c27623fb-7261-4464-862c-7a369d3c8f0a).|Dentro de un método, un indexador, un descriptor de acceso a propiedad o un descriptor de acceso a evento.|  
|unchecked|Crea un bloque [unchecked](http://msdn.microsoft.com/library/0c021f7c-923f-4b3d-a58f-55336f5ac27e).|Dentro de un método, un indexador, un descriptor de acceso a propiedad o un descriptor de acceso a evento.|  
|unsafe|Crea un bloque [unsafe](http://msdn.microsoft.com/library/7e818009-1c6e-4b9e-b769-3728a01586a0).|Dentro de un método, un indexador, un descriptor de acceso a propiedad o un descriptor de acceso a evento.|  
|utilizar|Crea una directiva [using](http://msdn.microsoft.com/library/b42b8e61-5e7e-439c-bb71-370094b44ae8).|Dentro de un espacio de nombres (incluido el espacio de nombres global).|  
|while|Crea un bucle [while](http://msdn.microsoft.com/library/72a0765c-6852-4aca-b327-4a11cb7f5c59).|Dentro de un método, un indexador, un descriptor de acceso a propiedad o un descriptor de acceso a evento.|  
  
## <a name="see-also"></a>Vea también  
 [Funciones de los fragmentos de código](../ide/code-snippet-functions.md)   
 [Fragmentos de código](../ide/code-snippets.md)   
 [Cómo: Crear un nuevo fragmento de código con sustituciones](http://msdn.microsoft.com/en-us/8d56d43c-097a-475b-aa85-cae1554b6338)   
 [Parámetros de plantilla](../ide/template-parameters.md)   
 [Cómo: usar fragmentos de código envolventes](../ide/how-to-use-surround-with-code-snippets.md)   
 [Cómo: Restaurar fragmentos de código de refactorización de C#](../ide/how-to-restore-csharp-refactoring-snippets.md)



