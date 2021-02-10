---
title: Depuración de un control ActiveX enlazado a datos | Microsoft Docs
description: Obtenga información sobre cómo depurar un control ActiveX enlazado a un control de origen de datos mediante la creación de una aplicación contenedora para la depuración.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 24de30887185ce4520817904ec6348ef6276b6d2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99872903"
---
# <a name="debugging-a-data-bound-activex-control"></a>Depurar un control ActiveX enlazado a datos
Si está desarrollando un control ActiveX que se enlazará a un control de origen de datos, puede crear su propia aplicación contenedora y utilizar dicho contenedor para depurar el control ActiveX.

 Por ejemplo, puede crear una aplicación MFC basada en cuadros de diálogo y colocar el control enlazado a datos y un control de origen de datos en el cuadro de diálogo. Puede utilizar esta aplicación MFC para la comprobación en tiempo de ejecución y como contenedor ejecutable para depurar el control ActiveX enlazado a datos.

## <a name="using-the-test-container"></a>Utilizar Test Container
 Si desea un contenedor que pueda modificar fácilmente para que admita diversas interfaces tanto en el control como en el contenedor, utilice ActiveX Test Container como archivo ejecutable para la sesión de depuración. En ActiveX Test Container, haga clic en **Opciones**, en el menú **Contenedor**, para habilitar diversas interfaces. Para más información, vea [Probar propiedades y eventos con un contenedor de prueba](/cpp/mfc/testing-properties-and-events-with-test-container).

 Si necesita ejecutar paso a paso el código del contenedor mientras realiza la depuración, utilice la versión de depuración del contenedor o emplee la versión del depurador de ActiveX Test Container. Para más información, vea [Ejemplo de TSTCON: contenedor de pruebas de controles ActiveX](/previous-versions/f9adb5t5(v=vs.100)).

## <a name="see-also"></a>Vea también
- [Depurar COM y ActiveX](../debugger/com-and-activex-debugging.md)
- [Controles ActiveX](/cpp/mfc/activex-controls)