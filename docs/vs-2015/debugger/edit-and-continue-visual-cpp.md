---
title: Editar y continuar (Visual C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
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
- Edit and Continue [C++]
- debugging [C++], Edit and Continue
- C/C++, Edit and Continue
ms.assetid: 1815251e-a877-433e-9e5e-69bd9ba254c7
caps.latest.revision: 28
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c82835c669eb1afd7f2fc558f89c3c30382a9b0a
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49255094"
---
# <a name="edit-and-continue-visual-c"></a>Editar y continuar (Visual C++)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede usar Editar y continuar en proyectos de Visual C++. Consulte [cambios de código compatible (C++)](../debugger/supported-code-changes-cpp.md) para obtener información acerca de las limitaciones de editar y continuar.  
  
 A partir de Visual Studio 2015 Update 1, ahora puede usar Editar y continuar en aplicaciones de C++ de Windows Store y aplicaciones de DirectX, ya que ahora admite la **/Zi** modificador del compilador con **/bigobj** cambie. También puede usar Editar y continuar con binarios compilados con la **/FASTLINK** cambie.  
  
 Otras mejoras de la actualización 1 incluyen un cuadro de diálogo de espera nuevo que se puede cancelar y una notificación cuando un archivo no admite Editar y continuar. Para obtener más información acerca de las mejoras de Update 1, consulte [mejoras para C++ editar y continuar de Visual Studio 2015 Update 1](http://blogs.msdn.com/b/vcblog/archive/2015/11/30/improvements-for-c-edit-and-continue-in-visual-studio-2015-update-1.aspx).  
  
 El [/Zo (mejorar la depuración optimizada)](http://msdn.microsoft.com/library/eea8d89a-7fe0-4fe1-86b2-7689bbebbd7f) opción del compilador que se introdujo en Visual Studio 2013 Update 3 agrega información adicional a los archivos .pdb (símbolo) para los archivos binarios compilan sin la [/Od (deshabilitar (depurar)) ](http://msdn.microsoft.com/library/aafb762y.aspx) opción.  
  
 **/ Zo** deshabilita Editar y continuar. Consulte [Cómo: depurar código optimizado](../debugger/how-to-debug-optimized-code.md).  
  
##  <a name="BKMK_Enable_or_disable_automatic_invocation_of_Edit_and_Continue"></a> Habilitar o deshabilitar Editar y continuar  
 Quizá quiera deshabilitar la invocación automática de Editar y continuar si realiza modificaciones en el código que no quiere aplicar durante la sesión de depuración actual. También puede volver a habilitar la invocación automática de Editar y continuar.  
  
1.  En el menú **Herramientas** , elija **Opciones**.  
  
2.  En el cuadro de diálogo **Opciones** , seleccione **Depuración / General**.  
  
3.  En el grupo **Editar y continuar** , active o desactive la casilla **Habilitar la opción Editar y continuar nativa** .  
  
 La modificación de esta configuración afecta a todos los proyectos en los que trabaje. No es necesario recompilar la aplicación después de cambiar esta configuración. Puede cambiarla incluso mientras realiza la depuración. Si compila la aplicación desde la línea de comandos o desde un archivo Make, pero realiza la depuración en el entorno de Visual Studio, puede seguir usando Editar y continuar si establece la opción **/ZI** .  
  
##  <a name="BKMK_How_to_apply_code_changes_explicitly"></a> Aplicar cambios en el código de forma explícita  
 En Visual C++, Editar y continuar puede aplicar cambios de código de dos maneras. Los cambios de código se pueden aplicar de forma implícita cuando se elige un comando de ejecución, o de forma explícita mediante el comando **Aplicar cambios en el código** .  
  
 Cuando los cambios en el código se aplican de forma explícita, el programa permanece en modo de interrupción y no se produce ninguna ejecución.  
  
-   Para aplicar los cambios en el código de manera explícita, vaya al menú **Depurar** y elija **Aplicar cambios en el código**.  
  
##  <a name="BKMK_How_to_stop_code_changes"></a> Detener cambios en el código  
 Mientras Editar y continuar se encuentra en proceso de aplicar los cambios del código, puede detener la operación.  
  
 Para detener la aplicación de los cambios en el código:  
  
-   En el menú **Depurar** , elija **Detener la aplicación de cambios en el código**.  
  
 Este elemento de menú sólo es visible cuando se están aplicando los cambios del código.  
  
 Si elige esta opción, no se confirmará ninguno de los cambios en el código.  
  
##  <a name="BKMK_How_to_reset_the_point_of_execution"></a> Restablecer el punto de ejecución  
 Algunos cambios realizados en el código pueden hacer que el punto de ejecución se desplace a una nueva ubicación cuando Editar y continuar aplique los cambios. Editar y continuar coloca el punto de ejecución con la mayor exactitud posible, pero puede ocurrir que los resultados no sean correctos en todos los casos.  
  
 En Visual C++, un cuadro de diálogo le informa cuando cambia el punto de ejecución. Deberá comprobar si la ubicación es correcta antes de continuar con la depuración. Si no es correcta, utilice el comando **Establecer instrucción siguiente** . Para más información, consulte [Establecer la siguiente instrucción que se debe ejecutar](http://msdn.microsoft.com/library/y740d9d3.aspx#BKMK_Set_the_next_statement_to_execute).  
  
##  <a name="BKMK_How_to_work_with_stale_code"></a> Trabajar con código obsoleto  
 En algunos casos, la función Editar y continuar no puede aplicar al archivo ejecutable cambios en el código de forma inmediata, pero puede que lo consiga más tarde si continúa la depuración. Esto ocurre si se modifica una función que llama a la función actual o se agregan más de 64 bytes de nuevas variables a una función que está en la pila de llamadas.  
  
 En esos casos, el depurador sigue ejecutando el código original hasta que se puedan aplicar los cambios. El código obsoleto aparece como una ventana de archivo de código fuente temporal en una ventana de código fuente independiente, con un título como `enc25.tmp`. El código fuente modificado continúa apareciendo en la ventana de código fuente original. Si intenta modificar el código obsoleto, aparece un mensaje de advertencia.  
  
## <a name="see-also"></a>Vea también  
 [Cambios admitidos en el código (C++)](../debugger/supported-code-changes-cpp.md)



