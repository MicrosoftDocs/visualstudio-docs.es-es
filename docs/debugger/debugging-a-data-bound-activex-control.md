---
title: Depurar un Control de ActiveX enlazado a datos | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- data-bound controls, ActiveX
- ActiveX controls, debugging
- controls [Visual Studio], ActiveX
ms.assetid: 9f6e1f00-e25b-48a9-8484-7e67a1232461
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6eae5820e7203b69ed6d08e398aef661d842906a
ms.sourcegitcommit: 5a65ca6688a2ebb36564657d2d73c4b4f2d15c34
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/16/2019
ms.locfileid: "53837854"
---
# <a name="debugging-a-data-bound-activex-control"></a>Depurar un control ActiveX enlazado a datos
Si está desarrollando un control ActiveX que se enlazará a un control de origen de datos, puede crear su propia aplicación contenedora y utilizar dicho contenedor para depurar el control ActiveX.  
  
 Por ejemplo, puede crear una aplicación MFC basada en cuadros de diálogo y colocar el control enlazado a datos y un control de origen de datos en el cuadro de diálogo. Puede utilizar esta aplicación MFC para la comprobación en tiempo de ejecución y como contenedor ejecutable para depurar el control ActiveX enlazado a datos.  
  
## <a name="using-the-test-container"></a>Utilizar Test Container  
 Si desea un contenedor que pueda modificar fácilmente para que admita diversas interfaces tanto en el control como en el contenedor, utilice ActiveX Test Container como archivo ejecutable para la sesión de depuración. En ActiveX Test Container, haga clic en **Opciones**, en el menú **Contenedor**, para habilitar diversas interfaces. Para obtener más información, consulte [Probar propiedades y eventos con un contenedor de prueba](/cpp/mfc/testing-properties-and-events-with-test-container).  
  
 Si necesita ejecutar paso a paso el código del contenedor mientras realiza la depuración, utilice la versión de depuración del contenedor o emplee la versión del depurador de ActiveX Test Container. Para obtener más información, consulte [ejemplo TSTCON: ActiveX Control Test Container.  
  
## <a name="see-also"></a>Vea también  
 [Depuración de COM y ActiveX](../debugger/com-and-activex-debugging.md)   
 [Controles ActiveX](/cpp/mfc/activex-controls)