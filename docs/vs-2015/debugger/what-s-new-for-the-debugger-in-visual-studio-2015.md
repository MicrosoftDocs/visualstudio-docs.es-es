---
title: Novedades del depurador de Visual Studio 2015 | Documentos de Microsoft
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
- debugger, what's new
- what's new [debugger]
- debugging [Visual Studio], what's new
- what's new [Visual Studio], debugging
ms.assetid: 2aed9caa-2384-4e49-8595-82d8b06cf271
caps.latest.revision: 86
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6b7a854e872a7739054379b1f6d01794f142f448
ms.sourcegitcommit: aea5cdb76fbc7eb31d1e5cc3c8d6adb0c743220f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/07/2018
ms.locfileid: "47593125"
---
# <a name="whats-new-for-the-debugger-in-visual-studio-2015"></a>Lo nuevo para el depurador en Visual Studio 2015
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [Novedades del depurador](https://docs.microsoft.com/visualstudio/debugger/what-s-new-for-the-debugger-in-visual-studio).  
  
Para obtener información sobre todas las novedades en materia de depuración y diagnóstico de Visual Studio 2015 Update 1, vea las [notas de la versión de Visual Studio 2015 Update 1](https://www.visualstudio.com/news/vs2015-update1-vs#debug).  
  
 Para obtener información sobre todas las novedades en materia de depuración y diagnóstico de Visual Studio 2015 RTM, vea las [notas de la versión de Visual Studio 2015](https://www.visualstudio.com/news/vs2015-vs#debug).  
  
## <a name="visual-studio-2015-update-1-changes"></a>Cambios en Visual Studio 2015 Update 1  
 La opción Editar y continuar de C++ admite más características. Para obtener más información, consulte [editar y continuar (Visual C++)](../debugger/edit-and-continue-visual-cpp.md).  
  
 Para depurar las infracciones de acceso de Visual C++, un nuevo cuadro de diálogo de excepción especifica el puntero que produjo la excepción. Para obtener más información, consulte [¿cómo se puede depurar una infracción de acceso?](../debugger/how-can-i-debug-an-access-violation-q.md) y [mejora Debugging C++ Access Violations in Visual Studio 2015 Update 1](http://blogs.msdn.com/b/visualstudioalm/archive/2015/10/29/improvement-to-debugging-c-access-violations-in-visual-studio-2015-update-1.aspx)  
  
## <a name="visual-studio-2015-rtm-debugger-ui-and-hotkey-changes"></a>Cambios en la interfaz de usuario y las teclas de acceso rápido del depurador de Visual Studio 2015 RTM  
 Se han introducido cambios importantes en la interfaz de usuario de puntos de interrupción y excepciones.  
  
### <a name="breakpoints"></a>Puntos de interrupción  
 En Visual Studio de 2015 hay una nueva manera de configurar los puntos de interrupción: la ventana **Configuración del punto de interrupción** .  
  
 A continuación tiene un resumen de las ventanas y teclas de acceso rápido principales de los puntos de interrupción:  
  
|Característica|Ubicación en el menú|Tecla de acceso rápido|  
|-------------|-------------------|------------|  
|Nuevo punto de interrupción, alternar puntos de interrupción|**Depurar / Alternar punto de interrupción**<br /><br /> Menú contextual en el editor / **Insertar punto de interrupción**<br /><br /> Clic en el margen izquierdo|F9|  
|Nuevo punto de interrupción de función|**Depurar / nuevo punto de interrupción / punto de interrupción de función**|En Visual Studio 2015 RTM (con ninguna actualización), use ALT + F9, B<br /><br /> En Visual Studio 2015 Update 1 y versiones posteriores, utilice CTRL + B|  
|Ventana**Puntos de interrupción** |**Depurar / Windows / puntos de interrupción**|CTRL + ALT + B|  
|**Configuración del punto de interrupción**, **Condiciones**|Menú contextual en el punto de interrupción / **Condiciones**|ALT + F9, C|  
|**Configuración**, **Acciones**|Menú contextual en el punto de interrupción / **Acciones**|Sin tecla de acceso rápido|  
  
 Para obtener más información, vea los artículos siguientes:  
  
1.  [Usar puntos de interrupción](../debugger/using-breakpoints.md)  
  
2.  [Nueva experiencia de configuración de punto de interrupción](http://blogs.msdn.com/b/visualstudioalm/archive/2014/10/06/new-breakpoint-configuration-experience.aspx)  
  
3.  [Experiencia de configuración de puntos de interrupción](http://channel9.msdn.com/Events/Visual-Studio/Connect-event-2014/711)  
  
### <a name="exception-settings"></a>Configuración de excepciones  
 La nueva ventana **Configuración de excepciones** le permite especificar el tipo de control de excepciones que desea aplicar en excepciones únicas o en categorías de excepciones.  
  
|Característica|Ubicación en el menú|Tecla de acceso rápido|  
|-------------|-------------------|------------|  
|Ventana**Configuración de excepciones** |**Depurar / Windows / Configuración de excepciones**|CTRL + ALT + E|  
  
 Para obtener más información, vea los artículos siguientes:  
  
1.  [Administración de excepciones con el depurador](../debugger/managing-exceptions-with-the-debugger.md)  
  
2.  [La nueva ventana de excepciones](http://blogs.msdn.com/b/visualstudioalm/archive/2015/02/23/the-new-exception-settings-window-in-visual-studio-2015.aspx)  
  
### <a name="edit-and-continue"></a>Editar y continuar  
 En Visual Studio de 2015, Editar y continuar puede establecerse en la página **Herramientas/Opciones/Depuración/General** . En versiones anteriores, estas opciones estaban en una categoría de opciones independiente.  
  
### <a name="attach-to-process"></a>Asociar al proceso  
 En Visual Studio 2015, el comando Asociar al proceso solo está disponible en el menú Depurar. En la versión anterior también estaba disponible en el menú Herramientas. La tecla de acceso rápido CTRL + ALT + P funciona en todas las versiones.  
  
## <a name="see-also"></a>Vea también  
 [Depurar en Visual Studio](../debugger/debugging-in-visual-studio.md)



