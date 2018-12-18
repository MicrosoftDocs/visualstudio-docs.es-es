---
title: Depuración histórica | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 7cc5ddf2-2f7c-4f83-b7ca-58e92e9bfdd2
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0a622fcb91ad40e7d0777f37ce87e9a2cb950695
ms.sourcegitcommit: a749c287ec7d54148505978e8ca55ccd406b71ee
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/21/2018
ms.locfileid: "46542408"
---
# <a name="historical-debugging"></a>Depuración histórica
Depuración histórica es un modo de depuración que depende de la información recopilada por IntelliTrace. Le permite desplazarse hacia atrás y hacia delante por la ejecución de la aplicación y comprobar su estado.  
  
 Puede usar IntelliTrace en Visual Studio Enterprise (pero no en las ediciones Professional o Community).  
  
## <a name="why-use-historical-debugging"></a>¿Por qué usar depuración histórica?  
 Establecer puntos de interrupción para encontrar errores puede ser cuestión de suerte. Establezca un punto de interrupción cerca del lugar en el código donde sospecha que está el error y luego ejecute la aplicación en el depurador. Con suerte, se alcanzará el punto de interrupción en un lugar que revele el origen del error. Si no es así, tendrá que probar la configuración de un punto de interrupción en alguna otra parte en el código y vuelva a ejecutar al depurador, ejecutar los pasos de prueba y otra vez hasta que encuentre el problema.  
  
 ![establecer un punto de interrupción](../debugger/media/breakpointprocesa.png "BreakpointProcesa")  
  
 Puede usar IntelliTrace y depuración histórica para recorrer la aplicación e inspeccionar su estado (pila de llamadas y variables locales) sin tener que establecer puntos de interrupción, reinicie la depuración y repita los pasos de prueba. Esto puede ahorrarle mucho tiempo, especialmente cuando el error se encuentra escondido en un escenario de prueba que se tarda en ejecutar.  
  
## <a name="how-do-i-start-using-historical-debugging"></a>¿Cómo se puede iniciar depuración histórica?  
 De forma predeterminada, IntelliTrace está habilitado. Todo lo que debe hacer es decidir qué eventos y llamadas de función son de interés para usted, y si desea ver las instantáneas de su estado de la aplicación completa. Para obtener más información acerca de cómo definir lo que desea buscar, ver [las características de IntelliTrace](../debugger/intellitrace-features.md).  

 - Para ver las instantáneas con depuración histórica, vea [inspeccionar el estado anterior de aplicación con IntelliTrace](../debugger/view-historical-application-state.md)
 - Para obtener información sobre cómo inspeccionar variables y navegar por el código, consulte [inspeccionar la aplicación con depuración histórica](../debugger/historical-debugging-inspect-app.md)
 - Para más información sobre cómo depurar con eventos de IntelliTrace, consulte [Tutorial: uso de IntelliTrace](../debugger/walkthrough-using-intellitrace.md).