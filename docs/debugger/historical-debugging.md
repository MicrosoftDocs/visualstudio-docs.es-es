---
title: Depuración histórica | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 7cc5ddf2-2f7c-4f83-b7ca-58e92e9bfdd2
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 45d62cec0116ae029237423a7453c9572d20a895
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53883933"
---
# <a name="historical-debugging"></a>Depuración histórica
Depuración histórica es un modo de depuración que depende de la información recopilada por IntelliTrace. Le permite desplazarse hacia atrás y hacia delante por la ejecución de la aplicación y comprobar su estado.  
  
 Puede usar IntelliTrace en Visual Studio Enterprise (pero no en las ediciones Professional o Community).  
  
## <a name="why-use-historical-debugging"></a>¿Por qué usar la característica Depuración histórica?  
 Establecer puntos de interrupción para encontrar errores puede ser cuestión de suerte. Establezca un punto de interrupción cerca del lugar en el código donde sospecha que está el error y luego ejecute la aplicación en el depurador. Con suerte, se alcanzará el punto de interrupción en un lugar que revele el origen del error. De lo contrario, tendrá que establecer un punto de interrupción en otro lugar del código y volver a ejecutar el depurador, y así una y otra vez hasta que encuentre el problema.  
  
 ![establecer un punto de interrupción](../debugger/media/breakpointprocesa.png "BreakpointProcesa")  
  
 Puede usar IntelliTrace y depuración histórica para recorrer la aplicación e inspeccionar su estado (pila de llamadas y variables locales) sin tener que establecer puntos de interrupción, reiniciar la depuración y repetir los pasos de prueba. Esto puede ahorrarle mucho tiempo, especialmente cuando el error se encuentra escondido en un escenario de prueba que se tarda en ejecutar.  
  
## <a name="how-do-i-start-using-historical-debugging"></a>¿Cómo empiezo a usar la depuración histórica?  
 De forma predeterminada, IntelliTrace está habilitado. Todo lo que debe hacer es decidir qué eventos y llamadas de función son de interés para usted, y si desea ver las instantáneas de su estado de la aplicación completa. Para obtener más información sobre cómo definir lo que quiere buscar, consulte [Características de IntelliTrace](../debugger/intellitrace-features.md).  

 - Para ver las instantáneas con depuración histórica, vea [inspeccionar el estado anterior de aplicación con IntelliTrace](../debugger/view-historical-application-state.md)
 - Para obtener información sobre cómo inspeccionar variables y navegar por el código, consulte [inspeccionar la aplicación con depuración histórica](../debugger/historical-debugging-inspect-app.md)
 - Para más información sobre cómo depurar con eventos de IntelliTrace, consulte [Tutorial: Uso de IntelliTrace](../debugger/walkthrough-using-intellitrace.md).