---
title: Edit and Continue (Visual C++) | Microsoft Docs
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
- Edit and Continue [C++]
- debugging [C++], Edit and Continue
- C/C++, Edit and Continue
ms.assetid: 1815251e-a877-433e-9e5e-69bd9ba254c7
caps.latest.revision: 28
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: fef02f08ac635687eaaf071188ba0455c6389d9e
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2019
ms.locfileid: "74301061"
---
# <a name="edit-and-continue-visual-c"></a>Editar y continuar (Visual C++)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede usar Editar y continuar en proyectos de Visual C++. See [Supported Code Changes (C++)](../debugger/supported-code-changes-cpp.md) for information about the limitations of Edit and Continue.  
  
 Starting in Visual Studio 2015 Update 1, you can now use Edit and Continue in Windows Store C++ apps and DirectX apps, because it now supports the **/ZI** compiler switch with **/bigobj** switch. You can also use Edit  and Continue with binaries compiled with the **/FASTLINK** switch.  
  
 Other Update 1 improvements include a new, cancelable wait dialog, and notification when a file does not support Edit and Continue. For more information about Update 1 improvements, see [Improvements for C++ Edit and Continue in Visual Studio 2015 Update 1](https://devblogs.microsoft.com/cppblog/improvements-for-c-edit-and-continue-in-visual-studio-2015-update-1/).  
  
 La opción de compilador [/Zo (Mejorar la depuración optimizada)](https://msdn.microsoft.com/library/eea8d89a-7fe0-4fe1-86b2-7689bbebbd7f) que se introdujo en Visual Studio 2013 actualización 3 agrega información adicional a los archivos .pdb (símbolo) para los archivos binarios que se compilan sin la opción [/Od (Deshabilitar (Depurar))](https://msdn.microsoft.com/library/aafb762y.aspx).  
  
 **/Zo** disables Edit and Continue. Consulte [Cómo: Depurar código optimizado](../debugger/how-to-debug-optimized-code.md).  
  
## <a name="BKMK_Enable_or_disable_automatic_invocation_of_Edit_and_Continue"></a> Habilitar o deshabilitar Editar y continuar  
 Quizá quiera deshabilitar la invocación automática de Editar y continuar si realiza modificaciones en el código que no quiere aplicar durante la sesión de depuración actual. También puede volver a habilitar la invocación automática de Editar y continuar.  
  
1. En el menú **Herramientas** , elija **Opciones**.  
  
2. En el cuadro de diálogo **Opciones** , seleccione **Depuración / General**.  
  
3. En el grupo **Editar y continuar** , active o desactive la casilla **Habilitar la opción Editar y continuar nativa** .  
  
   La modificación de esta configuración afecta a todos los proyectos en los que trabaje. No es necesario recompilar la aplicación después de cambiar esta configuración. Puede cambiarla incluso mientras realiza la depuración. Si compila la aplicación desde la línea de comandos o desde un archivo Make, pero realiza la depuración en el entorno de Visual Studio, puede seguir usando Editar y continuar si establece la opción **/ZI** .  
  
## <a name="BKMK_How_to_apply_code_changes_explicitly"></a> Aplicar cambios en el código de forma explícita  
 En Visual C++, Editar y continuar puede aplicar cambios de código de dos maneras. Los cambios de código se pueden aplicar de forma implícita cuando se elige un comando de ejecución, o de forma explícita mediante el comando **Aplicar cambios en el código** .  
  
 Cuando los cambios en el código se aplican de forma explícita, el programa permanece en modo de interrupción y no se produce ninguna ejecución.  
  
- Para aplicar los cambios en el código de manera explícita, vaya al menú **Depurar** y elija **Aplicar cambios en el código**.  
  
## <a name="BKMK_How_to_stop_code_changes"></a> Detener cambios en el código  
 Mientras Editar y continuar se encuentra en proceso de aplicar los cambios del código, puede detener la operación.  
  
 Para detener la aplicación de los cambios en el código:  
  
- En el menú **Depurar** , elija **Detener la aplicación de cambios en el código**.  
  
  Este elemento de menú sólo es visible cuando se están aplicando los cambios del código.  
  
  Si elige esta opción, no se confirmará ninguno de los cambios en el código.  
  
## <a name="BKMK_How_to_reset_the_point_of_execution"></a> Restablecer el punto de ejecución  
 Algunos cambios realizados en el código pueden hacer que el punto de ejecución se desplace a una nueva ubicación cuando Editar y continuar aplique los cambios. Editar y continuar coloca el punto de ejecución con la mayor exactitud posible, pero puede ocurrir que los resultados no sean correctos en todos los casos.  
  
 En Visual C++, un cuadro de diálogo le informa cuando cambia el punto de ejecución. Deberá comprobar si la ubicación es correcta antes de continuar con la depuración. Si no es correcta, utilice el comando **Establecer instrucción siguiente** . Para más información, consulte [Establecer la siguiente instrucción que se debe ejecutar](https://msdn.microsoft.com/library/y740d9d3.aspx#BKMK_Set_the_next_statement_to_execute).  
  
## <a name="BKMK_How_to_work_with_stale_code"></a> Trabajar con código obsoleto  
 En algunos casos, la función Editar y continuar no puede aplicar al archivo ejecutable cambios en el código de forma inmediata, pero puede que lo consiga más tarde si continúa la depuración. Esto ocurre si se modifica una función que llama a la función actual o se agregan más de 64 bytes de nuevas variables a una función que está en la pila de llamadas.  
  
 En esos casos, el depurador sigue ejecutando el código original hasta que se puedan aplicar los cambios. El código obsoleto aparece como una ventana de archivo de código fuente temporal en una ventana de código fuente independiente, con un título como `enc25.tmp`. El código fuente modificado continúa apareciendo en la ventana de código fuente original. Si intenta modificar el código obsoleto, aparece un mensaje de advertencia.  
  
## <a name="see-also"></a>Vea también  
 [Cambios admitidos en el código (C++)](../debugger/supported-code-changes-cpp.md)
