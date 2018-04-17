---
title: Depuración histórica | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
ms.assetid: 7cc5ddf2-2f7c-4f83-b7ca-58e92e9bfdd2
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1f8019d9363b2a599ac4115c3d6d25a465a3bd0a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="historical-debugging"></a>Depuración histórica
Depuración histórica es un modo de depuración que depende de la información recopilada por IntelliTrace. Le permite desplazarse hacia atrás y hacia delante por la ejecución de la aplicación y comprobar su estado.  
  
 Puede usar IntelliTrace en Visual Studio Enterprise (pero no en las ediciones Professional o Community).  
  
## <a name="why-use-historical-debugging"></a>¿Por qué usar depuración histórica?  
 Establecer puntos de interrupción para encontrar errores puede ser cuestión de suerte. Establezca un punto de interrupción cerca del lugar en el código donde sospecha que está el error y luego ejecute la aplicación en el depurador. Con suerte, se alcanzará el punto de interrupción en un lugar que revele el origen del error. Si no es así, tendrá que establecer un punto de interrupción en alguna otra parte en el código y volver a ejecutar el depurador, los pasos de prueba una y otra vez hasta que encuentre el problema.  
  
 ![establecer un punto de interrupción](../debugger/media/breakpointprocesa.png "BreakpointProcesa")  
  
 Puede usar IntelliTrace y depuración histórica para recorrer la aplicación e inspeccionar su estado (pila de llamadas ni variables locales) sin tener que establecer puntos de interrupción, reinicie la depuración y repita los pasos de prueba. Esto puede ahorrarle mucho tiempo, especialmente cuando el error se encuentra escondido en un escenario de prueba que se tarda en ejecutar.  
  
## <a name="how-do-i-start-using-historical-debugging"></a>¿Cómo empezar a usar depuración histórica?  
 De forma predeterminada, IntelliTrace está habilitado. Lo único que tiene que hacer es decidir qué eventos y llamadas a funciones son de interés y, si desea ver las instantáneas de su estado completo de la aplicación. Para obtener más información acerca de cómo definir lo que desea buscar, consulte [características de IntelliTrace](../debugger/intellitrace-features.md).  

 - Para ver las instantáneas con depuración histórica, vea [ver instantáneas mediante la devolución de paso de IntelliTrace](../debugger/how-to-use-intellitrace-step-back.md)
 - Para obtener información sobre cómo inspeccionar variables y navegar por el código, vea [inspeccionar la aplicación con depuración histórica](../debugger/historical-debugging-inspect-app.md)
 - Para más información acerca de cómo depurar con eventos de IntelliTrace, vea [Tutorial: uso de IntelliTrace](../debugger/walkthrough-using-intellitrace.md).