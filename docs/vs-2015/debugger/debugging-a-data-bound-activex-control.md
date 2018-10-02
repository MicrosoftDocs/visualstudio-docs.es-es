---
title: Depurar un Control de ActiveX enlazado a datos | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
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
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6642b3687e4459cc001aef14ce0c1186231f8c97
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47577340"
---
# <a name="debugging-a-data-bound-activex-control"></a>Depurar un control ActiveX enlazado a datos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [depurar un ActiveX Control enlazado a datos](https://docs.microsoft.com/visualstudio/debugger/debugging-a-data-bound-activex-control).  
  
Si está desarrollando un control ActiveX que se enlazará a un control de origen de datos, puede crear su propia aplicación contenedora y utilizar dicho contenedor para depurar el control ActiveX.  
  
 Por ejemplo, puede crear una aplicación MFC basada en cuadros de diálogo y colocar el control enlazado a datos y un control de origen de datos en el cuadro de diálogo. Puede utilizar esta aplicación MFC para la comprobación en tiempo de ejecución y como contenedor ejecutable para depurar el control ActiveX enlazado a datos.  
  
## <a name="using-the-test-container"></a>Utilizar Test Container  
 Si desea un contenedor que pueda modificar fácilmente para que admita diversas interfaces tanto en el control como en el contenedor, utilice ActiveX Test Container como archivo ejecutable para la sesión de depuración. En ActiveX Test Container, haga clic en **opciones** desde el **contenedor** menú para habilitar diversas interfaces. Para obtener más información, consulte [Probar propiedades y eventos con un contenedor de prueba](http://msdn.microsoft.com/library/626867cf-fe53-4c30-8973-55bb93ef3917).  
  
 Si necesita ejecutar paso a paso el código del contenedor mientras realiza la depuración, utilice la versión de depuración del contenedor o emplee la versión del depurador de ActiveX Test Container. Para obtener más información, consulte [ejemplo TSTCON: ActiveX Control Test Container](http://msdn.microsoft.com/en-us/72fa40ef-27d3-400c-813f-10b03236e600).  
  
## <a name="see-also"></a>Vea también  
 [Depurar COM y ActiveX](../debugger/com-and-activex-debugging.md)   
 [Controles ActiveX](http://msdn.microsoft.com/library/52aaec4d-3889-402e-b57d-758078f8ac57)



