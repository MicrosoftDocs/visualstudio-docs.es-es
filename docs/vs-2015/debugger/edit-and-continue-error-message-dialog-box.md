---
title: Editar y continuar en el cuadro de diálogo de mensaje de Error | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.ENC.SupportedButNotAvaiable
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
manager: ghogen
ms.openlocfilehash: c311f6243ddbf087fd18fd9209e2e17bbe3065a6
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51771325"
---
# <a name="edit-and-continue-error-message-dialog-box"></a>Editar y continuar (Cuadro de diálogo de mensaje de error)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Este cuadro de diálogo aparece cuando se depura en un lenguaje que admite Editar y continuar, pero **editar y continuar** no está disponible para el tipo de cambios de código que ha realizado. El mensaje de error incluido en el cuadro proporciona una explicación más detallada. Entre las posibles razones para que aparezca este cuadro de diálogo se incluyen:  
  
-   Se intentó editar código administrado cuando estaba habilitada la depuración no administrada. Editar y continuar no funciona con la depuración en modo mixto.  
  
-   Se intentó editar código de SQL Server.  
  
-   Se intentó editar código mientras se depuraba un volcado de memoria de Dr. Volcado de memoria de Watson.  
  
-   Se intentó editar código después de que se produjo una excepción no controlada y la opción "**desenredar la pila de llamadas en las excepciones no controladas**" no se ha seleccionado.  
  
-   Se intentó editar código mientras se depuraba una aplicación incrustada en tiempo de ejecución.  
  
-   Se intentó editar código en un programa que asoció, en lugar de a partir de la **depurar** menú.  
  
-   Se intentó editar código optimizado.  
  
-   Se intentó editar código administrado cuando el destino es una aplicación de 64 bits. Si desea utilizar la opción Editar y continuar, deberá establecer el destino en x86. (*Proyecto* **propiedades**, **compilar** ficha, **compilador avanzada** configuración.).  
  
-   Se intentó editar código en un ensamblado que se modificó durante la depuración y se ha vuelto ha cargar.  
  
-   Se intentó editar código en un ensamblado que no se ha cargado.  
  
-   Se inició la depuración de una versión anterior de la aplicación (ya que la nueva versión tenía errores de compilación).  
  
-   Se intentó editar código mientras se estaba ejecutando.  
  
## <a name="uielement-list"></a>Lista de UIElement  
 **VALE**  
 Sale del cuadro de diálogo y cancela el intento de edición inmediatamente anterior.  
  
## <a name="see-also"></a>Vea también  
 [Cambios admitidos en el código (C++)](../debugger/supported-code-changes-cpp.md)



