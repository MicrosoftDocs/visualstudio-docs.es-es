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
ms.openlocfilehash: 95d76781f651b681b81e4dd18848b404d8a85664
ms.sourcegitcommit: c57ae28181ffe14a30731736661bf59c3eff1211
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/11/2018
ms.locfileid: "38809273"
---
 Puede depurar su código con los símbolos que se generan en el equipo de Visual Studio. El rendimiento del depurador remoto es mucho mejor cuando se usan símbolos locales.  Si debe usar símbolos remotos, deberá indicar al monitor de depuración remota que busque símbolos en el equipo remoto.  
  
 A partir de Visual Studio 2013 Update 2, puede usar el siguiente modificador de línea de comandos de msvsmon para usar símbolos remotos para código administrado: `Msvsmon /FallbackLoadRemoteManagedPdbs`  
  
 Para obtener más información, consulte la Ayuda de depuración remota (presione **F1** en la ventana del depurador remoto, o haga clic en **Ayuda > uso**). Puede encontrar más información en [remoto cargar cambios de símbolos .NET en Visual Studio 2012 y 2013](http://blogs.msdn.com/b/visualstudioalm/archive/2013/10/16/net-remote-symbol-loading-changes-in-visual-studio-2012-and-2013.aspx)