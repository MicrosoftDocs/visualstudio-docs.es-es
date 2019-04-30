---
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.openlocfilehash: 26d9169be242990b9ca99b4fe4fe043d56fb7f30
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62903539"
---
Puede depurar su código con los símbolos que se generan en el equipo de Visual Studio. El rendimiento del depurador remoto es mucho mejor cuando se usan símbolos locales.  Si debe usar símbolos remotos, deberá indicar al monitor de depuración remota que busque símbolos en el equipo remoto.  

A partir de Visual Studio 2013 Update 2, puede usar el siguiente modificador de línea de comandos de msvsmon para usar símbolos remotos para el código administrado: `Msvsmon /FallbackLoadRemoteManagedPdbs`  

Para obtener más información, vea la ayuda de depuración remota (presione **F1** en la ventana del depurador remoto, o haga clic en **Ayuda > Uso**). Encontrará más información en [Cambios en la carga remota de símbolos .NET en Visual Studio 2012 y 2013](http://blogs.msdn.com/b/visualstudioalm/archive/2013/10/16/net-remote-symbol-loading-changes-in-visual-studio-2012-and-2013.aspx).
