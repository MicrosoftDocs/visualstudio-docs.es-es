---
title: Cuadro de diálogo Editar y continuar mensaje de error | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.ENC.SupportedButNotAvailable
- vs.debug.ENC.CannotEditWhileException
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Edit and Continue Error Message dialog box
ms.assetid: f98c91c0-447a-4533-85b6-87170a0dc4c3
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5437ef982309ef8595f08283f2685e93d346e764
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "62428305"
---
# <a name="edit-and-continue-error-message-dialog-box"></a>Editar y continuar (Cuadro de diálogo de mensaje de error)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Este cuadro de diálogo aparece cuando se depura en un lenguaje que admite editar y continuar, pero **Editar y continuar** no está disponible para el tipo de cambios de código realizados. El mensaje de error incluido en el cuadro proporciona una explicación más detallada. Entre las posibles razones para que aparezca este cuadro de diálogo se incluyen:  
  
- Se intentó editar código administrado cuando estaba habilitada la depuración no administrada. Editar y continuar no funciona con la depuración en modo mixto.  
  
- Se intentó editar código de SQL Server.  
  
- Se intentó editar código durante la depuración de un volcado de Dr. Watson.  
  
- Se intentó editar código después de que se produjera una excepción no controlada y no se seleccionó la opción "**desenredar la pila de llamadas en excepciones no controladas**".  
  
- Se intentó editar código mientras se depuraba una aplicación incrustada en tiempo de ejecución.  
  
- Se intentó editar código en un programa al que se adjuntó en lugar de iniciarse en el menú **depurar** .  
  
- Se intentó editar código optimizado.  
  
- Se intentó editar código administrado cuando el destino es una aplicación de 64 bits. Si desea utilizar la opción Editar y continuar, deberá establecer el destino en x86. (*Project* **Propiedades**del proyecto, pestaña **compilar** , configuración de **compilador avanzada** ).  
  
- Se intentó editar código en un ensamblado que se modificó durante la depuración y se ha vuelto ha cargar.  
  
- Se intentó editar código en un ensamblado que no se ha cargado.  
  
- Se inició la depuración de una versión anterior de la aplicación (ya que la nueva versión tenía errores de compilación).  
  
- Se intentó editar código mientras se estaba ejecutando.  
  
## <a name="uielement-list"></a>Lista de UIElement  
 **OK (CORRECTO)**  
 Sale del cuadro de diálogo y cancela el intento de edición inmediatamente anterior.  
  
## <a name="see-also"></a>Consulte también  
 [Cambios admitidos en el código (C++)](../debugger/supported-code-changes-cpp.md)
