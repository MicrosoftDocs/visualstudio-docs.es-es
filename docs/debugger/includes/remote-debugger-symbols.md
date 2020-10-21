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
ms.openlocfilehash: 5033580f253a5eb42cbc64656e8c4661a2e246c1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72912859"
---
Puede depurar su código con los símbolos que se generan en el equipo de Visual Studio. El rendimiento del depurador remoto es mucho mejor cuando se usan símbolos locales.  Si debe usar símbolos remotos, deberá indicar al monitor de depuración remota que busque símbolos en el equipo remoto.  

A partir de Visual Studio 2013 Update 2, puede usar el siguiente modificador de línea de comandos de msvsmon para usar símbolos remotos para el código administrado: `Msvsmon /FallbackLoadRemoteManagedPdbs`  

Para obtener más información, vea la ayuda de depuración remota (presione **F1** en la ventana del depurador remoto, o haga clic en **Ayuda > Uso**). Encontrará más información en [Cambios en la carga remota de símbolos .NET en Visual Studio 2012 y 2013](https://devblogs.microsoft.com/devops/net-remote-symbol-loading-changes-in-visual-studio-2012-and-2013/).
