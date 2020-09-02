---
title: Depuración de un control ActiveX enlazado a datos | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- data-bound controls, ActiveX
- ActiveX controls, debugging
- controls [Visual Studio], ActiveX
ms.assetid: 9f6e1f00-e25b-48a9-8484-7e67a1232461
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6945d1ccf72385b4d2fbe76736668e84b804e446
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "65686750"
---
# <a name="debugging-a-data-bound-activex-control"></a>Depurar un control ActiveX enlazado a datos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Si está desarrollando un control ActiveX que se enlazará a un control de origen de datos, puede crear su propia aplicación contenedora y utilizar dicho contenedor para depurar el control ActiveX.  
  
 Por ejemplo, puede crear una aplicación MFC basada en cuadros de diálogo y colocar el control enlazado a datos y un control de origen de datos en el cuadro de diálogo. Puede utilizar esta aplicación MFC para la comprobación en tiempo de ejecución y como contenedor ejecutable para depurar el control ActiveX enlazado a datos.  
  
## <a name="using-the-test-container"></a>Utilizar Test Container  
 Si desea un contenedor que pueda modificar fácilmente para que admita diversas interfaces tanto en el control como en el contenedor, utilice ActiveX Test Container como archivo ejecutable para la sesión de depuración. En ActiveX Test Container, haga clic en **Opciones**, en el menú **Contenedor**, para habilitar diversas interfaces. Para más información, vea [Probar propiedades y eventos con un contenedor de prueba](https://msdn.microsoft.com/library/626867cf-fe53-4c30-8973-55bb93ef3917).  
  
 Si necesita ejecutar paso a paso el código del contenedor mientras realiza la depuración, utilice la versión de depuración del contenedor o emplee la versión del depurador de ActiveX Test Container. Para más información, vea [Ejemplo de TSTCON: contenedor de pruebas de controles ActiveX](https://msdn.microsoft.com/72fa40ef-27d3-400c-813f-10b03236e600).  
  
## <a name="see-also"></a>Consulte también  
 [Depuración COM y ActiveX](../debugger/com-and-activex-debugging.md)   
 [Controles ActiveX](https://msdn.microsoft.com/library/52aaec4d-3889-402e-b57d-758078f8ac57)
